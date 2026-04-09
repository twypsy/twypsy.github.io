---
title: Notes on the Cyber Resilience Act (CRA)
date: 2026-04-10
categories: [learning,reviews]
tags: [CRA,compliance,legislation]
description: An overview of the Cyber Resilience Act (CRA)
---

## Intro

The [Cyber Resilience Act (CRA)](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R2847) is a legislative effort by the European Union in order to promote security by design on products with digital elements commercialized on the EU market, ensuring their adherence to a minimum set of cybersecurity requirements.

Most importantly, the legislation entails **notification obligations** for manufacturers if they become aware of an actively exploited vulnerability or severe incident having an impact on the security of products with digital elements.

A product with digital elements is defined as “a software or hardware product and its remote data processing solutions, including software or hardware components being placed on the market separately” - (Article 3(1)). This perspective considers not only the product as a whole, but also its individual components.

On this post, I will share my notes and thoughts after researching the following sources:

1. [Cyber Resilience Act (CRA)](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32024R2847)
2. [Draft Commission guidance on the Cyber Resilience Act - Annex - Ares(2026)2319816](https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/16959-Draft-Commission-guidance-on-the-Cyber-Resilience-Act_en)
3. [Cyber Resilience Act implementation - Frequently asked questions](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions)

## Timeline

From **11 September 2026**, manufacturers must comply with the notification requirements outlined by the Cyber Resilience Act, notifying any actively exploited vulnerability or severe incident having an impact on the security of products with digital elements (PDE) via the single reporting platform.

The regulation will then be fully applied from **11 December 2027**.

Therefore, the CRA will start gaining relevance in the upcoming months from a notification perspective.

![CRA Timeline](/assets/img/posts/2026/2026-04-07-cra/cra-timeline-eu.png)

>Reporting obligations laid down in Article 14 apply from 11 September 2026. As of that date, manufacturers are required to notify actively exploited vulnerabilities and severe incidents having an impact on the security of their products with digital elements via the single reporting platform.

>The obligations of manufacturers to ensure that products with digital elements are in conformity with the essential cybersecurity requirements set out in Annex I, the provisions on market surveillance and enforcement, as well as all the other provisions set out in the CRA, apply from 11 December 2027.

Source: [European Commission](https://digital-strategy.ec.europa.eu/en/factpages/cyber-resilience-act-implementation)

## Risk evaluation criteria

Source: [Draft Guidance - Annex - Ares(2026)2319816](https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/16959-Draft-Commission-guidance-on-the-Cyber-Resilience-Act_en)

>In organisational risk management, risks are commonly evaluated against acceptance criteria derived from the organisation’s internal objectives or risk appetite. 
>
>By contrast, under the CRA, residual cybersecurity risk is assessed against a regulatory threshold: the product placed on the market needs to ensure an appropriate level of cybersecurity based on the risks, taking into account its intended purpose and reasonably foreseeable use.

Manufacturers may have their own risk evaluation criteria, but overall, they need to comply with the minimum security requirements outlined by the Cyber Resilience Act.

>Accordingly, the manufacturer’s internal risk tolerance, commercial strategy or cost considerations are not relevant in determining whether the essential cybersecurity requirements are met. 
>
>For the purposes of Articles 13(2) and (3), manufacturers must be in a position to determine whether identified cybersecurity risks have been sufficiently addressed to meet the essential requirements of Part I of Annex I, in light of the product’s intended purpose, reasonably foreseeable use and conditions of use, including, where relevant, the operational environment and the assets to be protected, taking into account the length of time the product is expected to be in use.
>
>[…]
>
>Considerations relating solely to cost or commercial feasibility do not constitute sufficient grounds for leaving such risks untreated where this would prevent the product from meeting the essential cybersecurity requirements.”

In the past, a manufacturer may have accepted a vulnerable behaviour due to a greater risk appetite, as part of a commercial strategy in order to rush a market release, or simply because the implementation costs were higher than the security benefits. 

The CRA turns the tables since those arguments can no longer be held if the essential cybersecurity requirements aren't met.

___

Source: [Cyber Resilience Act implementation - Frequently asked questions](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions)

>The CRA does not mandate a specific cybersecurity risk assessment methodology.
>
>The manufacturers can decide on the methodology they use to identify and treat the relevant risks.
>
>Manufacturers need to address all relevant risks emerging from the cybersecurity risk assessment, and the risk assessment methodology should therefore support manufacturers in documenting that this has been done (in accordance with Article 13(3)), allowing market surveillance authorities to verify how risks have been identified, evaluated and mitigated.
>
>[Reference to Article 13.3]
>
>"3. The cybersecurity risk assessment shall be documented and updated as appropriate during a support period to be determined in accordance with paragraph 8 of this Article. […]”

As stated before, manufacturers can use their own cybersecurity assessment methodology to identify and treat relevant risks. Yet, it’s emphasized that the result of those assessments should be documented, in order to demonstrate compliance with article 13.3.

## Integrated components

Source: [Draft Guidance - Annex - Ares(2026)2319816](https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/16959-Draft-Commission-guidance-on-the-Cyber-Resilience-Act_en)

>Due diligence relates to elements that form part of the product itself, in particular integrated software or hardware components provided by a third-party. Manufacturers are required to take appropriate measures to ensure that such components do not undermine the product’s compliance with the essential cybersecurity requirements.
>
>This can only be achieved by determining what the product requires from its components in order to meet its cybersecurity objectives, and verifying, in a risk-based manner, that those components are in line with the product’s needs, as also indicated in recital 34”

CRA considers the product with digital elements (PDE) as a whole, as well as the 3rd party components that integrate it, which can be:
1. Software or hardware in nature.
2. Proprietary or open source from an ownership perspective.

Accordingly, manufacturers need to ensure that the components integrated within the product don’t undermine its security, so that it still meets the minimum essential requirements outlined in the act.

>Components that are physically or logically inside the product but supplied by a third party must also be considered as part of the risk assessment.
>
>However, for compliance purposes these are treated as external inputs whose external properties must be verified upon integration through due diligence, as they cannot be re-designed or re-developed by the manufacturer”

I could be wrong, but I personally found this remark to be quite confusing, given that 3rd-party open source software components could be precisely re-designed in order to fit the intended usage and security criteria of the implementer.

___

Source: [Cyber Resilience Act implementation - Frequently asked questions](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions)

>5.4 If an actively exploited vulnerability is contained in a third-party component, are all manufacturers integrating that component required to notify it?
>
>[…] A manufacturer shall notify any actively exploited vulnerability contained in the product with digital elements that it becomes aware of (Article 14(1))
>
>Manufacturers are required to notify any actively exploited vulnerability contained in their product with digital elements.
>
>Where the product with digital elements contains an actively exploited vulnerability originating from an integrated component, the manufacturer of the product with digital elements is required to notify that vulnerability.
>
>The manufacturer of the integrated component is also required to notify it, if that component has been placed on the market.
>
>If the manufacturer of a product with digital elements is aware that an integrated component contains a vulnerability, but that vulnerability cannot be exploited in its product with digital elements, that vulnerability is not actively exploited, and therefore it is not subject to mandatory reporting.
>
>Manufacturers can still notify that vulnerability on a voluntary basis, in accordance with Article 15, and are required to report the vulnerability to the person or entity manufacturing or maintaining the component, in accordance with Article 13(6).

1. Manufacturers shall report actively exploited vulnerabilities within their products with digital elements, including those arising from 3rd party components.

2. The manufacturer of the 3rd party component is required to notify that vulnerability as well (assuming awareness of it), in case the affected component is commercially available on the market.

3. While a component could contain a vulnerability, it might not be exploitable on the product with digital elements. In such case, reporting to ENISA and the designated CSIRT is not mandatory, given that there’s no active exploitation in place.<br>However, the manufacturer is still required to notify the vulnerability in the component to the person or entity manufacturing or maintaining that component. And in case a fix might have been developed by the manufacturer, it should be shared as part of the notification as well.

## Reporting obligations

Source: [Draft Guidance - Annex - Ares(2026)2319816](https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/16959-Draft-Commission-guidance-on-the-Cyber-Resilience-Act_en)

>Under Article 14(1) and (3) of the CRA, a manufacturer is required to notify simultaneously to the CSIRT designated as coordinator and to ENISA of (i) any actively exploited vulnerability contained in its product that it becomes aware of; and (ii) any severe incident having an impact on the security of the product that it becomes aware of.

Based on the above statement, the following conditions are to be met:

1. Manufacturers need to be aware of an impact affecting the security of the product.

2. Two kind of events should be reported:
    1. Actively exploited vulnerabilities
    2. Severe incidents having an impact on the security of the product

3. Notification should be sent to both ENISA and the CSIRT designated as coordinator.

>In some cases, a manufacturer will detect a suspicious event, or a third party, such as an individual, a customer, an entity, an authority, a media organisation or other source will bring a potential incident or vulnerability to its attention.

1. The detection and reporting could be done by the manufacturer and a third party:
    1. Individuals
    2. Customers
    3. Entities
    4. Authorities
    5. Media organisations
    6. Other sources

2. The security impact could be due to:
    1. An event on the potential or suspicious stage.
    2. A potential vulnerability, non-associated to a real event, thus falling into the theoretical realm, which would be in line with security research.

>"In such cases, the manufacturer should assess the suspicious event immediately to determine whether it constitutes an actively exploited vulnerability or a severe incident having an impact on the security of the product."
>
>
>"However, the emphasis should be on prompt action to carry out the initial assessment to determine whether such conditions are indeed met, particularly where the vulnerability may pose a significant risk, and if so, to take remedial action and notify in accordance with the CRA."
>
>"The manufacturer is therefore to be regarded as having become aware when, after such an initial assessment, it has a reasonable degree of certainty that: (i) a vulnerability contained in its product is being actively exploited; or (ii) a severe incident has occurred and has led to the security of its product being compromised.”

On both cases, the legislation prompts the manufacturer to assess the detected or reported issue immediately, in order to determine if it qualifies as an active exploited vulnerability or a severe incident which should be notified according to the CRA.

Once the manufacturer determines there’s an actively exploited vulnerability or a severe incident, the manufacturer should then fulfill the notification requirements.

>In particular, manufacturers are required to submit an early warning notification containing limited information without undue delay and in any event within 24 hours of becoming aware.
>
>Additional information is subsequently required as part of the notification to be submitted without undue delay and in any event within 72 hours of becoming aware (’72-hour notification’).
>
>The complete report needs to be submitted within 14 days after a corrective or mitigating measure is available for actively exploited vulnerabilities, or within one month after the 72-hour notification for severe incidents.

The notification chain entails 3 steps:
1. An early-warning notification within 24-hours of becoming aware, based on the conducted assessment, of an active exploitation or severe incident.
2. An additional information notification within 72-hours
3. A final report notification with the following deadlines:
    1. 14 days for actively exploited vulnerabilities, once a corrective or mitigating measure is in place.
    2. One month after the additional information notification for severe incidents.

>After becoming aware of an actively exploited vulnerability or a severe incident, manufacturers are required, in accordance with Article 14(8), to inform impacted users and, where appropriate, all users. Where they fail to do so in a timely manner, the CSIRTs that received the notification may provide such information to users when this is considered proportionate and necessary to prevent or mitigate the impact of that vulnerability or incident.

The user base, either as a whole or just the affected parts of it, should be notified of any active exploited vulnerability or severe incident. Additionally, if a manufacturer doesn’t inform users on time, the CSIRT might step in by notifying users.

## Vulnerability handling

Source: [Draft Guidance - Annex - Ares(2026)2319816](https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/16959-Draft-Commission-guidance-on-the-Cyber-Resilience-Act_en)

>Article 13(6) of the CRA requires manufacturers to report vulnerabilities in integrated components to the person or entity manufacturing or maintaining that component (‘reporting upstream’).
>
>Manufacturers are required to report upstream only in respect of the version of the component that they integrate.
>
>Furthermore, manufacturers are required to report upstream only those vulnerabilities that exist in the integrated component itself, and not vulnerabilities that exist as result of the integration between the component and other code developed by the manufacturer or by the integration of other components.

The Cyber Resilience Act requires manufacturers to report vulnerabilities within 3rd party components to the person or entity responsible for that component, as long as the following conditions are met:

1. The vulnerable behavior leading to a security impact should be a result of the component integration.

2. Only vulnerabilities affecting the current version being used.

The regulator wants to remove the obligation of reporting any vulnerable behavior that might be a result of an interaction between the 3rd party component and custom code developed by the manufacturer, or due to interaction with other integrated components.

From my perspective, this entails conceiving security as an “all or nothing”, where manufacturers should only report a vulnerability affecting a 3rd party component as long as it can be 100% attributed to the integration of that component.

Still, it misses the point that there might be a vulnerable and valid behavior within a 3rd party component, and the responsibility could be split between that component, and the custom code implementation or other components.

>Finally, manufacturers are also not required to report the vulnerability upstream where the component no longer has a maintainer, or when the manufacturer has itself duplicated (‘forked’) the free and open-source component and no longer relies on the original maintainer for new versions or security fixes.

Accordingly, manufacturers won’t be required to report 3rd party vulnerabilities as long as the component no longer has a maintainer (which could be the case for deprecated and unmaintained software), or when working on a forked version.

>Furthermore, under Article 13(6) manufacturers that have developed a software modification to address a vulnerability in an integrated component are required to share that software modification (‘security fix’) with the person or entity manufacturing or maintaining the component (‘sharing upstream’).

Additionally, if a manufacturer develops a fix for a vulnerability within a 3rd party component, the fix must be shared with the entity or individual responsible for that component.

___

Source: [Cyber Resilience Act implementation - Frequently asked questions](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions)

>4.3.1 Are manufacturers required to patch all vulnerabilities that are discovered during the support period?”
>
>Manufacturers of products with digital elements shall […] in relation to the risks posed to products with digital elements, address and remediate vulnerabilities without delay, including by providing security updates (Annex I, Part II, point 2).
>
>The CRA does not require manufacturers to provide a patch for all vulnerabilities that are discovered during a product’s support period. When discovering a vulnerability, manufacturers are expected to determine its relevance for their product, and assess the resulting risk, in the framework of the manufacturer’s risk assessment.
>
>Depending on the risk, remedies may take different forms, including but not limited to immediate patches, advisories on workarounds to be later complemented by a software updates, updates to user manuals, configuration guidance to disable the affected features.

Several conclusions might be extracted from the above answer:
1. Manufacturers might assess a security risk based on their severity framework
2. The assessed risk will provide guidance on the remediation measure to be applied, whether that’s a software security patch, an advisory, a documentation update, or other remediation measures.
3. All security risks need to be properly addressed and remediated in order to comply with the essential security requirements outlined by the Cyber Resilience Act. The manufacturer can’t reject a security fix from a cost or severity perspective. 

If there’s a risk, it needs to be remediated, but not necessarily with a software patch, like the example below.

>Finally, a manufacturer of an office laser printer discovers that the printer’s motherboard has a debugging interface that remains enabled.
>
>While the vulnerability could theoretically be exploited to bypass authentication and inject malicious code, exploiting the vulnerability requires physical access to the printer, breaking its tamper-evident seal, disassembling internal components and soldering to the motherboard.
>
>The manufacturer’s risk assessment shows that the vulnerability presents a very low risk and has no exploitability in its operational environment. **The manufacturer may be expected, for example, to document the vulnerability, update its technical documentation and provide appropriate recommendations to its users.**

## What's an exploitable vulnerability?

Source: [Draft Guidance - Annex - Ares(2026)2319816](https://ec.europa.eu/info/law/better-regulation/have-your-say/initiatives/16959-Draft-Commission-guidance-on-the-Cyber-Resilience-Act_en)

>[…] products must be made available on the market without known exploitable vulnerabilities. Article 3(41) defines ‘exploitable vulnerability’ as ‘a vulnerability that has the potential to be effectively used by an adversary under practical operational conditions’.”

The earlier statement reinforces the interpretation that the CRA conceives not only active exploitation events, whether those are deemed as actively exploited vulnerabilities or severe incidents, but also potential ones, in the line of security research or responsible disclosure.

>The CRA requires manufacturers to have appropriate policies and procedures to handle and remediate potential vulnerabilities reported from internal or external sources (Article 13(8)).

This is further reinforced by recognizing manufacturers should consider reports coming from internal sources, and external sources, along with the potential reference. In consequence, the regulator acknowledges the contributions of security researchers to manufacturers’ security.

>However, it does not explicitly specify when an exploitable vulnerability should be considered to be known by the manufacturer, thereby triggering the obligation to comply with this essential requirement at the moment of placement on the market.
>
>An exploitable vulnerability should be regarded as known when it is listed in relevant publicly accessible vulnerability databases, such as the European vulnerability database established by Article 12(2) of Directive (EU) 2022/2555 or other prominent vulnerability databases, such as the Common Vulnerability and Exposures (CVE) List maintained by the MITRE Corporation.
>
>Additionally, an exploitable vulnerability may also be known when the manufacturer has been made aware of it via non-public information, for example via coordinated disclosure by a security researcher or through the manufacturer’s own internal testing and analysis.
>
>Likewise, an exploitable vulnerability may be known when it has been publicly and prominently reported in reliable media outlets, including specialized cybersecurity publications or general mass media.

The regulator admits that the CRA doesn’t specify when the manufacturer should be considered as aware of an exploitable vulnerability, providing then a list of case-scenarios:

1. If the vulnerability is listed under a publicly accessible vulnerability database
2. **A coordinated disclosure sent by a security researcher**
3. Internal tests conducted by the manufacturer
4. Vulnerabilities reported on the media

>Not all vulnerabilities are exploitable under practical operational conditions, and some vulnerabilities can only be exploited in theoretical conditions (e.g. in a lab or in a simulation) and/or not under conditions which would occur in a product’s operational environment.

Additionally, the regulator admits certain vulnerabilities might only be exploitable under certain circumstances.

>Nevertheless, the mere fact that a vulnerability is reported as exploitable does not, in itself, mean that it is exploitable in practice or applicable to the specific product concerned. The manufacturer will need to investigate it and confirm the veracity of such information and applicability to its own product.
>
>Accordingly, a limited period of time may elapse between the first report of the vulnerability and its confirmation. As indicated in Section 9.1 On reporting obligations, the emphasis should be on prompt action to investigate and react.
>
>[Section 9.1 Reference]
>However, the emphasis should be on prompt action to carry out the initial assessment to determine whether such conditions are indeed met, particularly where the vulnerability may pose a significant risk, **and if so, to take remedial action and notify in accordance with the CRA**

Vulnerabilities <u>reported as exploitable</u> need to undergo proper validation before being considered as truly exploitable. Then, if valid, the manufacturer should be considered as aware, thus being required to fulfill the reporting obligations to ENISA and CSIRT.

___

Source: [Cyber Resilience Act implementation - Frequently asked questions](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions)

>5.1 How can a manufacturer become aware of an actively exploited vulnerability or a severe incident?
>
>The CRA does not specify how a manufacturer is to become aware of an actively exploited vulnerability or a severe incident, but rather imposes the obligation to notify in accordance with Articles 14 once it does.
>
>[…]
>
>A manufacturer may also become aware via threat intelligence reports, e.g. security researchers or cybersecurity firms publish reports detailing a zero-day vulnerability (i.e. a vulnerability for which a patch or a security update is not yet available) in the manufacturer’s product being used in targeted attacks.
>
>[…]. Ethical hackers may also report a vulnerability that is already being exploited in the wild.

The regulator confirms that security researchers and ethical hackers may disclose zero-day vulnerabilities **being exploited in the wild**, affecting the manufacturer’s product, thus fitting the category of actively exploited vulnerabilities which should be notified.

>5.2 Does a manufacturer need to report zero-day vulnerabilities?
>
>Vulnerabilities for which a patch or a security update is not yet available (so-called ‘zero-day vulnerabilities’) are subject to reporting in accordance with Article 14, when the manufacturer has reliable evidence that a malicious actor has exploited that vulnerability.
>
>For example, a zero-day vulnerability discovered by ethical hackers, for which there is no evidence of previous malicious exploitation, and which is disclosed to the product’s manufacturer as part of its bug-bounty programme (see Recital 76) is not an actively exploited vulnerability subject to mandatory reporting.
>
>[…] Manufacturers may still notify those vulnerabilities on a voluntary basis, in accordance with Article 15.
>
>[Reference - Recital 68]
>
>“Vulnerabilities that are discovered with no malicious intent for purposes of good faith testing, investigation, correction or disclosure to promote the security or safety of the system owner and its users should not be subject to mandatory notification.”

Moreover, security researchers might report vulnerabilities **outside of an active exploitation scenario**. Those won’t be subject to the notification obligations outlined on article 14, still, organisations might choose to report them voluntarily.

In conclusion, there are 2 possible outcomes for responsible disclosures:

1. If the reported vulnerability is not part of an active exploitation scenario within a manufacturer’s product, the mandatory reporting of article 14 doesn’t apply.

2. However, if a security researcher demonstrated not only a zero-day vulnerability, but an active exploitation behavior as well, notifications to the responsible CSIRT and ENISA are definitely required.

## Comments on Cyber Resilience Act regulation

Source: [Regulation (EU) 2024/2847 of the European Parliament and of the Council of 23 October 2024 on horizontal cybersecurity requirements for products with digital elements and amending Regulations (EU) No 168/2013 and (EU) 2019/1020 and Directive (EU) 2020/1828 (Cyber Resilience Act) (Text with EEA relevance)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng)

>(68)
>
>[…] Vulnerabilities that are discovered with no malicious intent for purposes of good faith testing, investigation, correction or disclosure to promote the security or safety of the system owner and its users should not be subject to mandatory notification.

The CRA regulation states on recital 68 that any vulnerability discovered as a result of a coordinated responsible disclosure, shouldn’t be subject to mandatory notification to the designated CSIRT and ENISA.

However, it must be noticed that if a vulnerability disclosed to a manufacturer of a product with digital elements is associated with an active exploitation event, the manufacturer shall notify the designated CSIRT and ENISA, complying with the notification requirements accordingly.

>(74)
>
>[...]Manufacturers and other natural and legal persons should be able to notify to a CSIRT designated as coordinator or ENISA, on a voluntary basis, any vulnerability contained in a product with digital elements, cyber threats that could affect the risk profile of a product with digital elements, any incident having an impact on the security of the product with digital elements as well as near misses that could have resulted in such an incident.

1. Vulnerabilities can be reported to CSIRT or ENISA not only to comply with notification requirements, but also on a voluntary basis as well.

2. Security researchers will have up to 3 channels to report any vulnerability:
    1. Manufacturer
    2. CSIRT
    3. ENISA

3. Implicitly, a vulnerability reported directly to a manufacturer which was deemed originally as invalid, could be reviewed again upon notification to CSIRT and ENISA. This definitely reduces the likelihood of valid vulnerabilities being rejected by introducing new actors into the equation.<br>Therefore, it’s fair to assume CSIRT and ENISA will perform a minimum review of reported vulnerabilities, which combined with the fact that an external public entity is contacting the manufacturer, it should prompt the manufacturer for a double-check.

>(75)
>
>Member States should aim to address, to the extent possible, the challenges faced by vulnerability researchers, including their potential exposure to criminal liability, in accordance with national law.
>
>Given that natural and legal persons researching vulnerabilities could in some Member States be exposed to criminal and civil liability, Member States are encouraged to adopt guidelines as regards the non-prosecution of information security researchers and an exemption from civil liability for their activities.

The regulator encourages Member States to protect security researchers from criminal liability, assuming good faith on their activities.

>(76)
>
>[…] Given the fact that information about exploitable vulnerabilities in widely used products with digital elements can be sold at high prices on the black market, manufacturers of such products should be able to use programmes, as part of their coordinated vulnerability disclosure policies, to incentivise the reporting of vulnerabilities by ensuring that individuals or entities receive recognition and compensation for their efforts. This refers to so-called ‘bug bounty programmes’”

Recital 76 highlights the importance of bug bounty programs in order to reward researchers efforts as part of coordinated vulnerability disclosure policies, which seems like a step in the right direction for cybersecurity.

>Article 13 - Obligations of Manufacturers
>
>[…] 5.- For the purpose of complying with paragraph 1, manufacturers shall exercise due diligence when integrating components sourced from third parties so that those components do not compromise the cybersecurity of the product with digital elements, including when integrating components of free and open-source software that have not been made available on the market in the course of a commercial activity.
>
> 6.- Manufacturers shall, upon identifying a vulnerability in a component, including in an open source-component, which is integrated in the product with digital elements report the vulnerability to the person or entity manufacturing or maintaining the component, and address and remediate the vulnerability in accordance with the vulnerability handling requirements set out in Part II of Annex I. 
>
>Where manufacturers have developed a software or hardware modification to address the vulnerability in that component, they shall share the relevant code or documentation with the person or entity manufacturing or maintaining the component, where appropriate in a machine-readable format.

1. Regulation considers the product with digital elements as a whole, as well as the integrated components from third parties.

2. Components can be commercial, as well as free and open-source.

3. Vulnerabilities in a component shall be reported to the person or entity maintaining or manufacturing that component. In case a fix was developed by the product manufacturer, it must be shared as well.

>Article 14 - Reporting obligations of Manufacturers
>
>"1. A manufacturer shall notify any actively exploited vulnerability contained in the product with digital elements that it becomes aware of simultaneously to the CSIRT designated as coordinator, in accordance with paragraph 7 of this Article, and to ENISA. The manufacturer shall notify that actively exploited vulnerability via the single reporting platform established pursuant to Article 16.”
>
>“[…] 3. A manufacturer shall notify any severe incident having an impact on the security of the product with digital elements that it becomes aware of simultaneously to the CSIRT designated as coordinator, in accordance with paragraph 7 of this Article, and to ENISA. The manufacturer shall notify that incident via the single reporting platform established pursuant to Article 16.”

Manufacturers shall notify actively exploited vulnerabilities (1) or severe incidents (2) impacting the security of the product with digital elements they become aware of.

>Article 14 - Reporting obligations of Manufacturers
>
>**[Actively Exploited Vulnerabilities]**
>
>“2. For the purposes of the notification referred to in paragraph 1, the manufacturer shall submit:
>
>(a) **an early warning notification of an actively exploited vulnerability, without undue delay and in any event within 24 hours of the manufacturer becoming aware of it**, indicating, where applicable, the Member States on the territory of which the manufacturer is aware that their product with digital elements has been made available;
>
>(b) **unless the relevant information has already been provided, a vulnerability notification, without undue delay and in any event within 72 hours of the manufacturer becoming aware of the actively exploited vulnerability**, which shall provide general information, as available, about the product with digital elements concerned, the general nature of the exploit and of the vulnerability concerned as well as any corrective or mitigating measures taken, and corrective or mitigating measures that users can take, and which shall also indicate, where applicable, how sensitive the manufacturer considers the notified information to be;
>
>(c) **unless the relevant information has already been provided, a final report, no later than 14 days after a corrective or mitigating measure is available, including at least the following**:
>
>- (i) a description of the vulnerability, including its severity and impact;
>
>- (ii) where available, information concerning any malicious actor that has exploited or that is exploiting the vulnerability;
>
>- (iii) details about the security update or other corrective measures that have been made available to remedy the vulnerability.”
>
>**[Severe Incidents]**
>
>4.- For the purposes of the notification referred to in paragraph 3, the manufacturer shall submit:
>
>(a) **an early warning notification of a severe incident having an impact on the security of the product with digital elements, without undue delay and in any event within 24 hours of the manufacturer becoming aware of it**, including at least whether the incident is suspected of being caused by unlawful or malicious acts, which shall also indicate, where applicable, the Member States on the territory of which the manufacturer is aware that their product with digital elements has been made available;
>
>
>(b) **unless the relevant information has already been provided, an incident notification, without undue delay and in any event within 72 hours of the manufacturer becoming aware of the incident**, which shall provide general information, where available, about the nature of the incident, an initial assessment of the incident, as well as any corrective or mitigating measures taken, and corrective or mitigating measures that users can take, and which shall also indicate, where applicable, how sensitive the manufacturer considers the notified information to be;
>
>(c) **unless the relevant information has already been provided, a final report, within one month after the submission of the incident notification under point (b)**, including at least the following:
>- (i) a detailed description of the incident, including its severity and impact;
>
>- (ii) the type of threat or root cause that is likely to have triggered the incident;
>
>- (iii) applied and ongoing mitigation measures.

The notification timeline should be the following for both cases:

1. An early warning notification without undue delay, and at most within 24 hours of the manufacturer becoming aware.

2. An additional notification, unless the information was already provided, within 72 hours of the manufacturer becoming aware. This is definitely a tight deadline, since it should include information concerning corrective or mitigating measures taken.

3. A final report, unless the information was already provided, with the following deadlines:
    1. 14 days after a corrective or mitigating measure is available for an actively exploited vulnerability
    2. 1 month after the severe incident additional notification

>Article 14 - Reporting obligations of Manufacturers
>
>“5. For the purposes of paragraph 3, **an incident having an impact on the security of the product with digital elements** shall be considered to be severe where:
>
>(a) it negatively affects or is capable of negatively affecting the ability of a product with digital elements to protect the availability, authenticity, integrity or confidentiality of sensitive or important data or functions; or
>
>(b) it has led or is capable of leading to the introduction or execution of malicious code in a product with digital elements or in the network and information systems of a user of the product with digital elements.”
>
>Article 3 - Definitions
>
>(43) ’incident’ means an incident as defined in Article 6, point (6), of Directive (EU) 2022/2555;
>
>(44) ’incident having an impact on the security of the product with digital elements’ means an incident that negatively affects or is capable of negatively affecting the ability of a product with digital elements to protect the availability, authenticity, integrity or confidentiality of data or functions;
>
><u>[Directive (EU) 2022/2555]</u>
>
>Article 6 - Definitions
>
>(6) ‘incident’ means an event compromising the availability, authenticity, integrity or confidentiality of stored, transmitted or processed data or of the services offered by, or accessible via, network and information systems.

1. An incident, based on Directive EU 2022/2555 is an event compromising the CIA triad, thus denoting current exploitation.

2. The CRA regulation expands the definition on article 3-(44) by including incidents capable of negatively affecting the availability, authenticity, integrity or confidentiality of data or functions, thus falling into the theoretical realm.

Let’s take a step back to review the stance of the regulator in regards to security research.

____

Source: [Cyber Resilience Act implementation - Frequently asked questions](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions)

>5.1 How can a manufacturer become aware of an actively exploited vulnerability or a severe incident?
>
>The CRA does not specify how a manufacturer is to become aware of an actively exploited vulnerability or a severe incident, but rather imposes the obligation to notify in accordance with Articles 14 once it does.
>
>[…]
>**A manufacturer may also become aware via threat intelligence reports, e.g. security researchers or cybersecurity firms publish reports detailing a zero-day vulnerability (i.e. a vulnerability for which a patch or a security update is not yet available) in the manufacturer’s product being used in targeted attacks.**
>
>[…]. Ethical hackers may also report a vulnerability that is already being exploited in the wild.

>5.2 Does a manufacturer need to report zero-day vulnerabilities?
>
>Vulnerabilities for which a patch or a security update is not yet available (so-called ‘zero-day vulnerabilities’) are subject to reporting in accordance with Article 14, when the manufacturer has reliable evidence that a malicious actor has exploited that vulnerability.
>
>For example, **a zero-day vulnerability discovered by ethical hackers, for which there is no evidence of previous malicious exploitation, and which is disclosed to the product’s manufacturer as part of its bug-bounty programme (see Recital 76) is not an actively exploited vulnerability subject to mandatory reporting.**
>
>[…] Manufacturers may still notify those vulnerabilities on a voluntary basis, in accordance with Article 15.
>
>[Reference - Recital 68]
>“Vulnerabilities that are discovered with no malicious intent for purposes of good faith testing, investigation, correction or disclosure to promote the security or safety of the system owner and its users should not be subject to mandatory notification.”

Therefore, for the regulator, there are only 2 possibilities from a security research perspective:

A. Vulnerabilities being exploited on the wild, which must be notified to CSIRT and ENISA.

B. Vulnerabilities with no evidence of previous malicious exploitation, not subject to mandatory reporting **since they don’t qualify as an actively exploited vulnerability**.

The problem is that a vulnerability without evidence of previous malicious exploitation should qualify as an incident capable of negatively affecting the CIA triad, thus being considered as a severe incident. Yet, the regulator denies the possibility of this scenario.

>Article 15 Voluntary reporting
>
>1.- Manufacturers as well as other natural or legal persons may notify any vulnerability contained in a product with digital elements as well as cyber threats that could affect the risk profile of a product with digital elements on a voluntary basis to a CSIRT designated as coordinator or ENISA.
>
>2.- Manufacturers as well as other natural or legal persons may notify any incident having an impact on the security of the product with digital elements as well as near misses that could have resulted in such an incident on a voluntary basis to a CSIRT designated as coordinator or ENISA.

This is a reinforcement of recital 74, stating that vulnerabilities and incidents might be reported voluntarily to CSIRT or ENISA.

>Article 15 Voluntary reporting
>
>3.- The CSIRT designated as coordinator or ENISA shall process the notifications referred to in paragraphs 1 and 2 of this Article in accordance with the procedure laid down in Article 16. The CSIRT designated as coordinator may prioritise the processing of mandatory notifications over voluntary notifications.
>
>4.- Where a natural or legal person other than the manufacturer notifies an actively exploited vulnerability or a severe incident having an impact on the security of a product with digital elements in accordance with paragraph 1 or 2, the CSIRT designated as coordinator shall without undue delay inform the manufacturer.

Going down the 🐇 lawbit hole, things get interesting for security researchers voluntarily notifying CSIRT or ENISA:

1. CSIRT may prioritise mandatory notifications over voluntary ones.

2. CSIRT will inform the manufacturer about actively exploited vulnerabilities or severe incidents.

3. The regulator doesn’t seem to consider the possibility of zero-day vulnerabilities with no evidence of previous malicious exploitation, which should qualify as a severe incident.

4. In consequence, only zero-day vulnerabilities associated with an active exploitation scenario, that is, actively exploited vulnerabilities, would be effectively processed and notified.

## What if...?

The [Cyber Resilience Act implementation - FAQ](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions) document conveys the position of the EU Commission in regards to zero-day vulnerabilities reported by security researchers. However, the document was prepared by the EU Commission Services, and it should not be considered as representative of the commission's official position.

>FAQs on the Cyber Resilience Act
>
>[...]
>
>The FAQs are not meant to cover exhaustively the scope of the CRA, but rather aim to address recurring questions that the Commission services have collected since the entry into force of the CRA. This is intended to be a ‘living document’ that will be updated as and when necessary.
>
>This document is prepared by the Commission services and should not be considered as representative of the European Commission’s official position. The replies to the FAQs do not extend in any way the rights and obligations deriving from applicable legislation nor introduce any additional requirement. 
>
>The expressed views are not authoritative and cannot prejudge any future actions the European Commission may take, including potential positions before the Court of Justice of the European Union, which is competent to authoritatively interpret Union law.
>
>The Commission is also working on guidance pursuant to Article 26 of the CRA, to be adopted in the coming months.

What if zero-day vulnerabilities reported by security researchers could actually be considered as severe incidents having an impact on the security of products with digital elements? If that were the case, the notification chain, and the associated consequences, could be as follows:

1.- An early-warning notification by the manufacturer within 24-hours of becoming aware after performing an initial assessment and validation of the issue. This could indirectly cause an influx of notifications to the Single Reporting Platform, since any reported issue could be considered as severe regardless of severity, given the broad definition.

>(a) an early warning notification of a severe incident having an impact on the security of the product with digital elements, without undue delay and in any event within 24 hours of the manufacturer becoming aware of it, including at least whether the incident is suspected of being caused by unlawful or malicious acts, which shall also indicate, where applicable, the Member States on the territory of which the manufacturer is aware that their product with digital elements has been made available;

___
>[Article 14.5] For the purposes of paragraph 3, an incident having an impact on the security of the product with digital elements shall be considered to be severe where:
>
>(a) it negatively affects or is capable of negatively affecting the ability of a product with digital elements to protect the availability, authenticity, integrity or confidentiality of sensitive or important data or functions; or
>
>(b) it has led or is capable of leading to the introduction or execution of malicious code in a product with digital elements or in the network and information systems of a user of the product with digital elements.

2.- An additional information notification within 72-hours, containing any corrective or mitigating measures taken. This creates an implicitly tight deadline of 72 hours in order to fix any reported issue, disregarding severity, prioritization efforts, and workload capacity.

>(b) unless the relevant information has already been provided, an incident notification, without undue delay and in any event within 72 hours of the manufacturer becoming aware of the incident, which shall provide general information, where available, about the nature of the incident, an initial assessment of the incident, **as well as any corrective or mitigating measures taken**, and corrective or mitigating measures that users can take, and which shall also indicate, where applicable, how sensitive the manufacturer considers the notified information to be;

3.- A final report notification within one month after the additional information notification for severe incidents.

>unless the relevant information has already been provided, a final report, within one month after the submission of the incident notification under point (b), including at least the following:
>
>(i) a detailed description of the incident, including its severity and impact;
>
>(ii) the type of threat or root cause that is likely to have triggered the incident;
>
>(iii) applied and ongoing mitigation measures.

4.- Manufacturers shall inform users about severe incidents having an impact on the security of products with digital elements, and if they failed to do so, the notified CSIRTs designated as coordinators may provide such information, if appropriate. 

This introduces the possibility of users being notified about responsible disclosures not associated with actively exploited vulnerabilities.

>Article 14 - Reporting obligations of manufacturers
>
>8.-   After becoming aware of an actively exploited vulnerability or a severe incident having an impact on the security of the product with digital elements, the manufacturer shall inform the impacted users of the product with digital elements, and where appropriate all users, of that vulnerability or incident and, where necessary, of any risk mitigation and corrective measures that the users can deploy to mitigate the impact of that vulnerability or incident, where appropriate in a structured, machine-readable format that is easily automatically processable. 
>
>Where the manufacturer fails to inform the users of the product with digital elements in a timely manner, the notified CSIRTs designated as coordinators may provide such information to the users when considered to be proportionate and necessary for preventing or mitigating the impact of that vulnerability or incident.

## Notification flow for responsible disclosures

![notification flow](/assets/img/posts/2026/2026-04-07-cra/diagram.png)

## Penalties

>Article 64 - Penalties
>
>[…] 2. Non-compliance with the essential cybersecurity requirements set out in Annex I and the obligations set out in Articles 13 and 14 shall be subject to administrative fines of **up to EUR 15 000 000 or, if the offender is an undertaking, up to 2,5 % of the its total worldwide annual turnover for the preceding financial year, whichever is higher.**
>
>3.- Non-compliance with the obligations set out in Articles 18 to 23, Article 28, Article 30(1) to (4), Article 31(1) to (4), Article 32(1), (2) and (3), Article 33(5), and Articles 39, 41, 47, 49 and 53 shall be subject to administrative fines of **up to EUR 10 000 000 or, if the offender is an undertaking, up to 2 % of its total worldwide annual turnover for the preceding financial year, whichever is higher**.
>
>4.- The supply of incorrect, incomplete or misleading information to notified bodies and market surveillance authorities in reply to a request shall be subject to administrative fines of **up to EUR 5 000 000 or, if the offender is an undertaking, up to 1 % of its total worldwide annual turnover for the preceding financial year, whichever is higher.**

![account overdrawn](https://i.makeagif.com/media/4-09-2026/TxMZHK.gif)

## Additional resources

##### [Understanding the EU Cyber Resilience Act (CRA) (LFEL1001)](https://training.linuxfoundation.org/express-learning/understanding-the-eu-cyber-resilience-act-cra-lfel1001/)

![LFEL1001](https://training.linuxfoundation.org/wp-content/uploads/2025/04/LFEL1001-Course-Badge-300x300.png){: width="250" .normal}

##### <u>OpenChain Webinar - Introduction to the Cyber Resilience Act (CRA)</u>

<iframe width="560" height="315" src="https://www.youtube.com/embed/eczSUFGN2h8" title="OpenChain Webinar - Introduction to the Cyber Resilience Act (CRA)" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<br>

##### <u>How The EU CRA Will Change The Software Industry Forever - Olle E. Johansson</u>

<iframe width="560" height="315" src="https://www.youtube.com/embed/XMAfeQQ2ZOM" title="How The EU Cyber Resilience Act Will Change The Software Industry Forever - Olle E. Johansson" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>
<br>

##### <u>What is the Cyber Resilience Act?</u>
<iframe width="560" height="315" src="https://www.youtube.com/embed/ltBtIDvav6c" title="What is the Cyber Resilience Act?" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## ⚠️ Disclaimer 𓂃✍︎ : 

1. I am not a lawyer, nor does this post constitutes legal advice. 
2. These are my personal thoughts and reflections into the subject, which might not be necessarily right.