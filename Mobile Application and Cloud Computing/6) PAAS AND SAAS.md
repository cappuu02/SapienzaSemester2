# IaaS (Infrastructure as a Service)
È il livello più “basso” del cloud:
- Il provider fornisce **infrastruttura virtuale** (server, rete, storage).
- L’utente gestisce **sistemi operativi, middleware e applicazioni**.
- Esempi: AWS EC2, Microsoft Azure VM, Google Compute Engine.

Un utente IaaS può sviluppare software e distribuirlo ad altri: per esempio, può creare una web app installata sui propri server virtuali.
# SAAS
**SaaS** è il livello più “alto” dei servizi cloud.
An IaaS user can develop software that is delivered to other users.
==SaaS (Software as a Service)== refers to software applications that are delivered as a service, that is used without managing their underlying infrastructure or platform. 
Users can be either humans or other software systems. 

>**_SaaS_** = software già pronto, accessibile online, senza necessità di installazione/manutenzione.

```ad-example
Gmail, Google Docs, Microsoft 365, Salesforce, Zoom.

```

![[M84.png|400]]

# PAAS
È uno strato intermedio tra IaaS e SaaS.

- Il provider fornisce **una piattaforma di sviluppo completa** (sistema operativo, linguaggi, database, strumenti di sviluppo).
- Il programmatore può concentrarsi **solo sul codice e sull’applicazione**, senza preoccuparsi della configurazione del server o del sistema operativo.

>==PaaS== = piattaforma pronta per sviluppare, testare e distribuire applicazioni.

```ad-example
Google App Engine

```

![[M85.png|400]]

Let’s now focus on how to deliver a software as a service in case the users are other programs. 
As the software is included in a larger application, this software is accessed through an **_API (Application Program Interface)_**, and since they are accessed exploiting the web technologies (**_HTTP_** is the de-facto standard), sometimes they are called **_Web-API_**.

![[M86 1.png]]

- ==Client application (consumer)==→ l’app che usi sul telefono.
    - È l’utente finale che invia richieste al sistema (“Share”, “Hello!”, “Timeline”).
    - Comunica con il backend tramite **Web API** (cioè richieste HTTP verso un server).
- ==SOCNET backend (server application / provider)== → il cervello del sistema.
    - Riceve le richieste dai client e le elabora.
    - Espone API per operazioni come _Share_ o _Timeline_.
- ==SOCNET infra (infrastructure layer)== → componenti interni che gestiscono funzioni specifiche:
    - **Friends** → aggiunge e rileva amici.
    - **Messages** → salva e cerca messaggi.  
        Queste componenti comunicano **tra loro** tramite **inter-server API calls** (cioè API usate _dall’interno_ del sistema, non da utenti esterni).

Flusso Comunicazioni:
- **L’utente sull’app mobile (client)** invia una richiesta, es. “Share post”.
- La richiesta viaggia su Internet → raggiunge il **SOCNET backend**.
- Il backend, per completare l’operazione, può:
    - Interagire con altre parti della sua infrastruttura (Friends, Messages, ecc.) tramite API interne.
    - Salvare dati, aggiornare la timeline, ecc.
- Il backend restituisce la risposta al client → ad esempio, “post condiviso”.
- Il browser web (altra interfaccia client) può mostrare lo stesso contenuto aggiornato.

**_Example of operation_**
- Client invia un messaggio di Hello e lo condivide.
	- Dunque il client genera una HTTP request.
- Il backend (SOCNET backend) elabora la richiesta.
	- SOCNET backend genera una HTTP response.
- il client ha l-interfaccia aggiornata che indica con successo che lo share è avvenuto.
![[M87.png]]

**_Access Scope_**
![[M88.png]]

**_HTTP (Hyper Text Transfer Protocol)_**
![[M89.png]]

**_REST API_**
```ad-abstract
title: Definizione
==REST== significa **REpresentational State Transfer** — è **uno stile di architettura per creare servizi web**.  
Le ==REST API (o API RESTful)== permettono a due sistemi diversi (ad esempio, un’app e un server) di **comunicare via Internet** usando **le regole standard del protocollo HTTP** (lo stesso usato dai siti web).

In parole semplici:
Una **REST API** è un “ponte” che permette a un programma (client) di chiedere dati o servizi a un altro programma (server).  
➡️ Il client manda una **richiesta HTTP**, e il server risponde con dei **dati strutturati**, di solito in **JSON**.

```

Un'app (client) chiama la REST API usando le stesse regole di un browser dunque fa richieste HTTP (GET e POST). A differenza del browser, che riceve **pagine HTML** da mostrare sullo schermo,  
una REST API restituisce **dati puri**, in formato **JSON** o **XML**. L’app poi userà questi dati per mostrarli graficamente all’utente (es. la scheda prodotto).

Tutto ciò che la REST API gestisce (utenti, prodotti, messaggi, post…) è visto come una **risorsa** (_resource_).  Ogni risorsa è identificata da un **URL** e può essere manipolata tramite le operazioni HTTP (GET, POST, PUT, DELETE).

>Rest API è lo standard web/mobile.

![[M90.png]]

**_CONTRASTING REST WITH NON-HTTP-COMPLIANT WEB APIS_**
Tutte le API web usano HTTP, ma non tutte seguono le regole di HTTP come fanno le API REST. Ad esempio, se si prova a cancellare un prodotto inesistente: un’API REST risponde con **404 Not Found**, mentre un’API non conforme potrebbe dare un generico **200 OK** o un messaggio diverso, rendendo difficile capire cosa è successo.

![[M91.png]]

**_RESTFUL API_**
Per far sì che un’API sia **RESTful**, bisogna **mappare le funzionalità dell’API secondo il paradigma REST**, cioè:

1. **Identificare le risorse** – Una risorsa è qualsiasi oggetto o dato gestito dall’API (ad esempio, un prodotto, un utente, un ordine).
2. **Definire le azioni sulle risorse** – Le operazioni che si possono fare sulle risorse (come `GET`, `POST`, `PUT`, `DELETE`) corrispondono ai metodi HTTP.
3. **Stabilire input e output** – Per ogni azione bisogna definire quali dati servono come input e cosa viene restituito come output.

```ad-example
title: Example of API capability
![[M92.png]]

![[M93.png]]


```

```ad-important
REST API e RESTful API sono equivalenti, la differenza è solo terminologica, non tecnica.

```

**_RELASHIONSHIP AMONG RESOURCES_**
Hierarchical Relationship among resources should be mapped to a path hierarchy for easier interpretation.. 

```ad-example
 `/merchants/{merchant id}/products/ {product reference}` is more readable than 
 `/products/merchant/{product reference}/ {merchant id}`

```

**_REST INTERFACE_**
Fare solo **elaborazioni sui dati** (cioè “fare qualcosa con i dati”) **non è una vera operazione CRUD** (Create, Read, Update, Delete).

Tuttavia, anche queste operazioni possono essere **mappate su una risorsa** e quindi avere un **percorso (path) nell’URL**. In questo caso:

- La risorsa rappresenta l’azione da compiere, non un oggetto che viene creato o modificato.
- Si inviano i dati in input all’API, che li elabora, senza necessariamente creare una nuova risorsa sul server.

![[M94.png]]

**_Data Representation_**
![[M95.png]]

```ad-info
title: Summary
![[M96.png]]

```

## RPC API (OR ACTION – BASED)
Differently than REST, in the Action-oriented API (RCP = Remote Procedure Call) there is only one URL for all the operations, e.g. /api. Operations not restricted to CRUD. An operation gets input parameters and provides a result, just like any function (procedure).

``` node
POST /api { 
"action": "createUser",
 "params": { "name": "Alice", "email": "alice@example.com" } 
 }
```

>Qui, l’API non mappa risorse su URL distinti come REST, ma espone operazioni come funzioni accessibili dallo stesso endpoint.


==Differenza REST API & RPC API==

|Caratteristica|REST API|RPC API|
|---|---|---|
|URL|Ogni risorsa ha il suo|Un unico endpoint (`/api`)|
|Operazioni|CRUD|Qualsiasi azione/funzione|
|Semantica HTTP|Rispetta codici HTTP|Codici HTTP meno importanti|
|Mapping risorse/azioni|Risorsa → URL|Azione → parametro JSON|

## API Security
I fornitori di API devono garantire che **solo gli utenti autorizzati possano accedere alle operazioni e ai dati rilevanti**.

==API Key==
La forma più semplice di sicurezza è utilizzare una **API key**, una chiave segreta che deve essere inviata in ogni richiesta all’API. Permette di identificare il client, ma offre un controllo limitato sulle operazioni e sui dati accessibili.


==Token== (access control più avanzato)
I token offrono un **controllo più fine** rispetto alle API key.
Possono:
    - **Consentire o negare** l’accesso a specifiche operazioni (controllo degli accessi).
    - **Definire lo scope** della chiamata, cioè quali dati possono essere letti o modificati.
    - **Delegare l’identità** ad altre applicazioni, permettendo a un servizio di agire per conto di un utente.

```ad-example
Ad esempio, i Token JWT!

```


==Standard comuni per i token==
- **OAuth 2.0:** permette di delegare l’accesso alle risorse senza condividere le credenziali dell’utente.
- **OpenID Connect:** estende OAuth 2.0 per l’autenticazione dell’utente, fornendo informazioni sull’identità in modo sicuro.

![[M97 1.png]]
## API GATEWAY
The API Gateway is a single-entry point for a set of microservices. I’s like a ‘smart’ proxy that receives requests from the client for services and before routing the request to the specific service, may apply.
- Authorization control.. 
- Rate limiting 
- Transformation 
- Monitoring and logging … 
- Whitelisting and blacklisting

![[M98.png]]

```ad-example
title: Example of Scope Control
Alice and Bob want see their account an transfer money, Bob can't transfer more than 10000$. Alice can transfer any amount she wants.
SpendAdvize can only see information on accounts.

![[M99.png]]

```

## API efficiency
![[M100.png]]

```ad-info
title: Info (Other types of API)
- gRPC (Google Remote Procedure Call) is an open-source framework developed by Google for high- performance communication between services. 
- It fully uses HTTP/2’s possibilities, including bidirectional streaming. Messages use the Protobuf binary format, which is more compact and has more efficient serialization than JSON. 
- graphQL, developed internally at Facebook in 2012 to address issues with over-fetching and under-fetching data in their mobile apps. It was publicly released in 2015 as an open standard.
- GraphQL allows clients to specify exactly which fields they want in a query. This reduces over-fetching and under-fetching of data compared to traditional REST endpoints. 
- Callback API: An API can be used asynchronously, which means that the replies is set back to the client (much) later than the request. Avoids to block the client 
- Client registers a callback endpoint that the server uses to notify the reply 

```

## Tools to Design an API
**_OpenAPI Specification_** (formerly known as Swagger Specification) is an open-source format for describing and documenting APIs. 

API Catalog: https://apislist.com/