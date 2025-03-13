---
description: >-
  Présentation du concept d'opcode, instruction élémentaire comprise par le
  processeur, et illustration de son usage à travers un exemple concret en
  assembleur x86-64.
---

# Principe d'Opcode

Un opcode, ou code d'opération, est une instruction de bas niveau qui dicte une tâche spécifique à accomplir - qui est reconnue et exécutée par le processeur d'un ordinateur. C'est en quelque sorte le langage natif du processeur. Chaque type de processeur a son propre ensemble spécifique d'opcodes défini par l'architecture du processeur. Par exemple, l'opcode "ADD" indique au processeur de réaliser une addition.

| Code source en C | Code assembleur correspondant                                                       |   |
| ---------------- | ----------------------------------------------------------------------------------- | - |
| `arg1 += arg2;`  | `add rsi, rdi`                                                                      |   |
| `arg1 = arg2;`   | `mov rsi, rdi`                                                                      |   |
| `arg1 *= 2;`     | `sal rdi, 1`                                                                        |   |
| `arg2 /= 3;`     | <p><code>mov rsi, 3</code><br><code>xor rax, rax</code><br><code>div rsi</code></p> |   |

Il est important de noter que les opcodes sont très basiques. Chaque opcode ne fait qu'une petite partie du travail. Mais en combinant des séquences d'opcodes, les programmeurs peuvent réaliser des tâches plus complexes.

Un exemple simple d'une séquence d'opcodes pourrait être le suivant :

Disons que nous avons une fonction simple en langage C :

```c
int add_and_subtract(int A, int B, int C) {
    return (A + B) - C;
}
```

Dans l'assembleur x86-64, cette fonction pourrait ressembler à :

```asm
; Définition de la fonction add_and_subtract
; En entrée, les arguments A, B et C sont respectivement dans les registres rdi, rsi, et rdx
; Le résultat sera renvoyé dans le registre rax
add_and_subtract:
    ; On commence par additionner A et B
    mov rax, rdi ; On place A dans rax
    add rax, rsi ; On additionne B à rax. A ce stade, rax = A + B

    ; On soustrait ensuite C
    sub rax, rdx ; On soustrait C de rax. A ce stade, rax = (A + B) - C

    ; On a terminé, on retourne à l'appelant. Le résultat est dans rax
    ret
```

Dans cet exemple, chaque ligne représente une instruction opcode que le processeur va exécuter. Chaque opcode représente une opération de bas niveau très spécifique que le processeur va exécuter, et en combinant ces opcodes, nous pouvons créer des opérations plus complexes.
