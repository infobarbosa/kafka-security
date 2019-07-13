# Kafka Security | Base Box

Este projeto tem como objetivo exercitar as features de segurança do [Kafka](https://kafka.apache.org/).<br/>
Normalmente são esperados três níveis de segurança: [**encriptação**](kafka-ssl/instructions/kafka-ssl-encryption.md), [**autenticação**](kafka-kerberos/instructions/kafka-sasl-authentication.md) e **autorização**.<br/>
Uma instalação inicial do Kafka não habilita qualquer nível de segurança. Portanto, é de responsabilidade do administrador do sistema habilitar tais recursos.<br/>
Não é propósito deste laboratório substituir as documentações disponíveis sobre o tema. As mesmas são claras e objetivas e podem ser encontradas [aqui](https://kafka.apache.org/documentation/#security) e [aqui](https://docs.confluent.io/current/security.html).<br/>
Com o laboratório pretendo simular um cenário onde há basicamente três atores (ou times):

- Desenvolvedor: profissional responsável pelo desenvolvimento da aplicação cliente do Kafka;
- Administrador: profissional responsável pela administração do ambiente Kafka;
- Segurança: profissional responsável pelo manejo de credenciais e permissões de segurança da empresa.

Para tanto, o conteúdo do laboratório possui algumas imagens Linux que sobem via [Vagrant](https://github.com/infobarbosa/kafka-security-base-box/blob/master/Vagrantfile):
- Zookeeper;
- Kafka;
- Aplicação cliente: imagem Linux com duas aplicações cliente simples, uma produtora e outra consumidora;
- Autoridade Certificadora: emite certificados publicos e privados;
- Kerberos: emite credenciais de usuarios para autenticacao.

By the way, se não estiver familiarizado com o Vagrant, sugiro começar por [aqui](https://www.vagrantup.com/intro/index.html).<br/>
No [primeiro artigo](kafka-ssl/instructions/kafka-ssl-encryption.md) pretendo inicialmente trabalhar a encriptação de dados via SSL.<br/>
Os demais artigos ainda serão escritos assim como a montagem dos laboratórios. Be patient! Em breve estarão disponíveis.

Para iniciar os boxes basta digitar:
```
vagrant up
```

A montagem dos boxes leva entre 15 e 30 minutos, a depender da máquina que você tem. Vá tomar um café!

> **Atencao!**
> Os diretorios [_kafka-ssl_](kafka-ssl/) e [_kafka-kerberos_](kafka-kerberos/) sao independentes, cada um com o seu proprio Vagrantfile.</br>
> Fiz isso porque talvez voce queira exercitar cada tema separadamente.
> Ao optar por fazer o lab de [Kerberos](kafka-kerberos/), por exemplo, entao o setup SSL eh feito automaticamente pelo script Vagrant. :)</br>
> Isso nao te impede de seguir do lab [SSL](kafka-ssl/) para o de Kerberos. Apenas tenha em mente de que neste ultimo voce tera que subir apenas o Kerberos.
```
vagrant up kerberos
```
> Recomendo que ao final do lab SSL voce simplesmente o destrua e inicie um ambiente novo com _kafka-kerberos_.</br>
> Para destruir o ambiente no Vagrant eh muito simples:
```
cd kafka-ssl
vagrant destroy -f
```

## Encriptação

As instruções para encriptação utilizando este lab podem ser encontradas [aqui](kafka-ssl/instructions/kafka-ssl-encryption.md).

## Autenticação

Esse lab explora dois tipos de autenticacao: o [primeiro](kafka-ssl/instructions/kafka-ssl-authentication.md) baseado em TLS e o [segundo](kafka-kerberos/instructions/kafka-sasl-authentication.md) baseado em SASL e Kerberos.

## Autorização

Comming soon
