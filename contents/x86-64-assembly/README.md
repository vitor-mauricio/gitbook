---
description: Meu progresso/resumos no curso de Assembly.
cover: ../../.gitbook/assets/getimg_ai_img-JyZ7l3kPLrqN4ox6HVwuD.png
coverY: -111
---

# x86-64 Assembly

## Motivação

Esse curso é o passo inical para um path de estudos de segurança em sistemas complexos (OS Internals, Kernel e aplicações nativas). Minha motivação basicamente foi a curiosidade e aprimorar o skill set de segurança.&#x20;

Apesar de ter estudado na faculdade, são conceitos que não vejo a muito tempo e vou precisar fazer uma grande revisão.

&#x20;                                             ![](https://media3.giphy.com/media/6v2UJRyFAsTXgvJrin/giphy.gif?cid=ecf05e475uupa48i9xxnfa519z7ur1l243wizs0gj663nwye\&ep=v1_gifs_search\&rid=giphy.gif\&ct=g)

## Introdução

A base do estudo será o curso de [x86-64 Assembly](https://p.ost2.fyi/courses/course-v1:OpenSecurityTraining2+Arch1001_x86-64_Asm+2021_v1/about) da [OpenSecurityTraning2](https://opensecuritytraining.info/Home.html). É um curso bastante complexo e denso e esse espaço vai ser utilizado para os resumos do que eu entendi do curso (e talvez algumas outras pesquisas extracurriculares :disappointed\_relieved:).

A intenção do estudo/curso é que ao final dele o aluno consiga entender como um programa em C é interpretado em Assembly - e conseguir entender o funcionamento das instruções de máquina geradas.

{% hint style="success" %}
Aprender a linguagem Assembly é fundamental para estudar segurança de aplicações, pois permite uma compreensão mais profunda do funcionamento interno dos sistemas, análise de código binário, desenvolvimento de exploits, análise de malware e engenharia reversa. Essas habilidades são essenciais para identificar vulnerabilidades de segurança, desenvolver contramedidas efetivas e proteger sistemas contra ameaças cibernéticas.
{% endhint %}

:bulb:_<mark style="background-color:blue;">A plataforma da OpenSecurityTraining foi um achado muuuito massa. Tem vários conteúdos legais e o learning path oferecido por eles é exatamente o que eu tava procurando.</mark>_

## Assembly

Assembly é uma linguagem de programação de baixo nível que representa as instruções executáveis ​​em um computador ou dispositivo. Ela fornece uma representação simbólica das operações de nível mais baixo do processador, permitindo um controle direto sobre o hardware.&#x20;

Ao contrário das linguagens de alto nível, o Assembly usa instruções simples e diretas que correspondem às instruções de máquina. A representação dos mnemónicos (instruções de máquina) são caracterizados por valores hexadecimais.

## Referências

Xeno Kovah. (2023). Architecture 1001: x86-64 Assembly. Recuperado de: [https://p.ost2.fyi/courses/course-v1:OpenSecurityTraining2+Arch1001\_x86-64\_Asm+2021\_v1/about](https://p.ost2.fyi/courses/course-v1:OpenSecurityTraining2+Arch1001_x86-64_Asm+2021_v1/about)

Bryan, R. E. & O’Hallaron, D.R. (2010). Computer Systems: A Programmer's Perspective (2nd Edition). Online: Prentice Hall.

## Conteúdos

<table data-card-size="large" data-column-title-hidden data-view="cards"><thead><tr><th></th><th data-hidden></th><th data-hidden></th><th data-hidden data-card-target data-type="content-ref"></th></tr></thead><tbody><tr><td>Decimal -> Binário -> Hexadecimal</td><td></td><td></td><td><a href="decimal-greater-than-binary-greater-than-hexadecimal.md">decimal-greater-than-binary-greater-than-hexadecimal.md</a></td></tr><tr><td>x86-64 Architecture</td><td></td><td></td><td><a href="x86-64-architecture/">x86-64-architecture</a></td></tr><tr><td>Machine Level</td><td></td><td></td><td><a href="machine-level/">machine-level</a></td></tr></tbody></table>
