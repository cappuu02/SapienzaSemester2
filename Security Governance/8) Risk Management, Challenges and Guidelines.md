# Challenges in the Cyber-Risk Management Process
There are different challenges in Cyber-Risk Management Process:

## Which Measure of Risk Level to Use?
 Up to now, we measured risk level based on two factors:
 1. loss of asset value when a potential incident occurs (**_Impatto_**)
 2. how often this happens (i.e., likelihood) (**_Frequenza-Probabilità_**)

### Two-Factor Measure of Risk
 This is a classical **_two-factor_** measure of risk:
 ![[ISG72.png|500]]

### Three-Factor Measure of Risk
**_Three-factor_** Measure
NIACAP defines risk as: "a combination of the likelihood that a threat will occur, the likelihood that a threat occurrence will result in an adverse impact, and the severity of the resulting impact".

>Analisi più granulare

![[ISG73.png]]

![[ISG74.png|500]]

### Many-Factor Measure of Risk
**Many-factor** Measure:
In some methodologies (e.g., OWASP) threats and vulnerabilities are analysed under different factors.  Such factors may be considered independently as factors affecting the risk level
 - threat agent factors
 - vulnerability factors

Similarly, consequence is represented by
- technical impact factors
- business impact factors

![[ISG75.png]]

```ad-attention
title: 3-factor vs Multi-factor Risk Model


| 3-Factor Model                                   | Multi-Factor Model                                        |
| ------------------------------------------------ | --------------------------------------------------------- |
| Simple conceptual (Threat-Vulnerability-Impact)  | Breaks probability and impact into measurable sub-factors |
| Good for awareness and high level decisions      | More objective, repeatable scoring                        |
| Limited differentiation: many risks look "equal" | Enables smarter priorization                              |
**_Multi-factor_** = from understanding the risk to managing the risk effectively


```

 The choice of approach and how to apply it depends on **context** and the **specific assessment scenario**.
#### Key Considerations
- **Data availability** is a crucial factor in deciding how to measure risk.
    - If you have reliable data on **frequency** and **consequence**, use the **two-factor approach**.
- In **cybersecurity**, **multi-factor models** are becoming more common.
    - However, estimating **likelihood** with reasonable accuracy often involves significant uncertainty.
- The main issue in risk assessment is **not the lack of data**, but the **lack of the right kind of data** for the predefined factors.
    - Most cyber systems automatically generate **logs** with numerous indicators.
    - In these cases, you may define a **custom risk function** using factors that align with the available log indicators.
    - ⚠️ **Warning:** this requires both **experience** and **careful judgment**.
- When relying on **expert or stakeholder opinions**, ensure that all **factors are clearly defined** and **distinct** from each other.
- Always choose an **appropriate scale** for each factor to ensure consistency and interpretability.
 
## What Scales Are Best Suited Under What Conditions?
There is no universal scale for measuring risk. The most suitable scale depends on:
- **_The factor you're measuring_** (probability, impact, frequency, etc.)
- **_The type of analysis_** (technical, strategic, qualitative, quantitative)
- **_The target_** (asset or system to be protected)
- **_The data sources_** (numerical, expert, incomplete, etc.)

### Classification of Scales

#### Nominal Scale
- Serve solo a **classificare** in categorie separate, senza ordine.
- Ti dice se due elementi sono uguali o diversi.

```ad-example
“non-human threat”, “accidental human threat”, “intentional human threat”.  
👉 Qui non c’è un “più grave” o “meno grave”, sono solo **etichette** diverse.

```

>**Uso tipico:** per classificare **tipi di minacce** o **categorie di vulnerabilità**.

#### Ordinal Scale
It lets you **order** the levels (major/minor).
But it doesn't tell you _by_ how much one is greater than the other.

```ad-example
**Esempio:** “Minor” < “Moderate” < “Major”.  
👉 Sappiamo che “Major” è più grave, ma non quanto più grave.

```

>**Uso tipico:** valutazioni qualitative di **impatto** o **probabilità**, quando i dati sono vaghi o basati su opinioni.

#### Difference Scale
It allows you to measure **equal differences** between values.

```ad-example
la scala **Celsius** → la differenza di 10°C è sempre uguale, indipendentemente dal punto di partenza. Qui però lo zero è **arbitrario** (0°C non significa “assenza di temperatura”).

```

> **Uso tipico:** quando i tuoi dati sono numerici e **gli intervalli** hanno significato, ma **lo zero non è assoluto**.

#### Ratio Scale
È come la Difference Scale, **ma con un vero zero**.
Permette di confrontare **rapporti** (es. due volte, metà, ecc.).

```ad-example
- Numero di furti d’identità all’anno

- Perdita economica (€) causata da incidenti informatici

```

>**Uso tipico:** per **analisi quantitative** rigorose (es. monetizzazione del rischio, modelli statistici, KPI di sicurezza).



![[ISG76.png]]
### Qualitative vs Quantitative Risk Assessment

| **Quantitative**                                                    | **Qualitative**                                                         |
| ------------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Dati **omogenei**, numerici, misurabili                             | Dati **eterogenei**, difficili da quantificare                          |
| Adatto ad **analisi tecniche** o di dettaglio                       | Utile per **discussioni strategiche o iniziali**                        |
| In teoria molto preciso, ma **poco pratico** senza dati affidabili  | Più pratico ma **meno preciso**                                         |
| Produce risultati numerici (€, %), ma può dare **falsa precisione** | Deve comunque essere tradotto in numeri (es. costi o impatti) alla fine |

>Every risk must ultimately be translated into numbers — cost, time, or impact avoided. The key is balancing quantitative precision with qualitative practicality

### Scales for Likelihood (Probabilità)
La **probabilità di un evento** è **molto difficile da stimare** in cybersecurity, perché:

- Spesso mancano dati storici affidabili.
- Gli scenari sono nuovi o unici.
- Gli attaccanti cambiano comportamento.

```ad-fail
title: Attenzione
Usare **numeri troppo precisi** (es. 37.5%) dà **un’illusione di accuratezza**.

```

```ad-done
title: Solution
Usa **categorie ampie** o **intervalli di frequenza**, ad esempio:  
    `Rare / Unlikely / Possible / Likely / Almost Certain`
Queste classi comunicano bene e **riduccono l’illusione di precisione**.

```

➡️ **In pratica:**  
Preferisci **scale qualitative o semi-quantitative** per la probabilità, soprattutto quando devi comunicare con manager o decisori.

### Scales for Consequence (Impatto)
Una **risk evaluation** spesso finisce per essere usata in un’**analisi costi-benefici**, cioè:
- Si misura quanto costa proteggere un asset
- Si confronta con quanto si perderebbe se non lo si proteggesse

> Ma questo approccio funziona **solo se riesci a quantificare bene le conseguenze**.  In pratica, **non sempre è possibile tradurre tutto in soldi**.

```ad-example
title: Example 1
If the asset in question is a bag of diamonds the consequence of an incident in which some or all of the diamonds are stolen might be equal to the monetary value of the diamonds stolen

```

```ad-example
title: Example 2
If the asset is the integrity of a customer database, it may be easy to characterize the number of records harmed, but hard to say what this means in euros

```

```ad-example
title: Example 3
If the asset is the company’s reputation, it is hard to know or characterize the impact of some incident on it, and even harder to estimate what this impact corresponds to in euros

```

**_The suitability of a consequence scale obviously depends on the asset in question_**.
**_Every good requires an adequate scale of measurement_**

```ad-attention
Non possiamo utilizzare la stessa scala per diversi contesti!

```

It is recommended to:
- Define specialized consequence scales for each asset of relevance
- Define a consequence scale in such a way that it fits its intended usage
	- Per i tecnici, scale più dettagliate
	- per manager, scale più chiare e sintetiche

>A consequence scale suited for communicating consequences to decision makers may be unsuited to discussions with technical people.

```ad-question
title: What Scales to Use for Cyber-risk?

```

Nel **cyber-risk**, molti sistemi sono **automatizzati e digitali**:
- Registrano eventi, errori, accessi, tempi di risposta.
- Questi dati permettono **misure automatiche e quantitative** (es. numero di intrusioni, tempo medio di downtime).

>La parte tecnica del rischio si presta bene a **scali quantitative (ratio/difference)**.

## How to Deal with Uncertainty?
```ad-cite
ISO 31000 defines uncertainty to be "**the state, even partial, of deficiency of information related to, understanding or knowledge of an event, its consequence, or likelihood**".

```

L’**incertezza** è una **mancanza (totale o parziale) di informazioni** riguardo:
- **Un evento** (cosa accadrà o meno)
- **Le sue conseguenze** (quanto sarà grave)
- **La sua probabilità** (quanto spesso accadrà)

>In altre parole, è tutto ciò che **non sappiamo o non possiamo sapere con certezza** su un rischio.

 We will distinguishes between two kinds of uncertainty:
- ==epistemic== uncertainty
- ==aleatory== uncertainty

 We will focus on how to represent uncertainty and how to reduce it. We will address challenges related to uncertainty in the setting of cyber-risk assessment.

### Epistemic Uncertainty  

```ad-note
title: Epistemic Uncertainty
 Epistemic Uncertainty relates to the uncertainty due the lack of knowledge
- If knowledge were perfect, epistemic uncertainty would disappear.
- Better data and evidence can reduce epistemic uncertainty

> In practice, knowledge is never perfect — so some epistemic uncertainty always remains

```

💡 Hint: In pratica: l’incertezza epistemica si **riduce con più informazione** (meglio monitoraggio, threat intelligence, test).


```ad-question
title: How can we Represent Uncertainty?
Two methods for represent the uncertainty:

**_Quantitative representation_**
We use numeric intervals for indicating the uncertainty.
The width of the interval specifies the level of uncertainty.


💡 **Vantaggio:** più preciso e matematicamente gestibile.  
⚠️ **Limite:** richiede dati numerici affidabili, non sempre disponibili in cybersecurity.

How much uncertainty is tolerable?
It depends on the uncertainty impacts over the decision procedure.

![[Pasted image 20251028121157.png]]


**_Qualitative representation_**
we are labels or text descriptions as a separate attribute.


💡 **Vantaggio:** più adatta quando i dati non sono numerici.  
⚠️ **Limite:** meno rigorosa, ma più chiara per comunicare con manager o stakeholder.


  
![[Pasted image 20251028121234.png]]

> We can represent uncertainty visually (using the risk matrix) or explicitly as a quality of the estimate: these are not alternatives, but complementary tools



```

### Aleatory Uncertainty

```ad-seealso
title: Aleatory Uncertainty
Aleatory Uncertainty relates to the uncertainty due to inherent randomness.

> If uncertainty remains even with complete knowledge, then it is aleatory, not epistemic

```

💡 In pratica: l’incertezza aleatoria **non si riduce con più dati**, perché è **intrinseca al fenomeno**.

### Reducing Uncertainty
 We may use different assessment methods to reduce uncertainty using data already acquired:
 - Fuzzy logic
 - Iterating data collection
 - Comparative Analysis

>Testing the risk model against historical data or by conducting various surveys across larger groups of stakeholders


## High-consequence Risk with Low Likelihood
Non tutti i rischi si presentano con alta probabilità.  
Alcuni sono **estremamente rari**, ma se accadono possono avere **conseguenze catastrofiche** per l’organizzazione.

Questi eventi non si comportano come i “rischi normali”:
- Non seguono modelli prevedibili.
- Non compaiono nei dati storici.
- Non si lasciano facilmente stimare nei processi di _risk assessment_.

Questi sono i cosiddetti **Black Swans** e **Gray Swans**.

### Black Swans 
```ad-seealso
title: Definition

A black swan is an incident that is extremely rare and unexpected, but has very significant consequences.
```

Un **Black Swan** (cigno nero) è un evento:
- **Imprevedibile** — non ci sono segnali chiari prima che accada.
- **Rarissimo** — nessuno lo include nelle analisi di rischio.
- **Devastante** — causa danni enormi a livello operativo, economico o reputazionale.

Il normale processo di _risk assessment_ funziona solo quando:
- Hai **dati storici** per stimare frequenze e impatti.
- I rischi sono **prevedibili** entro certi limiti.

>Questo perché i black swans non hanno precedenti e non seguono pattern riconoscibili

```ad-success
title: Solution
La soluzione non è prevederli ma prepararsi a reagire quando accadono.

```

### Gray Swans
```ad-note
title: Definition
A **Gray Swan** is an incident that has far-reaching consequences, but, unlike a Black Swan, can be anticipated to some degree.



```

Un **Gray Swan** (cigno grigio) è un evento:
- **Molto grave**, ma **non completamente imprevedibile**.
- **Parzialmente conosciuto** o **intuibile**.
- **Spesso trascurato** perché non riceve abbastanza attenzione.

💡 È un “rischio ignorato”:  
non è invisibile, ma nessuno lo prende abbastanza sul serio.

```ad-warning
Gray swans may also easily be overlooked.

- they are not present in the documentation that we (as risk assessors) consider as input

- we are not interacting with the right group of stakeholders

- we cannot extract the required information

- by definition, relevant gray swans are known somewhere in the organization; if not documented, then implicitly in stakeholders’ knowledge or inferable from existing data

```

#### Communicating Gray Swans
 It is fundamental to define an effective process to convey the good message to managers
 - Using probability is not recommended
- When using quantitative scale, always use a reference
- if there is considerable uncertainty then it must be communicated to relevant decision makers

> The real challenge with gray swans is not estimating them, it is making sure they are heard.

 We are in the treatment phase trying to aid the decision makers in making the right decision regarding a gray swan.

![[ISG80.png]]