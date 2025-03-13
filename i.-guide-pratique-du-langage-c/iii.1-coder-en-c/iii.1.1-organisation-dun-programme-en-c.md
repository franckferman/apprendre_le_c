---
description: >-
  Cette section explore l'organisation d'un programme en C, en présentant les
  notions fondamentales telles que les instructions, les fonctions, les
  commentaires, la fonction main...
---

# III.1.1 Organisation d’un programme en C

Comme mentionné précédemment, le langage C repose sur un paradigme de programmation procédurale, qui se caractérise par l'organisation des programmes en fonctions. Les fonctions en C regroupent un ensemble d'instructions spécifiquement conçues pour accomplir une tâche particulière. Les instructions en C peuvent être de deux types : simples et composées.

* **Instructions simples** : Une instruction simple représente une action unique dans l'exécution d'un programme. Par exemple, pour afficher une chaîne de caractères à l'écran, on utilise l'instruction simple `puts("Bonjour");`. Chaque instruction simple se termine par un point-virgule.

Voici quelques exemples d'instructions simples en langage C :

* **Affichage d'un message à l'écran** :

```c
printf("Bonjour, Monde!");
```

* **Assignation d'une valeur à une variable** :

```c
int age = 25;
```

* **Instructions composées** : Les instructions composées, quant à elles, regroupent plusieurs instructions simples ou d'autres instructions composées, entourées par des accolades.

Voici quelques exemples d'instructions composées en langage C :

* **Affichage de plusieurs chaînes de caractères à l'écran** :

```c
{
puts("Bonjour");  
puts("Bonsoir");  
}
```

* **Structure conditionnelle if/else** :

```c
int age = 18;

if (age >= 18) {
    printf("Vous êtes majeur.");
} else {
    printf("Vous êtes mineur.");
}
```

**Exemple de programme en C, illustrant l'utilisation d'instructions composées et d'autres concepts fondamentaux sous-jacents :**

```c
/* Programme pour 
calculer la somme de 
deux nombres */

#include <stdio.h>

// Prototypage de la fonction
int calculerSomme(int a, int b);
void afficherResultat(int a, int b, int somme);

int main(void)
{
    // Déclaration et initialisation des variables
    int a = 5;
    int b = 7;
    int somme;
    
    // Calcul de la somme
    somme = calculerSomme(a, b);
    
    // Affichage du résultat à l'écran
    afficherResultat(a, b, somme);
    
    return 0; // Indique que le programme s'est terminé normalement
}

// Définition de la fonction calculerSomme
int calculerSomme(int a, int b) {
    return a + b;
}

// Définition de la fonction afficherResultat
void afficherResultat(int a, int b, int somme) {
    printf("La somme de %d et %d est : %d\n", a, b, somme);
}
```

* **Commentaires** : Les commentaires sont des annotations dans le code qui ne sont pas exécutées par le compilateur. Ils servent à expliquer le fonctionnement du code, facilitant ainsi sa compréhension pour les autres développeurs.

En C, on distingue deux types de commentaires :

**Commentaires sur une ligne** : Ils commencent par deux barres obliques `//` et permettent de commenter une seule ligne de code.

```c
int a = 5; // Affectation de la valeur 5 à la variable a
```

**Commentaires sur plusieurs lignes** : Ils commencent par `/*` et se terminent par `*/`. Ils permettent de commenter plusieurs lignes de code.

```c
/* 
Ceci est un commentaire
sur plusieurs lignes
*/
```

* **Directives du préprocesseur** : La ligne `#include <stdio.h>` est une directive du préprocesseur qui inclut le fichier d'en-tête `stdio.h` dans le code source. Ce fichier contient les déclarations des fonctions d'entrée/sortie standard, y compris la fonction `printf()`.

Les directives du préprocesseur sont des instructions spéciales destinées à effectuer un traitement préliminaire du code source avant la phase de compilation. Elles sont différenciées des autres instructions C par le caractère dièse (#) qui les précède.

* **Inclusion d'un fichier d'en-tête de la bibliothèque standard** : Comme mentionné précédemment, le fichier d'en-tête `stdio.h` est inclus pour permettre l'utilisation de la fonction `printf()`. Cette dernière est nécessaire pour afficher des informations à l'écran.
* **Fonction principale** : La fonction `main` est la fonction principale et le point d'entrée de tout programme en C. Elle sert de coordinateur pour l'appel aux autres fonctions et gère le flux d'exécution du programme. Lorsque vous exécutez un programme, le système cherche cette fonction `main` et commence à exécuter le code qu'elle contient.

La fonction `main` peut prendre peut se présenter sous l’une ou\
l’autre des formes suivantes :

```c
int main(void)
```

Dans ce premier cas, `main` n'accepte aucun argument. C'est le choix habituel lorsque votre programme n'a pas besoin de recevoir des informations supplémentaires au moment de son exécution.

```c
int main(int argc, char *argv[])
```

Dans ce second cas, `main` accepte deux arguments :

* `argc` (argument count), qui est le nombre d'arguments passés à votre programme depuis la ligne de commande,
* `argv` (argument vector), qui est un tableau de chaînes de caractères représentant les arguments eux-mêmes.

Cette forme de `main` est utile lorsque vous voulez que votre programme réagisse différemment selon les options et les arguments fournis sur la ligne de commande. Par exemple, beaucoup de commandes Unix (comme `ls`, `grep`, etc.) utilisent cette technique pour permettre différents modes d'opération.

Pour illustrer la différence entre ces deux formes de la fonction `main`, voici deux exemples simples.

**Exemple 1 : `int main(void)`**

Dans cet exemple, le programme ne prend aucun argument et affiche simplement un message à l'écran.

```c
#include <stdio.h>

int main(void) {
    printf("Bonjour, monde !\n");
    return 0;
}
```

Lorsque vous exécutez ce programme, il affiche le message "Bonjour, monde !" à l'écran, indépendamment des arguments que vous pourriez passer à la ligne de commande.

**Exemple 2 : `int main(int argc, char *argv[])`**

```c
#include <stdio.h>

int main(int argc, char *argv[]) {
    for (int i = 0; i < argc; i++) {
        printf("Argument %d : %s\n", i, argv[i]);
    }
    return 0;
}
```

Si vous exécutez ce programme avec des arguments à la ligne de commande (par exemple `./mon_programme arg1 arg2 arg3`), il affiche quelque chose comme ceci :

```sh
Argument 0 : ./mon_programme
Argument 1 : arg1
Argument 2 : arg2
Argument 3 : arg3
```

Dans ce cas, `argv[0]` est le nom du programme lui-même, et les arguments suivants sont ceux que vous avez passés à la ligne de commande. Notez que le nombre d'arguments (y compris le nom du programme lui-même) est stocké dans `argc`.

Quelle que soit la forme de `main`, elle renvoie une valeur de type `int`. Cette valeur est le "code de sortie" du programme. Par convention, un code de sortie de `0` signifie que le programme s'est terminé avec succès, tandis que toute autre valeur indique une sorte d'erreur. Ce code de sortie peut être récupéré par d'autres programmes ou scripts qui ont exécuté votre programme, leur permettant ainsi de vérifier s'il s'est exécuté correctement ou non.

* **Affichage à l’écran** : La fonction `printf` (pour "print formatted") est utilisée pour afficher une séquence de caractères à la sortie standard, généralement l'écran. Il est à noter que `printf` n'est pas intrinsèquement partie du langage C, mais est une fonction fournie par la bibliothèque standard (déclarée dans le fichier d'en-tête `stdio.h`). La bibliothèque standard est un ensemble de fonctions qui doivent être disponibles sur tous les systèmes conformes à la norme ISO C. Dans l'exemple donné, la fonction `printf` n'a qu'un seul argument, mais elle peut en recevoir beaucoup plus.
* **Chaîne de caractères** : Une chaîne de caractères est une séquence ordonnée de caractères.
* **Formats de spécification** : Les formats de spécification sont utilisés dans les fonctions de la bibliothèque standard du langage C, telles que `printf`, pour spécifier le type et le format des données à afficher. Ils permettent de contrôler la façon dont les données sont formatées lors de leur affichage.

Lorsque nous utilisons `printf` avec des formats de spécification, nous utilisons le caractère `%` suivi d'un caractère spécifique pour représenter le type de données à afficher. Par exemple, `%d` est utilisé pour afficher des entiers décimaux (entiers signés).

Dans notre exemple, nous utilisons `%d` pour afficher les valeurs des variables `a`, `b` et `somme`. Lorsque `printf` est exécutée, chaque occurrence de `%d` est remplacée par la valeur entière correspondante.

```c
printf("La somme de %d et %d est : %d\n", a, b, somme);
```

Le spécificateur `%d` est remplacé par la valeur entière de `a`, puis de `b`, et enfin de `somme`, qui sont affichées à l'écran.

Il existe d'autres formats de spécification disponibles pour différents types de données, tels que `%f` pour les nombres flottants, `%c` pour les caractères, `%s` pour les chaînes de caractères, etc. Chaque format de spécification permet de contrôler différents aspects de l'affichage, tels que la précision, la largeur du champ, le remplissage, etc.

Il existe d'autres formats de spécification pour différents types de données, tels que `%f` pour les nombres flottants, `%c` pour les caractères, `%s` pour les chaînes de caractères, etc.

* **Caractères spéciaux** : Le caractère  est un symbole spécial qui représente un saut de ligne. En plus du caractère de saut de ligne (), il existe plusieurs autres caractères spéciaux, aussi appelés "caractères d'échappement", dans le langage de programmation C. Ces caractères commencent par une barre oblique inversée (`\`) et sont suivis d'une ou plusieurs autres lettres ou chiffres. Voici quelques exemples :
* &#x20;: Tabulation horizontale. Il déplace le curseur à la prochaine tabulation sur la ligne actuelle.
* `\b` : Retour arrière. Il déplace le curseur d'une position vers l'arrière sur la ligne actuelle.
* &#x20;: Retour chariot. Il déplace le curseur au début de la ligne actuelle sans passer à la ligne suivante.
* `\f` : Saut de page. Il provoque un saut à la page suivante.
* `\v` : Tabulation verticale. Il déplace le curseur à la position de tabulation suivante sur la colonne actuelle.
* `\a` : Carillon (BELL). Il provoque un bip sonore sur la console.
* `\\` : Barre oblique inversée. Il permet d'insérer une barre oblique inversée (`\`) dans une chaîne.
* `\'` : Apostrophe. Il permet d'insérer une apostrophe (`'`) dans une chaîne.
* `\"` : Guillemet. Il permet d'insérer un guillemet (`"`) dans une chaîne.
* `\?` : Point d'interrogation. Il permet d'insérer un point d'interrogation (`?`) dans une chaîne.
* `\0` : Caractère nul. Il représente la fin d'une chaîne de caractères en C.
* **Retour à la fonction appelante (et gestion de la pile d'appels)** : Lors de l'exécution d'un programme en C, le mécanisme du retour à la fonction appelante est géré par une structure appelée pile d'appels, qui fonctionne suivant le principe Last-In-First-Out (LIFO).

Chaque fois qu'une fonction est appelée, un cadre d'exécution (ou "frame") est créé. Ce frame contient plusieurs informations importantes, dont :

1. Les variables locales de la fonction ;
2. Les paramètres avec lesquels la fonction a été appelée ;
3. L'adresse de retour, indiquant l'endroit où le programme doit reprendre son exécution une fois que la fonction a terminé.

Ces frames sont empilés les uns sur les autres dans la pile d'appels. Le frame le plus récent, correspondant à la fonction actuellement en cours d'exécution, est toujours au sommet de la pile.

Voici un exemple simple d'un programme en C qui effectue une addition :

```c
#include <stdio.h>

// Prototypage de la fonction addition
int addition(int a, int b);

int main(void) {
    int x = 5;
    int y = 3;
    int resultat = addition(x, y);  // Appel de la fonction

    printf("La somme de %d et %d est %d\n", x, y, resultat);

    return 0;
}

// Définition de la fonction addition
int addition(int a, int b) {
    int somme = a + b;
    return somme;
}
```

Lorsque le programme est exécuté, voici comment la pile d'appels pourrait se présenter à un moment donné, pendant l'exécution de la fonction `addition` :

```
En haut de la pile (sommet)
-------------------------------
|  Frame de la fonction 'addition'  |
|    somme   |
|    b       |
|    a       |
|  Adresse de retour à main    |
-------------------------------
|  Frame de la fonction 'main' |
|    resultat  |
|    y         |
|    x         |
-------------------------------
En bas de la pile (base)
```

Une fois que la fonction `addition` a terminé son exécution, son frame est retiré de la pile d'appels. L'adresse de retour stockée dans le frame indique à l'exécution où reprendre dans la fonction `main`.

Cependant, la fonction `main`, étant le point d'entrée du programme, possède un rôle particulier. Lorsqu'elle a terminé son exécution, il n'y a pas de fonction appelante à laquelle retourner. À la place, le contrôle est rendu à l'environnement d'exécution qui a lancé le programme, généralement le système d'exploitation ou un shell.

La valeur de retour de la fonction `main` donne un statut de sortie au programme. Par convention, une valeur de retour de `0` indique que le programme s'est terminé normalement, alors que toute autre valeur peut signaler un type d'erreur spécifique. C'est un moyen de communication efficace avec l'environnement d'exécution, qui peut ainsi déterminer si le programme a été exécuté avec succès ou si une erreur est survenue.

Ces codes de sortie peuvent être utilisés par les scripts shell ou d'autres programmes qui appellent votre programme pour déterminer si votre programme a réussi ou non. Par exemple, dans un script shell, vous pouvez utiliser la variable spéciale `$?` pour obtenir le code de sortie du dernier programme exécuté. Voici un exemple :

```sh
if [ $? -eq 0 ]
then
  echo "Le programme s'est terminé avec succès."
else
  echo "Le programme a rencontré une erreur."
fi
```

Dans cet exemple, le script shell exécute `mon_programme`, puis vérifie le code de sortie. S'il est égal à 0, il affiche un message de succès, sinon il affiche un message d'erreur.

C'est une bonne pratique d'utiliser des codes de sortie significatifs dans vos programmes pour indiquer l'état de sortie de votre programme. Il est également utile de documenter ce que signifient les différents codes de sortie pour les utilisateurs de votre programme.

* **Prototypage et déclaration** : Le C est un langage de programmation statiquement typé, ce qui signifie que le type de chaque variable doit être déclaré avant son utilisation. De même, chaque fonction doit être déclarée ou prototypée avant son appel. Cette déclaration ou ce prototypage de fonction comprend le nom de la fonction, les types de ses paramètres et le type de sa valeur de retour.

Le prototypage de la fonction sert à informer le compilateur sur la façon dont une fonction est utilisée : son nombre de paramètres, le type de ces paramètres et le type de valeur qu'elle renvoie. Cela permet au compilateur de vérifier la validité des appels de fonction lors de la compilation et de signaler toute incohérence, contribuant ainsi à la prévention des erreurs.

Voici un exemple de prototypage d'une fonction :

```c
#include <stdio.h>

// Prototypes des fonctions
int addition(int a, int b);
int soustraction(int a, int b);
int multiplication(int a, int b);

int main(void) {
    int x = 10;
    int y = 5;
    
    // Appels des fonctions
    int somme = addition(x, y);
    int difference = soustraction(x, y);
    int produit = multiplication(x, y);
    
    printf("La somme de %d et %d est %d\n", x, y, somme);
    printf("La différence de %d et %d est %d\n", x, y, difference);
    printf("Le produit de %d et %d est %d\n", x, y, produit);
    
    return 0;
}

// Définition des fonctions
int addition(int a, int b) {
    return a + b;
}

int soustraction(int a, int b) {
    return a - b;
}

int multiplication(int a, int b) {
    return a * b;
}
```

Dans cet exemple, nous avons les prototypes des fonctions `addition`, `soustraction` et `multiplication` déclarés en haut du code. Ces prototypes indiquent au compilateur la signature des fonctions, c'est-à-dire le nombre et les types des paramètres, ainsi que le type de la valeur de retour.

La définition des fonctions se trouve après la fonction `main`. Les fonctions sont implémentées avec leurs opérations correspondantes.

Il convient de noter que le prototypage des fonctions n'est pas obligatoire en C si la définition de la fonction est placée avant son appel. Cependant, le prototypage des fonctions offre plusieurs avantages :

* Il permet de séparer la déclaration et l'implémentation des fonctions, rendant le code plus modulaire et plus facile à maintenir.
* Il facilite la compréhension du code en fournissant une description claire des fonctions et de leurs signatures.
* Il permet au compilateur de vérifier les appels de fonction et de détecter les erreurs de type lors de la compilation.

En général, il est recommandé de prototyper les fonctions dans des fichiers d'en-tête séparés (.h) et de les inclure dans les fichiers sources (.c) pour une meilleure organisation du code.
