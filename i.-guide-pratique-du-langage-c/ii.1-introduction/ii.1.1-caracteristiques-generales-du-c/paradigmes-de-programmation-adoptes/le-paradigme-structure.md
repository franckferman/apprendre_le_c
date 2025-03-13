---
description: >-
  Présentation du paradigme structuré, centré sur l’organisation hiérarchique du
  code et l’utilisation de structures de contrôle claires pour garantir
  lisibilité et maintenabilité.
---

# Le paradigme structuré

Le paradigme structuré, qui est également un sous-ensemble de l'impératif, met l'accent sur la création de structures de données claires et simples, et sur la gestion du flux du programme. Il favorise l'utilisation de blocs logiques comme les boucles et les instructions conditionnelles pour diriger le flux d'exécution, améliorant ainsi la lisibilité et la maintenabilité du code. Dans le langage C, les structures de contrôle comme les boucles `for`, `while` et `do...while` ainsi que les instructions conditionnelles `if...else` illustrent ce paradigme.

**Exemple d'utilisation de structures de données et de boucles `for` pour effectuer une opération sur un tableau d'entiers**

```c
#include <stdio.h>

#define SIZE 5

int main()
{
    int numbers[SIZE] = {1, 2, 3, 4, 5};
    int sum = 0;
    int i;

    // Boucle for pour calculer la somme des éléments du tableau
    for (i = 0; i < SIZE; i++)
    {
        sum += numbers[i];
    }

    printf("La somme des éléments du tableau est : %d\n", sum);

    return 0;
}
```

L'article fondateur de Dijkstra, "GO TO statement considered harmful", a grandement influencé le développement de la programmation structurée. Il mettait en exergue les problèmes causés par l'instruction `goto`, notamment la difficulté à suivre la logique du code et à le déboguer. La programmation structurée prône une organisation hiérarchique claire du code, souvent réalisée par le biais de structures de contrôle telles que `while`, `repeat`, `for`, `if..then..else`. Elle recommande aussi un unique point d'entrée et de sortie pour chaque boucle, une règle appliquée par certains langages de programmation.

**Exemple d'utilisantion d'instructions `goto`**

```c
#include <stdio.h>

#define SIZE 5

int main()
{
    int numbers[SIZE] = {1, 2, 3, 4, 5};
    int sum = 0;
    int i = 0;

    goto loop_start;

loop_start:
    if (i >= SIZE)
        goto loop_end;

    sum += numbers[i];
    i++;
    goto loop_start;

loop_end:
    printf("La somme des éléments du tableau est : %d\n", sum);

    return 0;
}
```

L'utilisation d'instructions `goto` rend le code moins lisible, moins prévisible et plus difficile à comprendre et à maintenir. Les instructions `goto` cassent la structure naturelle du code et rendent la logique du programme plus complexe à suivre.

En résumé, les paradigmes de programmation impératif, procédural et structuré sont des approches complémentaires permettant d'organiser et de structurer le code. Le paradigme impératif est axé sur les instructions, le paradigme procédural se concentre sur les fonctions et le paradigme structuré vise la mise en place de structures de données simples et de contrôles de flux efficaces.

