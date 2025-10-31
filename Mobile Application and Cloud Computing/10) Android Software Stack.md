Android OS is based on a Linux kernel that has been modified to meet the needs of mobile applications. The key modifications include:
- ==Memory Management==: 
	- **_Low Memory Killer_**: A mechanism that terminates background processes when memory resources become scarce, ensuring the system remains responsive (this is way components have a lifecycle)
	- **_Ashmem (Android Shared Memory)_**: A shared memory subsystem designed for efficient inter-process communication with minimal overhead (for example used when an intent has to send a lot of information to another activity)
- ==CPU Management==: 
	- **_Wake lock_**: prevents the device from entering sleep mode when specific tasks require the CPU to remain active
- ==Communication==
	- **_Binder_**: A new inter-process communication (IPC) mechanism that enables efficient and secure communication between different applications and system services, that implements Intent mechanism


# Applications are made of managed components
- **__Activity__** - Represents a single screen with a user interface
- **_Service_** - Performs background operations without a user interface
- **_BroadcastReceiver_** - Receives and handles broadcast messages from the system or other apps
-  **_ContentProvider_** - Manages shared access to app data

These components are "managed" by the Android system, which
means:
- Their lifecycle is controlled by the operating system (not by the app itself)
- The system decides when to create, pause, resume, or destroy them
- They must be declared in the AndroidManifest.xml file
- The system can terminate them when necessary (e.g., low memory situations)
- They communicate with each other through Intents (using Binder as we discussed)

![[M137.png|500]]

# Supported HW: The application Binary Interface
Different Android devices use different CPUs, which in turn support different instruction sets.
Each hardware is labelled with a specific Application Binary Interface (ABI), that includes:
- The CPU instruction set (and extensions) that can be used.
- The endianness of memory stores and loads at runtime.
- Conventions for passing data between applications and the system, including alignment constraints, and how the system uses the stack and registers when it calls functions.
- How to integrate C++ code
- The software stack for AOSP is rather complex and contains the following software layers

![[M138.png|500]]

## Android Apps
Any application that a user installs from the Google Play Store or via sideloading (APK). When an app is installed, its files (APK + data + configs) are saved in the /data/app partition that is readable and writable only by the system and by the app.

> Every app has its private folder in `/data/app` where to store dati, preferences, cache, ...

Every Android app lives in a sandbox, an environment isolated from other processes. When an app is installed, the underlying Linux system assigns it a unique ID and a separate set of permissions. This isolation prevents an app from accessing another app's files or data.

If an app needs to interact with other apps or the system (e.g., open the camera, read a contact, open a map), it must do so only through public APIs controlled by Android.

**_Permissions_**: An app can request specific permissions from the user, defined in the AndroidManifest.xml file. Permissions are approved by the user during installation or upon first use. The app can never obtain system-level permissions unless it is a system app signed by the manufacturer.

The user retains full control over the app:
- They can uninstall it at any time.
- Uninstalling removes everything: APK, data, cache, database.
## Privileged Apps
System apps do not reside in the `/data/app` partition like user apps, but in the read-only OS partition:` /system/app/` or inside `/system/priv-app/` for more privileged apps. These folders are located in the system partition, which is read-only for the regular user.

>Gli `APK` delle app di sistema fanno parte dell'immagine del OS e vengono caricate insieme ad esso.

**_Special permissions_**: these permissions are not accessible to regular user apps

The user **cannot uninstall** system apps. At most, they can **disable** them (i.e., prevent them from starting and hide them), but they cannot physically remove them from the system. This is because the files are stored in `/system`, and that partition is **mounted read-only**.
## Device Manufacturer Apps
 "==Device Manufacturer App==" is any app (privileged or not) that the manufacturer (Samsung, Xiaomi, etc.) pre-installs to customize the device and differentiate it from the competition. 
## Android API
==Android API== is the portion of the framework are publicly accessible, as accessible as SDK, for example: 
- `Android.Graphics`: A low-level 2D graphics drawing API including colors, points, filters, rectangles and canvases
## System APIs
==System APIs==, is the portion of the framework available only to OEMs (Original Equipment Manufacturer), These APIs are marked as @SystemApi in the source code.
## Android framework
==Android framework==: all the API plus several managers 
## System Services
==System Services== are modular, focused components such as, SurfaceFlinger, Window Manager, and MediaService. 
## Android runtime (ART)
==ART (Android Runtime)== è la **macchina virtuale** (VM) che esegue le applicazioni Android.  
Quando sviluppi un’app in Java o Kotlin, il codice sorgente viene **compilato in bytecode** (file `.dex` – _Dalvik Executable_), e questo bytecode **non viene eseguito direttamente dal processore**, ma interpretato o compilato da ART.
## Native Daemons and Libraries
I ==daemons nativi== (processi di sistema in background) sono programmi scritti in linguaggi nativi come **C o C++**, e **non** vengono eseguiti dentro l’ART. Sono parte integrante del sistema operativo Android, e interagiscono **direttamente con il kernel Linux**

```ad-example
`init` Primo Processo avviato dal kernel.
`logd` gestisce i log di sistema (logcat)

```

>Questi processi **vivono “fuori” dall’ambiente Android delle app**

Le ==librerie native== sono **software compilati in linguaggio C o C++** per l’architettura specifica del dispositivo (ARM, x86, ecc.). Queste librerie forniscono funzionalità _ad alte prestazioni_ o _di basso livello_ che non possono essere realizzate solo in Kotlin/Java.

Le librerie native non possono essere eseguite direttamente dall’Android Runtime, perché **ART gestisce solo bytecode `.dex`**, non codice nativo.   Per collegare il codice Kotlin/Java con quello C/C++ serve un **“ponte”** chiamato: ==JNI==

**JNI (Java Native Interface)** è un meccanismo che permette a un’app scritta in Kotlin/Java di **chiamare funzioni native (C/C++)**.

![[M139.png]]

# Platform Channels
I ==Platform Channels== sono un **meccanismo di comunicazione** che permette a **Flutter (Dart)** di **chiamare codice nativo** scritto in **Kotlin/Java** (su Android) o **Swift/Objective-C** (su iOS).  
Servono per accedere a funzionalità del sistema operativo non disponibili direttamente in Dart (es. fotocamera, GPS, sensori, Bluetooth, ecc.).

**_How it works?_**
Il sistema si basa su **messaggi** che vengono inviati tra:
- il **codice Dart (Flutter app)**
- e il **codice nativo della piattaforma**.

Ogni messaggio viene **serializzato (convertito in binario)**, trasmesso e poi **deserializzato** dall’altra parte.  
Questo introduce un leggero **overhead**, ma consente una comunicazione sicura e bidirezionale.

# A classification of Application Based
- **_Platform-native_** = code uses only the official and standard API (Kotlin/Java for android) 
- **_CPU-native_** = code compiled directly to machine of a specific CPU code without VM (C/C++ via NDK) 
- **_Hybrid_** = combines web technologies with native code (PhoneGap,..) 
- **_Cross-platform UI_** = use a proprietary an efficient rendering engine (flutter) 

# External Libraries
Android extend by numerous and powerful libraries, for example for ML and CV:

## ML Kit
==ML Kit== è una libreria di Google che permette di integrare funzionalità di **machine learning direttamente nei dispositivi Android**, senza dover inviare i dati a un server esterno.  
È progettata per **casi d’uso in tempo reale**, come l’elaborazione di **flussi video della fotocamera** o l’analisi di immagini e testi sul dispositivo.

```ad-example
title: Example of ML Features
**Text Recognition**
**Barcode Scanning**
**Image Labeling**
**Face Detection**
**Pose Detection**
**Digital Ink Recognition**


```

## OPENCV for Android
==OpenCV (Open-Source Computer Vision Library)== is a library of programming functions mainly for real-time computer vision, including:
- **Image and Video Processing**
- **Video Analysis**
- **Augmented Reality**

![[M140.png]]

## ARCORE
==ARCore== is Google’s platform for building augmented reality experiences. Using different APIs, ARCore enables a phone to sense its environment, understand the world and interact with information. Some of the APIs are available across Android and iOS to enable shared AR experiences.
- **_Motion tracking_** allows the phone to understand and track its position relative to the world. 
- **Environmental understanding** allows the phone to detect the size and location of all type of surfaces: horizontal, vertical and angled surfaces like the ground, a coffee table or walls. 
- **Light estimation** allows the phone to estimate the environment's current lighting conditions. 

## Firebase
Firebase for Android is a comprehensive cloud platform that provides a suite of backend services. It include services like:
- **Authentication**
- **Cloud Firestore**
- **Realtime Database**
- **Cloud Storage**
- **Cloud Messaging (FCM)**

# Workflow and build variant
![[M141.png]]

# Core Software Components (ANDROID.$*$)
I **Core Components** di Android sono le **unità fondamentali** su cui si basa qualsiasi applicazione Android “classica”. 

Quattro componenti principali:
1. **_Activity_**: rappresenta una singola schermata con interfaccia utente, è il punto di interazione tra utente e l'app. Ogni app può avere una o più Activity (_LoginActivity_, _MainActivity_), gestita dal ciclo di vita dell’Activity (onCreate, onStart, onResume, ecc.).
2. **Service**: Componente che **esegue operazioni in background**, senza interfaccia utente, utile per attività di lunga durata o periodiche. Può essere foreground o background.
3. **Broadcast Receiver**: Componente che ascolta e reagisce a eventi di sistema o app. Gli eventi possono essere inviati dal sistema o altre app. Esegue codice in risposta all'evento, spesso per brevi operazioni.
4. **Content Provider**: Componente che gestisce l’accesso strutturato ai dati condivisi tra app. Fornisce un’interfaccia standard per `leggere/scrivere` dati (simile a un database).

>These libraries are in any android phone and then are not included in the APK 

# Software Architecture
**_Presentation Layer (UI Layer)_**: responsible for displaying information to the user and handling user interactions. 
**_Business Logic Layer_**: the core logic of the application, responsible for processing data, making decisions, and enforcing business rules. 
**_Data Access Layer (Persistence Layer)_**: handles interactions with data sources, such as databases, files, or external services.

![[M142.png]]

# Jetpack Architecture Components 
Gli **Android Jetpack Components** sono un insieme di **librerie moderne** sviluppate da Google per **semplificare lo sviluppo di app Android**. Sono progettate per rendere le app:
- più stabili
- più scalabili
- più manutenibili
- e resilienti al ciclo di vita di Activity e Fragment

Jetpack fornisce strumenti modulari che seguono l’architettura **MVVM (Model-View-ViewModel)**, separando chiaramente **UI, logica e dati**.

![[M143.png|500]]

## Modern App Development
- Model-View-ViewModel (MVVM) 
- View implements the presentation Layer 
- ViewModel implements the business logic 
- Mode implements the Data Access Layer

Data/Event flows in the MVVM: 
- **_One bidirectional flow_**
	- La **View** invia gli eventi utente al **ViewModel** (es. “login cliccato”).
	- Il **ViewModel** aggiorna lo stato dell’interfaccia (UI state), che la View osserva automaticamente.
	- Questo meccanismo di **binding implicito** consente una **sincronizzazione automatica** tra UI e dati.
- **_Unidirectional flows_**
	- - **Dal ViewModel al Model:** il ViewModel invia richieste di aggiornamento o di scrittura dei dati (es. salvataggio nel database).
	- **Dal Model al ViewModel:** il Model restituisce i dati aggiornati (es. risposta da un’API o query Room).

>In UDF, data flows in only one direction. The events that modify the data flow in the opposite direction. 

![[M144.png]]

- **_UI Layer_**: displays application data on the screen.
- **_Domain Layer_**: is an optional layer that sits between the UI and data layers, responsible for encapsulating complex business logic
- **_Data layer_**: contains (simple) business logic of the app and exposes application data.

![[M145.png]]

### Domain Layer
The **Domain Layer** is **optional** and sits between the **UI** and **Data** layers.  
It encapsulates **business logic**, whether complex or simple, that may be **reused** by one or more ViewModels.  

This layer is introduced mainly to **handle complexity** and **improve reusability** and maintainability of the app’s logic.  
Not all applications require it — smaller apps can often manage logic directly within the ViewModel.

![[M146.png]]

# Design Principles
The **design principles** of modern Android development aim to ensure clarity, modularity, and maintainability.

- **Separation of concerns:**  
  Code should be divided into focused parts. UI classes manage only interface and system interactions, while business logic and data handling are placed elsewhere.

- **Drive UI from data models:**  
  UI elements should depend on data models that represent the app’s data independently from the interface and component lifecycles.

- **Single Source of Truth (SSOT):**  
  Each data element should have one authoritative source that owns and updates it. The SSOT exposes immutable data and provides functions or events to modify it safely.

- **Unidirectional Data Flow (UDF):**  
  Data flows in a single direction—from the SSOT to the UI—while events that modify data flow in the opposite direction, keeping state changes predictable and consistent.
