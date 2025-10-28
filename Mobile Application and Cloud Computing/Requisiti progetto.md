# 📱 Linee Guida per il Progetto – _Mobile Applications and Cloud Computing_

Questo documento riassume in modo chiaro e completo le istruzioni per lo sviluppo del progetto del corso **Mobile Applications and Cloud Computing**, sulla base delle lezioni introduttive e del laboratorio su **Google Cloud Platform (GCP)**.

---

## 1. 🎯 Obiettivo del progetto

Il progetto consiste nello sviluppo di un’applicazione mobile che integri servizi cloud.  
L’obiettivo è dimostrare la capacità di **progettare, implementare e distribuire un sistema mobile-cloud completo**, che includa:

- autenticazione,
- persistenza dei dati,
- e almeno **un servizio personalizzato lato server**.
## 2. 🧩 Struttura del progetto
Il progetto deve essere composto da due parti principali:

1. **Applicazione mobile**  
    Sviluppata in **Kotlin per Android**, preferibilmente con ==Jetpack Compose== e ==architettura MVVM==.
2. **Servizio cloud personalizzato**  
    Un backend sviluppato e distribuito su **Google Cloud Platform (GCP)**.

## 3. ⚙️ Requisiti tecnici
Il progetto deve includere i seguenti elementi richiesti dal corso:

- Applicazione mobile Android.
- Utilizzo di un servizio cloud (es. Firebase o GCP).
- Autenticazione utente (Firebase Authentication consigliato).
- Multiutenza e ==gestione dei permessi==.
- Operazioni ==CRUD== (Create, Read, Update, Delete). (Operazioni del database)
- Uso di almeno **una funzionalità del dispositivo mobile** (es. sensori, fotocamera, grafica o concorrenza).
- ==Un servizio personalizzato (API REST)== eseguito su infrastruttura cloud (**PaaS/IaaS**).
	- Devi sviluppare una piccola **API REST** (cioè un servizio web con endpoint HTTP) che faccia qualcosa di utile per la tua app, e **distribuirla su Google Cloud Run o Compute Engine** usando il coupon da 50 €.

## 4. 🗄️ Database e persistenza dei dati
Non è obbligatorio mantenere parte del database in locale.  
È perfettamente accettato mantenere **tutti i dati nel cloud**.

Puoi utilizzare:
- **Firebase Firestore** o **Realtime Database** come database principale,
- **Firebase Authentication** per la gestione utenti,
- **Firebase Storage** per immagini o file.

> L’uso di una cache locale (es. Room o DataStore) è **facoltativo**, ma utile per migliorare le performance offline.

## 5. ☁️ Integrazione con Google Cloud Platform (GCP)

Durante il corso, ogni studente riceve un **account GCP con un credito di 50 €**.  
Questo credito serve per creare e gestire le risorse necessarie al **deploy del servizio backend personalizzato**.

Nel laboratorio su GCP viene mostrato come:

1. Creare un nuovo progetto su GCP e impostarlo con la CLI `gcloud`.
2. Scrivere una semplice API REST in **Python (Flask)**.
3. Creare un **container Docker** dell’applicazione.
4. Eseguire il build e il deploy su **Cloud Run** (servizio serverless).
5. Ottenere un **endpoint pubblico** accessibile dall’app Android.

Il backend su GCP rappresenta la parte _“Your service running on a PaaS/IaaS”_ richiesta nelle linee guida.  
Può essere un servizio semplice che riceve dati dall’app, li elabora e restituisce un risultato.

## 6. 💰 Uso del coupon GCP

Il **credito di 50 €** serve a coprire i costi di utilizzo delle risorse GCP durante lo sviluppo e i test.  
In particolare, verrà usato per:

- Build e deploy di container tramite **Cloud Build**.
- Archiviazione delle immagini container in **Artifact Registry**.
- Esecuzione del servizio API su **Cloud Run** o su una **VM Compute Engine**.

## 7. 🏗️ Architettura consigliata

**Frontend (Mobile):**
- Android (Kotlin)
- Jetpack Compose
- MVVM + Hilt + Retrofit + Coroutines/Flow

**Backend (Custom):**
- Flask / FastAPI (Python) o Node.js
- Container Docker distribuito su **Cloud Run**

**Cloud Services:**
- **Database:** Firebase Firestore
- **Autenticazione:** Firebase Authentication
- **Storage:** Firebase Storage (per immagini o file)


## 8. ✅ Conclusione
In sintesi:
- Il progetto deve integrare un’app mobile Android con servizi cloud.
- Il database può risiedere **interamente nel cloud** (Firebase).
- Devi realizzare **almeno un servizio backend personalizzato** distribuito su GCP.
- Il credito GCP serve per il deploy e i test del tuo servizio.

L’obiettivo finale è **dimostrare la capacità di sviluppare un ecosistema mobile-cloud completo e funzionante**.


----

![[M136.png]]
