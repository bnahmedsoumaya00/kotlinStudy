# 📘 Résumé ultra-complet – Bases de Kotlin + Coroutines + Concepts du TD

Ce document est conçu pour les **débutants en Kotlin**. Il couvre :

- Les **bases du langage Kotlin**,
- Les **coroutines** (programmation asynchrone),
- Et les **concepts essentiels** à maîtriser pour réussir vos TD et examens.

Les explications sont simples, avec des analogies du quotidien et des exemples pratiques, en s’appuyant sur la [documentation officielle de Kotlin](https://kotlinlang.org/).

---

# 🧱 Bases de Kotlin

## 1. Déclaration de package et importations

```kotlin
package mon.package
import kotlin.math.*
```

### 🧠 Explications :

- **`package`** : comme un **dossier** dans votre ordinateur, il organise vos fichiers (classes, fonctions…).
- **`import`** : comme **emprunter un outil** dans une bibliothèque — ici, des fonctions comme `sqrt()` ou `max()`.

### ✅ Exemple :

```kotlin
import kotlin.math.sqrt

fun main() {
    println(sqrt(16.0)) // Affiche : 4.0
}
```

🗒️ *Ici, `sqrt` calcule la racine carrée. On l’importe pour pouvoir l’utiliser directement.*

---

## 2. Fonctions

```kotlin
fun somme(a: Int, b: Int): Int {
    return a + b
}

fun sommeRapide(a: Int, b: Int) = a + b
```

### 🧠 Explications :

Une fonction, c’est comme une **recette** :

- Elle prend des **ingrédients** (paramètres),
- Fait une **opération** (le corps),
- Et **renvoie un résultat**.

Détails :

- `fun` : mot-clé pour déclarer une fonction,
- `(a: Int, b: Int)` : paramètres typés (ici, des entiers),
- `: Int` : type de retour (ici, un entier),
- `sommeRapide` : version simplifiée sans `return`.

### ✅ Exemple :

```kotlin
fun direBonjour(prenom: String): String {
    return "Salut, $prenom !"
}

fun main() {
    println(direBonjour("Emma")) // Affiche : Salut, Emma !
}
```

Version courte :

```kotlin
fun direSalut(prenom: String) = "Salut, $prenom !"

fun main() {
    println(direSalut("Léo")) // Affiche : Salut, Léo !
}
```

💡 **Astuce** : Utilisez la syntaxe courte (`=`) pour les fonctions simples, cela rend le code plus lisible !

---
## 3. Variables
```kotlin
**val** pi = 3.14
```kotlin
**var** compteur = 0
compteur += 1
```


Explications :
```kotlin
**val** : une valeur qui ne change jamais, comme votre date de naissance.
```kotlin
**var** : une variable qui peut changer, comme le score dans un jeu.
```


Exemple pour débutants :**val** ville = "Paris" // Ne change pas
```kotlin
**var** temperature = 20 // Peut changer
temperature = 25    // OK
// ville = "Lyon"   // Erreur : **val** ne peut pas être modifié
println("Il fait $temperature°C à $ville.") // Affiche : Il fait 25°C à Paris.
```


Astuce : Préférez **val** pour éviter les erreurs, sauf si vous devez vraiment modifier la valeur.


## 4. Modèles de chaînes (String Templates)
```kotlin
**val** nom = "Kotlin"
println("Bonjour, $nom!")
println("Longueur du nom : ${nom.length}")
```


Explications :
Les modèles de chaînes permettent d’insérer des variables ou des calculs dans du texte.
$nom : insère directement la valeur de nom.
${expression} : insère le résultat d’un calcul ou d’une méthode (ex. : nom.length donne la longueur).


Exemple pour débutants :**val** age = 15
println("J’ai $age ans.") // Affiche : J’ai 15 ans.
println("L’année prochaine, j’aurai ${age + 1} ans.") // Affiche : L’année prochaine, j’aurai 16 ans.


Astuce : C’est comme remplir un formulaire avec des informations automatiques.


## 5. Expressions conditionnelles
```kotlin
**val** max = if (a > b) a else b
```


Explications :
En Kotlin, if peut donner un résultat directement, comme choisir entre deux options.
Pas besoin d’un bloc complet pour des cas simples.


Exemple pour débutants :**val** note = 75
```kotlin
**val** message = if (note >= 50) "Bravo, tu as réussi !" else "Essaie encore."
println(message) // Affiche : Bravo, tu as réussi !
```


Astuce : Utilisez if comme expression pour écrire moins de code.


## 6. Sécurité des nulls
```kotlin
**var** nomNullable: String? = "Kotlin"
println(nomNullable?.length ?: 0)
```


Explications :
? : indique que la variable peut être null (vide, sans valeur).
?. : appelle une méthode uniquement si la variable n’est pas null.
?: : donne une valeur par défaut (ici 0) si la variable est null.


Exemple pour débutants :**var** message: String? = null
println(message?.length ?: "Pas de message") // Affiche : Pas de message
message = "Salut"
println(message?.length) // Affiche : 5


Astuce : La sécurité des nulls évite les erreurs courantes, comme essayer d’utiliser une valeur inexistante.


## 7. Classes et objets
```kotlin
**class** Personne(**val** nom: String, **var** age: Int)
```kotlin
**val** personne = Personne("Alice", 30)
```


Explications :
Une classe, c’est comme un plan pour créer des objets (ex. : une personne avec un nom et un âge).
```kotlin
**val** nom : propriété non modifiable.
```kotlin
**var** age : propriété modifiable.
```


Exemple pour débutants :**class** Animal(**val** nom: String, **var** poids: Int)
```kotlin
**val** chien = Animal("Max", 10)
chien.poids = 12 // Le chien a grossi
println("${chien.nom} pèse ${chien.poids} kg.") // Affiche : Max pèse 12 kg.
```


Astuce : Une classe, c’est comme une fiche descriptive pour un objet.


## 8. Collections
```kotlin
**val** nombres = listOf(1, 2, 3)
```kotlin
**val** nombresMutables = mutableListOf(1, 2, 3)
```

for (nombre in nombres) {
    println(nombre)
}


Explications :
Une collection, c’est comme un panier contenant plusieurs éléments (nombres, mots, etc.).
listOf : crée une liste non modifiable.
mutableListOf : crée une liste où vous pouvez ajouter ou retirer des éléments.


Exemple pour débutants :**val** animaux = listOf("Chat", "Chien", "Oiseau")
for (animal in animaux) {
    println("J’ai un $animal.") // Affiche : J’ai un Chat. J’ai un Chien. J’ai un Oiseau.
}
```kotlin
**val** panier = mutableListOf("Pomme", "Banane")
panier.add("Orange")
println(panier) // Affiche : [Pomme, Banane, Orange]
```


Astuce : Utilisez mutableListOf si vous devez modifier la liste, sinon listOf.


# ⚙️ Coroutines Kotlin
Les coroutines permettent de gérer des tâches longues (comme charger une image depuis Internet) sans bloquer votre programme. Elles rendent le code asynchrone simple à lire.
## 1. Lancement d'une coroutine
```kotlin
```kotlin
import kotlinx.coroutines.*
```
```


```kotlin
**fun** main() = **runBlocking** {
    **launch** {
        delay(1000L)
        println("Monde!")
    }
    println("Bonjour,")
}
```


Explications :
**runBlocking** : bloque le programme principal pour exécuter les coroutines (utile pour tester).
**launch** : démarre une coroutine qui s’exécute en parallèle.
delay : pause la coroutine sans bloquer tout le programme.


Exemple pour débutants :**fun** main() = **runBlocking** {
    **launch** {
        delay(2000L)
        println("Tâche terminée !")
    }
    println("Début...")
}
// Affiche : Début... (immédiatement)
// Puis : Tâche terminée ! (après 2 secondes)


Astuce : Les coroutines, c’est comme faire plusieurs choses à la fois sans tout arrêter.


## 2. Fonctions suspendues
```kotlin
**suspend** **fun** faireQuelqueChose() {
    delay(1000L)
    println("Fait!")
}
```


Explications :
```kotlin
**suspend** : indique que la fonction peut être mise en pause (utilisée dans une coroutine).
Elle peut appeler d’autres fonctions **suspend** comme delay.
```


Exemple pour débutants :**suspend** **fun** telechargerImage() {
    delay(1500L)
    println("Image téléchargée !")
}
```kotlin
**fun** main() = **runBlocking** {
    telechargerImage()
    println("Prêt à afficher.")
}
// Affiche : Image téléchargée ! (après 1,5 seconde)
// Puis : Prêt à afficher.
```


Astuce : Les fonctions **suspend** sont parfaites pour les tâches qui prennent du temps.


## 3. **async** / **await**
```kotlin
**val** resultat = **async** {
    5 + 3
}
println(resultat.**await**())
```


Explications :
**async** : lance une coroutine qui retourne un résultat (stocké dans un Deferred).
**await** : attend le résultat de la coroutine.


Exemple pour débutants :**fun** main() = **runBlocking** {
    **val** somme = **async** {
        delay(1000L) // Simule un calcul long
        10 + 20
    }
    println("Résultat : ${somme.**await**()}") // Affiche : Résultat : 30
}


Astuce : Utilisez **async** quand vous voulez un résultat d’une tâche asynchrone.


## 4. Concurrence structurée
**coroutineScope** {
    **launch** { delay(500L); println("Tâche 1") }
}


Explications :
**coroutineScope** : crée un groupe de coroutines qui doivent toutes se terminer avant de continuer.
Si une coroutine échoue, les autres sont annulées.


Exemple pour débutants :**fun** main() = **runBlocking** {
    **coroutineScope** {
        **launch** { delay(500L); println("Préparer le café") }
        **launch** { delay(300L); println("Chauffer l’eau") }
    }
    println("Petit déjeuner prêt !")
}
// Affiche : Chauffer l’eau (après 0,3 seconde)
// Puis : Préparer le café (après 0,5 seconde)
// Puis : Petit déjeuner prêt !


Astuce : **coroutineScope** garantit que tout est fini avant de passer à la suite.


## 5. Annulation
```kotlin
**val** job = **launch** {
    repeat(1000) { i -> println("Je dors $i"); delay(500L) }
}
job.cancelAndJoin()
```


Explications :
job : représente une coroutine que vous pouvez arrêter.
cancelAndJoin : annule la coroutine et attend qu’elle soit complètement arrêtée.


Exemple pour débutants :**fun** main() = **runBlocking** {
    **val** tache = **launch** {
        repeat(3) {
            println("Travail en cours...")
            delay(200L)
        }
    }
    delay(400L) // Attendre un peu
    tache.cancelAndJoin()
    println("Tâche arrêtée.")
}
// Affiche : Travail en cours... (2 fois)
// Puis : Tâche arrêtée.


Astuce : L’annulation est utile pour arrêter une tâche devenue inutile.


# 🔧 Concepts du TD à maîtriser
## ✅ Enum **class**
```kotlin
**enum** **class** Statut {
    EN_ATTENTE, EN_COURS, TERMINEE, ANNULEE
}
```


Explications :
Une **enum** **class** définit une liste fixe de choix, comme les jours de la semaine ou les statuts d’une tâche.
Chaque valeur est un objet unique que vous pouvez utiliser dans des conditions ou des boucles.


Exemple pour débutants :**enum** **class** Couleur {
    ROUGE, VERT, BLEU
}
```kotlin
**fun** estCouleurPreferee(couleur: Couleur): String {
    return if (couleur == Couleur.BLEU) "J’aime le bleu !" else "Pas ma préférée."
}
println(estCouleurPreferee(Couleur.BLEU)) // Affiche : J’aime le bleu !
println(estCouleurPreferee(Couleur.ROUGE)) // Affiche : Pas ma préférée.
```


Astuce : Les **enum** sont parfaits pour des choix limités et clairs.


## ✅ Sealed **class**
```kotlin
**sealed** **class** Tache {
    data **class** Simple(**val** description: String) : Tache()
    data **class** AvecPriorite(**val** description: String, **val** priorite: Int) : Tache()
    data **class** Deleguee(**val** description: String, **val** responsable: String) : Tache()
}
```


Explications :
Une **sealed** **class** définit un ensemble fermé de sous-classes, comme un menu avec quelques options précises.
Utilisée avec when pour gérer tous les cas possibles sans erreur.


Exemple pour débutants :**sealed** **class** Vehicule
```kotlin
**class** Voiture(**val** nom: String) : Vehicule()
```kotlin
**class** Moto(**val** nom: String) : Vehicule()
```kotlin
**fun** description(vehicule: Vehicule): String {
    return when (vehicule) {
        is Voiture -> "${vehicule.nom} a 4 roues."
        is Moto -> "${vehicule.nom} a 2 roues."
    }
}
```kotlin
**val** maVoiture = Voiture("Toyota")
```kotlin
**val** maMoto = Moto("Yamaha")
println(description(maVoiture)) // Affiche : Toyota a 4 roues.
println(description(maMoto))   // Affiche : Yamaha a 2 roues.
```


Astuce : Les **sealed** **class** garantissent que vous n’oubliez aucun cas dans un when.


## ✅ Data **class**

Explications :
Une data **class** est une classe conçue pour stocker des données, comme une carte d’identité.
Kotlin génère automatiquement des fonctions utiles : toString() (pour afficher), equals() (pour comparer), hashCode(), et copy() (pour copier avec modifications).


Exemple pour débutants :data **class** Livre(**val** titre: String, **val** auteur: String)
```kotlin
**val** livre1 = Livre("Kotlin Facile", "Jean")
```kotlin
**val** livre2 = livre1.copy(titre = "Kotlin Avancé")
println(livre1) // Affiche : Livre(titre=Kotlin Facile, auteur=Jean)
println(livre2) // Affiche : Livre(titre=Kotlin Avancé, auteur=Jean)
```


Astuce : Utilisez data **class** pour des objets simples, comme des produits ou des utilisateurs.


## ✅ Object
```kotlin
**object** TrieurDeTaches {
    **fun** trierParDescription(taches: List<Tache>) = taches.sortedBy {
        when (it) {
            is Tache.Simple -> it.description
            is Tache.AvecPriorite -> it.description
            is Tache.Deleguee -> it.description
        }
    }
}
```


Explications :
Un **object** crée une instance unique d’une classe, comme un guichet unique dans une banque.
Utile pour des outils ou des gestionnaires partagés par tout le programme.


Exemple pour débutants :**object** GestionnaireDePoints {
    **var** points = 0
    **fun** ajouterPoint() {
        points += 1
        println("Points totaux : $points")
    }
}
GestionnaireDePoints.ajouterPoint() // Affiche : Points totaux : 1
GestionnaireDePoints.ajouterPoint() // Affiche : Points totaux : 2


Astuce : Pas besoin de créer une instance, l’objet est toujours disponible.


## ✅ Fonctions lambda & retour de fonction
```kotlin
**fun** appliquerFiltre(taches: List<Tache>, filtre: (Tache) -> Boolean): List<Tache> =
    taches.**filter**(filtre)
```

```kotlin
**fun** genererRapport(taches: List<Tache>): (Statut) -> List<String> = { statut ->
    taches.mapNotNull {
        **val** desc = when (it) {
            is Tache.Simple -> it.description
            is Tache.AvecPriorite -> it.description
            is Tache.Deleguee -> it.description
        }
        if (desc.contains(statut.name.lowercase(), ignoreCase = true)) desc else null
    }
}
```


Explications :
Une lambda est une petite fonction sans nom, comme une instruction rapide (ex. : "prends les nombres pairs").
Une fonction peut retourner une lambda, ce qui permet de créer des comportements personnalisés.


Exemple pour débutants :**val** nombres = listOf(1, 2, 3, 4)
```kotlin
**val** trierPairs = { x: Int -> x % 2 == 0 } // Lambda pour vérifier les nombres pairs
println(nombres.**filter**(trierPairs)) // Affiche : [2, 4]
// Fonction qui retourne une lambda
```kotlin
**fun** createurDeMessage(prefixe: String): (String) -> String = { nom -> "$prefixe, $nom !" }
```kotlin
**val** saluer = createurDeMessage("Salut")
println(saluer("Emma")) // Affiche : Salut, Emma !
```


Astuce : Les lambdas simplifient le code en évitant des fonctions complexes.


## ✅ Opérations sur collections
```kotlin
**val** livres = mutableListOf(
    Livre("Titre1", "Auteur1", 2001),
    Livre("Titre2", "Auteur2", 1995)
)
```

```kotlin
**val** livresFiltres = livres.**filter** { it.anneePublication > 2000 }
```kotlin
**val** titres = livres.**map** { it.titre }
```kotlin
**val** groupes = livres.**groupBy** { it.auteur }
```


Explications :
Les collections (listes, ensembles, dictionnaires) sont manipulées avec des fonctions comme **filter**, **map**, sortedBy, **groupBy**, et **partition**.
Ces fonctions utilisent souvent des lambdas pour définir ce qu’on veut faire.


Exemple pour débutants :data **class** Fruit(**val** nom: String, **val** prix: Int)
```kotlin
**val** fruits = listOf(
    Fruit("Pomme", 2),
    Fruit("Banane", 3),
    Fruit("Orange", 1)
)
// Filtrer les fruits chers
```kotlin
**val** chers = fruits.**filter** { it.prix > 2 }
println(chers) // Affiche : [Fruit(nom=Banane, prix=3)]
// Extraire les noms
```kotlin
**val** noms = fruits.**map** { it.nom }
println(noms) // Affiche : [Pomme, Banane, Orange]
// Grouper par prix
```kotlin
**val** parPrix = fruits.**groupBy** { it.prix }
println(parPrix) // Affiche : {2=[Fruit(nom=Pomme, ...)], 3=[Fruit(nom=Banane, ...)], 1=[Fruit(nom=Orange, ...)]}
// Diviser en deux groupes
```kotlin
**val** (chers, pasChers) = fruits.**partition** { it.prix > 2 }
println("Chers : $chers, Pas chers : $pasChers")
// Affiche : Chers : [Fruit(nom=Banane, ...)], Pas chers : [Fruit(nom=Pomme, ...), Fruit(nom=Orange, ...)]
```


Astuce : Les fonctions sur collections sont comme des outils pour trier ou organiser un panier de fruits.


# 📚 Concepts avancés pour débutants
Cette section explique les concepts avancés mentionnés dans "À retenir pour l’examen et le TD", avec des explications simples pour les débutants et des exemples pratiques basés sur la documentation officielle de Kotlin (https://kotlinlang.org/).
## 1. Coroutines et fonctions suspendues

Explications :
Les coroutines permettent de gérer des tâches longues (comme télécharger un fichier) sans bloquer le programme.
Une fonction **suspend** peut être mise en pause et reprise, mais elle doit être utilisée dans une coroutine.


Exemple pour débutants :import kotlinx.coroutines.*
```kotlin
**suspend** **fun** envoyerMessage() {
    delay(1000L) // Simule l’envoi
    println("Message envoyé !")
}
```kotlin
**fun** main() = **runBlocking** {
    envoyerMessage()
    println("Message reçu.")
}
// Affiche : Message envoyé ! (après 1 seconde)
// Puis : Message reçu.
```


Astuce : Les coroutines simplifient les tâches asynchrones, comme attendre une réponse d’un serveur.


## 2. Fonctions d’ordre supérieur

Explications :
Une fonction d’ordre supérieur prend une lambda comme argument ou en retourne une.
Cela permet de personnaliser le comportement d’une fonction.


Exemple pour débutants :**fun** modifierNombres(nombres: List<Int>, action: (Int) -> Int): List<Int> {
    return nombres.**map**(action)
}
```kotlin
**val** nombres = listOf(1, 2, 3)
```kotlin
**val** triples = modifierNombres(nombres) { it * 3 }
println(triples) // Affiche : [3, 6, 9]
// Retourner une lambda
```kotlin
**fun** createurDeFiltre(max: Int): (Int) -> Boolean = { it < max }
```kotlin
**val** filtrePetits = createurDeFiltre(3)
println(nombres.**filter**(filtrePetits)) // Affiche : [1, 2]
```


Astuce : Les fonctions d’ordre supérieur rendent votre code flexible, comme choisir une règle pour trier des cartes.


## 3. Délégation, **lazy**, et **Delegates.observable**
Délégation avec by

Explications :
La délégation permet à une classe de confier certaines tâches à une autre classe.
Le mot-clé by simplifie cela en réutilisant une implémentation existante.


Exemple pour débutants :interface Robot {
    **fun** travailler()
}
```kotlin
**class** RobotStandard : Robot {
    override **fun** travailler() = println("Robot travaille...")
}
```kotlin
**class** RobotAmeliore(delegate: Robot) : Robot by delegate
```kotlin
**val** robot = RobotAmeliore(RobotStandard())
robot.travailler() // Affiche : Robot travaille...
```


Astuce : La délégation, c’est comme demander à un collègue de faire une partie de votre travail.

**lazy**

Explications :
**lazy** retarde la création d’une propriété jusqu’à ce qu’elle soit utilisée.
Utile pour les objets lourds (ex. : charger une grande image).


Exemple pour débutants :**val** donnees: String by **lazy** {
    println("Chargement des données...")
    "Données prêtes !"
}
println("Avant d’utiliser les données")
println(donnees) // Affiche : Chargement des données... puis Données prêtes !
println(donnees) // Affiche : Données prêtes ! (sans recharger)


Astuce : **lazy** économise du temps et des ressources.

**Delegates.observable**

Explications :
Permet de surveiller les changements d’une propriété et de réagir à chaque modification.
Nécessite import kotlin.properties.Delegates.


Exemple pour débutants :import kotlin.properties.Delegates
```kotlin
**var** argent: Int by **Delegates.observable**(100) { prop, ancien, nouveau ->
    println("L’argent est passé de $ancien à $nouveau")
}
argent = 150 // Affiche : L’argent est passé de 100 à 150
argent = 200 // Affiche : L’argent est passé de 150 à 200
```


Astuce : Utilisez observable pour suivre les changements, comme un journal de bord.




