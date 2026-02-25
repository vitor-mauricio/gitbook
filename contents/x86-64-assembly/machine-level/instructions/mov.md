# MOV

A instrução MOV, basicamentee, copia um valor do operando fonte (source) para o operando destino (destination).

A operação de MOV aceita algumas combinações de operando, sendo elas:

| Destino     | Fonte       | Permitido? |
| ----------- | ----------- | ---------- |
| Registrador | Registrador | ✔️         |
| Registrador | Imediato    | ✔️         |
| Registrador | Memória     | ✔️         |
| Memória     | Registrador | ✔️         |
| Memória     | Imediato    | ✔️         |
| Memória     | Memória     | ❌          |

{% hint style="danger" %}
A combinação **memória → memória NÃO existe** diretamente.

Além disso, o MOV exige que os operandos tenham **tamanho explícito ou inferível**.
{% endhint %}

## Syntax

```asm
mov destino, fonte
```

## MOVZX & MOVSX

As duas instruções fazem **movimentação + expansão**:

| Instrução   | Expansão    | Interpretação do valor                      |
| ----------- | ----------- | ------------------------------------------- |
| **`movzx`** | Zero-extend | trata o valor como **sem sinal** (unsigned) |
| **`movsx`** | Sign-extend | trata o valor como **com sinal** (signed)   |

Elas pegam um valor menor (8 ou 16 bits) e o movem para um registro maior (16, 32 ou 64 bits), **preenchendo os bits superiores** diferentemente.

### MOVZX

`movzx` faz duas coisas:

1. Copia o valor-fonte (8 ou 16 bits)
2. Preenche os bits superiores com **zeros**

Dessa forma, o valor é interpretado como **unsigned**.

#### Exemplo: copiar um byte para um registrador 64-bit

```asm
movzx rax, byte [foo]
```

Se o byte é:

```
0xFF (255 decimal)
```

O resultado será:

```
RAX = 00000000000000FFh
```

Os bits superiores ficam **zerados**, então 0xFF = **255**, nunca -1.

### MOVSX

`movsx`:

1. Copia o valor-fonte (8 ou 16 bits)
2. Replica o **bit de sinal** (bit mais significativo) por todos os bits superiores

Logo, preserva o valor **signed** em two’s complement.

#### Exemplo: copiar um byte negativo para 64 bits

```asm
movsx rax, byte [foo]
```

Se o byte é:

```
0xFF (mas como 8 bits signed, é -1)
```

O resultado será:

```
RAX = FFFFFFFFFFFFFFFFh   ; -1 em 64 bits
```

Ou seja:

* movzx → interpreta 0xFF como 255
* movsx → interpreta 0xFF como -1
