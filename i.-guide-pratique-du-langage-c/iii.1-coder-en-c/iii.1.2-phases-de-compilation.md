---
description: >-
  Cette section détaille les différentes phases du processus de compilation en
  langage C, depuis le prétraitement du code source jusqu'à la création du
  fichier exécutable final.
---

# III.1.2 Phases de compilation

Il est essentiel de distinguer les langages compilés des langages interprétés. Le langage C est un exemple parfait de langage compilé, ce qui signifie qu'avant d'être exécuté par la machine, le code source C doit être traduit en langage machine, un ensemble d'instructions directement compréhensible par le processeur. En comparaison, les langages interprétés, comme Python ou JavaScript, sont exécutés ligne par ligne par un interpréteur, sans nécessiter de compilation préalable. Voici un tableau illustrant quelques exemples de ces deux types de langages :

| Langages compilés | Langages interprétés |
| ----------------- | -------------------- |
| C                 | Python               |
| C++               | JavaScript           |
| Java              | Ruby                 |
| C#                | PHP                  |
| Go                | Perl                 |
| Rust              | Lua                  |
| Swift             | Shell scripts        |

En C, le code source est initialement écrit dans un ou plusieurs fichiers textes appelés fichiers source (avec l'extension `.c`). Comme ce code source n'est pas directement exécutable par le système, il doit être traduit en langage machine. Cette traduction est réalisée par un logiciel spécialisé appelé compilateur.

La compilation elle-même se déroule en plusieurs phases successives :

* **Prétraitement** : Le préprocesseur effectue des transformations purement textuelles du code source. Il traite des directives spécifiques du préprocesseur telles que l'inclusion de fichiers (`#include`), le remplacement de macros (`#define`), la compilation conditionnelle (`#ifdef`, `#ifndef`, `#endif`), et d'autres. Le résultat de cette phase est un fichier prétraité avec l'extension `.i`.
* **Compilation proprement dite** : Ensuite, le compilateur traduit le code source prétraité en code assembleur, qui est une suite d'instructions de bas niveau exprimées en mnémoniques, un format proche du langage machine mais encore lisible par les humains. Le fichier résultant de cette phase a l'extension `.s`.
* **Assemblage** : L'assembleur transforme le code assembleur en code machine. Chaque mnémonique est traduite en une instruction compréhensible par le processeur spécifique de la machine sur laquelle le code sera exécuté. Le fichier résultant de cette étape, appelé fichier objet, porte l'extension `.o`.
* **Édition de liens** : Enfin, l'éditeur de liens (ou "linker") combine tous les fichiers objets, ainsi que d'éventuelles bibliothèques, en un seul fichier exécutable. Il résout toutes les références mutuelles entre les diverses parties du programme, y compris les appels à des fonctions qui sont définies ailleurs. Le fichier final peut être un fichier exécutable ou une bibliothèque de fonctions. Les fichiers exécutables n'ont généralement pas d'extension sur les systèmes UNIX et l'extension `.exe` sur les systèmes Windows. Les bibliothèques ont généralement l'extension `.a` ou `.so` sur les systèmes UNIX, et `.dll` sur les systèmes Windows.

Les différents fichiers résultants de ces différentes étapes se distinguent en premier par leur suffixe. Les fichiers source sont suffixés par .c, les fichiers prétraités par le préprocesseur par .i, les fichiers assembleur par .s, et les fichiers objet par .o. Les fichiers objets correspondant aux librairies pré-compilées ont pour suffixe .a.
