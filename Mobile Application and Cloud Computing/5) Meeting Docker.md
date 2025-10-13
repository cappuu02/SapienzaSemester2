# Docker Architecture
- **_Docker Host_** = The computer (physical or virtual) where containers run.
- **_Docker Daemon_** = The background process that manages Docker containers, images, and networks. It executes the commands sent to it.
- **_Docker CLI_** = The Command Line Interface that allows the user to send commands to the Docker Daemon.

![[M70.png|500]]

# Docker Workflow
Le attività in Docker si possono classificare come build, run, push e pull. Un container è fondamentalmente un'immagine in esecuzione, e la loro relazione è paragonabile a quella che esiste tra un processo e un programma. Le immagini vengono memorizzate in un registry, che può essere pubblico o privato, e Docker Hub è il registry principale mantenuto da Docker Inc.

![[M71.png]]

![[M73.png]]
# Docker Architecture
- Plugins: add functionalities of the (core) daemon, e.g. buildx
- Extensions: functionalities seen by users

![[M72.png|600]]

# Docker Images
Un ==Dockerfile== è un template di sola lettura utilizzato per creare un'immagine Docker. L'operazione di "build" si riferisce proprio alla creazione di un'immagine che include tutte le dipendenze di un'applicazione. Per eseguire questa operazione, si utilizza il comando "$docker build", che legge le istruzioni da un Dockerfile. Il Dockerfile stesso consiste in una lista di istruzioni, ciascuna delle quali segue una semplice sintassi del tipo "ISTRUZIONE argomento".

![[M74.png]]

```ad-example
![[Pasted image 20251013141014.png]]

```

## Image File
Un'immagine Docker è strutturata come una pila di livelli.
- I primi livelli sono in sola lettura, il che permette una condivisione efficiente tra diverse immagini.
- L'ultimo livello, creato ad ogni esecuzione, è in lettura-scrittura ed è ciò che rende i container di base stateless.
Questi livelli sono generati dai comandi nel Dockerfile. È importante distinguere la funzione dei comandi: l'istruzione `RUN` crea un livello temporaneo di lettura-scrittura durante la costruzione dell'immagine, mentre il comando `CMD` non crea un livello, ma definisce semplicemente il comando da eseguire all'interno del container in fase di runtime.

![[M77.png|400]]
# Registry
Le immagini Docker possono essere scaricate (pull) o caricate (push) da un registry. Un repository con nome funziona come un contenitore nominato per le immagini, e il suo nome è simile a un URL. Ad esempio, AWS mette a disposizione un registry pubblico all'indirizzo [https://gallery.ecr.aws](https://gallery.ecr.aws). Allo stesso modo, Docker Hub è accessibile tramite l'indirizzo [https://hub.docker.com/](https://hub.docker.com/).

# APP.PY
Flask è un micro-framework open-source utilizzato per sviluppare applicazioni web e web API. La funzione `jsonify` serve a convertire oggetti Python, tipicamente dizionari, in risposte formattate in JSON. L'annotazione `app.route` è uno strumento che configura il server per indirizzare una richiesta HTTP GET su un percorso specifico, come "/", verso un metodo associato, che in questo esempio è `get_data`.

![[M76.png|500]]

# Build the image and Run It
`docker buildx build --load -t simple-flask-api .
`docker run -d -p 5000:5000 simple-flask-api:latest`
`docker ps`

# Lifecycle of a container
![[M78.png|600]]

# Image Handling
List the image on the host (local repository)
`docker images`
`docker image ls`
`docker rmi imageid`

>Remove an image (by id or name)

# Container Management
`docker ps`
`docker stop containerid`
`docker start containerid`
`docker kill containerid`
`docker rm containerid`

# Docker Networking
Docker gestisce la comunicazione tra container sullo stesso host o verso processi esterni attraverso una struttura di rete. Per impostazione predefinita, Docker include tre reti distinte, ciascuna gestita da un driver specifico.

- La rete di nome `bridge` è la rete predefinita, fornita dal driver "bridge".

Il driver bridge ha la funzione specifica di fornire connettività tra i container per tutti quelli in esecuzione sulla stessa macchina.


![[M79.png]]

Il driver "host" permette ai container di interagire con lo stack di rete del sistema host direttamente, proprio come farebbero dei processi non containerizzati. Per esporre una porta all'esterno del container, si utilizza il flag `-p` (publish) con il comando `docker run`. Esiste inoltre una rete chiamata "none", che utilizza un driver nullo. I container collegati a questa rete non avranno alcuna connettività di rete al di fuori di se stessi, risultando così completamente isolati a livello di rete.

![[M80.png]]

# Docker Storage
In Docker, la gestione dell'archiviazione si basa sul principio dei filesystem Linux, dove l'albero delle directory può avere dispositivi montati in punti specifici. Per rendere i dati persistenti, un container può montare una parte del filesystem dell'host nel proprio albero delle directory, un'operazione chiamata "bind-mount". Tuttavia, questa soluzione vincola il container a una configurazione specifica dell'host.

L'opzione preferita è invece l'utilizzo di volumi Docker, che sono generati e gestiti direttamente da Docker. I volumi forniscono una gestione dei dati indipendente dal ciclo di vita del container.

- **Bind-mount:** Collega il container a un percorso specifico sull'host.
- **Volume:** Gestito da Docker, è l'opzione consigliata per la persistenza.
- **Tmpfs:** Un'ultima opzione è l'uso di un filesystem in memoria RAM, utile per cache o dati temporanei.

![[M81.png]]

# Docker Volume
Per gestire i volumi in Docker, è disponibile una serie di comandi specifici. Il comando `docker volume create` seguito da un nome permette di creare un nuovo volume; questa azione crea una directory in un'area gestita dal motore Docker all'interno del filesystem dell'host, destinata a contenere i dati del volume.

Per visualizzare tutti i volumi esistenti, si utilizza il comando `docker volume ls`. Se si necessita di visualizzare informazioni dettagliate su un volume specifico, come il suo percorso effettivo sull'host, si può usare `docker volume inspect` seguito dal nome del volume.

Per rimuovere un volume non più necessario, il comando è `docker volume rm`. Infine, per montare un volume all'interno di un container in esecuzione, si utilizza il flag `-v` con il comando `docker run`, specificando la sorgente (il nome del volume) e la destinazione (il percorso all'interno del container) nel formato `-v sorgente:destinazione`.

![[M82.png]]

# Multi-Container Applications
Per gestire applicazioni complesse, è necessario orchestrare più container. Docker Compose è lo strumento progettato per questo scopo, permettendo di coordinare più container in esecuzione sullo stesso host. Questi container comunicano tra loro tramite un bridge, che crea una rete privata isolata.

La configurazione dell'intera composizione di container viene definita in un unico file di testo, formattato in YAML.

Quando l'applicazione deve essere distribuita su più macchine, è necessario utilizzare strumenti di orchestrazione più avanzati. I due più comuni sono:

- **Docker Swarm:** Lo strumento nativo di Docker per il clustering.
- **Kubernetes (K8s):** La piattaforma di orchestrazione più diffusa nell'industria per la gestione di container su vasta scala e su più host.

# Docker Compose
Docker Compose è uno strumento fondamentale per definire ed eseguire applicazioni Docker multi-container. Attraverso questo strumento, è possibile coordinare una composizione di più container in esecuzione su un singolo host, gestito da un'unica istanza del Docker engine. Lo sviluppatore definisce in un unico file tutti i container da istanziare simultaneamente e le relative dipendenze e relazioni tra di essi. La documentazione ufficiale è disponibile all'indirizzo [https://docs.docker.com/compose/](https://docs.docker.com/compose/).

Per avviare una composizione di Docker Compose in background, si utilizza il comando `docker compose up -d`. Per impostazione predefinita, Docker Compose cerca un file denominato `compose.yaml` nella directory di lavoro corrente.

Per fermare i container in esecuzione senza rimuoverli, è possibile utilizzare il comando `docker compose stop`. Per arrestare completamente la composizione e rimuovere tutti i container, le reti e le risorse create, si utilizza il comando più definitivo `docker compose down`.

# Docker Service 
In Docker, un "Servizio" (Service) è un'astrazione che definisce le risorse di calcolo all'interno di un'applicazione. Nel contesto di Docker Compose, l'opzione "build" indica di utilizzare il Dockerfile presente nella directory corrente per costruire l'immagine. Successivamente, il container in esecuzione basato su quell'immagine può essere referenziato con un nome specifico, come ad esempio `my_python_app`.
![[M83.png]]