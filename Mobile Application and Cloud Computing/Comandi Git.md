# Git Commands Cheat Sheet - EverRun Project

## 📋 Verifica Situazione

```bash
# Vedi su quale branch sei
git status

# Lista branch locali
git branch

# Lista tutti i branch (locali e remoti)
git branch -a

# Ultimi commit
git log --oneline -5

# Mostra differenze con l'ultimo commit
git diff
```

## 🌿 Gestione Branch

```bash

# Crea branch (rimani sul corrente)
git branch nome-branch

# Crea branch e vai subito
git checkout -b feature/nome-feature


# Cambia branch
git checkout develop
git checkout main
git checkout feature/nome_feature

# Elimina branch locale
git branch -d feature/branch-da-eliminare

```

## 💾 Commit e Modifiche

```bash
# Aggiungi tutti i file modificati
git add .

# Aggiungi file specifici
git add app/src/main/java/com/example/everrun/MainActivity.kt

# Commit con messaggio
git commit -m "feat: aggiunto login con Firebase"

# Commit dettagliato (multi-linea)
git commit -m "feat: implementato sistema autenticazione

- Login con email/password
- Integrazione Firebase Auth  
- Gestione errori
- UI migliorata"

# Aggiungi e commit in uno (solo file già tracked)
git commit -am "fix: corretto bug nel GPS tracking"

```

## 📤 Push e Sincronizzazione

```bash
# Prima push del branch (crea remote) (solo prima volta -u)
git push -u origin feature/nome-feature 

# Push successivi
git push

# Aggiorna branch con develop (REBASE)
git checkout feature/tuo-branch
git fetch origin
git rebase origin/develop

# Aggiorna branch con develop (MERGE)
git checkout feature/tuo-branch  
git fetch origin
git merge origin/develop

# Scarica ultime modifiche senza merge
git fetch origin
```
## 🔄 Workflow Completo Feature

```bash
# 1. Inizia da develop aggiornato
git checkout develop
git pull origin develop

# 2. Crea branch feature
git checkout -b feature/nuova-feature

# 3. Lavora e commit frequenti
git add .
git commit -m "feat: primo passo feature"
git add . 
git commit -m "feat: secondo passo feature"

# 4. Tieniti aggiornato con develop
git fetch origin
git rebase origin/develop

# 5. Push sul remote
git push -u origin feature/nuova-feature

# 6. Crea Pull Request su GitHub
```
## 🛠 Risoluzione Problemi

```bash
# Annulla modifiche file non committati
git checkout -- nome-file.txt

# Rimuovi file dall'area di staging
git reset HEAD nome-file.txt

# Durante rebase con conflitti:
# 1. Risolvi conflitti manualmente
# 2. Aggiungi file risolti
git add .
# 3. Continua rebase
git rebase --continue

# Annulla rebase in corso
git rebase --abort

# Ripristina a commit precedente (PERICOLOSO)
git reset --hard HEAD~1

```

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