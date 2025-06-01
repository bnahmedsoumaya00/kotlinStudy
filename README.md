
# 📘 Résumé  – Bases de Kotlin + Coroutines + Concepts du TD

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
fun sommeRapide(a: Int, b: Int) = a + b
```

- `fun` : déclare une fonction.
- `(a: Int, b: Int)` : paramètres avec leurs types.
- `: Int` : type de retour.
- `return` : mot-clé pour retourner une valeur.

---

### 3. Variables

```kotlin
val pi = 3.14
var compteur = 0
compteur += 1
```

- `val` : valeur immuable (constante).
- `var` : variable mutable.

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
var nomNullable: String? = "Kotlin"
println(nomNullable?.length ?: 0)
```

- `?` : type nullable.
- `?.` : appel sécurisé, évite les NullPointerException.
- `?:` : opérateur Elvis, valeur par défaut si `null`.

---

### 7. Classes et objets

```kotlin
class Personne(val nom: String, var age: Int)
val personne = Personne("Alice", 30)
```

---

### 8. Collections

```kotlin
val nombres = listOf(1, 2, 3)
val nombresMutables = mutableListOf(1, 2, 3)

for (nombre in nombres) {
    println(nombre)
}
```

---

## ⚙️ Coroutines Kotlin

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

- `runBlocking` : bloque le thread principal.
- `launch` : lance une coroutine.
- `delay` : suspend l’exécution.

---

### 2. Fonctions suspendues

```kotlin
suspend fun faireQuelqueChose() {
    delay(1000L)
    println("Fait!")
}
```

---

### 3. async / await

```kotlin
val resultat = async {
    5 + 3
}
println(resultat.await())
```

---

### 4. Concurrence structurée

```kotlin
coroutineScope {
    launch { delay(500L); println("Tâche 1") }
}
```

---

### 5. Annulation

```kotlin
val job = launch {
    repeat(1000) { i -> println("Je dors $i"); delay(500L) }
}
job.cancelAndJoin()
```

---

## 🔧 Concepts du TD à maîtriser

### ✅ enum class

```kotlin
enum class Statut {
    EN_ATTENTE, EN_COURS, TERMINEE, ANNULEE
}
```

---

### ✅ sealed class

```kotlin
sealed class Tache {
    data class Simple(val description: String) : Tache()
    data class AvecPriorite(val description: String, val priorite: Int) : Tache()
    data class Deleguee(val description: String, val responsable: String) : Tache()
}
```

---

### ✅ object

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

---

### ✅ Fonctions lambda & retour de fonction

```kotlin
fun appliquerFiltre(taches: List<Tache>, filtre: (Tache) -> Boolean): List<Tache> =
    taches.filter(filtre)

fun genererRapport(taches: List<Tache>): (Statut) -> List<String> = { statut ->
    taches.mapNotNull {
        val desc = when (it) {
            is Tache.Simple -> it.description
            is Tache.AvecPriorite -> it.description
            is Tache.Deleguee -> it.description
        }
        if (desc.contains(statut.name.lowercase(), ignoreCase = true)) desc else null
    }
}
```

---

### ✅ Opérations sur collections

```kotlin
val livres = mutableListOf(
    Livre("Titre1", "Auteur1", 2001),
    Livre("Titre2", "Auteur2", 1995)
)

val livresFiltres = livres.filter { it.anneePublication > 2000 }
val titres = livres.map { it.titre }
val groupes = livres.groupBy { it.auteur }
```

---

## 📌 À retenir pour l’examen et le TD

- Bien comprendre `enum`, `sealed class`, `data class`, `object`, `lambda`.
- Manipuler les collections : `filter`, `map`, `sortedBy`, `groupBy`, `partition`, etc.
- Utiliser les coroutines et fonctions `suspend`.
- Savoir créer et utiliser des fonctions d'ordre supérieur (prenant ou retournant une lambda).
- Utiliser la délégation (`by`), `lazy`, `Delegates.observable`.

---


