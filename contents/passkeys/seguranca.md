---
description: Cara, isso é seguro?
---

# Segurança

## Benefícios

* Não existem senhas para serem roubadas, copiadas, reutilizadas;
* Se houver um vazamento de dados, o que vai ser roubado será a chave pública;
* O bem mais precioso fica com você: sua chave privada;
* O protocolo garante, por padrão, o armazenamento seguro da sua chave privada; (~~e você não precisa fazer nada por isso~~)
* Segurança + UX (Experiência do usuário): você estará mais seguro e não vai ser difícil fazer isso.

## Mas... Considerações

<figure><img src="https://media3.giphy.com/media/v1.Y2lkPTc5MGI3NjExZGwwZDRlZzBiZGlhNzM4b2t2aDBnMTFjMjJ3NGVmMHY0YnV5ejN6YSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/da75JuW2HHuBNqOHHE/giphy.gif" alt="" width="375"><figcaption><p>giphy.com</p></figcaption></figure>

Claro, vão existir algumas ponderações quanto ao Passkeys. Ele não vai deixar a internet segura de um dia pro outro. E isso é esperado (~~é sobre isso e tá tudo bem~~). Mesmo na concepção do protocolo são levantados os possíveis problemas. Vamos lá:

### E o token de acesso

O uso de passkeys irá garantir uma forma de comprovar que você é o dono da conta pela extinção do método clássico: senhas. Mas ainda existem os outros protocolos (~~que ainda sobrevivem~~), para garantir a parte de autorização e acesso a um recurso. Por exemplo o [OAuth e OIDC](../oauth-2.0/).

### A sua credencial é sua responsabilidade

A sua chave privada está sob sua responsabilidade. Apesar do sistema operacional e/ou cofre de senhas possua seus mecanismos de segurança, ele também vai possuir falhas. Então é importante que você mantenha seu dispositivo seguro, ou seja, sempre faça as atualizações de segurança e fique longe de malwares.

### Implementação segura

O protocolo garante alguns padrões a serem seguidos, ou seja, é importante que ele seja seguido porque podem existir benefícios de segurança.

#### Método de autenticação clássico + Passkeys

As pessoas não vão parar de usar senhas de uma dia pro outro e o serviço precisa se adequar a esse paradigma.&#x20;

Além disso, se o usuário perder ou acontecer algo com o seu dispositivo, a chave privada também será perdida. Para isso, o serviço precisa deixar habilitado opções de "emergencia" (~~senhas e recuperação de conta)~~ para que usuário possa logar na conta e possivelmente cadastrar uma nova passkey. Isso abre portas para que a conta desse usuário possa sofrer dos mesmos problemas que ele já sofria: senhas.&#x20;

Não existe um jeito certo de lidar com esse problema. Isso vai depender muito do contexto da aplicação e do apetite de risco que aquele app/serviço se propõe a aceitar.

#### Parâmetro challenge&#x20;

Esse parâmetro é gerado, salvado (pelo servidor do serviço) e enviado em todas as cerimônias no protocolo. Ele, basicamente, é o objeto que atestará que quem fez a primeira requisição é realmente quem concluiu a última etapa.

É extremamente importante que o servidor faça a checagem correta desse parâmetro nas requisições e que ele seja gerado verdadeiramente de forma randômica (ou pelo menos com uma entropia suficiente), para não acontecerem ataques do tipo [replay attack](https://www.kaspersky.com/resource-center/definitions/replay-attack).

#### Man-in-the-middle na cerimônia de registro

Existe a possibilidade, mesmo que remota, de um atacante conseguir injetar a chave pública dele no meio da cerimônia de registro. Ou seja, o atacante iria estar usando o par de chaves dele na sua conta. Ele seria o dono da sua conta.&#x20;

Esse tipo de ataque é bem complicado de ser executado mas é previsto no [protocolo](https://www.w3.org/TR/webauthn-2/#sctn-attestation-limitations).

Não existe uma "bala de prata" pra resolver esse tipo de problema (~~no mundo com senhas isso também pode acontecer~~). Talvez a melhor abordagem para esse problema é garantir a integridade e segurança do seu dispositivo.

***

De forma resumida, o protocolo é relativamente novo. Mas, além disso, as implementações são novas. Ou seja, com certeza vão existir novos ataques e novas melhorias para o processo do WebAuthN e Passkeys.

Dá uma lida lá no protocolo: [https://www.w3.org/TR/webauthn-2/#sctn-security-considerations](https://www.w3.org/TR/webauthn-2/#sctn-security-considerations)

E, tem uns links legais:

* [https://slashid.com/blog/passkeys-security-implementation](https://slashid.com/blog/passkeys-security-implementation/)
* [https://medium.com/@heritage.tech/passwordless-authentication-with-passkey-how-it-works-and-why-it-matters-part-1-dcae2a004988#e273](https://medium.com/@heritage.tech/passwordless-authentication-with-passkey-how-it-works-and-why-it-matters-part-1-dcae2a004988#e273)
