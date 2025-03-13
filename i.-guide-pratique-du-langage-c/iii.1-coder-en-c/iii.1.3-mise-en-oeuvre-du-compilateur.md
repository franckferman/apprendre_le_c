---
description: >-
  Cette section explique comment compiler et exécuter un programme en C,
  notamment à l’aide du compilateur GCC, et présente les principales options
  permettant de contrôler le processus de compilation.
---

# III.1.3 Mise en oeuvre du compilateur

En général, l'ensemble du processus de compilation d'un programme est réalisé en une seule étape, de manière transparente pour l'utilisateur. Cette opération peut être initiée via une simple commande, telle que `gcc fichier.c`, si nous prenons l'exemple du compilateur GCC (GNU Compiler Collection) très couramment utilisé.

L'exécution de cette commande produit un fichier exécutable nommé `a.out` par défaut. Ce fichier peut être lancé depuis l'interface de ligne de commande du système d'exploitation. Voici un exemple illustrant cette opération à travers un programme :

```c
#include <stdio.h>

int main(void)
{
    int nombre1, nombre2, somme;

    printf("Entrez le premier nombre : ");
    scanf("%d", &nombre1);

    printf("Entrez le deuxième nombre : ");
    scanf("%d", &nombre2);

    somme = nombre1 + nombre2;

    printf("La somme des deux nombres est : %d\n", somme);

    return 0;
}
```

Ce programme demande à l'utilisateur d'entrer deux nombres, puis calcule leur somme et l'affiche à l'écran.

Pour exécuter ce programme, vous devez suivre les étapes suivantes :

1. Créez un nouveau fichier avec l'extension `.c`, par exemple `somme.c`.
2. Copiez le code ci-dessus dans ce fichier.
3. Ouvrez un terminal et placez-vous dans le répertoire où se trouve le fichier `somme.c`.
4. Compilez le fichier C en utilisant la commande `gcc somme.c -o somme` (cette commande crée un fichier exécutable nommé `somme`).
5. Exécutez le programme en tapant `./somme` dans le terminal.
6. Suivez les instructions pour entrer les nombres, puis appuyez sur Entrée.
7. Le programme affichera la somme des deux nombres entrés.

Il est important de souligner que le compilateur GCC, comme la plupart des compilateurs, offre une multitude d'options qui permettent de contrôler plus finement le processus de compilation. L'option `-o` permet de spécifier le nom du fichier exécutable résultant, tandis que l'option `-c` est utile lorsque plusieurs modules requièrent des compilations séparées. L'option `-Wall`, qui intensifie les vérifications du compilateur, est très pratique pour détecter toute anomalie potentielle dans le code source.

Voici une liste non exhaustive des options les plus couramment utilisées avec GCC :

* `-c` : Omet l'étape d'édition de liens et produit uniquement un fichier objet.
* `-E` : Active seulement le préprocesseur. Le résultat est envoyé sur la sortie standard.
* `-g` : Génère des informations de débogage dans le fichier exécutable.
* `-I<directory>` : Spécifie le répertoire où le compilateur doit chercher les fichiers d'en-tête à inclure, en plus du répertoire courant.
* `-L<directory>` : Spécifie le répertoire où le compilateur doit chercher les bibliothèques à lier, en plus des répertoires standard.
* `-o <filename>` : Spécifie le nom du fichier exécutable à générer. Par défaut, le nom est `a.out`.
* `-O, -O1, -O2, -O3` : Options d'optimisation du code. Un nombre plus élevé indique un niveau d'optimisation plus élevé.
* `-S` : Active seulement le préprocesseur et le compilateur. Produit un fichier assembleur.
* `-v` : Affiche les commandes effectuées à chaque étape de la compilation.
* `-W` : Affiche des messages d'avertissement supplémentaires.
* `-Wall` : Affiche tous les messages d'avertissement.

En utilisant ces options, les développeurs peuvent affiner le processus de compilation pour répondre à des besoins spécifiques, tels que la génération de code de débogage, l'optimisation du code produit, ou la résolution de problèmes spécifiques identifiés lors de la compilation.
