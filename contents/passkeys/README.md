---
description: >-
  Eu não lembro as minhas senhas. Talvez o próximo passo para o futuro da
  autenticação virtual seja através do passowordless. Passkey é o bixo?
---

# Passkeys

## Introdução

Historicamente o mecanismo de uso de senhas é usado para comprovar que você é realmente você. Dito isso, esse processo de identificar para um sistema que você é realmente quem está por trás da tela é chamado de Autenticação. Contudo, as senhas por si só trazem uma fraqueza inerente ao processo - uma vez que você sabe a minha senha você pode se passar por mim.&#x20;

<figure><img src="https://media4.giphy.com/media/v1.Y2lkPTc5MGI3NjExN2p6ZGxkanFtNzZ4NjFhdDhhbnM4azAwa2x5dmp5bHpqYnJybXdpdCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/09bVX2WzBhZK8KwhqP/giphy.gif" alt=""><figcaption><p>ghipy.com</p></figcaption></figure>

Historicamente, também, foram adicionados outros fatores de autenticação para garantir a integridade desse processo (Tokens por SMS, verificações biométricas, validação em um dispositivo confiável etc.). Dessa forma, as tecnologias por trás do Passkeys tentam resolver o problema da senha com outros sabores (~~nada novo mas tudo diferente~~): criptografia, chaves e facilidade de uso.

### Senhas e suas fragilidades

Desde a Grécia Antiga as senhas eram utilizadas como mecanismo de segurança para garantir a autenticidade de uma informação e/ou conhecimento sobre algo. Na era digital, trouxemos essa herança. Porém, é importante ter a ciência das fragilidades que envolvem esse artifício:

1. **Fraqueza das senhas**: Muitas pessoas escolhem senhas fracas ou previsíveis, como datas de nascimento, nomes de familiares, ou sequências simples de caracteres. Isso torna mais fácil para os hackers adivinharem ou quebrarem a senha usando técnicas de força bruta ou ataques de dicionário.
2. **Reutilização de senhas**: Muitas pessoas têm o hábito de reutilizar a mesma senha em vários serviços. Se uma dessas senhas for comprometida, todos os serviços que ela utiliza estão em risco.
3. **Ataques de phishing**: Os ataques de phishing enganam os usuários para que revelem suas senhas através de e-mails ou sites falsos que se parecem com legítimos. Mesmo que a senha seja forte, se um usuário for enganado, sua conta ainda pode ser comprometida.
4. **Roubo de senhas**: As senhas podem ser roubadas de várias maneiras, incluindo violações de dados em grandes empresas ou serviços online, malware que rouba informações do dispositivo do usuário, ou até mesmo observação de alguém digitando sua senha.

Tá, e o passkeys?

### Então, Passkeys

Utilizando Passkeys você não precisa digitar nada e não precisa lembrar de nada (~~em teoria~~). A ideia aqui é não utilizar uma palavra, um conjunto de caracteres que você conhece ou guarda em algum lugar, mas sim uma dupla de chaves.&#x20;

Uma chave fica com você e outra chave fica com o serviço que você quer autenticar. Então, a integridade nesse processo vai ser garantida por um embaralhamento matemático que uma chave consegue fazer e por um _desembaralhamento_ matemático que a outra chave consegue fazer, também conhecido como :sparkles:CRIPTOGRAFIA :sparkles:.

Existem 2 conceitos macros que são importantes pra entender o Passkeys:

#### Criptografia Assimétrica

Criptografia assimétrica é um método de criptografia que utiliza pares de chaves distintas para cifrar e decifrar informações. Cada par de chaves consiste em uma chave pública e uma chave privada. Esse [vídeo](https://www.youtube.com/watch?v=AQDCe585Lnc) é legal e bem simples pra entender.

<figure><img src="https://nakamoto.com/content/images/2020/11/asymmetric-encryption-optimized.gif" alt="" width="375"><figcaption><p>nakamoto.com</p></figcaption></figure>

#### Únicas por serviço por dispositivo (e por usuário)

Nessa dinâmica de criação dos pares de chaves, existirá um par de chaves para cada dispositivo que efetuar o cadastro de uma Passkey para aquele serviço específico. Ou seja, de forma simples, para cada usuário e dispositivo que for efetuar o login em um serviço (por exemplo, o Google), será utilizado uma chave privada única previamente cadastrada naquele dispositivo.\
\
Além disso, a chave privada do usuário que existe em cada dispositivo será guardada em um "cofre seguro" dentro daquele dispositivo. Esse cofre é mantido pelo sistema operacional (ou em alguns casos por um aplicativo de cofre de senhas) do dispositivo, que oferece outros mecanismos de segurança para abertura do cofre, como por exemplo: checagem de biometrica, prompt de PINs, entre outros métodos.

***

Eu juro que te explico o resto na próxima [página](funcionamento.md).

<figure><img src="https://media2.giphy.com/media/v1.Y2lkPTc5MGI3NjExaXVwaDhuOWJ6OXJ5emFiaXoxc2RiYmp6OXc5NnNuODA1a3NlNHg3cCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/HDh0aBxvC9atgwN0nK/giphy.gif" alt="" width="375"><figcaption><p>giphy.com</p></figcaption></figure>
