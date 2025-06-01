
# 📘 Résumé – Bases de Kotlin & Coroutines
## 🧱 Bases de Kotlin

### 1. Déclaration de package et importations

```kotlin
package mon.package
import kotlin.math.*
```

- `package` : organise les classes et fonctions en espaces de noms.
- `import` : permet d'utiliser des classes ou fonctions d'autres packages sans avoir à spécifier leur nom complet.

---

### 2. Fonctions

```kotlin
fun somme(a: Int, b: Int): Int {
    return a + b
}
```

- `fun` : déclare une fonction.
- `(a: Int, b: Int)` : paramètres avec leurs types.
- `: Int` : type de retour.
- `return` : mot-clé pour retourner une valeur.

**Fonction à expression unique :**

```kotlin
fun somme(a: Int, b: Int) = a + b
```

---

### 3. Variables

- `val` : valeur immuable (constante).
- `var` : variable mutable.

```kotlin
val pi = 3.14
var compteur = 0
compteur += 1
```

---

### 4. Modèles de chaînes (String Templates)

```kotlin
val nom = "Kotlin"
println("Bonjour, $nom!")
println("Longueur du nom : ${nom.length}")
```

- `$nom` : insère la variable dans la chaîne.
- `${expression}` : insère le résultat d'une expression.

---

### 5. Expressions conditionnelles

```kotlin
val max = if (a > b) a else b
```

- `if` peut être utilisé comme expression.

---

### 6. Sécurité des nulls

```kotlin
var nom: String = "Kotlin"
nom = null // Erreur

var nomNullable: String? = "Kotlin"
nomNullable = null // OK

println(nomNullable?.length)
```

- `?` : type nullable.
- `?.` : appel sécurisé, évite les NullPointerException.

---

### 7. Classes et objets

```kotlin
class Personne(val nom: String, var age: Int)
val personne = Personne("Alice", 30)
```

- `val` dans le constructeur = propriété en lecture seule.
- `var` = modifiable.

---

### 8. Collections

```kotlin
val nombres = listOf(1, 2, 3) // Liste immuable
val nombresMutables = mutableListOf(1, 2, 3) // Liste mutable

for (nombre in nombres) {
    println(nombre)
}
```

---

## ⚙️ Bases des Coroutines

Les coroutines permettent d'exécuter du code asynchrone de manière non bloquante.

---

### 1. Lancement d'une coroutine

```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("Monde!")
    }
    println("Bonjour,")
}
```

- `runBlocking` : démarre une coroutine bloquante.
- `launch` : démarre une coroutine sans retour de valeur.
- `delay` : suspend l'exécution sans bloquer.

---

### 2. Fonctions suspendues

```kotlin
suspend fun faireQuelqueChose() {
    delay(1000L)
    println("Fait!")
}
```

- `suspend` : fonction pouvant être suspendue dans une coroutine.

---

### 3. Constructeurs de coroutine

- `launch` : sans valeur de retour.

```kotlin
launch {
    // ...
}
```

- `async` : retourne un résultat différé (Deferred).

```kotlin
val resultat = async {
    5 + 3
}
println(resultat.await())
```

---

### 4. Concurrence structurée

```kotlin
fun main() = runBlocking {
    launch {
        delay(1000L)
        println("Tâche depuis runBlocking")
    }

    coroutineScope {
        launch {
            delay(500L)
            println("Tâche depuis coroutineScope")
        }

        delay(100L)
        println("Coroutine scope terminé")
    }

    println("Programme terminé")
}
```

- `coroutineScope` : attend la fin de toutes les coroutines enfants.

---

### 5. Annulation de coroutines

```kotlin
val job = launch {
    repeat(1000) { i ->
        println("Job : Je dors $i ...")
        delay(500L)
    }
}
delay(1300L)
println("Main : J'en ai assez d'attendre!")
job.cancelAndJoin()
println("Main : Je peux maintenant quitter.")
```

- `cancelAndJoin()` : annule la coroutine et attend sa fin.

---

## 📌 À retenir pour l'examen

- Syntaxe `fun`, `val`, `var`, `if`, `when`, `for`, `class`.
- Types : `String`, `Int`, `Boolean`, `List`, `MutableList`, `Map`, `Nullable` (`?`).
- Fonctions suspendues et `runBlocking`, `launch`, `async`, `await`, `delay`.
- Sécurité des nulls avec `?.`, `!!`, `?:`.
- Structure des classes et collections.

---


