# Operating System

## OS as Security and Abstraction

Quando rodamos o código em um computador ou em um celular, é esperado que ele possua um Sistema Operacional. Apesar de, nas instruções de máquina, termos a capacidade de manipulação e controle granular dos componentes de um computador, ainda existe uma limitação. O Sistema Operacional (aka Kernel) é quem fornece a abstração e proteção para os acessos reais (físicos) dos componentes.

Entende-se então que o Sistema Operacional tem 2 grandes objetivos:

* Segurança - proteger o Hardware de usos indevidos por parte de programas/aplicativos;
* Abstração - fornecer mecanismos simples e uniformes para manipular dispositivos de hardware de baixo nível.

<figure><img src="../../../.gitbook/assets/image (13).png" alt="" width="430"><figcaption><p>Application programs are located at the top of the OS</p></figcaption></figure>

Dito isso, o OS fornece a abstração dos componentes de hardware da seguinte forma: Processos, Memória Virtual e Arquivos. Demonstração:<br>

<figure><img src="../../../.gitbook/assets/image (8).png" alt="" width="369"><figcaption><p>Process -> Virtual Memory -> Files</p></figcaption></figure>

### Processes

Um processo é a abstração do sistema operacional para um programa em execução. Múltiplos processos podem ser executados simultaneamente no mesmo sistema, e cada processo parece ter uso exclusivo do hardware. Por "simultaneamente", é entendido que as instruções de um processo são intercaladas com as instruções de outro processo.&#x20;

Mais detalhes [aqui](https://www.youtube.com/watch?v=DKmBRl8j3Ak).

#### Threads

Embora normalmente pensemos em um processo como tendo um único fluxo de controle, nos sistemas modernos um processo pode realmente consistir em várias unidades de execução, chamadas de **threads**, cada uma executando no contexto do processo e compartilhando o mesmo código e dados globais.

A utilização de multi-threading é também uma maneira de fazer com que os programas sejam executados mais rapidamente quando múltiplos processadores estão disponíveis.&#x20;

Mais detalhes [aqui](https://www.youtube.com/watch?v=7ENFeb-J75k).

### Virtual Memory

A memória virtual é uma abstração que fornece a cada processo a **ilusão** de que ele tem uso exclusivo da memória principal. Cada processo possui a mesma visão uniforme da memória, conhecida como seu espaço de endereçamento virtual.

A virtualização da memória é um processo interessante e por vezes complexo, vamos tratar mais detalhes na próxima discussão - [Stack x Heap](stack-x-heap.md).

### Files

Um arquivo é uma sequência de bytes, nada mais e nada menos. Todo dispositivo de entrada/saída, incluindo discos, teclados, monitores e até mesmo redes, é modelado pelo OS como um arquivo. Entende-se então que toda entrada e saída no sistema é realizada por meio da leitura e escrita de arquivos, utilizando um pequeno conjunto de chamadas de sistemas.
