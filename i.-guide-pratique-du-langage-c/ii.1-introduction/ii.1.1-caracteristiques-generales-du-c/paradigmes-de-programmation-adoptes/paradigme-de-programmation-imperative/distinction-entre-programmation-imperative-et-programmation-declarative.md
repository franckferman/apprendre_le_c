---
description: >-
  Cette section présente les différences fondamentales entre programmation
  impérative et déclarative, illustrées par des exemples concrets et des
  analogies accessibles.
---

# Distinction entre programmation impérative et programmation déclarative

La programmation impérative se différencie de la programmation déclarative, où les instructions dépeignent le résultat escompté, plutôt que la manière de l'atteindre.

Effectivement, la programmation déclarative consiste à rédiger des instructions qui décrivent ce que l'on souhaite accomplir, plutôt que de spécifier comment le faire. La programmation déclarative est souvent perçue comme plus intuitive et plus aisée à comprendre que la programmation impérative, car elle se focalise sur ce que le code fait, plutôt que sur les détails de son fonctionnement interne.

Le concept de programmation impérative s'apparente à celui de suivre une recette de cuisine ou un processus industriel. Dans ce contexte, chaque étape est considérée comme une instruction, et le monde physique est considéré comme l'état modifiable. Étant donné que les principes fondamentaux de la programmation impérative sont à la fois familiers et directement intégrés dans l'architecture des microprocesseurs, la plupart des langages de programmation adoptent ce type de paradigme.

Pour illustrer la divergence entre programmation déclarative et programmation impérative, nous utiliserons deux exemples simples : le calcul de la somme des nombres pairs d'une liste d'entiers et la recherche de données dans une base de données.

* **Exemple 1 : Calcul de la somme des nombres pairs**

**Impératif (Python)**

```python
def somme_nombres_pairs(liste_nombres):
    somme = 0
    for nombre in liste_nombres:
        if nombre % 2 == 0:
            somme += nombre
    return somme

liste_nombres = [1, 2, 3, 4, 5, 6, 7, 8, 9]
resultat = somme_nombres_pairs(liste_nombres)
print(resultat)
```

Dans cette approche impérative, chaque étape du calcul est explicitement définie. L'état initial est déclaré (somme = 0), puis une boucle parcourt la liste de nombres, et pour chaque nombre pair (si son reste après division par 2 est égal à zéro), celui-ci est ajouté à la somme. L'impératif ici est dans la description explicite du processus de calcul.

**Déclaratif (Haskell)**

```haskell
sommeNombresPairs :: [Int] -> Int
sommeNombresPairs listeNombres = sum (filter even listeNombres)

listeNombres = [1, 2, 3, 4, 5, 6, 7, 8, 9]
resultat = sommeNombresPairs listeNombres
print resultat
```

Dans cette approche déclarative, le calcul est exprimé sans l'explicitation de chaque étape. Les fonctions `filter` et `sum` sont employées pour obtenir une liste de nombres pairs, puis calculer leur somme. L'intention du "quoi" (la somme des nombres pairs) est mise en avant plutôt que le "comment" (le filtrage et l'addition).

Ces deux exemples mettent en exergue les différences entre la programmation impérative et déclarative. L'impérative fournit une séquence détaillée d'instructions pour obtenir le résultat, tandis que la déclarative décrit le résultat souhaité, laissant les détails du "comment" au système d'exécution.

* **Exemple 2 : Recherche de données dans une base de données**

**Impératif (Python)**

```python
import sqlite3

conn = sqlite3.connect('ma_base_de_donnees.db')
curseur = conn.cursor()

curseur.execute("SELECT nom, prenom FROM utilisateurs WHERE age > 18")
resultats = curseur.fetchall()

for resultat in resultats:
    print(resultat)

conn.close()
```

Cet exemple en Python est impératif. Il spécifie chaque étape de la requête, incluant l'ouverture et la fermeture de la connexion à la base de données, l'exécution de la requête SQL et la gestion des résultats.

**Déclaratif (SQL)**

```sql
SELECT nom, prenom FROM utilisateurs WHERE age > 18
```

Cette requête SQL est déclarative. Elle se focalise sur la description de l'information souhaitée, laissant le système de gestion de base de données se charger des détails de comment obtenir ces informations.

**Déclaratif (Haskell)**

```haskell
import Database.HDBC.Sqlite3 (connectSqlite3, Connection)
import Database.HDBC (runRaw, quickQuery')

trouverUtilisateurs :: Int -> IO [[String]]
trouverUtilisateurs age = do
    conn <- connectSqlite3 "ma_base_de_donnees.db"
    let requete = "SELECT nom, prenom FROM utilisateurs WHERE age > ?"
    resultats <- quickQuery' conn requete [toSql age]
    return resultats
```

Ce code Haskell est également déclaratif, utilisant des fonctions pour interagir avec la base de données. Il offre un certain niveau d'abstraction en cachant certains détails d'implémentation tout en offrant plus de contrôle comparé à l'exemple SQL.

Pour les trois exemples ci-dessus, la tâche consiste à chercher les noms et prénoms des utilisateurs dont l'âge est supérieur à 18 ans dans une base de données. Le code Python, de nature impérative, requiert une séquence d'étapes détaillées comme l'ouverture de la connexion, la création d'un curseur, l'exécution de la requête SQL, la récupération des résultats et la fermeture de la connexion.

Le code SQL, par contre, est déclaratif : il définit la requête pour extraire les données sans s'embarrasser des détails techniques.

Enfin, le code Haskell, également déclaratif, utilise des fonctions pour interagir avec la base de données, offrant une plus grande flexibilité et un meilleur contrôle que la simple requête SQL.

* **Analogie : Préparer une tasse de thé**

Si l'on devait préparer une tasse de thé, une approche impérative dicterait toutes les étapes nécessaires à la préparation :

```markdown
1. Trouver une tasse propre.
2. Placer un sachet de thé dans la tasse.
3. Faire bouillir de l'eau.
4. Verser l'eau bouillante dans la tasse avec le sachet de thé.
5. Laisser infuser pendant environ 3 minutes.
6. Retirer le sachet de thé.
7. Ajouter du sucre et du lait selon les préférences.
```

Dans une approche déclarative, on pourrait simplement décrire le résultat final souhaité sans préciser comment l'atteindre. Par exemple :

```markdown
- J'aimerais une tasse de thé avec un peu de sucre et du lait.
```

La programmation déclarative se concentre sur le résultat escompté, laissant le soin aux abstractions et aux outils sous-jacents de déterminer les détails spécifiques de la mise en œuvre pour atteindre ce résultat.
