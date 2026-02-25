# SHL & SHR

Ambas são instruções de **deslocamento lógico** (_logical shift_):

| Instrução | Significado         | Operação                              |
| --------- | ------------------- | ------------------------------------- |
| **SHL**   | Shift Logical Left  | desloca todos os bits para a esquerda |
| **SHR**   | Shift Logical Right | desloca todos os bits para a direita  |

#### Em resumo:

* **SHL** → multiplica por potências de 2
* **SHR** → divide por potências de 2 (unsigned)

## Syntax

```asm
shl destino, count
shr destino, count
```

Onde `count` pode ser:

* um **imediato** (0–255),
* o registrador **CL** (apenas CL).

Exemplos:

```asm
shl rax, 1
shr rbx, 4
shl rcx, cl
```

## SHL

Exemplo com 8 bits:

```
Antes:  0110 1101
SHL 1 → 1101 1010
```

O bit que "sai" pela esquerda vai para o **CF**, e um **0** entra pela direita.

#### Regra:

```
(destino << count)
```

#### Efeito matemático:

```
destino = destino * (2^count)
```

## SHR

Exemplo com 8 bits:

```
Antes:  0110 1101
SHR 1 → 0011 0110
```

O bit que "sai" pela direita vai para o **CF**, e um **0** entra pela esquerda.

#### Regra:

```
(destino >> count)  com 0 preenchendo a esquerda
```

#### Efeito matemático (unsigned):

```
destino = destino / (2^count)
```
