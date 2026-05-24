---
title: Study notes for (C-AI/MLPen) and (C-AgAIPen) certifications
date: 2026-05-23
categories: [infosec,ai]
tags: [general,ai]
description: A curated list of learning resources
---

## Intro

Below you may find a curated list of the learning resources I used for the [Certified AI/ML Pentester
(C-AI/MLPen)](https://pentestingexams.com/certifications/professional/certified-ai-ml-pentester/) and [Certified Agentic AI Pentester (C-AgAIPen)](https://pentestingexams.com/certifications/professional/certified-agentic-ai-pentester/) certifications by The SecOps Group. These are the officially recommended resources, along with some additional ones I picked, properly organized and formatted to keep track of your progress.

<iframe width="560" height="315" src="https://www.youtube.com/embed/5I5dfI4SyLg?si=NL2qLQI9SOx03fwL&amp;start=22" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## Learning resources

### Theory 

- [Compromising LLMs using Indirect Prompt Injection](https://arxiv.org/pdf/2302.12173) 
- [LearnPrompting - Prompt Hacking](https://learnprompting.org/docs/prompt_hacking/introduction)
- OWASP
    - [Top 10 for LLM Applications 2025](https://genai.owasp.org/llm-top-10/)
    - [Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026/) (💡 Read the linked references at the end of each section)
- [Lakera: Real World LLM Exploits](https://lakera-marketing-public.s3.eu-west-1.amazonaws.com/Lakera%2BAI%2B-%2BReal%2BWorld%2BLLM%2BExploits%2B(Jan%2B2024)-min.pdf)
- Bugcrowd
  - [Ultimate Guide to AI Safety and Security](https://www.bugcrowd.com/wp-content/uploads/2024/04/Ultimate-Guide-AI-Security.pdf) 
  - [AI vulnerability deep dive: Prompt injection](https://www.bugcrowd.com/blog/ai-vulnerability-deep-dive-prompt-injection/) 
- Prompting Guide
  - [Retrieval Augmented Generation (RAG) for LLMs](https://www.promptingguide.ai/research/rag) 
  - [Adversarial Prompting in LLMs](https://www.promptingguide.ai/risks/adversarial)
- [Static code analysis on Top 10 for LLM Applications](https://github.com/HadessCS/Delta)
- [Simon Willison - Prompt injection explained, with video, slides, and a transcript](https://simonwillison.net/2023/May/2/prompt-injection-explained/)
- [Medium - Hacking LLMs with prompt injections](https://archive.ph/oTGX7#selection-259.0-264.0) 
- WithSecureLabs - Synthetic Recollections
   - [Article](https://labs.withsecure.com/publications/llm-agent-prompt-injection)
   - [Talk](https://www.youtube.com/watch?v=43qfHaKh0Xk)
- [NCC - Exploring prompt injection attacks](https://web.archive.org/web/20221205221210/https://research.nccgroup.com/2022/12/05/exploring-prompt-injection-attacks/)
- [LLM Pentest: Leveraging Agent Integration for RCE](https://www.blazeinfosec.com/post/llm-pentest-agent-hacking/) 
- [AI Village - Threat Modelling LLM Applications](https://web.archive.org/web/20230607042919/https://aivillage.org/large%20language%20models/threat-modeling-llm/): 
- [Pentesting LLMs](https://systemweakness.com/large-language-model-llm-pen-testing-part-i-2ef96acb6763) 
- [Snyk.io - Addressing Top 10 LLMs](https://go.snyk.io/rs/677-THP-415/images/owasp-top-10-llm.pdf)
- [Unite AI - Prompt Hacking and Misuse of LLMs](https://www.unite.ai/prompt-hacking-and-misuse-of-llm/?trk=article-ssr-frontend-pulse_little-text-block)
- [NVIDIA: AI Red Team - An introduction](https://developer.nvidia.com/blog/nvidia-ai-red-team-an-introduction/) 
- [Microsoft: Planning red teaming for large language models (LLMs) and their applications](https://learn.microsoft.com/en-us/azure/foundry/openai/concepts/red-teaming)
- [Cobalt: Prompt Injection Attacks](https://www.cobalt.io/learning-center/prompt-injection-attacks-overview) 
- [IBM - Prompt injection attacks](https://www.ibm.com/think/topics/prompt-injection#1696046959)

### Labs
- [Mock exams by The SecOps Group](https://pentestingexams.com/mock-pentesting-exams/)
- [Tryhackme: AI Learning Path](https://tryhackme.com/path/outline/aisecurity)
- [OWASP Prompt Me](https://owasp.org/www-project-promptme/)
- [Portswigger - Web LLM Attacks](https://portswigger.net/web-security/llm-attacks)
- Hackaprompt:
   - [Tutorial](https://www.hackaprompt.com/track/tutorial_competition)
   - [HackAPrompt 1.0](https://www.hackaprompt.com/track/hackaprompt_1.0_competition)
- [Immersive Labs](https://prompting.ai.immersivelabs.com) (⚠️ Slow)
- [Prompt Airlines](https://promptairlines.com)
- Gandalf by Lakera
   - [Password reveal](https://gandalf.lakera.ai/baseline)
   - [Agent Breaker](https://gandalf.lakera.ai/agent-breaker)

### Payloads
- [Payloads for attacking large language models](https://github.com/mik0w/pallms?tab=readme-ov-file)

### Compilations
- [LLMSecurity](https://llmsecurity.net)
- [Awesome-LLM](https://github.com/Hannibal046/Awesome-LLM)
- [Awesome-LLM-Security](https://github.com/corca-ai/awesome-llm-security)
- [Awesome-AI Security](https://github.com/ottosulin/awesome-ai-security)
- [Offensive ML Playbook](https://wiki.offsecml.com/Offensive+ML/Application+Security/Preparing+webpages+for+LLM+ingestion)

### Tools
- [Garak](https://github.com/NVIDIA/garak) 
- [Promptfoo](https://github.com/promptfoo/promptfoo)
- [Promptmap](https://github.com/utkusen/promptmap)