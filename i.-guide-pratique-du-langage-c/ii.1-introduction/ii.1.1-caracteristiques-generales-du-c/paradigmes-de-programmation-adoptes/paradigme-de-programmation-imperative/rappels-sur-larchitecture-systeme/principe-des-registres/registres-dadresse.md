---
description: >-
  Présentation des registres d'adresse, essentiels pour gérer les adresses
  mémoire, la pile, et le séquencement des instructions lors de l'exécution d'un
  programme.
---

# Registres d'adresse

Ces registres stockent les adresses mémoire des instructions ou des données. Par exemple, le registre `rip` (Instruction Pointer) stocke l'adresse de la prochaine instruction à exécuter. De même, le registre `rsp` (Stack Pointer) stocke l'adresse du sommet de la pile.

Le registre `rbp` (Base Pointer) sert généralement de point de référence pour accéder aux variables locales et aux paramètres de la fonction en cours d'exécution. Dans certaines conventions d'appel, `rbp` est utilisé pour sauvegarder l'adresse du sommet de la pile (`rsp`) au début de l'appel de fonction, permettant un accès stable aux variables locales et aux arguments de la fonction, même lorsque `rsp` change au cours de la fonction (par exemple, lors de l'allocation de l'espace sur la pile pour les variables locales).

Ces registres sont indispensables pour la gestion de la pile et le séquençage des instructions lors de l'exécution d'un programme.
