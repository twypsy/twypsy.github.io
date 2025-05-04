---
title: Crypto-failures - Tryhackme write-up
date: 2025-05-04
categories: [infosec]
tags: [codereview,tryhackme,scripting]
description: An interesting machine entailing code-review, cryptography, scripting, and problem-solving skills
---

## Introduction

I have done many rooms in Tryhackme along the years, yet none of them invited me to consider creating a write-up. 

This room was quite different from the others. Crypto-failures is a room that will require the user to conduct a code-review, research into cryptographic functions, develop a script to automate its exploitation, and overall, exercise problem-solving skills.

The idea of creating a write-up brought into the surface an older desire of mine regarding the creation of a blog. Therefore, this blog was created indirectly as a result of this room, something I am thankful for. Without further ado, let's proceed to hack this machine.


**Room**: [https://tryhackme.com/room/cryptofailures](https://tryhackme.com/room/cryptofailures)


## Port scan

Performing a port scan using [rust-scan](https://github.com/bee-san/RustScan) reveals ports 22 and 80 are open. 
As it might be seen on the second screenshot, said ports are associated with the SSH and HTTP services.
The exposed software, accordingly, is OpenSSH 8.9p1 and Apache 2.4.59.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/1.png)

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/2.png)

## First contact with the HTTP service

Upon accessing the HTTP service, we see a message warning us of 3 things:
* We are logged in as the guest user
* The cookie is protected with encryption
* A hint regarding **crypt** within the encryption word

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/3.png)

Checking the cookies within our browser, we can see 2 cookies:
* A cookie named user, with the value guest
* A cookie named secure_cookie

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/8.png)

One of the very first things we should do upon accesing a page, it's checking the source code. Sometimes, developers might leave comments as an internal note for themselves or others, which could lead to an information disclosure. Below, we see a note regarding the removal of backup files, with a .bak extension.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/4.png)

## Using ffuf for enumeration

[ffuf](https://github.com/ffuf/ffuf) is one of my favourite fuzzing tools, which I combine with wordlists from [Seclists](https://github.com/danielmiessler/SecLists). 

The following are my 3 preferred wordlists for web content discovery.

1. [quickhits](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/quickhits.txt)
2. [raft-large-files](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/raft-large-files.txt)
3. [raft-large-directories](https://github.com/danielmiessler/SecLists/blob/master/Discovery/Web-Content/raft-large-directories.txt)

If none of them work, you might need to dig deeper, trying different wordlists and file extension combinations. 

As we might see below, ffuf detected the presence of an index.php.bak file with the quickhits wordlist.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/5.png)


In case it didn't, we could have combined raft-large-files.txt wordlist with the .bak extension.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/6.png)

We can download the bak file using wget for further inspection.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/7.png)

## Code review

This is the whole content of the index.php.bak file for your reference, which we will proceed to analyze [bit by bit](https://youtu.be/lqlyPJXAjnc).

```
<?php
include "config.php";

function generate_cookie($user, $ENC_SECRET_KEY) {
    $SALT = generatesalt(2);
    $secure_cookie_string = $user . ":" . $_SERVER["HTTP_USER_AGENT"] . ":" . $ENC_SECRET_KEY;
    $secure_cookie = make_secure_cookie($secure_cookie_string, $SALT);

    setcookie("secure_cookie", $secure_cookie, time() + 3600, "/", "", false);
    setcookie("user", "$user", time() + 3600, "/", "", false);
}

function cryptstring($what, $SALT) {
    return crypt($what, $SALT);
}

function make_secure_cookie($text, $SALT) {
    $secure_cookie = "";

    foreach (str_split($text, 8) as $el) {
        $secure_cookie .= cryptstring($el, $SALT);
    }

    return $secure_cookie;
}

function generatesalt($n) {
    $randomString = "";
    $characters = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";

    for ($i = 0; $i < $n; $i++) {
        $index = rand(0, strlen($characters) - 1);
        $randomString .= $characters[$index];
    }

    return $randomString;
}

function verify_cookie($ENC_SECRET_KEY) {
    $crypted_cookie = $_COOKIE["secure_cookie"];
    $user = $_COOKIE["user"];
    $string = $user . ":" . $_SERVER["HTTP_USER_AGENT"] . ":" . $ENC_SECRET_KEY;
    $salt = substr($_COOKIE["secure_cookie"], 0, 2);

    if (make_secure_cookie($string, $salt) === $crypted_cookie) {
        return true;
    } else {
        return false;
    }
}

if (isset($_COOKIE["secure_cookie"]) && isset($_COOKIE["user"])) {
    $user = $_COOKIE["user"];

    if (verify_cookie($ENC_SECRET_KEY)) {
        if ($user === "admin") {
            echo "congrats: ******flag here******. Now I want the key.";
        } else {
            $length = strlen($_SERVER["HTTP_USER_AGENT"]);
            print "<p>You are logged in as " . $user . ":" . str_repeat("*", $length) . "\n";
            print "<p>SSO cookie is protected with traditional military grade en<b>crypt<b>ion\n";
        }
    } else {
        print "<p>You are not logged in\n";
    }
} else {
    generate_cookie("guest", $ENC_SECRET_KEY);
    header("Location: /");
}
?>
```

On a global level, we can see:
* 5 PHP functions
* 1 include
* 1 main block of code

### Include

PHP inclusion of a config.php file, which might contain sensitive configuration information.

Unfortunately for us, there's no config.php.bak file available.

```
<?php
include('config.php');
```

### Main block of code

The main block of code checks if there are 2 cookies defined as secure_cookie and user.
In case they were, execution continues to the next line of code within [snip].
Otherwise, the execution flow moves to the else statement, where a call to the generate_cookie function happens, along with a redirection to the main path. 

As the name implies, this function is used in order to generate the two aforementioned cookies within our browser.

```
if (isset($_COOKIE["secure_cookie"]) && isset($_COOKIE["user"])) {
   [snip]
} else {
    generate_cookie("guest", $ENC_SECRET_KEY);
    header("Location: /");
}
```

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/8.png)


The call to generate_cookie also makes reference to an ENC_SECRET_KEY variable, not defined within the index.php file. Therefore, it must have been defined within the included config.php file.


Returning to the snip of code, in case both cookies are defined, we see the user cookie is assigned to the variable user. 

Then, a call to the verify_cookie function happens, taking as an argument the secret key defined within the config.php file. If said function returns true, the execution flow continues, otherwise, we would get a printed messaged stating we are not logged in.


```
if (isset($_COOKIE["secure_cookie"]) && isset($_COOKIE["user"])) {    
    $user = $_COOKIE["user"];

    if (verify_cookie($ENC_SECRET_KEY)) {
        [snip]
    } else {
        print "<p>You are not logged in\n";
    }
}
```
Assuming the verify_cookie function returned true, there are 2 checks:

1. In case the username provided within the cookie is admin, the flag would be printed.


2. Otherwise, the **length** of the User-Agent header within our request would be assigned to the length variable. That variable would influence the number of asterisks printed in the message to the guest user, due to the [str_repeat](https://www.php.net/manual/en/function.str-repeat.php) function call.


```
if ($user === "admin") {
    echo "congrats: ******flag here******. Now I want the key.";
} else {
    $length = strlen($_SERVER["HTTP_USER_AGENT"]);
    print "<p>You are logged in as " . $user .  ":" . str_repeat("*", $length) ."\n";
    print "<p>SSO cookie is protected with traditional military grade en<b>crypt</b>ion\n";
}
```

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/3.png)

In consequence, if the User-Agent header consisted of one character, only an asterisk would be printed.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/10.png)


### Functions

#### function verify_cookie($ENC_SECRET_KEY)

The first 2 lines of the function will assign the values of the cookies to variables.

Then, a string will be generated consisting of 3 pieces:
* Username within the cookie
* User-Agent header
* The value of the secret key within config.php

The salt will be the first 2 chars of the secure_cookie cookie.

Finally, a strict comparison is made between the secure_cookie cookie (stored as $crypted_cookie), and the result of calling the make_secure_cookie function with the previously generated string and salt. Based on that comparison, the function will return either true or false.


```
function verify_cookie($ENC_SECRET_KEY){
    $crypted_cookie = $_COOKIE["secure_cookie"];
    $user = $_COOKIE["user"];
    $string = $user . ":" . $_SERVER["HTTP_USER_AGENT"] . ":" . $ENC_SECRET_KEY;
    $salt = substr($_COOKIE["secure_cookie"], 0, 2);

    if (make_secure_cookie($string, $salt) === $crypted_cookie) {
        return true;
    } else {
        return false;
    }
}
```

#### function generatesalt($n)

This function will generate a salt whose length is determined based on the argument provided as $n.

The number of iterations of the for loop is determined based on that value accordingly. Each iteration of the for loop will take a random index between 0, and the length of the string of characters minus one. Then, a random character will be picked based on that index, and appended to the randomString variable representing the salt.


```
function generatesalt($n){
    $randomString = "";

    $characters = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ";

    for ($i = 0; $i < $n; $i++) {
        $index = rand(0, strlen($characters) - 1);
        $randomString .= $characters[$index];
    }

    return $randomString;
}
```
#### function make_secure_cookie($text, $SALT)

The function make_secure_cookie, invoked within verify_cookie, will take a string and a salt as arguments.

A secure_cookie empty string is declared initially.

Then, the [str-split](https://www.php.net/manual/en/function.str-split.php) function will split the provided $text variable into chunks of 8 characters, represented as the $el variable within the foreach loop. On each iteration, the secure_cookie string will be appended the result of calling the cryptstring function with the 8 characters chunk ($el), and the salt.

In the end, the resulting cookie is returned.


```
function make_secure_cookie($text, $SALT){
    $secure_cookie = "";

    foreach (str_split($text, 8) as $el) {
        $secure_cookie .= cryptstring($el, $SALT);
    }

    return $secure_cookie;
}
```
#### function cryptstring($what, $SALT){

The cryptstring function is merely an alias for the PHP [crypt](https://www.php.net/manual/en/function.crypt.php) function, which will take as arguments the 8 characters chunk of text, along with a salt.

```
function cryptstring($what, $SALT){
    return crypt($what, $SALT);
}
```

As noted in the documentation, by default, the crypt function will return a hash using the DES algorithm.

> crypt() will return a hashed string using the standard Unix DES-based algorithm or alternative algorithms. password_verify() is compatible with crypt(). Therefore, password hashes created by crypt() can be used with password_verify(). 

But especially, there are two key facts to bear in mind:

* The first 2 characters of the hash represent the salt.
* It uses the first 8 characters of the string, even if longer strings were provided.

> The standard DES-based crypt() returns the salt as the first two characters of the output. It also only uses the first eight characters of string, so longer strings that start with the same eight characters will generate the same result (when the same salt is used). 

That's the reason why the string was divided into pieces of 8 characters.

#### function generate_cookie($user, $ENC_SECRET_KEY)

This is the initial function used to generate a cookie in case no cookie was provided by the user.

The first line of code will generate a salt of 2 characters.

Then, a string will be generated that combines:
* The username provided as an argument
* The user agent header, **which is under our control**
* The secret key defined within config.php

This resulting string is passed along with the salt to make_secure_cookie, which, as we saw earlier, will divide it into chunks of 8 characters length. Then, each portion will be passed to the PHP crypt function, eventually generating the final secure cookie.

The last 2 lines of code define the cookies within the browser, along with an expiration time of 1 hour (60 minutes * 60 seconds = 3600 seconds).

```
function generate_cookie($user, $ENC_SECRET_KEY){
    $SALT = generatesalt(2);
    $secure_cookie_string = $user . ":" . $_SERVER["HTTP_USER_AGENT"] . ":" . $ENC_SECRET_KEY;
    $secure_cookie = make_secure_cookie($secure_cookie_string, $SALT);

    setcookie("secure_cookie", $secure_cookie, time() + 3600, "/", "", false);
    setcookie("user", "$user", time() + 3600, "/", "", false);
}
```
### Recap

1. If no cookies are provided, new ones will be generated for the **guest** user.
```
if (isset($_COOKIE["secure_cookie"]) && isset($_COOKIE["user"])) {
   [snip]
} else {
    generate_cookie("guest", $ENC_SECRET_KEY);
    header("Location: /");
}
```
2. The verify_cookie function takes as an argument the encryption key, whose value (unknown to us), is defined within config.php.
3. We need to generate a valid cookie for the user admin in order to grab the flag.  Therefore, we need to obtain the encryption key to forge a valid cookie.
```
if (verify_cookie($ENC_SECRET_KEY)) {
      if ($user === "admin") {
         echo "congrats: ******flag here******. Now I want the key.";
      }
```
4. Within the verify_cookie function, the cookie named secure_cookie is compared to the result of invoking make_secure_cookie($string, $salt). If the strict string comparison returns true, we will be logged in as admin, and obtain the flag accordingly.
5. The $string argument is a result of concatenating 3 components:
* Username (guest by default)
* User-Agent header (under our control)
* Secret key
6. The value of the salt is within the first 2 chars of the secure_cookie string.
```
function verify_cookie($ENC_SECRET_KEY){
    $crypted_cookie = $_COOKIE["secure_cookie"];
    $user = $_COOKIE["user"];
    $string = $user . ":" . $_SERVER["HTTP_USER_AGENT"] . ":" . $ENC_SECRET_KEY;
    $salt = substr($_COOKIE["secure_cookie"], 0, 2);

    if (make_secure_cookie($string, $salt) === $crypted_cookie) {
        return true;
    } else {
        return false;
    }
}
```
7. The make_secure_cookie function will divide the string into chunks of 8 chars, which will be passed into the cryptstring function, alias of the native PHP crypt function.
8. The default implementation of the crypt function involves 2 core concepts:
* The first 2 characters of the resulting hash represent the salt
* It will take as input the first 8 characters of a string, even if the string is longer

```
function make_secure_cookie($text, $SALT){
    $secure_cookie = "";

    foreach (str_split($text, 8) as $el) {
        $secure_cookie .= cryptstring($el, $SALT);
    }

    return $secure_cookie;
}
```
## Script development

### Understanding the cookie verification process

_Example values_

```
$user = "guest"
$_SERVER["HTTP_USER_AGENT"] = "x"
$ENC_SECRET_KEY = "secret12"
$salt = "XD"
```

_Verify cookie function_
```
function verify_cookie($ENC_SECRET_KEY) {
    $crypted_cookie = $_COOKIE["secure_cookie"];
    $user = $_COOKIE["user"];
    $string = $user . ":" . $_SERVER["HTTP_USER_AGENT"] . ":" . $ENC_SECRET_KEY;
    $salt = substr($_COOKIE["secure_cookie"], 0, 2);

    if (make_secure_cookie($string, $salt) === $crypted_cookie) {
        return true;
    } else {
        return false;
    }
}
```

Based on the example values above, the resulting $string variable would be: 

```
$string = "guest:x:secret12"
```

The string and the salt would then be passed as arguments to the make_secure_cookie function. 

```
function make_secure_cookie($text, $SALT){
    $secure_cookie = "";

    foreach (str_split($text, 8) as $el) {
        $secure_cookie .= cryptstring($el, $SALT);
    }

    return $secure_cookie;
}
```

The str_split function would divide the string into pieces of 8 characters, resulting in 2 portions for our example.

1. guest:x:
2. secret12

Each of those portions, along with the salt, would be passed into the cryptstring function. As noted earlier, the cryptstring function is an alias for the native php crypt function. The resulting hashes may be found below accordingly. You may notice as well that the first 2 characters of the hashes represent the salt.
1. **XD**nXUFj3QXPLg
2. **XD**unhCekWZPpA

All the obtained hashes are concatenated into the final secure cookie.

Secure cookie: XDnXUFj3QXPLgXDunhCekWZPpA

Finally, the generated cookie is compared to the one provided by the user, returning either true or false.

Now, let's take a step back with our deeper understanding of the cookie verification process.

1. The cookie is a concatenation of hashes, resulting from chunks of 8 characters each.
2. The user value will be guest by default.
3. We don't know the secret.
4. The User-Agent header is **under our control**.

In consequence, we could use the User-Agent header as padding until the 8th position of the block is filled with a letter of the secret key. For example, if we used the User-Agent xxxxxxxx, the 2nd block would have at the 8th position an S belonging to the secret key.

1. guest:xx
2. xxxxxx:s
3. ecret12

If we debugged the make_secure_cookie function, each iteration of the foreach loop would work as follows:

_1st iteration_

* Input: guest:xx

* Hash: XDjZuoRhSt57.

_2nd iteraction_

* Input: xxxxxx:s

* Hash: XDtnxgXePUw2o

_3rd iteration_

* Input: ecret12

* Hash: XDD71hCT4HIXE

Final cookie: XDjZuoRhSt57.XDtnxgXePUw2oXDD71hCT4HIXE

Let's assume we didn't know the value of the 8th character within the 2nd chunk. How could we obtain it?

We have the following pieces of information:

* The first 7 characters of the block - xxxxxx:?
* The hash resulting from the 8 characters block, located within the cookie - XDD71hCT4HIXE
* The salt, represented by the first 2 characters of the hash (XD)

Therefore, we have all the components required to bruteforce the last 8th character of the block, using the crypt function to generate hashes until we find a valid one matching the hash located on the cookie. The pseudo-code logic would be as follows:

```
alph = "0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ"
hash = "XDtnxgXePUw2o"
salt = "XD"
str  = "xxxxxx:"

for c in alph:
   attempt = str + c
   if crypt(attempt,salt) == hash:
      bingo!
      break
```

Once a character of the secret key is obtained, we would continue using the User-Agent header as padding, until we got the next Nth character of the secret key to match the 8th position within a block.


### Development explained

#### Imports and custom variables

```
import string
import requests
import crypt
from urllib import unquote

url = "http://10.10.15.174"
user = "admin"
agent = "x"
```

#### Main function

Our main function will perform 3 steps:

1. Getting the encryption key (getKey)
2. Forging a cookie as the admin user (genCookie)
3. Getting the flag based on the created cookie (getFlag)

```
def main():
   print("Getting the key ...")
   key = getKey()
   cookie = genCookie(user,key)
   getFlag(cookie)

main()
```
#### getCookie

This function will allow us to retrieve the cookie associated with the **user agent provided as padding**.

```
def getCookie(agent):
   req = requests.session()
   headers = {"User-Agent": agent}
   response = req.get(url, headers=headers)
   cookies = req.cookies.get_dict()
   cookie = unquote(cookies["secure_cookie"]).decode("utf-8")

   return cookie
```

#### getKey

```
def getKey():
   alph = string.printable
   secret = ""

   for i in range(1,155):
      user = "guest"
      pad = 1

      while True:
        agent = "x" * pad
        attempt = secret + "*" + "-" * (154 - i)
        text = user + ":" + agent + ":" + attempt

        if ((text.find("*") + 1) % 8 == 0):
           original_cookie = getCookie(agent)
           salt = original_cookie[0:2]

           j = text.find("*")
           chunk = text[j-7: j]

           for c in alph:
              attempt = chunk + c
              hashed_chunk = crypt.crypt(attempt, salt)
              if hashed_chunk in original_cookie:
                 secret += c
                 break
           break

        pad += 1

   print("*" * 20)
   print("Key:" + secret)

   return secret
```

At first, we will declare an alph variable containing the whole range of characters, along with an empty secret variable.

```
def getKey():
   alph = string.printable
   secret = ""
```
Then, we will proceed to iterate on a range from 1 to 155, representing each character of the encryption key.

```
   for i in range(1,155):
```

The length of 154 was determined in a lazy/smart way based on the placeholder value for the key at Tryhackme.


![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/22.png)

```
placeholder="Answer format: ***{***********_***_******_**_******_***********_***_****_*********_**_***_****_**_*****_****************************************************************}"
```

**Note**: If we couldn't follow this approach, we would have simply compared the length of the secret obtained in the current iteration, with our earlier attempt. If the length remained the same, we know there are no more chars to be discovered.

```
def getKey():
   alph = string.printable
   secret = ""
   found = False
   i = 1

   while not found:
      user = "guest"
      pad = 1

      while True:
         agent = "x" * pad
         attempt = secret + "*" + "-" * (154 - i)
         text = user + ":" + agent + ":" + attempt

         if ((text.find("*") + 1) % 8 == 0):
            original_cookie = getCookie(agent)
            salt = original_cookie[0:2]

            j = text.find("*")
            chunk = text[j-7: j]
            origLen = len(secret)
            for c in alph:
               attempt = chunk + c
               hashed_chunk = crypt.crypt(attempt, salt)
               if hashed_chunk in original_cookie:
                  secret += c
                  break
            if origLen == len(secret):
               found = True
            else:
               i += 1
            break
         pad += 1

   print("*" * 20)
   print("Key:" + secret)

   return secret
```

Following our original, lazy/smart approach, the user variable contains the default guest user.

An initial pad of 1 was assigned, which will determine the length of the user agent header.

```
user = "guest"
pad = 1
```

A while true statement is used in order to find the right padding which will fill the 8th character with the secret key.

The attempt variable contains:
* The discovered parts of the secret
* An asterisk, used as a sign mark for the 7th block
* Dashes used to indicate the remaining parts of the secret not discovered yet

Then, the text variable will contain a concatenation of:
* The user (guest)
* The padded User-Agent
* The earlier attempt variable

This will allow us to recreate how the string is processed on the server side based on the provided padding.

```
while True:
    agent = "x" * pad
    attempt = secret + "*" + "-" * (154 - i)
    text = user + ":" + agent + ":" + attempt
```


If the asterisk position plus 1 can be divided by 8, it means the asterisk is located on the 7th character. 

Therefore, the padding is correct. Otherwise, the pad would be increased by one.

```
if ((text.find("*") + 1) % 8 == 0):
    [snip]
pad += 1
```

Afterwards, a cookie is retrieved based on the padded user agent.

The first 2 characters of the cookie represent the salt.

Using the index of the asterisk sign, which is located at the 7th position, we can extract the right chunk of 7 characters from the earlier text variable.

```
original_cookie = getCookie(agent)
salt = original_cookie[0:2]

j = text.find("*")
chunk = text[j-7: j]
```

Then, it would be a matter of iterating through all possible chars, computing the associated hashes until a valid **sub**string with the hash is found in the cookie. Once a valid char is obtained, it will be appended to the secret string, breaking out of the for loop. 

It should be noted that a second break was added in order to break free from the while loop.

This would allow the for loop to continue iterating through the characters of the secret key, leading eventually to the disclosure of the secret key.


```
for c in alph:
    attempt = chunk + c
    hashed_chunk = crypt.crypt(attempt, salt)
    if hashed_chunk in original_cookie:
        secret += c
        break
break

pad += 1

[snip]
print("Key:" + secret)
return secret
```

#### genCookie

Once the key is obtained, we can forge a cookie for any user by following the same process.

```
def genCookie(user,key):
   salt = "ab"
   agent = "x"
   text = user + ":x:" + key
   cookie = ""

   for i in range(0, len(text), 8):
      el = text[i:i+8]
      cookie += crypt.crypt(el, salt)

   print("*" * 20)
   print("Generating the cookie ...")
   print("User-Agent: " + agent)
   print("Cookie: secure_cookie=" + cookie + "; user=" + user)

   return cookie
```

#### getFlag

With an admin forged cookie, we can issue a request and obtain the flag.

```
def getFlag(cookie):
   cookies = {"secure_cookie":cookie,"user":user}
   headers = {"User-Agent":agent}
   resp = requests.get(url, headers = headers, cookies = cookies)

   print("*" * 20)
   print("Getting the flag content ...")
   print(resp.text)
   print("*" * 20)
```

### Exploitation

Final script: [cryptofailures.py](https://github.com/twypsy/tryhackme-scripts/blob/main/crypto-failures/cryptofailures.py)

**Note**: You will need to edit the URL variable on line 6 within the script in order to match the target machine.

![img-description](assets/img/posts/2025/2025-05-03-crypto-failures/20.jpg)

