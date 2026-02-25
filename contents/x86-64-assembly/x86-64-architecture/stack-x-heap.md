# Stack x Heap

## Virtual Memory is central, powerfull and dangerous

A memória virtual é uma interação elegante entre exceções de hardware, tradução de endereços em hardware, memória principal, arquivos em disco e software do kernel, que fornece a cada processo um espaço de endereçamento amplo, uniforme e privado.

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Process virtual address<br>space.</p></figcaption></figure>

Uma das consequências (~~_da abstração_~~) da memória virtual é a criação da Heap e Stack - e enteder a diferença/funcionamento vai ser importante para o assembly.

## Stack

A **stack** é uma região de memória usada para **armazenar registros de ativação** (_activation records_) ou **stack frames**, representando o contexto de execução de cada chamada de função.

Ela segue a disciplina **LIFO (Last-In, First-Out)**, garantindo previsibilidade total em alocação e liberação:

* entrada em uma função → _push_ de um frame
* _return_ de uma função → _pop_ do frame correspondente

Essa estrutura é definida pela ABI [(_Application Binary Interface_)](https://learn.microsoft.com/pt-br/cpp/build/x64-software-conventions?view=msvc-170#stack-usage) de cada plataforma e seguida pelo código gerado pelo compilador.

## Heap

A **heap** é uma região de memória usada para **alocação dinâmica**, ou seja, para blocos cujo tamanho e tempo de vida são determinados em **tempo de execução**, não em tempo de compilação.

A heap é gerenciada por um **alocador dinâmico** (ex.: _glibc malloc_, _jemalloc_, _tcmalloc_) ou por um **runtime com garbage collector** (Java, Go, .NET, Python).



