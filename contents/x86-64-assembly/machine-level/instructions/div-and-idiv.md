# DIV & IDIV

Assim como **MUL** e **IMUL**, as instruções **DIV** e **IDIV** fazem parte do conjunto de operações aritméticas **implícitas**, ou seja:

> Elas **não recebem dois operandos**.\
> Elas usam **registradores fixos** como operando de entrada e de saída.

Os valores usados como dividendos e os registradores onde o resultado é armazenado **dependem do tamanho do operando** utilizado no DIV/IDIV.

| Instrução | Tipo     | Interpretação dos valores         | Onde guarda resultado        | Exceções                           |
| --------- | -------- | --------------------------------- | ---------------------------- | ---------------------------------- |
| **DIV**   | Unsigned | tudo é positivo                   | Quociente = RAX, resto = RDX | divisor=0, quociente fora do range |
| **IDIV**  | Signed   | números signed (two’s complement) | Quociente = RAX, resto = RDX | divisor=0, overflow signed         |

## DIV

### **Sintaxe**

```asm
div <src>
```

Assim como `mul`, `div` tem **apenas 1 operando explícito** (o divisor).

O dividendo é **sempre implícito** e depende do tamanho do operando.

#### 8-bit division

```asm
div r/m8
```

Operandos:

* **Dividend = AX** (16 bits)
* **Divisor = r/m8**
* **Quociente = AL**
* **Resto = AH**

#### 16-bit division

```asm
div r/m16
```

Operandos:

* **Dividend = DX:AX** (32 bits)
* **Divisor = r/m16**
* **Quociente = AX**
* **Resto = DX**

#### 32-bit division

```asm
div r/m32
```

Operandos:

* **Dividend = EDX:EAX** (64 bits)
* **Divisor = r/m32**
* **Quociente = EAX**
* **Resto = EDX**

#### 64-bit division (x86-64 principal caso)

```asm
div r/m64
```

Operandos:

* **Dividend = RDX:RAX** (128 bits)
* **Divisor = r/m64**
* **Quociente = RAX**
* **Resto = RDX**

## IDIV

A **IDIV** é a versão assinada da divisão, usando representação de **two’s complement**.

### Sintaxe

```asm
idiv <src>
```

A operação usa o mesmo esquema implícito do DIV:

| Tamanho | Dividendo | Divisor | Quociente | Resto |
| ------- | --------- | ------- | --------- | ----- |
| 8 bits  | AX        | r/m8    | AL        | AH    |
| 16 bits | DX:AX     | r/m16   | AX        | DX    |
| 32 bits | EDX:EAX   | r/m32   | EAX       | EDX   |
| 64 bits | RDX:RAX   | r/m64   | RAX       | RDX   |
