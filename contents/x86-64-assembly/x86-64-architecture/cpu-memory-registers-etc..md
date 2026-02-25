# CPU, Memory, Registers etc.

## Information is Bits + Context

Toda informação em um sistema - incluindo arquivos em disco, programas armazenados na memória, dados do usuário armazenados na memória e dados transferidos através de uma rede - é representada como um conjunto de bits. A única coisa que distingue esses dados é o contexto no qual os visualizamos.&#x20;

Por exemplo, em contextos diferentes, a mesma sequência de bytes pode representar um número inteiro, um float, uma string de caracteres ou uma instrução de máquina.

## Source Code to Compiler to Executable

Dado esse panorâma, imaginemos um programa em C chamado `hello.c` . Esse código escrito em C deve ser traduzido por outros programas em uma sequência de instruções de máquina de baixo nível. Essas instruções são então agrupadas em uma forma chamada de **objeto executável** e armazenadas como um arquivo binário em disco. Esse proceso é chamado de **compilação:**

<figure><img src="../../../.gitbook/assets/image (15).png" alt="" width="563"><figcaption><p>Compiler process</p></figcaption></figure>

Com o arquivo binário executável, podemos executar o programa. Para isso acontecer, diversas interações acontecem entre a memoria principal (RAM), memoria secundária (HD), CPU, register etc. Voltemos ao exemplo do código `hello.c` mas agora em execução:

<figure><img src="../../../.gitbook/assets/image (18).png" alt="" width="563"><figcaption><p>Loading executable into main memory</p></figcaption></figure>

Para iniciar o processo de execução, o arquivo executável é carregado do disco e é alocado na memória principal. Dessa forma, com o programa em memória, a interação entre a CPU (e os outros componentes de hardware) é possível e começa o processo de execução:

<figure><img src="../../../.gitbook/assets/image (10).png" alt="" width="543"><figcaption><p>Program in memory execution</p></figcaption></figure>

Sob o ponto de vista arquitetural ([Instruction Set Architecture - ISA](https://en.wikipedia.org/wiki/Instruction_set_architecture)) é assim que funciona. Vamos a algumas explicações sobre os componentes:

### Main Memory (aka RAM)

A memória principal é um dispositivo de armazenamento temporário que pode conter tanto um programa quanto os dados que ele manipula enquanto o processador está executando o programa.

Logicamente, a memória é organizada como um array linear de bytes, cada um com seu próprio endereço único (índice do array) começando em zero. Em geral, cada uma das instruções de máquina que compõem um programa pode consistir em um número variável de bytes.

### BUS (aka Databus)

Os barramentos (Buses) são responsáveis por transportar dados (bits e bytes) entre os diferentes componentes do computador. Eles geralmente são projetados para transferir chunks de bytes de tamanho fixo conhecidos como words (uma word x84-64 são 2 bytes).

No contexto desse conteúdo, levamos em consideração a arquitetura x86-64, onde o 64bits é o tamanho do barramento.

### Processor (aka CPU)

A unidade central de processamento (CPU), ou simplesmente processador, é o que interpreta (ou executa) as instruções armazenadas na memória principal. O CPU é composto por diferentes componentes, incluindo registradores, PC (contador de programa) e a ALU (unidade lógica e aritmética).

A interação entre o CPU, PC, registradores e ALU permite que o processador execute as instruções do programa, realizando cálculos e manipulando os dados de acordo com as operações especificadas.

#### ALU

A ALU é a parte do CPU responsável por realizar operações lógicas (como AND, OR, NOT) e operações aritméticas (como adição, subtração, multiplicação) nos dados armazenados nos registradores. A ALU recebe os dados dos registradores, executa as operações solicitadas pelas instruções do programa e armazena o resultado de volta nos registradores.

#### PC (aka Program Counter)

É um tipo de registrador especial, presente no processador. Ele controla o fluxo de execução das instruções e é atualizado continuamente para apontar para a próxima instrução no programa. Ou seja, age como uma espécie de "ponteiro" para o próximo passo a ser realizado pelo processador.

Além disso, o PC também desempenha um papel importante em desvios condicionais e incondicionais. Em certas situações, uma instrução pode alterar o valor do PC, direcionando o fluxo de execução para uma localização de memória diferente. Isso permite a execução de instruções não lineares, como loops, desvios condicionais (como instruções if-else) e chamadas de sub-rotinas.

#### Registers

Registradores são pequenas áreas de armazenamento de dados localizadas dentro do processador. Eles são usados para armazenar informações temporárias a serem usadas durante a execução de um programa.

Na arquitetura x86-64bits existem vários registradores que desempenham funções específicas. Seguem os mais importantes pra esse conteúdo - Registradores de Uso Geral (General-Purpose Registers):

* RAX, RBX, RCX, RDX: Registradores de propósito geral que podem ser usados para armazenar dados temporários, valores intermediários e resultados de cálculos.
* RSI, RDI, RBP, RSP: Registradores adicionais de propósito geral usados para diferentes finalidades, como índices de memória (RSI e RDI), ponteiro de base de stack (RBP) e ponteiro de stack (RSP).
* R8 a R15: Registradores adicionais de propósito geral disponíveis em x86-64 para armazenar dados temporários e intermediários.

Segue abaixo a demonstração do tamanho de um registrador (x86-64) e a as consequências da sua evolução no tempo (mais sobre [aqui](https://www.youtube.com/watch?v=XvJzR3eb0b4)):

<figure><img src="../../../.gitbook/assets/image (17).png" alt="" width="563"><figcaption><p>Inter Register Evolution</p></figcaption></figure>

