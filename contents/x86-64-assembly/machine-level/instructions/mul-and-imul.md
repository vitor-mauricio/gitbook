# MUL & IMUL

`mul` é a instrução de **multiplicação inteira&#x20;**_**sem sinal**_ (unsigned) no Assembly x86-64.

Ela faz parte das chamadas **multiplicações implícitas**, porque **utiliza registros fixos** como operando inicial e para guardar o resultado final.

A `mul` **não recebe dois operandos**. Ela recebe **apenas um operando**, e o outro é **implícito**, variando com o tamanho do operando informado.

Exemplo:

```asm
mul rbx
```

Isso NÃO é “rax = rax \* rbx”.\
É: multiplicar **RAX** por **RBX**, gravando o resultado em **RDX:RAX** (128 bits).

{% hint style="warning" %}
Ou seja, o resultado SEMPRE será em 128 bits para essa operação, precisando usar os 2 registradores (RDX e RAX) para guardarem o valor de resultado.
{% endhint %}

## Syntax

A sintaxe é:

```asm
mul <src>
```

## IMUL

Existe uma instrução de MUL para lidar com os valores 'signed'. Essa instrução tem algumas diferentas práticas.

### **Sinal**

&#x20;`mul` → **multiplicação&#x20;**_**sem sinal**_ (unsigned)

* Interpreta todos os operandos como **números positivos**.
* Não existe negativo para `mul`.

Exemplo:\
`0xFF` é sempre **255**, nunca −1.

&#x20;`imul` → **multiplicação&#x20;**_**com sinal**_ (signed)

* Usa representação **two’s complement**.
* Os valores podem ser positivos _ou negativos_.

Exemplo:\
`0xFF` é interpretado como **−1** quando o tamanho é 8 bits.

### Número de operandos

`mul` → sempre **1 operando explícito**

`imul` → pode ter **1, 2 ou 3 operandos**

#### **IMUL com 1 operando** (resultado em DX:AX ou RDX:RAX)

Funciona como `mul`, só que **com sinal**:

```asm
imul rbx      ; RDX:RAX = RAX * RBX (signed)
```

#### **IMUL com 2 operandos**

```asm
imul rax, rbx       ; RAX = RAX * RBX
```

* Usa **2 registradores** explicitamente.
* Resultado fica em **um único registrador**.
* É muito mais simples de usar.

#### **IMUL com 3 operandos**

```asm
imul rax, rbx, 10   ; RAX = RBX * 10
```

* Permite multiplicar com um imediato.
* Evita usar RDX.
* É a forma mais prática.
