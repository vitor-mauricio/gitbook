# CMP & TEST

## **CMP**

**CMP** significa _compare_ (comparar).

Ela faz uma comparação **aritmética** entre dois operandos, mas **sem armazenar o resultado**.

CMP executa a operação `op1 - op2`, descarta o resultado e altera apenas os FLAGS.

{% hint style="info" %}
No fim do dia, o CMP faz uma operação de SUB, descarta o resultado a salva as flags da operação
{% endhint %}

### Syntax

A forma geral é:

```asm
cmp destino, fonte
```

O destino é lido, **mas não é modificado**.\
Os operandos devem ter o **mesmo tamanho**.

### Flags

Segue a lista de flags que podem ser alteradas via instrução CMP

| **Flag** | **Nome**                         | **Quando é ativada (valor = 1)**                                            | **Interpretação prática**                        | **Saltos que usam essa flag**                    |
| -------- | -------------------------------- | --------------------------------------------------------------------------- | ------------------------------------------------ | ------------------------------------------------ |
| **ZF**   | Zero Flag                        | O resultado de `op1 - op2` é **0** → operandos são iguais                   | Testa igualdade                                  | `JE/JZ`, `JNE/JNZ`                               |
| **SF**   | Sign Flag                        | O bit mais significativo do resultado é **1** → resultado negativo (signed) | Usado para comparação **signed** junto com OF    | `JL`, `JGE`, `JG`, `JLE`                         |
| **CF**   | Carry Flag (borrow em subtração) | Ocorre **borrow** → `op1 < op2` (interpretação _unsigned_)                  | Usado para comparação **unsigned**               | `JB/JNAE`, `JAE/JNB`, `JA`, `JBE`                |
| **OF**   | Overflow Flag                    | A subtração gera overflow signed → resultado tem sinal inválido             | Combinado com SF indica maior/menor **signed**   | `JG`, `JL`, `JGE`, `JLE`                         |
| **PF**   | Parity Flag                      | Byte menos significativo do resultado tem número **par** de bits “1”        | Usado raramente; herança histórica               | `JP/JPE`, `JNP/JPO`                              |
| **AF**   | Auxiliary Carry                  | Carry/borrow entre os 4 bits inferiores (nibble baixo)                      | Apenas para aritmética BCD; raramente usado hoje | (nenhum salto moderno depende diretamente de AF) |

## TEST

A instrução **TEST** executa um **AND bit a bit** entre dois operandos, **sem armazenar o resultado** — apenas altera flags.

### Syntax

```asm
test op1, op2
```

#### ✔️ O que ela faz internamente:

```
resultado = op1 AND op2
(flags são ajustados)
resultado não é escrito de volta
```

Isto é **exatamente igual ao** [#and](and-or-not-and-xor.md#and "mention"), exceto pelo fato de não salvar o resultado.

Então TEST serve como uma forma de:

> **Verificar se certos bits estão ativos sem alterar os valores originais.**
