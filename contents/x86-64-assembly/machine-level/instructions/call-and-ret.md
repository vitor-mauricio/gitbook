# CALL & RET

CALL e RET são responsáveis por transferir o controle para uma função diferente - em uma maneira que o controle pode voltar para a função 'principal' (ou função de origem) quando acontecer um 'retorno'.

De forma resumida:

* **CALL** → chama uma função
* **RET** → retorna de uma função

## CALL

A instrução **CALL** faz duas operações fundamentais: empilha o endereço de retorno na pilha e salta para o endereço da função.

Ou seja, internamento o processador faz um "push" do endereço da próxima instrução: `push RIP ; Endereço da próxima instrução` .

Mais precisamente:

* `RSP = RSP - 8`
* `mem[RSP] = endereço_da_próxima_instrução`

Depois de empilhar o endereço de retorno, o CALL faz:

```asm
RIP = endereço_da_função
```

### Syntax

A instrução CALL pode ser feita de 2 maneiras: Indireta e diretamente.

#### Direta

Chama um símbolo/label diretamente conhecido no assembly.

```asm
call label ; Exemplo: call minha_funcao
```

Ou seja:

* O destino do salto é conhecido em tempo de montagem (assembler).
* O CALL escreve o endereço de retorno na pilha e pula para `label`.

#### Indireta

Aqui, o destino não é um label, mas um **valor armazenado num registrador ou numa posição de memória**.\
É usado para ponteiros de função, tabelas de despacho, vtables, trampolines etc.

```asm
call rax
call rbx
call r10
```

Significa:\
"Salta para o endereço contido dentro do registrador."

## RET

A instrução RET faz basicamente o oposto da CALL .

Ela:

1. Lê o valor que está no topo da pilha (que é o endereço de retorno).
2. Atribui esse valor a RIP (fazendo o salto de volta).
3. Ajusta o ponteiro da pilha.

Então:

```asm
RIP = mem[RSP]     ; pega o endereço que o CALL colocou
RSP = RSP + 8      ; remove o topo da pilha
```

Ou seja, **RET = POP RIP** (conceitualmente).

### Syntax

Existem 2 formas de executar o RET:

#### RET Simples:

```asm
ret
```

Equivalente a:

```asm
pop rip
```

Ou seja:

1. Lê o endereço de retorno da pilha
2. Ajusta RSP
3. Salta para onde estava antes do CALL

#### RET com argumento (limpeza de pilha)

```asm
ret n
```

* `n` deve ser um **imediato** (um número).
* Após fazer o RET normal, a CPU faz:\
  `RSP = RSP + n`

Exemplo:

```asm
ret 16
```

Significa:

1. `RIP = mem[RSP]`
2. `RSP = RSP + 8` ; comportamento normal do ret
3. `RSP = RSP + 16` ; limpeza extra da pilha

{% hint style="info" %}
Essa forma era usada em **stdcall (Windows x86)** para limpar argumentos da função.
{% endhint %}

{% hint style="warning" %}
No x86-64 (Linux, System V ABI), **RET com argumento é praticamente nunca usado**, porque os argumentos são passados em registradores, não na pilha.
{% endhint %}

Um bom resumo de como funciona:

{% embed url="https://www.youtube.com/watch?v=u_-oQx_4jvo" %}
