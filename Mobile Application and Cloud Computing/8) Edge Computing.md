# Beyond Cloud
Alcune applicazioni moderne (es. auto autonome, droni, realtà aumentata) richiedono **tempi di risposta molto bassi**, che il cloud, da solo, non può garantire.

# Application Landscape
Metriche fondamentali di latenza:
- **MTP (Motion-to-Photon)** → tempo tra un movimento fisico e la risposta visiva (importante in VR/AR).
- **PL (Perceivable Latency)** → soglia oltre la quale l’utente percepisce un ritardo.
- **HRT (Human Response Time)** → tempo medio di reazione umana (~100–200 ms).

![[M124.png]]

```ad-attention
title: Uncovered Zone
Indica un’area di latenza dove il **cloud non è abbastanza veloce** per supportare alcune applicazioni sensibili (ad esempio giochi VR o auto autonome).

```

# Cloud DC Distribution and Latency
Si cita uno **studio del 2021 (Khang Dang et al., ACM IMC)** dove:

- 115.000 sonde sono state distribuite in oltre 140 Paesi per misurare la **latenza dei data center cloud**.
- Risultato: anche se i provider cloud sono molto diffusi, la latenza **rimane elevata** in molte aree geografiche.

💡 _Significato_: il cloud ha ancora limiti di prossimità: non sempre c’è un data center “vicino” all’utente.
![[M125.png]]
# Cloud Limitation
**Il cloud da solo non basta**:

- Alcune app (fabbriche smart, veicoli autonomi, droni, assistenti vocali) **generano troppi dati** e **richiedono risposte in tempo reale**.
- L’invio continuo di questi dati al cloud genera **latenza e congestione**.

```ad-success
title: Solution
**Spostare parte dell’elaborazione e dello storage più vicino agli utenti**, cioè verso **l’Edge**.

```

>**“Portare il cloud ai margini della rete”** = Edge Computing.

# Cloud-Fog-Edge Computing
- **Cloud Computing** → elaborazione centralizzata in grandi data center (potente ma lontana).
- **Fog Computing** → “nebbia”: uno strato intermedio che collega cloud ed edge, distribuendo il carico.
- **Edge Computing** → elaborazione ai margini, cioè _vicinissimo alla sorgente dei dati_.

👉 L’obiettivo è **ridurre la latenza** e **limitare il traffico verso il cloud** elaborando i dati localmente.

![[M126.png]]

# Edge Computing in 5G
Questa è una **architettura a livelli** che mostra _come i dati vengono gestiti ed elaborati_ in punti diversi della rete.

- **UE (User Equipment)** → il dispositivo dell’utente finale: smartphone, sensore IoT, droni, auto, ecc.
- **RAN (Radio Access Network)** → la rete radio (antenne 4G/5G) che connette i dispositivi.
- **Far Edge DC** → piccoli server locali, spesso installati **vicino alle torri 5G** o ai gateway di rete.
    - Fanno elaborazioni immediate, ad esempio filtrare dati o rispondere a comandi in tempo reale.
- **Edge DC (Data Center di bordo)** → centri di calcolo regionali o aziendali.
    - Raccolgono dati da vari Far Edge e li elaborano a bassa latenza.
- **Core DC (Cloud Data Center)** → il grande cloud globale (AWS, Google, Azure, ecc.), dove avviene l’elaborazione pesante e l’archiviazione a lungo termine.

![[M127.png]]

Questa slide serve a **classificare i tipi di applicazioni** in base a _quanto velocemente devono ricevere una risposta_:
- **Real-time (<1 ms)** → risposta immediata.  
    🔹 Serve per applicazioni critiche come auto autonome, robot o realtà aumentata.  
    🔹 L’elaborazione avviene _molto vicino all’utente_ (Far Edge o dispositivo).
- **Near real-time (1–10 ms)** → risposta molto rapida ma non istantanea.  
    🔹 Usato per streaming, gaming online, o gestione dinamica di rete.  
    🔹 Avviene nell’_Edge Data Center_ (locale o regionale).
- **Non real-time (≫10 ms)** → può tollerare ritardi.  
    🔹 Per analisi, backup, o machine learning offline.  
    🔹 Avviene nel _Cloud centrale (Core DC)_.

![[M128.png]]
