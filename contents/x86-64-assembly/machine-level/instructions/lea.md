# LEA

**LEA** significa _Load Effective Address_. Ou seja, calcula o endereço efetivo resultante de uma expressão de endereçamento x86-64 e coloca esse valor em um registrador.

Em outras palavras: **LEA é uma instrução aritmética disfarçada de instrução de acesso à memória**.

No x86-64, a maioria das instruções que acessam memória usa uma sintaxe como:

```
mov rax, [rbx + rcx*4 - 8]
```

Aqui, o valor em memória no endereço\
&#xNAN;**(rbx + rcx\*4 - 8)**\
seria carregado para RAX.

A instrução **LEA** permite **calcular exatamente esse endereço**, mas sem acessar memória:

```
lea rax, [rbx + rcx*4 - 8]
```

Depois da execução:

```
rax = rbx + rcx*4 - 8
```

Nenhum byte da memória foi lido.

## Syntax

```asm
lea destino, origem
```

O operando de origem deve ser **uma expressão de endereçamento válida**, seguindo como exemplo:

```asm
[ base_reg + index_reg * escala + deslocamento ]
```

Onde:

* `base_reg`: qualquer registrador de 64 bits (exceto algumas combinações perigosas com RSP).
* `index_reg`: qualquer registrador de 64 bits, exceto RSP.
* `escala`: 1, 2, 4 ou 8.
* `deslocamento`: imediato (8, 32 ou, às vezes, 64 bits dependendo da codificação).
