# Audit and IT audits
## Introduzione
```ad-info

Questo corso esplora i **principi fondamentali dell'auditing** e li collega alla **sicurezza informatica, alla governance e ai framework di controllo IT**. Vengono introdotti gli **obiettivi** principali, le **metodologie** chiave e la **mentalità** professionale richiesta agli auditor che operano in ecosistemi digitali complessi.
```

```ad-abstract
title: Definition

L'auditing è la valutazione sistematica e indipendente di processi, sistemi e controlli per garantire il raggiungimento efficace e sicuro degli obiettivi organizzativi. 
```

Il corso collega la teoria classica dell'audit alla pratica moderna della cybersecurity, spiegando approcci basati sul rischio, raccolta di evidenze e verifica dei controlli come strumenti per fornire assurance all'organizzazione.

## Risultati di apprendimento
Al termine del corso, lo studente sarà in grado di:

- Definire _audit_ e _assurance_ nel contesto della cybersecurity
- Spiegare i principi dell'auditing basato sul rischio
- Identificare i principali framework di controllo e governance
- Descrivere gli IT General Controls e la loro rilevanza per l'integrità delle informazioni
- Applicare il ragionamento audit per valutare meccanismi di cybersecurity e compliance

## Motivazione
La fiducia digitale dipende dall'integrità dimostrabile di sistemi e dati. L'auditing trasforma la compliance tecnica in assurance credibile, abilitando trasparenza, accountability e fiducia degli stakeholder nella postura di sicurezza dell'organizzazione.

## Concetti fondamentali

### Audit vs Ispezione

L'==auditing== è un processo basato su evidenze e focalizzato sul rischio che valuta il design e l'efficacia dei controlli. A differenza delle ispezioni (basate su regole e punitive), **gli audit mirano a comprendere se i meccanismi di governance, gestione del rischio e controllo supportano adeguatamente gli obiettivi strategici**.

### Evoluzione storica
L'auditing ha origine nell'accountability finanziaria per garantire che i registri riflettessero accuratamente le transazioni. Con l'avvento dei sistemi informativi, la disciplina si è evoluta verso l'IT auditing, verificando affidabilità dei dati, integrità dei sistemi e adeguatezza dei controlli. Gli obiettivi moderni si estendono a cybersecurity, privacy e resilienza digitale.

### Il ruolo degli IT auditor
Gli ==IT auditor== valutano i controlli di sistema relativi ad accesso, change management e operazioni. Il loro ruolo è verificare che la **triade CIA (Confidentiality, Integrity, Availability)** sia **mantenuta** e che le **strutture di governance gestiscano efficacemente il rischio tecnologico**.

In un **_contesto professionale_**:
Le ==certificazioni professionali== (CISA, ISO 27001 Lead Auditor, framework ISACA, ecc.) **definiscono gli standard di competenza in auditing e assurance della cybersecurity**. Queste credenziali validano la conoscenza dei processi di audit, codici etici e requisiti normativi trasversali ai settori industriali.

## Definizione e obiettivi dell'audit

### Definizione
Secondo la ==ISO 19011==, un **_audit_** è un processo sistematico, indipendente e documentato per ottenere evidenze e valutarle oggettivamente rispetto a criteri stabiliti. Il risultato fornisce assurance riguardo compliance, performance o efficacia della governance.


```ad-success
title: Goal Audit
Gli ==audit== mirano a **verificare** che policy, controlli e operazioni **raggiungano i risultati attesi**. Forniscono fiducia a management, regolatori e stakeholder esterni sulla affidabilità, integrità e postura di sicurezza dell'organizzazione.

```

### Tipologie di audit
Tutti seguono una metodologia comune ma con focus diversi:

- **Financial Audit**: valida l'accuratezza dei rendiconti finanziari
- **Operational Audit**: valuta efficienza ed efficacia dei processi
- **Compliance Audit**: testa l'aderenza a leggi, regolamenti o standard
- **Performance Audit**: misura il raggiungimento degli obiettivi
- **IT Audit**: esamina l'infrastruttura tecnologica e l'ambiente di controllo

### Principi dell'audit
- Integrità e condotta etica
- Indipendenza e obiettività
- Dovuta diligenza professionale e competenza
- Approccio basato su evidenze
- Riservatezza e discrezione
- Scetticismo professionale e giudizio critico
## Assurance
### Definizione
L'==assurance== è una **valutazione indipendente e obiettiva che fornisce fiducia agli stakeholder sull'affidabilità, integrità ed efficacia dei processi, controlli o informazioni di un'organizzazione**. L'assurance è sia un engagement che il suo risultato: deriva da attività di audit o review che generano conclusioni basate su evidenze.

### Caratteristiche chiave
- **Indipendente**: eseguita da parti non coinvolte nelle operazioni (audit interno, audit esterno, enti di certificazione)
- **Obiettiva**: basata su evidenze, libera da bias o influenze
- **Guidata da evidenze**: le conclusioni si basano su dati verificabili e test documentati
- **Scopo**: accrescere la fiducia nelle asserzioni del management e nei processi di governance

### Livelli di assurance
- **Reasonable assurance**: alta ma non assoluta confidenza, basata su campionamento e test sufficienti
- **Limited assurance**: confidenza moderata, tipica degli engagement di review
- **No assurance**: osservazioni puramente descrittive o consultive

```ad-attention
title: Risultati negativi forniscono comunque assurance
L'==assurance== **non significa necessariamente un risultato positivo**. 
Rappresenta confidenza basata su evidenze, che i risultati siano buoni o cattivi. Quando un audit rivela debolezze o non conformità, fornisce comunque assurance sullo stato reale dei controlli. Anche un esito negativo dà assurance: assicura che i controlli non soddisfano gli standard attesi. Il valore dell'assurance risiede nella trasparenza e affidabilità, non in risultati favorevoli.

```

## Risk Management e Assurance

### Due prospettive complementari

|Aspetto|Risk Management|Assurance (Internal Audit)|
|---|---|---|
|**Obiettivo**|Identificare, valutare e mitigare minacce al raggiungimento degli obiettivi|Fornire valutazione indipendente su come rischi e controlli sono gestiti|
|**Responsabilità**|Management e staff operativo|Internal audit e altri fornitori di assurance|
|**Natura del lavoro**|Proattivo e continuo|Reattivo e periodico (revisione indipendente)|
|**Focus**|Gestire l'esposizione al rischio e implementare controlli|Testare, verificare e reportare sull'efficacia dei controlli|
|**Output**|Risk register, piani di mitigazione, risk appetite statement|Report di audit, opinion di assurance, raccomandazioni|
|**Orizzonte temporale**|Prospettico|Retrospettivo e valutativo|
|**Domanda chiave**|"Stiamo gestendo efficacemente i nostri rischi?"|"La nostra gestione del rischio è efficace?"|

### Da audit a assurance
L'==audit== è una **valutazione indipendente di processi, controlli o informazioni** rispetto a criteri definiti. L'==assurance== è la **fiducia o confidenza fornita come risultato di quella valutazione**. In sintesi: l'audit è il processo, l'assurance è il risultato. L'auditing fornisce la base di evidenze che supporta l'assurance sull'affidabilità ed efficacia dei controlli e processi di un'organizzazione.

## Principi operativi dell'audit
### Indipendenza e obiettività
- L'==indipendenza== salvaguarda **imparzialità e credibilità**. Gli auditor devono evitare conflitti di interesse, specialmente quando auditano funzioni di sicurezza interne. 
- L'==obiettività== richiede di **valutare le evidenze senza bias**, indipendentemente dalle pressioni organizzative.

```ad-important
title: Scetticismo Professionale
Un **_atteggiamento critico_** è essenziale per identificare incongruenze e potenziali errori. Gli auditor valutano criticamente le evidenze, cercano corroborazione da fonti multiple ed evitano di basarsi esclusivamente sulle asserzioni del management.

```

### Materialità
La ==materialità== definisce la **significatività di un problema rispetto al contesto di rischio complessivo**. 

```ad-example

In cybersecurity, una singola configurazione errata di un account privilegiato può essere materialmente significativa se espone dati sensibili o infrastrutture critiche.
```

### Evidenze di audit
Le ==evidenze di audit== devono essere **sufficienti (in quantità)** e **appropriate (in qualità)** per supportare le conclusioni. Evidenze affidabili rafforzano la credibilità dell'opinione dell'auditor.

Fonti chiave di evidenza:
- **Documentazione e registrazioni**: policy, log, report e file di configurazione
- **Osservazione dei processi**: revisione diretta dell'esecuzione dei controlli in tempo reale
- **Interviste e indagini**: discussioni con i process owner per corroborare le evidenze
- **Procedure analitiche**: confronti di dati, analisi di trend e test di correlazione
- **Re-esecuzione dei controlli**: ripetizione indipendente delle attività per confermarne l'efficacia

>Principio: evidenze credibili, verificabili e tracciabili sostengono ogni conclusione di audit.

## Il processo di audit
1. **Pianificazione**: definire obiettivi, scope e criteri
2. **Comprensione del sistema**: raccogliere contesto e identificare controlli
3. **Valutazione del rischio**: determinare rischi inerenti e di controllo
4. **Progettazione dei test**: stabilire procedure di audit e campionamento
5. **Raccolta delle evidenze**: eseguire fieldwork e documentare i risultati
6. **Valutazione dei risultati**: confrontare le evidenze con i criteri
7. **Reporting**: riepilogare finding, conclusioni e raccomandazioni
### Documentazione dell'audit
I workpaper registrano le procedure eseguite, le evidenze ottenute e il ragionamento applicato. Abilitano riproducibilità, peer review e tracciabilità, garantendo che ogni conclusione di audit sia logicamente supportata da evidenze documentate.
## Etica e qualità
### Etica professionale
Gli auditor devono rispettare codici etici che enfatizzano riservatezza, obiettività e competenza. Violazioni etiche minano la fiducia, danneggiano la credibilità professionale e possono invalidare gli engagement di assurance.

### Quality assurance
Meccanismi di ==quality assurance== (revisioni interne, valutazioni tra pari e assessment esterni) **assicurano conformità agli standard professionali**. Il miglioramento continuo rafforza affidabilità e rilevanza della funzione di audit.

## Sfide moderne
L'auditing moderno affronta nuove complessità:
- **Volumi massivi** di dati e automazione
- **Minacce** di cybersecurity in **evoluzione** e ambienti cloud
- Integrazione di **AI** e **analytics** nel testing dei controlli

>La disciplina si adatta attraverso continuous auditing, test data-driven e risk intelligence.

## Dall'teoria all'applicazione
L'auditing in cybersecurity traduce i principi tradizionali di assurance alle evidenze digitali. Log, export di configurazioni, matrici di controllo accessi e artefatti forensi sostituiscono i registri finanziari come oggetti di audit, mantenendo lo stesso rigore nella valutazione delle evidenze.

## Audit esterno vs audit interno

### Audit esterno
Condotto da **_auditor indipendenti_** o **_società di assurance_**, esterni all'organizzazione. 
Fornisce reasonable assurance sull'accuratezza, correttezza e affidabilità dei rendiconti finanziari o dei controlli di service organization.

Segue standard internazionali quali:
- **ISA** (International Standards on Auditing)
- **ISAE 3402** e **SSAE 18** per engagement di assurance

Assicura credibilità e trasparenza per investitori, regolatori e altri stakeholder. Tipicamente periodico, non continuo, e soggetto a obblighi formali di reporting.

**Focus**: accountability esterna, compliance normativa e fiducia pubblica.

### Audit interno
Eseguito da una **_funzione indipendente all'interno dell'organizzazione_**, che riporta al board o al comitato di audit.

**Obiettivo**: valutare e migliorare l'efficacia di governance, gestione del rischio e controllo interno.

Basato su framework come:
- **COSO** Internal Control
- **COBIT**
- **ISO 9001** / **ISO 27001**

Opera su base continua e orientata al miglioramento. Fornisce al management insight e raccomandazioni per rafforzare le operazioni e ridurre i rischi.

**Focus**: creazione di valore interno, maturità dei controlli e miglioramento dei processi.

### Confronto

|Aspetto|Audit interno|Audit esterno|
|---|---|---|
|**Posizione**|Parte dell'organizzazione|Indipendente dall'organizzazione|
|**Obiettivo**|Migliorare processi, governance e controlli|Fornire assurance esterna su statement o sistemi|
|**Frequenza**|Continuo o periodico|Tipicamente annuale o per engagement|
|**Linea di reporting**|Management / Comitato di audit|Board, azionisti, regolatori, clienti|
|**Standard principali**|COSO, COBIT, framework ISO|ISAE 3000/3402, ISA, SSAE 18|
|**Focus**|Efficienza, rischio, efficacia dei controlli|Accuratezza, compliance, affidabilità|
|**Natura**|Consultivo e preventivo|Certificativo e evidenziale|


```ad-note
title: Sintesi

L'==auditing== stabilisce fiducia attraverso la valutazione indipendente dei meccanismi di governance e controllo. Comprendere questi fondamenti è essenziale prima di affrontare l'auditing basato sul rischio e l'assurance IT guidata da framework.
```


# Risk-Based Auditing and Frameworks

## Introduzione al Risk-Based Auditing
==Il risk-based auditing== (audit basato sul rischio) è un metodo che concentra i controlli dove i rischi sono più alti, cioè dove è **più probabile** che si verifichi un problema e dove le **conseguenze** sarebbero più gravi.

Invece di controllare tutto allo stesso modo, l’auditor dà **priorità alle aree critiche**, così:
- si **usano meglio le risorse** (tempo e persone);
- i risultati dell’audit (**finding**) sono **più utili e mirati**;
- l’attività di audit è **coerente con gli obiettivi dell’organizzazione**;
- si passa da un approccio **reattivo** (scoprire gli errori dopo) a uno **proattivo** (prevenirli in anticipo).
## Il modello di audit risk
### Formula del rischio
**Audit Risk (AR) = Inherent Risk × Control Risk × Detection Risk**

- **Inherent Risk (IR)**: probabilità che si verifichi un errore o un'irregolarità in assenza di controlli interni.
- **Control Risk (CR)**: probabilità che i controlli interni esistenti falliscano nel prevenire o rilevare tale errore.
- **Detection Risk (DR)**: probabilità che le procedure di audit falliscano nell'identificare l'errore residuo.

>Gestire l'**audit risk** implica bilanciare profondità dei test, sufficienza delle evidenze e livello di confidenza dell'assurance.

### Inherent Risk e Control Risk

- L'==Inherent Risk== riflette la vulnerabilità intrinseca di un processo o sistema. 
- Il ==Control Risk== dipende dal design e dall'efficacia operativa delle misure di protezione. Una comprensione accurata di entrambi consente all'auditor di progettare strategie di testing proporzionate ed evitare procedure ridondanti.

### Detection Risk
Il ==Detection Risk== rappresenta la probabilità che le procedure di audit falliscano nel rilevare un errore materiale o una debolezza di controllo. Dipende da natura, tempistica ed estensione dei test, oltre che dall'efficacia delle procedure e dal giudizio dell'auditor.

Aspetti chiave:
- Inversamente correlato al livello di assurance: DR più basso → maggiore confidenza
- Gestito attraverso aumento della dimensione del campione, profondità dei test ed evidenze corroboranti
- Influenzato da competenza dell'auditor, strumenti di automazione e vincoli temporali
- Bilanciare DR con inherent e control risk assicura che l'audit risk complessivo rimanga a un livello accettabile

```ad-example

Se inherent e control risk sono elevati, il detection risk deve essere ridotto applicando procedure di audit più estensive o rigorose.
```

## Materialità
```ad-abstract
title: Definition

La ==materialità== è la soglia oltre la quale un errore o una debolezza di controllo diventa abbastanza significativa da influenzare decisioni o conclusioni di audit. Guida scope, profondità e prioritizzazione del lavoro di audit.
```

==Aspetti chiave==
- **Quantitativo**: impatto misurabile o dimensione dell'errore
- **Qualitativo**: sensibilità o natura del problema
- **Contestuale**: dipende da risk appetite ed aspettative normative

In cybersecurity, anche una singola vulnerabilità critica può essere materiale se minaccia sistemi core o dati sensibili.

### Materialità e rischio
Le soglie di materialità definiscono quali debolezze di controllo o incidenti sono abbastanza significativi da influenzare le conclusioni dell'auditor o le decisioni degli stakeholder. In un audit di cybersecurity, anche eventi a bassa probabilità (es. breach di accesso privilegiato) possono essere materiali se il loro impatto potenziale è critico.

La materialità interagisce con il modello di audit risk ($AR = IR × CR × DR$): maggiori inherent o control risk, o capacità di detection limitata, richiedono una soglia di materialità più bassa e test più estesi. Insieme, rischio e materialità guidano giudizio di audit, strategia di campionamento e valutazione delle evidenze.

## Assertions
Le ==assertions== sono affermazioni fatte dal management riguardo dati, processi o sistemi. Categorie comuni includono:
- **Existence**: l'elemento o controllo esiste effettivamente
- **Completeness**: tutti gli elementi rilevanti sono inclusi
- **Accuracy**: le informazioni sono registrate correttamente
- **Authorization**: le azioni sono propriamente approvate
- **Presentation**: i dati sono appropriatamente divulgati o formattati

Gli auditor progettano test per verificare oggettivamente ciascuna assertion.

## COSO
### Contesto storico
Il ==Committee of Sponsoring Organizations of the Treadway Commission== (==COSO==) è **un'iniziativa privata statunitense** istituita nel 1985 **per migliorare la qualità del reporting finanziario e del controllo interno**. Creato in risposta alle frodi aziendali dei primi anni '80, seguendo le raccomandazioni della Treadway Commission sul reporting finanziario fraudolento.

Sponsorizzato da cinque associazioni professionali: AICPA, IIA, FEI, IMA e AAA.

Nel 1992, COSO ha rilasciato l'Internal Control — Integrated Framework, successivamente espanso all'Enterprise Risk Management (ERM) nel 2004 e 2017.

>COSO fornisce la base globale per i moderni framework di controllo interno e gestione del rischio.

### Controlli interni

**Definizione**: Processi, policy e procedure stabiliti per garantire che gli obiettivi siano raggiunti efficacemente, efficientemente ed eticamente.

**Scopo**: Proteggere gli asset, garantire reporting affidabile e supportare compliance legale e normativa.

Visione COSO (1992, 2013): Un processo attuato da board, management e personale per fornire reasonable assurance su operazioni, reporting e compliance.

**Natura**: Continuativo, integrato nelle attività quotidiane.

**Rilevanza**: La fondazione di ogni sistema di audit, risk management e governance.

### Il modello COSO
Il ==COSO Framework== definisce **cinque componenti interrelate del controllo interno**:

1. **Control Environment**: tono etico, governance e accountability
2. **Risk Assessment**: identificazione e valutazione dei rischi per gli obiettivi
3. **Control Activities**: policy e procedure che mitigano tali rischi
4. **Information & Communication**: garantire flusso affidabile di dati
5. **Monitoring**: valutare la performance dei controlli nel tempo

COSO rimane una pietra miliare sia per i sistemi di controllo finanziario che IT.

### Obiettivi del controllo interno

1. **Operations**: garantire uso efficace ed efficiente delle risorse per raggiungere gli obiettivi organizzativi
2. **Reporting**: mantenere reporting finanziario e non finanziario affidabile, tempestivo e trasparente
3. **Compliance**: aderire a leggi, regolamenti e policy interne applicabili

## Tipologie e obiettivi dei controlli

### Classificazione per scopo ed esecuzione

- **Controlli preventivi**: bloccano errori o incidenti prima che si verifichino (es. restrizioni di accesso)
- **Controlli detective**: identificano problemi dopo il verificarsi (es. monitoraggio dei log)
- **Controlli correttivi**: ripristinano condizioni normali (es. deployment di patch)

I controlli possono essere anche manuali o automatizzati, ciascuno con profili di affidabilità distinti.

### Control objectives

Garantire la triade CIA all'interno dei sistemi informativi:
- **Controllo degli accessi** per preservare la **confidenzialità**
- **Validazione degli input** per proteggere l'**integrità**
- **Ridondanza e backup** per garantire la **disponibilità**

>Insieme, questi obiettivi sostengono resilienza operativa e fiducia nell'infrastruttura digitale.

## Risk-Control-Test Relationship
**Ogni rischio si collega a uno o più controlli**, e **ogni controllo è verificato attraverso test specifici**. Questa matrice (==Risk and Control Matrix==, RCM) fornisce trasparenza e tracciabilità. Collega scope di audit, procedure ed evidenze direttamente alle priorità di rischio organizzative.

### Esempio di RCM

|Rischio|Controllo|Procedura di test|Evidenza|
|---|---|---|---|
|Accesso non autorizzato|Applicazione di MFA|Revisione configurazione sistema e test autenticazione|Screenshot impostazioni policy, audit log|

Questa struttura consente documentazione chiara e supporta la riproducibilità delle conclusioni di audit.

## Campionamento e valutazione delle evidenze

### Sampling in auditing
Testare ogni transazione è impraticabile, quindi si ricorre al campionamento:
- Statistico
- A giudizio (non statistico)

Il campionamento deve bilanciare efficienza con assurance, garantendo che le conclusioni rimangano valide.
### Valutazione delle evidenze
Sufficienza e appropriatezza delle evidenze dipendono dal livello di rischio e dalla criticità del controllo. Aree ad alto rischio richiedono corroborazione da più tipi di evidenze: documenti, log, interviste e re-esecuzione. Il giudizio professionale dell'auditor determina quando la base di evidenze giustifica una conclusione.


## Panoramica sui framework di controllo
I framework di controllo traducono i principi di governance in set strutturati di controlli. Promuovono consistenza, comparabilità e accountability tra le organizzazioni. Framework come COSO, COBIT, ISO 27001 e NIST CSF aiutano gli auditor a benchmarking delle pratiche e all'allineamento con le aspettative normative.

### COBIT 2019
**COBIT** = Control Objectives for Information and Related Technologies (di ISACA - Information Systems Audit and Control Association)

Definisce obiettivi di governance e management attraverso domini:

- **Evaluate, Direct, Monitor (EDM)**: supervisione strategica e governance
- **Align, Plan, Organize (APO)**: policy, strategia e pianificazione
- **Build, Acquire, Implement (BAI)**: sviluppo sistema e integrazione
- **Deliver, Service, Support (DSS)**: operazioni e delivery dei servizi
- **Monitor, Evaluate, Assess (MEA)**: performance e compliance

COBIT allinea la governance IT con la strategia di business e il valore per gli stakeholder.

_Nota_: Management (APO, BAI, DSS, MEA) / Governance (EDM)

### ISO/IEC 27001 e Annex A
ISO/IEC 27001 stabilisce un Information Security Management System (ISMS), garantendo protezione continua degli asset informativi. L'Annex A enumera 93 controlli attraverso quattro temi: organizzativo, persone, fisico e tecnologico. Questi controlli operazionalizzano l'ISMS e supportano l'assurance basata su certificazione.

### NIST Cybersecurity Framework (CSF)
Il NIST CSF organizza le attività di cybersecurity in cinque funzioni core:

1. **Identify**: comprendere asset, rischi e contesto organizzativo
2. **Protect**: implementare salvaguardie per garantire sicurezza di dati e servizi
3. **Detect**: identificare e analizzare eventi di cybersecurity
4. **Respond**: contenere e mitigare gli incidenti
5. **Recover**: ripristinare capacità e servizi dopo un'interruzione

CSF 2.0 estende il framework per includere governance e gestione del rischio della supply chain, collegando direttamente la cybersecurity ai risultati di business.

### NIST SP 800-53
NIST Special Publication 800-53 offre un catalogo dettagliato di controlli ampiamente utilizzato dalle agenzie federali statunitensi. Definisce 20 famiglie di controlli, inclusi Access Control, Audit and Accountability, System and Communications Protection, e Security Assessment and Authorization. Il suo rigore lo rende un riferimento globale per il design e il testing dei controlli in infrastrutture critiche.


## Standard di assurance: ISAE e SOC

### ISAE (International Standard on Assurance Engagements)
Categoria di standard professionali emessi dall'International Auditing and Assurance Standards Board (IAASB), parte dell'International Federation of Accountants (IFAC). Diversi documenti su assurance.

### ISAE 3402: Panoramica
**ISAE 3402** (Assurance Reports on Controls at a Service Organization) è uno standard internazionale emesso dall'IAASB. Definisce come un auditor indipendente valuta e riporta sul design e sull'efficacia operativa dei controlli presso un'organizzazione di servizi.

**Scopo**: fornire assurance alle user entity e ai loro auditor che i processi in outsourcing sono affidabili e ben controllati.

**Si applica a**: servizi che impattano il reporting finanziario, come payroll, contabilità o hosting dati per sistemi ERP.

**Scope**: controlli presso fornitori terzi rilevanti per il reporting finanziario.

### Service Organizations e User Entities

|Termine|Significato|
|---|---|
|**Service Organization**|Fornitore terzo che esegue funzioni per un'altra entità che impattano il suo reporting finanziario (es. processore payroll, data center)|
|**User Entity**|L'azienda che esternalizza parte delle sue operazioni e si affida ai controlli della service organization|
|**User Auditor**|L'auditor esterno della user entity che si basa sul report ISAE 3402 / SOC 1|

**Esempio**: Una banca utilizza un cloud provider esterno per ospitare la sua piattaforma di contabilità prestiti: il provider è la service organization, e i suoi controlli sono rilevanti per i rendiconti finanziari della banca.

### Tipi di report ISAE 3402

|Tipo|Descrizione|Periodo coperto|Utilità|
|---|---|---|---|
|**Type I**|Design e implementazione dei controlli a un momento specifico|Una data|Verifica il design dei controlli|
|**Type II**|Design ed efficacia operativa dei controlli in un periodo (6-12 mesi)|Periodo temporale|Testa la performance dei controlli|

**Punto chiave**: I report Type II forniscono assurance più forte perché testano se i controlli hanno operato efficacemente nel tempo.

### Relazione con i SOC Reports (AICPA)
L'AICPA (U.S.) ha sviluppato il framework di reporting SOC sotto SSAE 18, che rispecchia i principi di ISAE 3402. Entrambi gli standard descrivono lo stesso tipo di engagement: assurance sui controlli presso service organization.

- SOC 1 reports = equivalente statunitense di ISAE 3402
- I SOC report si espandono oltre il reporting finanziario attraverso SOC 2 e SOC 3
- ISAE 3402: standard internazionale
- SOC 1: implementazione statunitense dello stesso concetto

### Tipologie di SOC Report — Framework AICPA

|Report|Standard|Focus|Audience|
|---|---|---|---|
|**SOC 1**|SSAE 18 / AT-C 320|Controlli rilevanti per reporting finanziario|User auditor, CFO|
|**SOC 2**|SSAE 18 / AT-C 205|Controlli su security, CIA e privacy|Clienti, regolatori, partner|
|**SOC 3**|SSAE 18 / AT-C 205|Versione pubblica e riassuntiva di SOC 2 (senza dettagli sensibili)|Pubblico generale, marketing|

- SOC 1 ⇔ ISAE 3402 (focus finanziario)
- SOC 2 & 3 ⇔ assurance più ampia su IT e data governance

### Perché ISAE 3402 e SOC Reports sono importanti
**Assurance e fiducia in ambienti in outsourcing**

Le organizzazioni si affidano sempre più a fornitori terzi per processi critici. ISAE 3402 e i SOC report danno confidenza che questi fornitori:

- Hanno controlli documentati ed efficaci
- Mantengono integrità, confidenzialità e disponibilità dei dati
- Supportano affidabilità del reporting finanziario e compliance normativa

Le user entity possono sfruttare questi report invece di duplicare il testing dei controlli sui fornitori.

**Risultato**: trasparenza, riduzione della duplicazione di audit e outsourcing fidato.

### ISAE 3402 vs SOC Reports (Riepilogo)

|Aspetto|ISAE 3402|SOC Reports|
|---|---|---|
|**Emittente**|IAASB / IFAC|AICPA (U.S.)|
|**Standard**|ISAE 3402|SSAE 18|
|**Scope**|Controlli service organization rilevanti per reporting finanziario|SOC 1: finanziario; SOC 2/3: IT e privacy più ampi|
|**Tipo report**|Type I / Type II|Stessa struttura: Type I / Type II|
|**Riconoscimento**|Internazionale|U.S. e riconoscimento globale|
|**Relazione**|Standard concettuale|Framework pratico di reporting|

Origini diverse — stesso obiettivo di assurance: fiducia negli ambienti di controllo di terze parti.

## Altri framework e concetti

### GDPR e audit della protezione dati
Sotto il ==General Data Protection Regulation (GDPR)==, gli** audit valutano la compliance con i principi di protezione dati quali liceità, correttezza, limitazione delle finalità, minimizzazione e integrità**. Gli auditor verificano l'esistenza di misure tecniche e organizzative (TOM) e valutano la documentazione di accountability e le procedure di gestione delle violazioni.

### Misure Tecniche e Organizzative (TOM)
Controlli che garantiscono protezione dati, mitigazione del rischio e compliance (es. GDPR, ISO 27001, SOC 2).

**Misure tecniche**:
- Crittografia, controllo accessi, backup, monitoraggio

**Misure organizzative**:
- Policy, formazione, incident response, gestione fornitori

Le TOM sono le salvaguardie pratiche che supportano i framework di sicurezza e compliance.

### Continuous Auditing
Il continuous auditing integra automazione e analytics per eseguire test dei controlli in tempo quasi reale. Supporta l'early detection di breakdown dei controlli, frodi o misconfigurazioni, colmando il divario tra audit periodici tradizionali e modelli di assurance continua. Principalmente interno.

### Mappatura dei framework
Gli auditor spesso cross-referenziano controlli tra framework (es. mappare NIST CSF su ISO 27001 Annex A o COBIT). Queste mappature garantiscono copertura completa, riducono ridondanza e migliorano interoperabilità attraverso regimi di compliance.

## Il toolbox dell'auditor
Gli auditor moderni impiegano un toolkit diversificato:

- Revisione di policy e documentazione
- Walkthrough e interviste
- Campionamento e re-esecuzione
- Ispezione delle configurazioni
- Data analytics e query automatizzate
- Osservazione dell'operatività dei controlli

L'integrazione di metodi tecnici e analitici rafforza l'affidabilità dell'audit.

## Flusso del processo di risk-based audit
Un workflow strutturato garantisce consistenza nell'audit:

1. **Plan**: definire obiettivi e scope
2. **Assess Risk**: identificare e classificare aree critiche
3. **Design Tests**: sviluppare procedure su misura
4. **Execute**: raccogliere e analizzare evidenze
5. **Evaluate**: confrontare risultati con criteri
6. **Report**: comunicare finding e raccomandazioni
7. **Follow-Up**: verificare remediation e miglioramento continuo


```ad-seealso
title: Sintesi

Il ==risk-based auditing== allinea le attività di assurance con le priorità organizzative e l'esposizione al rischio. Integrando framework di controllo come COSO, COBIT, ISO 27001 e NIST, gli auditor stabiliscono una base strutturata per l'auditing specifico IT.
```




# IT Audit Domains and Cases

## Introduzione all'IT Audit
L=='IT auditing== valuta la governance, l'infrastruttura e i controlli operativi dei sistemi informativi. Il suo **scopo** è **_verificare che la tecnologia supporti gli obiettivi organizzativi in modo sicuro, efficiente e affidabile_**. Attraverso un approccio strutturato, l'IT audit colma il divario tra assurance manageriale e validazione tecnica.

## IT General Controls (ITGC)
Gli ==ITGC== costituiscono la **base dell'affidabilità dei sistemi e dei controlli automatizzati**. Sono tipicamente raggruppati in tre domini:

1. **Access Management**: garantire accesso autorizzato e tracciabile ai sistemi
2. **Change Management**: mantenere modifiche di sistema controllate
3. **IT Operations**: sostenere funzionamento coerente, sicuro e recuperabile dei sistemi

ITGC solidi sono alla base di ogni livello di assurance dell'audit.

## Domini dei controlli IT

### Access Management Controls
Framework efficaci di controllo degli accessi includono:

- Procedure Joiner-Mover-Leaver per la gestione del ciclo di vita degli utenti
- Role-Based Access Control (RBAC) per applicare il principio del minimo privilegio
- Segregation of Duties (SoD) per prevenire conflitti e frodi
- Monitoraggio degli account privilegiati per azioni amministrative
- Multi-Factor Authentication (MFA) per rafforzare la resilienza dell'autenticazione

Gli auditor valutano sia la configurazione che l'applicazione operativa dei controlli.

### Change Management Controls

Il change management garantisce che le modifiche ai sistemi siano autorizzate, testate e tracciabili. Gli auditor esaminano:

- Sistemi di version control (es. Git) per tracciare le modifiche al codice
- Workflow di test e approvazione che validano l'affidabilità
- Documentazione delle release e piani di rollback che confermano la reversibilità

Un change management debole è una fonte frequente di incidenti di sicurezza e fallimenti operativi.

### IT Operations Controls

Le operazioni IT forniscono stabilità e continuità ai sistemi digitali. Aree chiave di controllo includono:

- Validazione di backup e recovery
- Gestione di patch e vulnerabilità
- Gestione di incident e problem con tracciamento della root cause
- Scheduling e monitoraggio dei job per processi automatizzati
- Capacity management e pianificazione della business continuity

Questi controlli garantiscono resilienza del servizio e protezione dei dati.
## Application Controls

I controlli applicativi operano all'interno di ambienti software specifici, garantendo accuratezza e completezza dell'elaborazione. Esempi includono:

- Validazione degli input per prevenire corruzione dei dati
- Controlli di elaborazione per confermare l'integrità
- Riconciliazione degli output per accuratezza e completezza
- Controlli di interfaccia che garantiscono l'integrità dello scambio dati

Quando automatizzati, riducono significativamente il rischio operativo.

### Testing dei controlli automatizzati

Gli auditor valutano i controlli automatizzati ispezionando parametri di configurazione, regole logiche e meccanismi di gestione delle eccezioni. Evidenze tipiche includono screenshot, export di configurazioni e log di sistema. I controlli automatizzati offrono maggiore affidabilità, ma solo se i sistemi sono propriamente configurati, mantenuti e protetti da modifiche non autorizzate.

## Tecniche e strumenti di audit

### CAAT (Computer-Assisted Audit Techniques)

Le CAAT integrano la tecnologia nel processo di audit. Strumenti e linguaggi comuni (es. SQL, Python, ACL, IDEA) abilitano:

- Analisi dell'intera popolazione di dati
- Rilevamento di anomalie, duplicati o eccezioni
- Validazione incrociata dell'integrità transazionale

Le CAAT migliorano efficienza, accuratezza e riproducibilità del testing di audit.

### Esempio di data analytics in audit

La data analytics può identificare problemi sistemici, come:

- Pagamenti duplicati o transazioni inconsistenti
- Record orfani che violano l'integrità referenziale
- Tentativi di accesso non autorizzato rilevati nei log di sistema

Le query automatizzate permettono agli auditor di validare la performance dei controlli su dataset di grandi dimensioni.

## Ambiti specialistici dell'IT audit

### Audit della sicurezza logica

Gli audit di sicurezza logica verificano che i meccanismi di accesso e protezione delle informazioni siano efficaci. Aree di focus chiave includono:

- Sistemi di Identity and Access Management (IAM)
- Policy di password e standard di crittografia
- Segmentazione di rete e access control list (ACL)
- Meccanismi di logging, monitoraggio e alerting

Gli auditor valutano la compliance con ISO 27002 (Information Security, Cybersecurity and Privacy Protection — Information Security Controls) e best practice correlate.

### Audit di infrastruttura e rete

Gli audit di infrastruttura valutano l'integrità e la resilienza di componenti fisiche e virtuali. Procedure tipiche includono:

- Revisione di configurazioni di firewall e router
- Verifica dei livelli di patch e dell'hardening dei sistemi
- Verifica dei processi di vulnerability management
- Assicurare che gli inventari degli asset siano accurati e completi

Una governance di rete solida supporta assurance di cybersecurity affidabile.

### Cloud Auditing

Gli ambienti cloud introducono modelli di responsabilità condivisa tra provider e cliente. Gli auditor devono:

- Distinguere tra domini di controllo del provider e del client
- Revisionare report SOC 2 e certificazioni per l'assurance del provider
- Valutare ruoli IAM, crittografia e segregazione dei dati
- Verificare SLA contrattuali e obblighi di data residency

Gli audit cloud richiedono comprensione sia della compliance normativa che della configurazione tecnica.

### Audit di vendor e terze parti

Le organizzazioni si affidano sempre più a fornitori di servizi esterni. Gli auditor valutano:

- Controlli contrattuali e SLA
- Meccanismi di monitoraggio della performance dei vendor
- Report di assurance di terze parti (es. SOC 2, ISO 27001)
- Coordinamento dell'incident response e clausole di protezione dati

Un auditing robusto di terze parti mitiga i rischi di supply chain e outsourcing.

### DevOps e Continuous Delivery

Gli ambienti DevOps combinano velocità e automazione, creando nuove sfide di audit. Gli auditor esaminano:

- Pipeline di change per evidenze di testing, approvazione e segregazione
- Documentazione di peer review e log di deployment automatizzati
- Meccanismi di rollback e version control

Un auditing efficace bilancia agilità con disciplina di controllo, garantendo tracciabilità in cicli di delivery veloci.

### Privacy Audits

Gli audit di privacy garantiscono compliance con GDPR e altre leggi sulla protezione dati. Valutano:

- Liceità e gestione del consenso
- Minimizzazione dei dati e limitazione delle finalità
- Policy di retention e cancellazione sicura
- Misure di crittografia e pseudonimizzazione
- Gestione dei diritti degli interessati (accesso, rettifica, cancellazione)

Gli audit di privacy collegano compliance legale con enforcement tecnico.

### Audit di AI e Machine Learning

L'auditing di sistemi AI coinvolge la valutazione sia della governance dei modelli che delle implicazioni etiche. Dimensioni chiave includono:

- Data lineage e qualità dei dataset di training
- Fairness, bias ed explainability degli output del modello
- Monitoraggio e drift detection per mantenere affidabilità
- Framework di accountability che definiscono supervisione umana

Gli auditor valutano se i sistemi AI si allineano ai principi di trasparenza, accountability e non discriminazione.

## Evidenze negli IT audit

Negli IT audit, le evidenze includono artefatti digitali come log di sistema, file di configurazione, access review, screenshot e report automatizzati. L'autenticità, integrità e tracciabilità delle evidenze ne determinano l'affidabilità. Gli auditor documentano fonte e contesto di ogni artefatto per mantenere un audit trail difendibile.

## Finding e reporting

### Finding comuni negli IT audit

I finding frequenti includono:

- Provisioning degli accessi debole o inconsistente
- Autorizzazioni o documentazione di change mancanti
- Backup incompleti o non testati
- Meccanismi di monitoraggio o alerting insufficienti
- Policy di sicurezza obsolete o disallineate

Ogni finding deve essere supportato da evidenze, valutato per rischio e accompagnato da raccomandazioni di remediation.

### Reporting dei risultati dell'IT audit

I report di audit sintetizzano le evidenze in insight azionabili. Struttura standard:

**Criterio → Condizione → Causa → Effetto → Raccomandazione**

Ogni problema include un rating di rischio e una risposta del management, garantendo tracciabilità e accountability. Un reporting efficace comunica sia profondità tecnica che rilevanza strategica.

## Casi di studio

### Case Study 1: Identity and Access Management

**Scenario**: Una piattaforma SaaS gestisce migliaia di utenti con ruoli in evoluzione.

**Rischi**: Privilegi eccessivi, account dormienti e mancanza di revisione periodica.

**Controlli**: Provisioning automatizzato, ricertificazione periodica degli accessi e disattivazione tempestiva degli account inattivi.

**Focus dell'audit**: Verificare l'applicazione di RBAC e la frequenza di review per garantire compliance con il least privilege.

### Case Study 2: Change Management

**Scenario**: Pipeline di continuous integration e delivery (CI/CD) che effettuano aggiornamenti frequenti.

**Procedure di audit**:

- Verificare autorizzazione delle modifiche al codice
- Revisionare evidenze di test e approvazione
- Confermare capacità di rollback e versioning

**Obiettivo**: Garantire delivery rapida senza compromettere controllo e tracciabilità.

### Case Study 3: Data Analytics Audit

**Scenario**: Log di eventi di sicurezza analizzati per anomalie.

**Metodo**: Utilizzare CAAT per rilevare outlier, accessi non autorizzati o asset non monitorati.

**Valore dell'audit**: Dimostrare la capacità di rilevamento continuo e identificare gap di controllo attraverso analisi automatizzata.

```ad-seealso
title: Sintesi

L'IT audit fornisce assurance strutturata sulla governance, sicurezza e affidabilità dei sistemi informativi. Attraverso la valutazione di ITGC, controlli applicativi, sicurezza logica e configurazioni tecniche, gli auditor collegano compliance normativa con prestazioni operative. L'uso di CAAT, l'analisi di evidenze digitali e l'applicazione di framework di controllo permettono agli auditor di fornire assurance credibile in ambienti tecnologici complessi e in rapida evoluzione.
```
