
```ad-todo
title: Recap
These are three elements without which there can be no risk:
- Asset
- Vulnerability
- Threat

```

# Cyber-Systems
```ad-abstract
title: Cyberspace
A ==cyberspace== is a collection of interconnected computerized networks, including services, computer systems, embedded processors, and controllers, as well as information in storage or transit.

```

```ad-abstract
title: CyberSystem
A ==cyber-system== is a system that makes use of a cyberspace.

```

```ad-abstract
title: Cyber-Physical-System
A ==cyber-physical system== is a cyber-system that controls and responds to physical entities through actuators and sensors. 

```

# Cybersecurity
==Cybersecurity== is the protection of cyber-systems against cyber- threats.
![[ISG57.png]]
```ad-question
title: QuestionHow does cybersecurity relate to information security?

![[Pasted image 20251010114001.png]]


```

```ad-question
title: How Does Cybersecurity Relate to Critical Infrastructure Protection?
Critical Infrastructure Protection (CIP) and Critical Information Infrastructure Protection (CIIP), is concerned with the prevention of the disruption, disabling, destruction, or malicious control of infrastructure.

![[Pasted image 20251010114103.png]]

```

# Cyber-Risk
```ad-abstract
title: Definition
A ==cyber-risk== is a risk that is caused by a cyber-threat. 

```

It can be:
- **_Malicious cyber-risk_**: hacker that steal our personal information
- **_Non malicious cyber-risk_**: posting data on an open website

>An incident of unauthorized access to some sensitive data can be caused by an hacker (i.e., malicious cyber-risk) or/and accidental posting of the data on an open website is (i.e., non-malicious cyber-risk) 

```ad-info
title: Recap Risk Management General Process
It is composed by 3 main sub-processes:
![[Pasted image 20251010114544.png]]


```

## Communication and Consultation of Cyber-risk
Additional challenges are issued when considering cyber-systems:
1. Cyber-Systems may potentially have stakeholders everywhere
2. There may potentially be adversaries everywhere

An help comes from:
Repositories of up-to-date information regarding, for example,
- Cyber-threats, 
- vulnerabilities and incidents, 
- potential and confirmed adversary profiles, 
- current strategies and mechanisms for cyber-risk mitigation

```ad-question
title: Why cyber-risk assessment is different from generic risk assessment?
1. The potentially far-reaching extent of a cyberspace implies that also the origins of threats are widespread, possibly global 
2. the number of potential threat sources and threats, both malicious and non- malicious, is very large

```

Need to define procedures and techniques that provide guidance and direction

## Cyber-Risk Assessment
![[ISG61.png]]

## Context Establishment for Cyber-risk
Understanding and documenting the interface to the cyberspace is important for cyber-risk management in general and for identification of cyber-risks in particular.

The **_Attack Surface_** is all of the different points where an attacker or other threat source could get into the cyber-system, and where information or data can get out.

## Identification of Malicious Cyber-risk
Observation: What we can expect from the adversary depends on:
- (i) motives, 
- (ii) abilities, 
- (iii) helpers 
- (iv) resources available to the adversary 

![[ISG63.png]]

### Malicious threat source identification
It is important to understand:
- who may want to initiate attacks
- What motivates them
- What their capabilities and intentions are
- how attacks can be launched

```ad-attention
Threat and threat sources as not just just external! 
Consider that they may be inside your cyber-system 

```

Pay particular attention to the interface to the cyberspace and the documented attack surface.
Make active use of the description of the target of assessment, investigating where and how attacks can be launched.

```ad-example
Examples of helpful catalogues and repositories that concern cybersecurity (and cyber-threats in particular) are those that are provided by MITRE and OWASP, NIST etc. 

```

### Malicious vulnerability identification
Focus on the identified attack surface: By investigating existing controls and defence mechanisms to determine their strength and adequacy with respect to the identified threats and assets.

By running security testing i.e., penetration testing and vulnerability scanning
- to check whether or how easily a specific threat source can actually launch an attack 
- to investigate the severity of known vulnerabilities, 
- to look for potential vulnerabilities, and 
- to look for possible incidents that the malicious threats may lead to 

### Malicious incident identification
investigating how the malicious threats can cause harm to the identified assets given the identified vulnerabilities 

Help and guidance come from 
- event logs about previous incidents of relevance 
- investigation of the kinds of incidents that the threats and vulnerabilities may lead to based on the result of penetration testing activities 

## Identification of Non-malicious Cyber-risk
Normally there is no intent or motive behind non-malicious risk...
It is not practical to start by identifying and documenting threat sources It is recommend to start from the valuables to be defended.

1. Answer to the question “In which way the considered asset may be directly harmed?” 
	- Each possibility corresponds to an incident 
2. Identify the vulnerabilities and threats that may cause these incidents 
	- focus only on the parts and aspects of the target that are of relevance to the identified incidents
3. identify the non-malicious threat sources that can cause the threats. 

![[ISG64.png]]

### Non-malicious Incident Identification
Start by investigating how the assets are represented and how they are related to the target of assessment. Accidents and unintended acts are often recurring and known this implies to use logs, monitored data, and other historical data to support the identification.

### Non-malicious vulnerability identification
It is possible to investigate technical parts of the target of assessment, as well as the culture, routines, awareness, and so forth of the organization and personnel in question. Open sources, such as the ISO 27005 standard, come with lists of typical vulnerabilities. 

### Non-malicious threat identification
We need to answer to the following question:

```ad-question
title: Which unintended events may lead to the identified incidents due to the identified vulnerabilities, and how?


```

We need to carefully consider the interface to the cyberspace to identify non- malicious threats that arise outside of the system. 

Relevant sources on typical threats include, for example, the ISO 27005 standard and the NIST risk assessment guide, which provide representative examples of non-malicious threats. 

### Non-malicious threat source identification
```ad-question
title: Who are the users of the system, and how can they cause the unintended or accidental events?


```
Consider non-human threat sources, such as failure of hardware or other technical components, wear and tear, acts of nature, and so forth. 

Event logs and historical data aid the identification of non-malicious threat sources, as do open sources such as the abovementioned ISO standard and NIST guide, which both provide categorized lists. 

## Analysis of Cyber-risk
There are two main aspects that distinguish the analysis of cyber-risk from risk analysis in general. 
1. for malicious threats behind which there is human intent and motive, it can be hard to estimate the likelihood of occurrence. 
2. due to the nature of cyber-systems we have several options for logging, monitoring, and testing that can facilitate the analysis. 

Use techniques for threat modelling to describe aspects such as attack prerequisites, attacker skills or knowledge required, resources required, attacker motive, attack opportunity, and so forth. Similar descriptions can be made for vulnerabilities, such as ease of discovery and ease of exploit. In combination, this information can be used to derive likelihoods of threats and incidents 

## Evaluation of Cyber-risk
4 main steps (not too much different from the general case)

![[ISG65.png]]

## Treatment of Cyber-risk
There are two features in particular that distinguish the risk treatment of cyber- systems from the general case: 
1. the highly technical nature of cyber-systems means that the options for risk treatment are also technical. There is also the need to consider the sociotechnical aspects and human involvement. 
2. the distinction between malicious and non-malicious cyber-risks has implications for the most adequate risk treatment 

```ad-example
title: Mitre Capec
Understanding how the adversary operates is essential to effective cyber security. CAPEC helps by providing a comprehensive dictionary of known patterns of attack employed by adversaries to exploit known weaknesses in cyber-enabled capabilities.

“**_Attack Patterns_**” are descriptions of common methods for exploiting software providing the attacker’s perspective and guidance on ways to mitigate their effect.

It can be used by analysts, developers, testers, and educators to advance community understanding and enhance defences

```

```ad-example
title: MITRE CWE
CWE is a community-developed list of common software security weaknesses. It serves as a common language, a measuring stick for software security tools, and as a baseline for weakness identification, mitigation, and prevention efforts. 

```

## Vulnerability Classification
Vulnerabilities may affect a system at different levels: 
- Hardware, 
- Software, 
- Network, 
- Personnel, 
- Organizational…

Mitre Corporation maintains a list of disclosed vulnerabilities in a system called Common Vulnerabilities and Exposures (CVE), where vulnerability are classified (scored) using Common Vulnerability Scoring System (CVSS).

### Common Vulnerability Scoring System (CVSS)
The Common Vulnerability Scoring System (CVSS) captures the principal technical characteristics of software, hardware and firmware vulnerabilities. Its outputs include numerical scores indicating the severity of a vulnerability relative to other vulnerabilities.
CVSS is composed of three metric groups: 
- **_Base metrics_**: reflect the severity of a vulnerability according to its intrinsic characteristics which are constant over time and assumes the reasonable worst case impact across different deployed environments 
- **_Temporal metrics_**: adjust the Base severity of a vulnerability based on factors that change over time, such as the availability of exploit code 
- **_Environmental metrics_**: adjust the Base and Temporal severities to a specific computing environment. They consider factors such as the presence of mitigations in that environment

#### CVSS 3.1
![[ISG66.png]]
#### CVSS Scoring
When the Base metrics are assigned values by an analyst, the Base equation computes a score computes a score ranging from 0.0 to 10.0.

![[ISG67.png]]

### Common Weakness Scoring System (CWSS)
The Common Weakness Scoring System (CWSS) provides a mechanism for prioritizing software weaknesses in a consistent, flexible, open manner.

It is a collaborative, community-based effort that is addressing the needs of its stakeholders across government, academia, and industry CWSS is distinct from (but not a competitor to) the Common Vulnerability Scoring System (CVSS). 
- CVSS and CWSS have different roles, and they can be leveraged together 

CWSS offers: 
- Quantitative Measurements of the unfixed weaknesses that are present within a software application 
- Common Framework for prioritizing security errors ("weaknesses") that are discovered in software applications 
- Customized Prioritization 

#### CWSS Structure
CWSS is organized into three metric groups: 
- **_Base Finding metric group_**: captures the inherent risk of the weakness, confidence in the accuracy of the finding, and strength of controls. 
- **_Attack Surface metric group_**: the barriers that an attacker must overcome in order to exploit the weakness. 
- **_Environmental metric group_**: characteristics of the weakness that are specific to a particular environment or operational context. 

![[ISG68.png]]
#### CWSS Scoring
Each factor in the Base Finding metric group is assigned a value 
- These values are converted to associated weights, and a Base Finding sub-score is calculated 
- The Base Finding sub-score can range between 0 and 100 2. 

The same method is applied to the Attack Surface and Environmental metric group 
- their sub-scores can range between 0 and 1 3.

The three sub-scores are multiplied together to get a CWSS score between 0 and 100.

![[ISG69.png]]