# Introduction

```ad-seealso
title: Smart Grid
A **_smart grid_** is an electricity distribution network that can monitor the flow of electricity within itself and automatically adjust to changing conditions.

```

An important component of the Smart Grid is the AMI.  

```ad-seealso
title: AMI (Advanced Metering Infrastructure)
**_AMI_** consists of power meters that use two-way communication to collect information related to electric power usage from electricity customers and to provide information to these customers.

```

Is composed by:
- **smart meters** (contatori intelligenti) installati presso i clienti;
- **canali di comunicazione bidirezionali** tra i contatori e il sistema centrale dell’operatore;
- **sistemi IT** per la raccolta, l’analisi e la gestione dei dati di consumo.

**OUR AIM:** assess risks for such an infrastructure, which includes components for switching on/off power to an electricity customer or limiting the amount of power provided (choking).  
$\to$
**PARTY:** distribution system operator

## Recap: Cyber-Risk Assessment

![[ISG81.png]]




# Context Establishment
## Recap: Context Establishment steps

- Context Identification and Description  
	- External Context  
	- Internal Context  
- Definition of the Assessment Goals and Objectives  
- Target, Scope and Focus of Assessment Definition  
- Assumptions  
- Assets Identification  
- Definition of the Likelihood Scale  
- Definition of the Consequence Scale  
- Definition of the Risk Evaluation Criteria

### External Context
```ad-seealso
title: Definition

description of societal, legal, regulatory, and financial environment and of the relationships with external stakeholders. 
```
 
A smart grid is a cyber-physical system that is part of a critical infrastructure.  
The distribution system operator (our party) is subject to a number of national laws and regulations governing its operations (e.g., NIS in Europe).  
- It is important to identify and document these laws and regulations.  
- Failure to comply may have significant legal and financial consequences, in the worst case putting the operator out of business.  

Power outages or incidents (i.e., charging the wrong amount or disclosing electricity customer data) can damage the reputation and public trust in the operator.


### Internal Context
```ad-note
title: Definition

description of relevant goals, objectives, policies, and capabilities that may determine how risk should be assessed.
```

**Party’s Mission:** distributing electrical power to electricity customers.

The overall goals of the operator are:
- to provide power in a reliable manner so that the electricity customers do not experience unintended power failures;
- to exchange correct and timely information with customers at all times so that they can be charged the right amount;
- to protect the privacy of its customers.

Most of the employees of the distribution system operator have strong technical competence, and a few of the staff have received special training in risk assessment.

### Goals and Objectives of the Assessment

- **Assess Risks wrt business continuity**  
  The assessment should help reduce the risk of incidents that may impact the business of the distribution system operator, by identifying appropriate treatments for important risks.

- **Law and regulation compliance**

- **Improve Situation Awareness**  
  The risk assessment should be documented in a way that can be understood by a wide range of internal and external stakeholders (including those who are not themselves experts on cybersecurity or smart grids).  
  Technical details should therefore be avoided as far as possible.

### Target of the Assessment

![[ISG82.png]]

### Scope of the Assessment
We limit the scope of the assessment to risks due to attacks on or via the target of assessment.  
- Other attacks (e.g., attacks via back-end systems) are outside the scope of the assessment.  
- Communication between Central system and Metering node via GPRS is supposed to be subject to a separate assessment and is therefore also outside our scope.

![[ISG83.png|500]]

### Focus of the Assessment
- Exchange of meter data and control data via the Internet and the ways in which this may affect the provisioning of power, as the distribution system operator is particularly concerned about this aspect.  
- Although within the scope, the main focus will not be on attacks via physical access to components.  
- Risks caused by malicious as well as non-malicious threat sources should be considered.  
- Regarding functionality, the focus of the assessment is on basic AMI functions, which include:  
	  - registering electricity customer meter data  
	  - transfer of data between Electricity customer and Distribution system operator  
	  - switching on/off or choking of power provided to the electricity customer.


### Assumptions
- Threat sources may be both internal and external.  
- Malicious and non-malicious threats may be both internal and external.  
- The target of assessment may be targeted not only by individuals with a purely financial or personal motive, but also by actors who wish to disrupt society.  
- All meter data and control data sent between the central system and metering nodes are encrypted.

### Assets
```ad-info
title: Note
The distribution system operator is the sole party for the cyber-risk assessment, which means that all consequence assessments and risk evaluation criteria will be defined from that perspective.

```

![[ISG84.png]]

### Likelihood Scale
For this risk assessment we specify likelihood in terms of frequencies.  

![[ISG85.png|500]]

We use **five-step scales of intervals for likelihood**.  
We need only determine which interval the likelihood of an incident lies within, rather than providing an exact value.  

It is a simple way of expressing the uncertainty — the granularity of the chosen scales depends on availability of data and the preferences of the decision makers.

## Consequence Scales 

**RECALL:** Consequences are related to Assets.  
$$\to$$
We need to define one consequence scale for each identified Asset.  

>Scales are defined from the perspective of the distribution system operator, which considers the overall business impact of potential incidents.



### Consequence Scales 
![[ISG86.png]]

![[ISG87.png]]

![[ISG88.png]]

## Slide 19 – Risk Evaluation Criteria
![[ISG90.png]]




# Risk Identification
## Risk Identification
The goal is to arrive at a collection of:
- threat sources  
- threats  
- vulnerabilities  
- incidents  
- risks  

...that is as correct and complete as possible for our particular target of assessment and assets.

## Risk Identification Techniques
In order to identify risks we should **gather information** about the **environment**:
- Logs, intrusion detection systems (IDSs) and other monitoring tools  
- Vulnerability scanners  
- Results from penetration tests or other kinds of security tests  
- Source code reviews  

**External Vulnerability and Threats Repositories**  
- Extract information from people who know the target of assessment well from their particular viewpoints.  

>When using historical data such as event logs, you should take great care not to fall into the trap of believing that tomorrow will be like yesterday.

## Identification of Malicious Cyber-risk
![[ISG91.png]]

### Threat Source Identification
```ad-note
title: Definition
 Understand who may want to initiate attacks and why

```
 
The potential for causing harm will depend on:
- the motive and intention of the threat sources  
- their capabilities  
- available resources  

>It is therefore important to document these characteristics in the threat source descriptions.


![[ISG92.png|500]]
![[ISG93.png|500]]
![[ISG94.png|500]]


### Vulnerability Identification
For **each malicious threat** we identify the **existing vulnerabilities** that the threat may exploit.  

The identification may start from looking to:
- Vulnerability lists such as **NISTIR 7628** (guidelines for smart grid cybersecurity)  
- **ISO 27005**, which offers a list of vulnerabilities related to hardware, software, network, personnel, site, and organization  
- Online resources offered by **OWASP** (http://www.owasp.org)  
- **Common Weakness Enumeration (CWE)** offered by MITRE  

Vulnerabilities may also be identified by scanners or as output of testing activities.

![[ISG95.png|500]]
![[ISG96.png|500]]
![[ISG97.png|500]]
### Incident Identification

![[ISG98.png]]



## Identification of Non-malicious Cyber-risk
![[ISG99.png]]


### Incident Identification (Non-malicious)
![[ISG100.png|500]]



# Risk Analysis
## Recap
```ad-seealso
title: Definition

The risk analysis is the activity aiming to estimate and determine the level of the identified risks.
```

**Observation 1:** The risk level is derived from the combination of the likelihood and consequence.

![[ISG101.png]]

```ad-success
title: Goal
assess the likelihood of the identified incidents and their consequence for each of the affected assets.  

```

**Information sources:** same as those used for risk identification.  

The main difference is that now we also need to consider:
- the severity of vulnerabilities  
- likelihood of threats and incidents  
- consequence of incidents

### Risk Analysis Process
According with the scales identified in the **Context Establishment** phase, we proceed by answering the following questions:

![[ISG102.png|500]]
## Malicious Threat Analysis

**Main sources of information for the likelihood estimation:**
- Event logs provided by the distribution system operator  
- Expert judgments of the participants  

We choose to follow an approach inspired by the **OWASP risk-rating method**  
The factors are rated on a scale from **0 to 9**.  

![[ISG103.png]]

Let’s now analyse each row of the Table relating Threats and Threat Sources
![[ISG104.png|500]]

 **_Threat_**: DDoS attack on the central system
 **_Threat Source_**: script kiddie

![[ISG105.png|500]]

Let’s now analyse each row of the Table relating **Threats** and **Threat Sources**.
![[ISG106.png|500]]

**Threat:** DDoS attack on the central system  
**Threat Source:** script kiddie

![[ISG107.png|500]]

 Based on these results (4,5 and 6,25), considering the worse case, and using our own likelihood scale, we estimate the likelihood of this threat to be Likely

![[ISG108.png]]

```ad-attention
Check that the estimate is supported by the available event logs and   confirmed by the participants from the distribution system operator

```

 Iterating over all the Threats identified we get the following estimation
![[ISG109.png]]



## Non-Malicious Threat Analysis
For each identified threat, start by considering the threat source.

![[ISG110.png|500]]

To estimate the likelihood, it is possible to consider information such as:
- Event logs  
- Expert judgments  
- Interviews or questionnaires  
- Available statistics about the typical likelihood of similar threats in enterprises and other organizations

![[ISG111.png|500]]
## Risk Analysis Process 
According with the scales identified in the Context Establishment phase, we proceed by answering to the following questions:

![[ISG112.png|500]]

### Vulnerability Analysis
The next step consists of analysing vulnerabilities.  
For this we choose to use a simple scale consisting of the steps **High**, **Medium**, and **Low**.

![[ISG113.png]]
### Malicious Threat Vulnerabilities
To provide vulnerability severity estimation, we can use as information sources:
- Expert judgments  
- Statistics and open repositories  
- Vulnerability scans  
- Security testing  
- Penetration testing  
- Code review  

Inspired by the OWASP risk-rating method, we rate vulnerabilities as follows.
![[ISG114.png|500]]

As a result of the analysis done in step 2 (Risk Identification), we identified **five different vulnerabilities** associated to the malicious threats:
1. Inadequate attack detection and response on central system  
2. Weak encryption and integrity check  
3. Unprotected local network, no sanitation of input data from the external meter  
4. Outdated antivirus protection on metering node  
5. Four-eyes principle not implemented, no logging of actions of individual central system operators  

Let’s analyse them one by one.

**Vulnerability:** Inadequate attack detection and response on central system.
![[ISG115.png|500]]

Iterating over all the Vulnerabilities identified we get the following estimation
![[ISG116.png]]
### Non-malicious Threat Vulnerabilities 
**Observation:**   For the non-malicious threats there is no intent to discover and exploit vulnerabilities.   We try to understand the extent to which there is a lack of barriers that could prevent threats from leading to incidents.

As a result of the analysis done in step 2 (Risk Identification), we identified **four different vulnerabilities** associated to non-malicious threats:
1. Single communication channel between central system and metering terminal  
2. Poor testing  
3. Poor training and heavy workload  
4. Inadequate overvoltage protection  

In this case, the assessment is done analysing the environment and making considerations over the processes in place.

![[ISG117.png|500]]

##  Risk Analysis Process
According with the scales identified in the Context Establishment phase, we proceed by answering to the following questions.

![[ISG118.png|500]]

### Likelihood of Incidents
In order to estimate the likelihood of incidents, we consider the analysis of:
- Threats that lead to the incidents  
- Vulnerabilities that the threats exploit

![[ISG119.png|500]]


### Likelihood of Incidents caused by Malicious Threats
At the end of the analysis done in step 2 (Risk Identification) we identified these incidents.

![[ISG120.png|500]]
![[ISG121.png]]

**Considerations:**
- Event logs show only two such incidents for the last three years (which corresponds to *Possible*).  
- However, there is an increasing trend of this type of incidents.  
- Although the number of DDoS attacks that succeed will likely be lower than the number of attempts, we still estimate that the frequency for the incident also lies within the interval of **Likely** on our scale.



### Likelihood of Incidents caused by Non-malicious Threats
At the end of the analysis done in step 2 (Risk Identification) we identified these incidents.

![[ISG122.png|500]]
![[ISG123.png|500]]
### Likelihood of Incidents caused by Malicious Threats 

**Considerations:**
At first glance, the two incidents seem to occur with the same frequency.  
However, we found before that there are routines in place for reviewing and testing the system before changes are launched.  

Considering that provisioning of power to the electricity customer is more critical than the continuous reading of meter data,  
the routines are stronger with respect to updates and changes that may affect control data.  

This observation, combined with the data logs, leads us to the likelihood:
- **Unlikely** regarding control data to the choke component  
- **Possible** regarding the reception of meter data

### Likelihood of Incidents caused by Non-malicious Threats 
![[ISG124.png|500]]

## Risk Analysis Process
According with the scales identified in the Context Establishment phase,  
we proceed by answering to the following questions:

![[ISG125.png|500]]
### Consequences of Incidents 
**Recall:** The consequence of an incident must be judged for each asset it harms.

At the end of the Analysis done in step 2 (Risk Identification) we identified these incidents harming the three identified assets.  

![[ISG126.png|500]]

In order to estimate consequences, we need to consider the **consequence scale** for the identified asset.

![[ISG127.png|500]]

This requires estimating:
- the expected time to detect and respond to an attack  
- the number of affected electricity customers

![[ISG128.png|500]]

**Considerations:**
- In the experience of the distribution system operator, supported by their internal investigation reports,  
  the DDoS attacks that have occurred before have never caused loss of availability for more than one day.  
- The number of electricity customers whose meter data becomes unavailable can, however, be higher than before, as the customer base has increased.  

Based on this information, we therefore assign the consequence estimate: **Moderate** to the incident.

![[ISG129.png| 500]]
![[ISG130.png|500]]

# Risk Evaluation
**4 main steps** (not too much different from the general case)

![[ISG131.png]]

## Consolidation of Risk Analysis Results
The goal of this activity is to make sure that the correct **risk level** is assigned to each risk.  

The central question is not whether each likelihood and consequence estimate is correct,  
but rather whether the resulting risk level is correct.

```ad-example
![[ISG132.png]]

```

We also make sure to check whether there are any risks that are both **malicious and non-malicious*

This is typically the case if both can result in the same **incident**.  
In our case, this would mean that the same incident occurs in both the malicious and non-malicious tables.  

In such cases, we need to check that:
- likelihood and consequence estimates are consistent, and  
- both causes (malicious & non-malicious) have been considered when estimating likelihood.  

This can be easy to overlook since we treat the two types separately for much of the assessment.

## Evaluation of Risk Level 
The risk level of each risk is determined by its **likelihood** and **consequence** according to the **risk matrix**. In our case, risk evaluation is performed simply by plotting each risk in the matrix.

![[ISG133.png]]

![[ISG134.png]]

![[ISG135.png]]



## Risk Aggregation (CASE 1)
During the evaluation we need to take into account that some risks may “pull in the same direction” to the degree that they should actually be evaluated as a single risk.
There are basically **two cases** where this may hold.

![[ISG136.png]]
## Risk Aggregation (CASE 2)

During the evaluation we need to take into account that some risks may “pull in the same direction” to the degree that they should be evaluated together.  There are basically two cases where this may hold.

![[ISG137.png]]

## Risk Aggregation con't
Going through Incident Tables, there are no instances where a single incident harms more than one asset.  → **Case 1 does not hold!**

![[ISG138.png]]
However, risk no. 4, Malware compromises meter data, and risk no. 11, Software bug on the metering terminal compromises meter data, both concern software on the metering nodes and harm the integrity of meter data.

 Case 2 hold
- they can therefore be viewed as special instances of a more generic incident, which we can call Software on the metering node compromises meter data.

![[ISG139.png]]

## Risk Matrix after Aggregation
![[ISG140.png]]
## Risk Grouping 
**Observation:** several risks may benefit from the same treatment.  

In order to find out how to further group risks for our assessment,  
we systematically go through the results of the risk identification.

> Do any of these risks have anything in common that indicates that they will benefit from the same treatment?

**Example:**  
![[ISG141.png]]

- Increasing the likelihood or consequence of either of them by a single step would bring its risk level to Medium.
- Treatments that address both these risks are therefore quite likely to be worth the cost.
- By grouping such risks we make it easier to take such considerations into account.

# Risk Treatment
The final step of the cyber-risk assessment starts with:
- Identification of treatments for selected risks  
- Assessment of the effect of treatments  
- Consideration of whether the **residual risk** is acceptable  

If the residual risk **is acceptable**, the documentation is finalized and the process terminates.  
Otherwise, we need to go back and do another iteration of treatment identification.
## Treatment Identification for Malicious Risks
Ideally, we would like to find treatments for all identified risks.  
However, since we always have **limited time and resources**, we need to focus on those that are most important.  

We therefore start by **selecting risks** based on the results of the **risk evaluation**.

![[ISG142.png]]

![[ISG143.png]]

The next step is to identify treatments for the selected risks.  
For each risk we therefore create a small table summarizing relevant information for the treatment.

![[ISG144.png]]

## Risk Acceptance
Implementing treatments always carries a **cost**.  
For each treatment we therefore need to weigh its **effect** against its **cost**.  
We first estimate the effect of a treatment in terms of **reduced risk level** for the affected risks,  
before estimating its cost.

**Quantitative vs Qualitative** assessment may be used.

## Cost-Benefit Analysis

![[ISG145.png]]

**Considerations:**
- Implementing the treatment will hardly prevent *script kiddies* or *cyber-terrorists* from launching DDoS attacks → **No effect on the threat itself**.  
- However, **early detection** will reduce the likelihood that the attack actually leads to the incident → Likelihood moves from *Likely* to *Possible*.  
- A **prompt response** implies that fewer electricity customers are affected, and that they are affected for a shorter period → Consequence moves from *Moderate* to *Minor*.  
- The treatment requires a significant investment in **hardware and network infrastructure**.  
- Arriving at an adequate set of detectors (preferably combining anomaly-based and signature-based approaches) will take time and effort.  

>The overall **risk level decreases from High to Low.**
>The **cost of the treatment is therefore High.**

## Cost-Benefit Analysis
Iterating over the risk, we got the following table:

![[ISG146.png|500]]