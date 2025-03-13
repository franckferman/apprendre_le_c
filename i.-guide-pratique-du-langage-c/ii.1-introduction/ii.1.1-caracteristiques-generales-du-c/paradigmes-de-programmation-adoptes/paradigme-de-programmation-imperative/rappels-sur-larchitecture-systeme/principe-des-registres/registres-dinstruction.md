---
description: >-
  Présentation du registre d'instruction, qui contrôle le séquencement des
  instructions exécutées par le processeur, essentiel au déroulement logique des
  programmes.
---

# Registres d'instruction

Le registre d'instruction, aussi appelé compteur de programme, indique l'adresse de la prochaine instruction que le processeur va exécuter. Dans l'architecture x86-64, il s'agit du registre `rip`. À chaque cycle d'instruction, le processeur charge l'instruction située à l'adresse pointée par `rip`, exécute cette instruction, puis met à jour `rip` pour qu'il pointe vers l'instruction suivante.

C'est ainsi que le processeur sait quelles instructions exécuter et dans quel ordre. Le registre `rip` est automatiquement mis à jour après chaque instruction, mais peut également être modifié par des instructions de contrôle de flux, comme les sauts et les appels de fonction, permettant la mise en œuvre de boucles, de branches conditionnelles et de sous-routines dans les programmes.
