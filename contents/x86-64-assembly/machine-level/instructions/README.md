# Instructions

<figure><img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExdXRmaGRyOWZ4anV4MWZzM21wcmNpZjV3ZHZjenhyNWNuOXB3eGVzaSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/dsny94L0irr8byJ9OM/giphy.gif" alt=""><figcaption></figcaption></figure>

Instruções em **assembly** são **comandos de baixo nível** que dizem ao processador exatamente o que fazer — passo a passo, operação por operação. Cada instrução corresponde **quase diretamente** a uma operação que a CPU sabe executar no nível de hardware (a chamada _ISA – Instruction Set Architecture_).

{% hint style="success" %}
A ideia central: **assembly é uma camada textual/humana** para representar as instruções de máquina binárias que o processador realmente entende.
{% endhint %}

## Working with Operations

O CPU só entende operações muito simples, como: mover dados entre registradores e/ou memória, fazer soma/subtração/deslocamento de bits, comparar valores, alterar fluxos de execução etc.

Cada uma dessas operações é mapeada para uma instrução Assembly.

{% hint style="info" %}
Uma instrução em Assembly depende totalmente da arquitetura do processador. Cada arquitetura tem: registradores diferentes, tamanho de palavras (words) diferentes, formas diferentes de endereçar memória etc. Ou seja, o Assembly depende da ISA em questão.&#x20;
{% endhint %}

Geralmente instruções são usadas da seguinte forma:

```css
[opcode] [operandos...]
```

**Opcode** → qual operação executar\
**Operandos** → sobre quais dados operar (registradores, memória, imediatos)

## Instructions Map

<table data-card-size="large" data-view="cards"><thead><tr><th></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>NOP</td><td><a href="nop.md">nop.md</a></td></tr><tr><td>PUSH &#x26; POP</td><td><a href="push-and-pop.md">push-and-pop.md</a></td></tr><tr><td>CALL &#x26; RET</td><td><a href="call-and-ret.md">call-and-ret.md</a></td></tr><tr><td>MOV</td><td><a href="mov.md">mov.md</a></td></tr><tr><td>ADD &#x26; SUB</td><td><a href="add-and-sub.md">add-and-sub.md</a></td></tr></tbody></table>
