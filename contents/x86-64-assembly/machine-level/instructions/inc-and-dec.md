# INC & DEC

* **INC** → _increment_
* **DEC** → _decrement_

Elas fazem uma operação aritmética **simples**, atuando diretamente sobre um registrador ou endereço de memória.

#### INC

```
destino = destino + 1
```

#### DEC

```
destino = destino - 1
```

Não exigem operando fonte — o único operando é o destino.

## Sintaxe

#### Incrementar:

```asm
inc rax
inc byte [rdi]
inc dword [rbp-4]
```

#### Decrementar:

```asm
dec rbx
dec qword [rsi]
dec word [rdi+8]
```

As instruções funcionam para **8, 16, 32 e 64 bits**.
