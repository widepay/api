---
title: Documentação API

language_tabs:
  - shell : cURL
  - php : PHP

includes:
  - bibliotecas
  - recebimentos
  - checkouts
  - botoes
  - modulos
  - sistemas
  - exemplos

search: true
---

# Introdução

Seja bem-vindo a documentação do Wide Pay! Aqui você encontrará as informações necessárias para fazer a integração com nossa infraestrutura.

Antes de iniciar, crie sua conta no Wide Pay.

Com a API do Wide Pay é possível utilizar qualquer recurso disponível em sua conta, como gerar transações, carnês, assinaturas, receber notificações toda vez que algum status sofrer alteração.

Também é possivel utilizar os recursos de pagamento de contas, recargas de celular, transferências bancárias, transferências entre contas Wide Pay e para Cartão Wide Pay.

### Carteira e token

Para utilização da API é necessário ter o ID da carteira e o token de autenticação.

O conceito de carteiras do Wide Pay serve para que você possa separar os recebimentos, pagamentos e transferências. Ex. no caso de você ter duas lojas. (Colocar um exemplo prático aqui)

Por padrão quando sua conta Wide Pay é feita, automaticamente é criada uma carteira padrão, essa carteira não pode ser usada em ambiente de testes nem em modo gateway.

Para ter um gerenciamento completo de suas carteiras como criar, editar, obter ID e token, logue em sua conta Wide Pay, acesse o menu superior "Configurações", depois clique em "Carteiras e integrações".

### Modo gateway

Caso você não queira que o Wide Pay faça a intermediação dos seus recebimentos, tanto para boletos e cartão de crédito, é possível utilizar o "Modo gateway". Ao adicionar uma carteira, você configura os parametros do banco para recebimento via boleto e da adquirente para recebimento via cartão de crédito.

Nesse modo não há "saldo" na carteira, uma vez que o Wide Pay só servirá como gateway. Desse modo os menus de pagamentos, transferências e extratos são desativados.

### Ambiente de testes

A configuração do ambiente de teste é feita na hora que você adiciona a carteira do Wide Pay.

Após feito os testes de integração você poderá migrar a carteira para o ambiente de produção. Lembramos que uma carteira já em produção não pode ser migrada para o ambiente de testes.

### Endpoint e respostas

Todas as requisições são feitas no endpoint:

`https://api.widepay.com`

Todas as respostas da API por padrão são em JSON, mas podendo ser em XML passando no header:

`Accept: application/xml`

### Dúvidas?

Surgiu alguma dúvida ou sugestão para tornar nossa documentação melhor? Mande um e-mail para integracao@widepay.com e iremos te ajudar!