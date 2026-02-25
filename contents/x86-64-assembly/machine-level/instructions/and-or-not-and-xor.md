# AND, OR, NOT & XOR

Essas quatro instruções realizam operações **bit a bit** (_bitwise_):

| Instrução | Operação                        |
| --------- | ------------------------------- |
| **AND**   | Conjunção (bitwise AND)         |
| **OR**    | Disjunção (bitwise OR)          |
| **XOR**   | Exclusão (bitwise XOR)          |
| **NOT**   | Negação bit a bit (bitwise NOT) |

São muito usadas em sistemas, criptografia, flags de controle, máscaras (_bitmasks_), manipulação de registradores e otimizações.

## AND

### Syntax

```asm
and destino, fonte
```

Formalmente:

```
destino ← destino & fonte
```

### Usos

* Criar máscaras para limpar bits:

```asm
and rax, 0xFF        ; mantém só o último byte
```

* Verificar bits específicos:

```asm
and rax, 1
jz par               ; testa se número é par
```

* Alinhamento:

```asm
and rsp, -16         ; alinha stack para múltiplo de 16
```

## OR

### Syntax

```asm
or destino, fonte
```

Formalmente:

```
destino ← destino | fonte
```

### Usos

* Ativar bits de um registrador:

```asm
or rax, 0x04    ; ativa o 3º bit
```

* Criar flags:

```asm
or eax, 0x80000000
```

* Criar combinações:

```asm
or rbx, rax
```

## NOT

### Syntax

```asm
not destino
```

Formalmente:

```
destino ← ~destino
```

### Usos

* Criar máscaras inversas:

```asm
not rax       ; inverte todos os bits
```

* Implementar operações lógicas mais complexas:

```asm
and rbx, rax
not rbx
```

* Preparar complementos aritméticos (two's complement):

```asm
not eax
inc eax     ; now eax = -(original eax) - 1 + 1 = -original
```

## XOR

### Syntax

```asm
xor destino, fonte
```

Formalmente:

```
destino ← destino ^ fonte
```

### Usos

* **Zerar registradores rapidamente**:

```asm
xor eax, eax   ; zera eax (mais rápido que mov eax, 0)
```

Esse padrão é tão clássico que os compiladores usam sempre.

* **Toggle de bits**:

```asm
xor rax, 1     ; alterna entre par/impar
```

* **Remover bits** (quando conhecidos):

```asm
xor rax, 0xFF  ; inverte apenas esses bits
```

* **Criptografia simples**:

```asm
xor [rdi], rax
```
