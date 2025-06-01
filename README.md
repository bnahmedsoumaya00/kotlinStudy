
# 📘 Résumé complet – Kotlin de base + Coroutines + Préparation au TD

## 🔹 1. Bases de Kotlin

### 🧱 Déclaration de package et importations
```kotlin
package mon.package
import kotlin.math.*
```
- `package` : organisation logique du code.
- `import` : permet d'utiliser des fonctions ou classes externes.

### 🧱 Fonctions
```kotlin
fun somme(a: Int, b: Int): Int {
    return a + b
}
fun sommeRapide(a: Int, b: Int) = a + b
```
- `fun` : mot-clé pour déclarer une fonction.
- `=` : fonction à expression unique.

### 🧱 Variables
```kotlin
val x = 10      // constante
var y = 5       // variable mutable
```

### 🧱 Chaînes et templates
```kotlin
val nom = "Kotlin"
println("Bonjour $nom, longueur = ${nom.length}")
```

### 🧱 Null Safety
```kotlin
var nom: String? = "Alice"
println(nom?.length ?: 0)
```

### 🧱 Classes et objets
```kotlin
class Personne(val nom: String, var age: Int)
```

### 🧱 Collections
```kotlin
val liste = listOf(1, 2, 3)
val listeMutable = mutableListOf(4, 5)
```

---

## 🔹 2. Coroutines Kotlin

### ⚙️ Concepts de base
```kotlin
import kotlinx.coroutines.*

fun main() = runBlocking {
    launch {
        delay(1000L)
        println("Coroutines Kotlin")
    }
    println("Début")
}
```

### ⚙️ Fonctions suspendues
```kotlin
suspend fun attendre() {
    delay(500L)
}
```

### ⚙️ async / await
```kotlin
val resultat = async { 5 + 3 }
println(resultat.await())
```

### ⚙️ Concurrence structurée
- `coroutineScope` garantit que toutes les coroutines internes sont terminées.

---

## 🔹 3. Concepts spécifiques au TD

### ✅ Enum
```kotlin
enum class Statut {
    EN_ATTENTE, EN_COURS, TERMINEE, ANNULEE
}
```

### ✅ Sealed class et sous-classes
```kotlin
sealed class Tache {
    data class Simple(val description: String) : Tache()
    data class AvecPriorite(val description: String, val priorite: Int) : Tache()
    data class Deleguee(val description: String, val responsable: String) : Tache()
}
```

### ✅ object pour utilitaire
```kotlin
object TrieurDeTaches {
    fun trierParDescription(taches: List<Tache>) = taches.sortedBy {
        when (it) {
            is Tache.Simple -> it.description
            is Tache.AvecPriorite -> it.description
            is Tache.Deleguee -> it.description
        }
    }
}
```

### ✅ Fonctions comme paramètres et retours
```kotlin
fun appliquerFiltre(taches: List<Tache>, filtre: (Tache) -> Boolean): List<Tache> {
    return taches.filter(filtre)
}

fun genererRapport(taches: List<Tache>): (Statut) -> List<String> {
    return { statut -> 
        taches.mapNotNull {
            val desc = when (it) {
                is Tache.Simple -> it.description
                is Tache.AvecPriorite -> it.description
                is Tache.Deleguee -> it.description
            }
            if (desc.contains(statut.name.lowercase(), ignoreCase = true)) desc else null
        }
    }
}
```

### ✅ Lambda, collections, map/filter/etc.
```kotlin
val livres = mutableListOf(
    Livre("Titre1", "Auteur1", 2001),
    Livre("Titre2", "Auteur2", 1995)
)
val apres2000 = livres.filter { it.anneePublication > 2000 }
```

---

## 📌 Ce que tu dois savoir faire pour réussir le TD

- Utiliser `enum class`, `sealed class`, `object`, `data class`.
- Comprendre la différence entre `val` et `var`.
- Utiliser des fonctions comme arguments ou retours (`(T) -> Boolean`).
- Savoir trier, filtrer, transformer des collections (`map`, `filter`, `sortedBy`, etc.).
- Manipuler des `List`, `Set`, `Map`.
- Utiliser des lambdas (`{ it > 0 }`) et des expressions `when`.
- Connaître les fonctions `find`, `any`, `all`, `count`, `associateBy`, `groupBy`, `partition`.
- Comprendre les concepts de délégation (`by`), lazy, et observable.
- Être capable d'écrire un programme structuré, modulaire et lisible.

---


