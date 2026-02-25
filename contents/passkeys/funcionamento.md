# Funcionamento

## Configuração e uso

Sob o ponto de vista do usuário final, será necessário configurar a criação dos pares de chave para  utilizar o mundo de autenticações sem senha. Uma vez criados os pares de chaves, será simplesmente usar o método de autenticação por Passkeys.

A criação, normalmente, é feita de maneira bem simples e _user-friendly._ E o uso é bem mais simples ainda.

Outro ponto muito importante de lembrar é que para utilizar as Passkeys o serviço que você quer fazer o login precisa implementar o uso do protocolo. Uma das grandes empresas que apostou nesse novo formato foi a Google.

A própria Google fornece um [tutorial](https://support.google.com/accounts/answer/13548313?hl=pt-BR#zippy=%2Ccriar-uma-chave-de-acesso) e uma [página](https://www.google.com/account/about/passkeys/) explicando o funcionamento.

<figure><img src="https://storage.googleapis.com/gweb-uniblog-publish-prod/original_images/keyword-blog_passkeys_hero-animated.gif" alt=""><figcaption><p><a href="https://blog.google/technology/safety-security/the-beginning-of-the-end-of-the-password/">https://blog.google/technology/safety-security/the-beginning-of-the-end-of-the-password/</a></p></figcaption></figure>

Além disso, existe um site bem legal que fornece uma implementação simples e uma forma de Demo pra apresentar o uso do Passkeys: [passkeys.io](https://www.passkeys.io/)

## Detalhes técnicos

<figure><img src="https://media1.giphy.com/media/v1.Y2lkPTc5MGI3NjExemliOWxicnZ5cnlzdnA5dWhxNXA4bHJrNW5sajF4cGlmeWp3ZnkzeCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/xlVvWxyeUJsDcHPMsO/giphy.gif" alt="" width="375"><figcaption><p>giphy.com</p></figcaption></figure>

A FIDO (Fast IDentity Online) Alliance publicou um [padrão](https://www.w3.org/TR/webauthn-2/) na W3C que define como o protocolo _WebAuthN_ deve funcionar. Esse protocolo é a base para o funcionamento das Passkeys.

Dado esse contexto, é importante identificar os atores que participam dos fluxos definidos no protocolo:

* **User**: o usuário final.
* **Client**: a aplicação (mobile app, web app, etc.)
* **Authenticator**: entidade que lida com as chaves criptográficas (sistema operacional, cofre de senhas, etc.)
* **Relying** **Party**: o provedor de serviço (Google, Amazon, Paypal, etc.)

O protocolo define diversas coisas, mas acho legal entender principalmente os dois principais fluxos. Que seriam:

### Registration Ceremony

Existem duas formas do início do fluxo de registro de Passkeys:

* O usuário já possui uma conta no serviço e utiliza de senha e/ou outros métodos _clássicos_ de login.
  * O usuário precisa se logar utilizando os métodos clássicos e deliberadamente ir até a opção de criação de Passkeys.
* O usuário não possui uma conta no serviço e deseja criar uma Passkey como metódo de login padrão.
  * A criação de usuário e Passkey acontece de forma simultânea no momento de criação de conta no serviço.

Para os dois cenários de início do fluxo a cerimônia de registro da Passkey se mantém abstrata e transparente (~~muda só o  botão e alguma lógica no back-end~~).

<figure><img src="https://miro.medium.com/v2/resize:fit:4800/format:webp/1*-ABKilniRLzVuITFECp14w.png" alt=""><figcaption><p><a href="https://medium.com/@heritage.tech/passwordless-authentication-with-passkey-how-it-works-and-why-it-matters-part-1-dcae2a004988">https://medium.com/@heritage.tech/passwordless-authentication-with-passkey-how-it-works-and-why-it-matters-part-1-dcae2a004988</a></p></figcaption></figure>

1. O usuário inicia o fluxo de registro de uma nova Passkey;
2. A aplicação envia uma requisição HTTP para o servidor do serviço;
3. O servidor do serviço gera, salva e envia um código de desafio (uma string aleatória) e envia outros metadados;
4. A aplicação solicita a criação do par de chaves para o Authenticator;
5. O Authenticator solicita a identificação para o usuário (PIN, FaceID, Fingerprint, etc.);
6. O Authenticator cria o par de chaves e envia para aplicação um objeto que contém: o código de desafio, a chave pública e um objeto de atestação (assinado com a chave privada);
7. A aplicação envia o objeto para o servidor do serviço;
8. O servidor do serviço verifica o conteúdo do objeto, checa a assinatura e salva a chave pública do usuário;
9. O servidor responde para a aplicação que a criação da Passkey foi bem sucedida.

### Authentication Ceremony

Uma vez que o processo de registro dos pares de chaves foram gerados, o usuário está apto a executar o fluxo de autenticação utilizando uma Passkey:

<figure><img src="https://miro.medium.com/v2/resize:fit:4800/format:webp/1*1LO_oGeEIiD5-yEU4MN4TA.png" alt=""><figcaption><p><a href="https://medium.com/@heritage.tech/passwordless-authentication-with-passkey-how-it-works-and-why-it-matters-part-1-dcae2a004988">https://medium.com/@heritage.tech/passwordless-authentication-with-passkey-how-it-works-and-why-it-matters-part-1-dcae2a004988</a></p></figcaption></figure>

1. O usuário inicia o fluxo de autenticação
2. A aplicação faz uma requisição para o servidor do serviço
3. O servidor do serviço gera, salva e envia um código de desafio e envia outros metadados;
4. A aplicação solicita para o Authenticator que o código de desafio seja assinado, utilizando a chave privada;
5. O Authenticator solicita a identificação para o usuário (PIN, FaceID, Fingerprint, etc.);
6. O Authenticator assina o desafio e envia para aplicação um objeto que contém: o código de desafio assinado, detalhes da autenticação e outros metadados;
7. A aplicação envia o objeto para o servidor do serviço;
8. O servidor do serviço verifica o conteúdo do objeto, checa se a assinatura está correta;
9. O servidor do serviço avisa para a aplicação que o login foi bem sucedido.

***

Esse é o Passkey (AKA WebAuthN). Ele garante um protocolo de autenticação verdadeiramente sem senhas (passwordless). Além disso, o serviço lida com a chave pública do usuário. Isso quer dizer que se houver um vazamento dessa chave pública, o atacante não pode fazer muita coisa.

Mas, como tudo na vida, não garante 100% de segurança. Nenhum sistema é 100% seguro.

Isso posto, chegamos ao fim e as considerações de [segurança](seguranca.md). (~~tá acabando, juro~~)
