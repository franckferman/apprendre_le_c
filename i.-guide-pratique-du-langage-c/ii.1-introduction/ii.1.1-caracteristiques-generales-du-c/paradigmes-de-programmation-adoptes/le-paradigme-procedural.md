---
description: >-
  Introduction au paradigme procédural, fondé sur le paradigme impératif, qui
  structure le code en fonctions pour améliorer la lisibilité, la modularité et
  la maintenance du programme.
---

# Le paradigme procédural

La programmation procédurale repose sur le paradigme impératif. Elle consiste à structurer le code en procédures, ou fonctions, qui sont des suites d'instructions ordonnées exécutées successivement, de haut en bas. Les fonctions regroupent des instructions liées entre elles, ce qui améliore la lisibilité et la modularité du code, et facilite son débogage. En C, cette approche est utilisée de manière extensive.

```c
#include <stdio.h>

// Déclarations de prototypes des fonctions
int addition(int a, int b);
void afficherResultat(int resultat);
void effectuerOperation(int x, int y);

// Fonction main (point d'entrée du programme)
int main()
{
    int a = 5;
    int b = 3;

	// Appel de la fonction effectuerOperation pour effectuer une opération
    effectuerOperation(a, b);

    return 0;
}

// Définition des fonctions

// Fonction qui calcule la somme de deux entiers
int addition(int a, int b)
{
    return a + b;
}

// Fonction qui affiche le résultat d'une opération
void afficherResultat(int resultat)
{
    printf("Le résultat est : %d\n", resultat);
}

// Fonction qui effectue une opération en utilisant les deux fonctions précédentes
void effectuerOperation(int x, int y)
{
    int somme = addition(x, y);
    afficherResultat(somme);
}
```
