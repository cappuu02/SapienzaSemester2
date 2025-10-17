In Kotlin ci sono due modi principali per dichiarare variabili:
- `val` → **immutabile** (come una costante, non puoi cambiare il valore dopo averla assegnata)
- `var` → **mutabile** (puoi cambiare il valore in seguito)

**Tipi più comuni:**
- `Int` → numeri interi
- `Double` → numeri decimali
- `String` → testo
- `Boolean` → true/false

**_Condizioni_**:
`if` e `else`
```kotlin
if (steps > 10000) {
        println("Obiettivo giornaliero raggiunto! 🎉")
    } else {
        println("Continua così!")
    }
```

**_Cicli_**:
`for` e `while`
```kotlin
val day = "Martedì"
    when (day) {
        "Lunedì" -> println("Inizia la settimana")
        "Martedì" -> println("Secondo giorno")
        else -> println("Altro giorno")
    }
```

**_Funzioni_**:
```kotlin
fun sum(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    val result = sum(5, 7)
    println("Somma: $result")
}
```

**Classi e Oggetti**
```kotlin
class User(val name: String, var age: Int)

fun main() {
    val user = User("Marco", 22)
    println("Nome: ${user.name}, Età: ${user.age}")

    user.age = 23
    println("Nuova età: ${user.age}")
}
```

**Lista Immutabile**
```kotlin
val workouts = listOf("Corsa", "Bicicletta", "Nuoto")
println(workouts[0]) // Corsa

for (w in workouts) {
    println(w)
}

```

**Lista mutabile**
```kotlin
val workouts = mutableListOf("Corsa", "Bicicletta")
workouts.add("Nuoto") // aggiunge un elemento
println(workouts)
workouts.remove("Corsa")
println(workouts)
```

**Mappe**
```kotlin
val userScores = mutableMapOf("Marco" to 5000, "Luca" to 7000)
println(userScores["Marco"]) // 5000

userScores["Anna"] = 6000
println(userScores)

```

**_Data Class_**
Una `data class` in Kotlin serve a **rappresentare un oggetto con dei dati**, come un “contenitore” strutturato.

```kotlin
data class Workout(
    val type: String,
    val distance: Double,
    val duration: Int
)
```

Poi possiamo creare **istanze** di questa classe:

```kotlin
val run = Workout("Corsa", 5.0, 30)
val bike = Workout("Bicicletta", 10.0, 40)

```

Ogni oggetto è un singolo allenamento.