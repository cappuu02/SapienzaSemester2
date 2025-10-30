# Informazioni App

L'applicazione deve avere:
- pagina login
- pagina registrazione
- home page
- pagina delle attività (permette di visualizzare le attività di se stesso e degli amici)
	- attività specifica (se clicco su una attività posso vedere le relative info)
- pagina profilo
	- informazioni con foto, numero di follower e following	
	- possibilità caricamento foto
 - con tre bottoni attività e statistiche e documenti
	- possibilità di aggiungere amici scansionando il qrcode dell'altro amico
- pagina mappa con registrazione attività personale che viene salvata automaticamente al termine dell'attività
- pagina impostazioni


Per ogni attività svolta si deve poter vedere:
- mappa con tracciamento del percorso
- Titolo attività 
- Descrizione
- tipologia
- Statistiche (Distanza, velocità media, tempo in movimento, passo medio, calorie, dislivello positivo, dislivello negativo)

In base ad ogni attività le statistiche saranno diverse, in base allo sport praticato!


# Database Locale

![[MW129.png]]

>La `SYNC_QUEUE` è una **"lista delle cose da fare"** quando torna la connessione.

![[MW130.png]]

# Tecnologie
Linguaggio: Kotlin
Cloud: Firebase
Sensori da sfruttare:
- Accelerometro
- Giroscopio
- Magnetometro
- Fotocamera
- GPS