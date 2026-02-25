---
description: >-
  A conversão de dados em binário, hexadecimal, decimal é algo que será
  imporante para entender o funcionamento do Assembly.
---

# Decimal -> Binary -> Hexadecimal

### Binary to Hex to Decimal

De maneira resumida, valores binários, hexadecimais ou decimais são maneiras de representar valores. Em suma, o que muda é a base que o cálculo é feito. Entende-se que:

* Os **binários** matematicamente são representados por $$2^x$$.
* Os **hexadecimais** matematicamente são representados por $$16^x$$.
* Os **decimais** matematicamente são representados por $$10^x$$.

**Vamos a revisão** :thinking:**.**

O byte é um conjunto de 8 bits. Dessa forma, pode-se entender o byte como:

<figure><img src="../../.gitbook/assets/image (16).png" alt="" width="503"><figcaption><p>byte lenght</p></figcaption></figure>

Com um byte é possível representar os valores de 0 a 255 (um caracter no ASCII por exemplo):

<figure><img src="../../.gitbook/assets/image (12).png" alt="" width="563"><figcaption><p>binary to ASCII "i"</p></figcaption></figure>

Para representar os valores de binário para Hexadecimal, existe uma abstração chamada de nibble. O nibble representa 4 bits. Ou seja, um nibble pode possuir 16 valores (0-15) e a representação de binário para hexadecimal acaba ficando mais simples.

{% hint style="warning" %}
Por convensão, os valores 10, 11, 12, 13, 14 e 15 não existem em hexadecimal. Ao invés disso, são representados por A, B, C, D, E e F - respectivamente.
{% endhint %}

<figure><img src="../../.gitbook/assets/image (7).png" alt="" width="563"><figcaption><p>1 byte 2 nibbles</p></figcaption></figure>

Dessa forma, a conversão do valor decimal 106 pode ser representada da seguinte forma:

<figure><img src="../../.gitbook/assets/image (14).png" alt=""><figcaption><p>Binary to Hex</p></figcaption></figure>

Assim, segue uma tabela exemplificando a conversão dos valores:

| Decimal | Binary |  Hex |
| :-----: | :----: | :--: |
|    00   |  0000  | 0x00 |
|    01   |  0001  | 0x01 |
|    02   |  0010  | 0x02 |
|    03   |  0011  | 0x03 |
|    04   |  0100  | 0x04 |
|    05   |  0101  | 0x05 |
|    06   |  0110  | 0x06 |
|    07   |  0111  | 0x07 |
|    08   |  1000  | 0x08 |
|    09   |  1001  | 0x09 |
|    10   |  1010  | 0x0A |
|    11   |  1011  | 0x0B |
|    12   |  1100  | 0x0C |
|    13   |  1101  | 0x0D |
|    14   |  1110  | 0x0E |
|    15   |  1111  | 0x0F |
