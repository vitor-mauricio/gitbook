# JMP & "JCC"

**JMP** significa _jump_ (salto). Mas basicamente ela muda o valor do RIP (Instruction Pointer) para um novo endereço e continua a execução dali.

Ou seja, A CPU passa a executar outro ponto do código, sem voltar automaticamente.

#### JMP vs CALL vs RET

| Instrução | Faz o quê?              |
| --------- | ----------------------- |
| **JMP**   | RIP = destino           |
| **CALL**  | empilha RIP, depois JMP |
| **RET**   | desempilha RIP          |

Então:

* `JMP` **não cria frame**, não retorna.
* `CALL` → usado para subrotinas.
* `RET` → volta para onde `CALL` deixou.

## Syntax

A sintaxe do **JMP** depende apenas do **tipo de salto** que você quer fazer.

### Salto Direto

```asm
jmp label
```

### Salto Indireto

O destino está **no registrador**:

```asm
jmp rax
jmp rbx
jmp rcx
jmp rdi
```

O destino está na memória

```asm
jmp qword [rax+8]
```

## "JCC"

Existem algumas instruções que usam do resultado da instrução CMP para "pular" para um novo trecho de código - nascendo a ideia do fluxo condicional no código. Ou seja, instruções "jcc" pulam para um rótulo _somente se_ uma condição nos FLAGS da CPU for verdadeira.

Eles não comparam valores diretamente.\
Eles **dependem do resultado da instrução anterior**, tipicamente:

```asm
cmp rax, rbx
```

Essa `CMP` ajusta diversos FLAGS (ZF, SF, CF, OF etc.),\
e então um `Jcc` interpreta esses flags de acordo com seu significado lógico.

| Jump        | Testa      | Condição no FLAG   | Tipo      |
| ----------- | ---------- | ------------------ | --------- |
| **JE/JZ**   | igual      | ZF = 1             | igualdade |
| **JNE/JNZ** | diferente  | ZF = 0             | igualdade |
| **JA**      | > unsigned | !CF & !ZF          | unsigned  |
| **JAE**     | ≥ unsigned | !CF                | unsigned  |
| **JB**      | < unsigned | CF                 | unsigned  |
| **JBE**     | ≤ unsigned | CF \|\| ZF         | unsigned  |
| **JG**      | > signed   | !ZF & (SF == OF)   | signed    |
| **JGE**     | ≥ signed   | SF == OF           | signed    |
| **JL**      | < signed   | SF != OF           | signed    |
| **JLE**     | ≤ signed   | ZF \|\| (SF != OF) | signed    |
