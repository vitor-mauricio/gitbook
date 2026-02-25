# "CMOVcc"

As **CMOVcc** são um _conjunto_ de instruções de **movimentação condicional** no x86/x86-64. Elas fazem um [mov.md](mov.md "mention"), **mas só se uma condição baseada nas flags for verdadeira**. Se a condição for falsa, **não acontece nada** (o destino permanece exatamente como estava).

Em vez de escrever:

```asm
cmp rax, rbx
jl  menor
mov rcx, rax
jmp fim
menor:
mov rcx, rbx
fim:
```

Você pode escrever:

```asm
mov rcx, rax
cmp rax, rbx
cmovl rcx, rbx
```

👉 **Sem salto (branch)**\
👉 **Sem mudança no fluxo de execução**\
👉 Tudo acontece **linearmente**

## Syntax

#### Intel syntax

```asm
cmovcc reg_dest, reg_src
```

* O **destino TEM que ser um registrador**
* A **fonte pode ser registrador ou memória**
* **Nunca** escreve em memória

Cada sufixo representa uma condição baseada nas **flags** do `RFLAGS`, normalmente setadas por:

* `CMP`
* `TEST`
* operações aritméticas (`ADD`, `SUB`, etc.)

Exemplos:

* `cmove` → equal
* `cmovne` → not equal
* `cmovl` → less (signed)
* `cmovg` → greater (signed)
* `cmova` → above (unsigned)
* `cmovb` → below (unsigned)

## Uso de Flags

As condições usam as **mesmas regras dos Jcc**.

#### Igualdade

| Instrução           | Condição |
| ------------------- | -------- |
| `cmove` / `cmovz`   | ZF = 1   |
| `cmovne` / `cmovnz` | ZF = 0   |

***

#### Comparação **signed**

Usadas quando os operandos são **com sinal** (`int`, `long`):

| Instrução | Condição          |
| --------- | ----------------- |
| `cmovl`   | SF ≠ OF           |
| `cmovle`  | ZF = 1 ou SF ≠ OF |
| `cmovg`   | ZF = 0 e SF = OF  |
| `cmovge`  | SF = OF           |

***

#### Comparação **unsigned**

Usadas quando os operandos são **sem sinal** (`unsigned int`, `size_t`):

| Instrução | Condição         |
| --------- | ---------------- |
| `cmova`   | CF = 0 e ZF = 0  |
| `cmovae`  | CF = 0           |
| `cmovb`   | CF = 1           |
| `cmovbe`  | CF = 1 ou ZF = 1 |

