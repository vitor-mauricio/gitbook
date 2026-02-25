# SAL & SAR

Essas são instruções de **deslocamento aritmético** (_arithmetic shift_).\
Elas são parecidas com [shl-and-shr.md](shl-and-shr.md "mention"), mas preservam ou tratam corretamente **valores signed**.

| Instrução | Nome                   | Tipo                               |
| --------- | ---------------------- | ---------------------------------- |
| **SAR**   | Shift Arithmetic Right | deslocamento aritmético à direita  |
| **SAL**   | Shift Arithmetic Left  | deslocamento aritmético à esquerda |

#### Em resumo:

* **SHL** → multiplica por potências de 2 (signed)
* **SHR** → divide por potências de 2 (signed)

## Syntax

```asm
sar destino, count
sal destino, count
```

Onde `count` pode ser:

* imediato (0–255)
* registrador CL

Exemplos:

```asm
sar rax, 1
sal ebx, 4
sar rcx, cl
```

## SAL

**SAL é idêntico a SHL.**\
São sinônimos arquiteturais.

```
SAL x, n  ==  SHL x, n
```

Ambos deslocam bits para a esquerda e entram zeros pela direita.

Exemplo:

```
Antes: 0101 1010
SAL 1 → 1011 0100
```

#### Interpretação matemática:

```
SAL x, n ≈ x * 2ⁿ
```

## SAR

Preserva o **bit de sinal**, e por isso implementa uma divisão signed.

```
SAR = signed shift right
```

#### Regra visual:

```
Antes:  1110 0100    (-28 decimal)
SAR 1 → 1111 0010    (-14 decimal)
```

Note que o bit mais significativo (MSB) é **copiado**, não substituído por zero.

#### Interpretação matemática:

```
SAR x, 1  ≈ x / 2   (divisão signed, arredonda para -∞)
```
