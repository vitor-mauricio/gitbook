# PUSH & POP

As instruções **PUSH** e **POP** manipulam a **stack** (pilha), uma área de memória organizada em modo _Last-In, First-Out_. Toda operação na pilha usa o registrador **RSP** (Stack Pointer), que aponta para o topo da pilha. A ideia do PUSH e POP é que essas operações "manipulam" o valor do RSP, movendo para cima ou para baixo.

Quando faz um PUSH:

```asm
RSP = RSP - 8     ; pilha cresce para baixo
[mem[RSP]] = valor
```

Quando faz um POP:

```asm
valor = mem[RSP]
RSP = RSP + 8     ; pilha "volta" para cima
```

{% hint style="info" %}
Em x86-64, a unidade de operação padrão é **8 bytes (64 bits)**.
{% endhint %}

## PUSH

Automaticamente decrementa o RSP em 8 - **subtrai 8** do valor atual de RSP, movendo o ponteiro para **8 bytes abaixo** (endereços menores), e em seguida grava o novo valor no topo da pilha.

<figure><img src="https://bh-cookbook.github.io/assets/images/push_logical_stack.gif" alt=""><figcaption><p>push - <a href="https://bh-cookbook.github.io/mips-asm/the-stack-part-4.html">https://bh-cookbook.github.io/mips-asm/the-stack-part-4.html</a></p></figcaption></figure>

{% hint style="success" %}
Ou seja, quando você faz uma operação de PUSH, será 'incrementado' 8 bytes na pilha e o valor passado como operando é adicionado na stack - nesse 'novo' lugar criado:
{% endhint %}

```asm
push X ; RSP -= 8 e grava X em mem[RSP]
```

### Syntax

```asm
push [operando]
```

Tipos de operando:

* Registradores de 64 bits → `push rax`
* Imediatos (inteiros) → `push 10`
* Operandos de memória → `push QWORD [rbp - 8]`

## POP

Automaticamente incrementa o RSP em 8 - **adiciona 8** no valor atual de RSP, movendo o ponteiro para 8 bytes acima (endereços maiores), e em seguida grava o valor que está em RSP para o destino passado como operando.

<figure><img src="https://bh-cookbook.github.io/assets/images/pop_logical_stack.gif" alt=""><figcaption><p>pop - <a href="https://bh-cookbook.github.io/assets/images/pop_logical_stack.gif">https://bh-cookbook.github.io/assets/images/pop_logical_stack.gif</a></p></figcaption></figure>

{% hint style="success" %}
Ou seja, quando você faz uma operação de POP, será 'decrementado' 8 bytes na pilha e o valor passado como operando vai receber o valor atual do RSP.
{% endhint %}

### Syntax

<pre class="language-asm"><code class="lang-asm">pop rax; Grava o conteúdo de mem[RSP] no registrador rax e executa o RSP += 8
<strong>/* 
</strong><strong>Ou seja:
</strong><strong>rax = mem[RSP]
</strong><strong>RSP = RSP + 8 
</strong><strong>*/
</strong></code></pre>

