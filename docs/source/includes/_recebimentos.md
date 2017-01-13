# Recebimentos

...

### Marketplace

...

## Gerando Transações

...

```shell
curl \
    -X POST 'https://www.widepay.com/api/recebimentos/transacoes/adicionar' \
        -H 'Accept: application/json' \
    -u '1001-2:a436691a169d06e56d4abc8e821c212b' \
    -d 'tipo=Boleto' \
    -d 'cliente=Claudio' \
    -d 'itens[0][descricao]=Mensalidade' \
    -d 'itens[0][valor]=10.50'
```

```php
<?php

require_once('WidePay.php');

$wp = new WidePay('1001-2','a436691a169d06e56d4abc8e821c212b');

$dados = $wp->api('recebimentos/transacoes/adicionar', array(
	'tipo' => 'Boleto',
	'vencimento' => '2016-03-30',
	'pessoa' => 'Física',
	'cliente' => 'Claudio Almeida',
	'itens' => array(
		array(
			'descricao' => 'Mensalidade de Internet',
			'valor' => 30
		)
	)
));
```

> Retorno JSON da requisição:

```json
{
	"success": true,
	"id": "39147EA89103C909",
	"link": "https://www.widepay.com/39147EA89103C909",
	"boleto": {
		"numero": "4842590",
		"codigo": "03399.71095 28800.000482 42590.701027 6 00000000001050",
		"configuracoes": {
			"banco": "033",
			"agencia": "4582",
			"codigo": "7109288",
			"carteira": "102",
			"empresa": "Almeida Desenvolvimento de Softwares Ltda - ME",
			"cnpj": "12.655.911/0001-36"
		}
	}
}
```



### Transações / Consultar

> Consulta as transacoes

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

###### URL

widepay.com/api/transacoes/consultar

###### PARAMETROS

| Campos | Obrigatório | Tipo   | Observações       |
| ------ | ----------- | ------ | ----------------- |
| id     | Não         | String | Pode ser múltiplo |

###### RETORNO

```php
Array(3) {
    ['success'] = Boolean(1) true
    ['total'] = Integer(1) 2
    ['transacoes'] => Array(2) {
        ['0'] => Array(16) {
            ['id'] = String(16) 2b1197bb86714ab1
            ['tipo'] = String(6) Boleto
            ['cliente'] => Array(13) {
                ['pessoa'] = String(7) Física
                ['nome'] = String(14) Lays Pontarolo
                ['cpf'] = NULL(0) null
                ['cnpj'] = NULL(0) null
                ['email'] = NULL(0) null
                ['celular'] = NULL(0) null
                ['rua'] = NULL(0) null
                ['numero'] = NULL(0) null
                ['complemento'] = NULL(0) null
                ['bairro'] = NULL(0) null
                ['cep'] = NULL(0) null
                ['cidade'] = NULL(0) null
                ['estado'] = NULL(0) null
            }
            ['itens'] => Array(1) {
                ['0'] => Array(4) {
                    ['descricao'] = String(7) Produto
                    ['valor'] = Integer(2) 50
                    ['quantidade'] = String(1) 1
                    ['desconto'] = Integer(1) 0
                }
            }
            ['desconto'] = NULL(0) null
            ['valor'] = String(5) 50.00
            ['identificador'] = NULL(0) null
            ['notificacao'] = NULL(0) null
            ['redirecionamento'] = NULL(0) null
            ['vencimento'] = String(10) 2015-10-10
            ['criacao'] = String(19) 2015-08-19 15:40:09
            ['status'] = String(10) Compensada
            ['cancelamento'] = NULL(0) null
            ['pagamento'] => Array(4) {
                ['data'] = String(10) 2015-08-10
                ['valor'] = Integer(2) 50
                ['tarifa'] = Double/Float(4) 1.95
                ['disponivel'] => Array(2) {
                    ['data'] = String(10) 2015-08-13
                    ['valor'] = Double/Float(5) 48.05
                }
            }
            ['historico'] => Array(2) {
                ['0'] => Array(2) {
                    ['status'] = String(20) Aguardando pagamento
                    ['data'] = String(19) 2015-08-19 15:40:09
                }
                ['1'] => Array(2) {
                    ['status'] = String(10) Compensada
                    ['data'] = String(19) 2015-08-19 15:56:14
                }
            }
            ['boleto'] => Array(6) {
                ['beneficiario'] = String(7) Almeida
                ['banco'] = String(3) 033
                ['agencia'] = String(4) 4582
                ['codigo'] = String(7) 7109288
                ['carteira'] = String(3) 102
                ['numero'] = String(3) 262
            }
        }
        ['1'] => Array(16) {
            ['id'] = String(16) 2b797d2775b357a3
            ['tipo'] = String(7) Cartão
            ['cliente'] => Array(13) {
                ['pessoa'] = String(7) Física
                ['nome'] = String(14) Lays Pontarolo
                ['cpf'] = NULL(0) null
                ['cnpj'] = NULL(0) null
                ['email'] = NULL(0) null
                ['celular'] = NULL(0) null
                ['rua'] = NULL(0) null
                ['numero'] = NULL(0) null
                ['complemento'] = NULL(0) null
                ['bairro'] = NULL(0) null
                ['cep'] = NULL(0) null
                ['cidade'] = NULL(0) null
                ['estado'] = NULL(0) null
            }
            ['itens'] => Array(1) {
                ['0'] => Array(4) {
                    ['descricao'] = String(7) Produto
                    ['valor'] = Integer(2) 50
                    ['quantidade'] = String(1) 1
                    ['desconto'] = Integer(1) 0
                }
            }
            ['desconto'] = NULL(0) null
            ['valor'] = String(5) 50.00
            ['identificador'] = NULL(0) null
            ['notificacao'] = NULL(0) null
            ['redirecionamento'] = NULL(0) null
            ['vencimento'] = NULL(0) null
            ['criacao'] = String(19) 2015-08-19 15:42:03
            ['status'] = String(14) Em compensação
            ['cancelamento'] = NULL(0) null
            ['pagamento'] => Array(6) {
                ['data'] = String(19) 2015-08-19 15:51:48
                ['valor'] = String(5) 50.00
                ['parcelas'] = Integer(1) 1
                ['tarifa'] => Array(2) {
                    ['recebimento'] = Double/Float(3) 2.5
                    ['parcelamento'] = Integer(1) 0
                }
                ['disponivel'] => Array(2) {
                    ['data'] = String(10) 2015-09-18
                    ['valor'] = Double/Float(4) 47.5
                }
                ['cartao'] => Array(2) {
                    ['bandeira'] = String(4) Visa
                    ['final'] = Integer(4) 5466
                }
            }
            ['historico'] => Array(2) {
                ['0'] => Array(2) {
                    ['status'] = String(20) Aguardando pagamento
                    ['data'] = String(19) 2015-08-19 15:42:03
                }
                ['1'] => Array(2) {
                    ['status'] = String(14) Em compensação
                    ['data'] = String(19) 2015-08-19 15:51:48
                }
            }
            ['boleto'] = NULL(0) null
        }
    }
}
```


---------------------------------------------------------------


### Transações / Gerar

> Gera transação

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

###### URL

widepay.com/api/transacoes/gerar

###### PARAMETROS

| Campos               | Obrigatório | Tipo     | Observações                                                           |
| -------------------- | ----------- | -------- | --------------------------------------------------------------------- |
| tipo                 | Sim         | Definido | Boleto / Cartão                                                       |
| desconto             | Não         | Decimal  | -                                                                     |
| identificador        | Não         | String   | Tamanho máximo: 30                                                    |
| notificacao          | Não         | URL      | -                                                                     |
| redirecionamento     | Não         | URL      | Somente para tipo: Cartão                                             |
| vencimento           | Sim         | Data     | Somente para tipo: Boleto                                             |
| cliente              | Sim         | Array    | -                                                                     |
| cliente[pessoa]      | Sim         | Definido | Física / Jurídica                                                     |
| cliente[nome]        | Sim         | String   | Tamanho máximo: 100                                                   |
| cliente[cpf]         | Não         | CPF      | Somente para pessoa: Física                                           |
| cliente[cnpj]        | Não         | CNPJ     | Somente para pessoa: Jurídica                                         |
| cliente[email]       | Não         | E-mail   | -                                                                     |
| cliente[celular]     | Não         | Telefone | -                                                                     |
| cliente[rua]         | Não         | String   | Tamanho máximo: 100                                                   |
| cliente[numero]      | Não         | String   | Tamanho máximo: 10                                                    |
| cliente[complemento] | Não         | String   | Tamanho máximo: 100                                                   |
| cliente[bairro]      | Não         | String   | Tamanho máximo: 100                                                   |
| cliente[cep]         | Não         | CEP      | -                                                                     |
| cliente[estado]      | Não         | String   | Tamanho: 2                                                            |
| cliente[cidade]      | Não         | String   | Tamanho máximo: 100                                                   |
| itens                | Sim         | Array    | Múltiplo                                                              |
| itens[descricao]     | Sim         | String   | Tamanho máximo: 255                                                   |
| itens[valor]         | Sim         | Decimal  | -                                                                     |
| itens[quantidade]    | Não         | Numérico | Valor mínimo: 1, Valor máximo: 99999                                  |
| itens[desconto]      | Não         | Decimal  | -                                                                     |
| instrucoes           | Não         | Array    | Múltiplo até 5 itens, Tamanho máximo: 1024, Somente para tipo: Boleto |
| enviar               | Não         | Definido | E-mail / SMS (Pode ser um ou mais)                                    |

###### RETORNO (TIPO BOLETO)

```php
Array(4) {
    ['success'] = Boolean(1) true
    ['id'] = String(16) 2b1197bb86714ab1
    ['link'] = String(44) https://widepay.com/2b1197bb86714ab1
    ['boleto'] => Array(6) {
        ['beneficiario'] = String(7) Almeida Desenvolvimento de Softwares
        ['banco'] = String(3) 033
        ['agencia'] = String(4) 4582
        ['codigo'] = String(7) 7109288
        ['carteira'] = String(3) 102
        ['numero'] = String(3) 262
    }
}
```

###### RETORNO (TIPO CARTÃO)

```php
Array(3) {
    ['success'] = Boolean(1) true
    ['id'] = String(16) 2b797d2775b357a3
    ['link'] = String(44) https://widepay.com/2b797d2775b357a3
}
```


---------------------------------------------------------------


### Transações / Vender

> Processo de venda para aplicativo mobile

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

`É obrigatória uma conexão HTTPS`

###### URL

widepay.com/api/transacoes/vender

###### PARAMETROS

| Campos        | Obrigatório | Tipo          | Observações                                                     |
| ------------- | ----------- | ------------- | --------------------------------------------------------------- |
| identificador | Não         | String        | Tamanho máximo: 30                                              |
| descricao     | Sim         | String        | Tamanho máximo: 255                                             |
| valor         | Sim         | Decimal       | Valor mínimo: 1                                                 |
| parcelas      | Sim         | Numérico      | Valor mínimo: 1, Valor máximo: 12                               |
| parcelamento  | Sim         | Definido      | Vendedor / Comprador (Somente se parcelas for maior que 1)      |
| numero        | Sim         | Numérico      | Tamanho mínimo: 14, Tamanho máximo: 19                          |
| validade      | Sim         | Data (AAAAMM) | Valor mínimo ano e mês atual, Valor máximo ano + 10 e mês atual |
| codigo        | Sim         | Numérico      | Tamanho mínimo: 3, Tamanho máximo: 4                            |

###### RETORNO

```php
Array(3) {
    ['success'] = Boolean(1) true
    ['id'] = String(16) 2b797d2775b357a3
    ['status'] = String(14) Em compensação
}
```


---------------------------------------------------------------


### Transações / Parcelamento

> Retorna cálculo de parcelamento sobre os valores

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

###### URL

widepay.com/api/transacoes/parcelamento

###### PARAMETROS

| Campos | Obrigatório | Tipo    | Observações |
| ------ | ----------- | ------- | ----------- |
| valor  | Sim         | Decimal | -           |

###### RETORNO

```php
Array(2) {
    ['success'] = Boolean(1) true
    ['parcelamento'] => Array(3) {
        ['0'] => Array(3) {
            ['parcela'] = Integer(1) 1
            ['valor'] = Double/Float(2) 20
            ['total'] = Double/Float(2) 20
        }
        ['1'] => Array(3) {
            ['parcela'] = Integer(1) 2
            ['valor'] = Double/Float(5) 10.23
            ['total'] = Double/Float(5) 20.46
        }
        ['2'] => Array(3) {
            ['parcela'] = Integer(1) 3
            ['valor'] = Double/Float(4) 6.87
            ['total'] = Double/Float(5) 20.61
        }
        ['3'] => Array(3) {
            ['parcela'] = Integer(1) 4
            ['valor'] = Double/Float(3) 5.2
            ['total'] = Double/Float(4) 20.8
        }
    }
}
```


---------------------------------------------------------------


### Transações / Enviar

> Envia transação como solicitação de pagamento para o comprador via e-mail e SMS

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

###### URL

widepay.com/api/transacoes/enviar

###### PARAMETROS

| Campos  | Obrigatório | Tipo     | Observações                                    |
| ------- | ----------- | -------- | ---------------------------------------------- |
| id      | Sim         | String   | -                                              |
| email   | Sim         | E-mail   | Obrigatório se não existir o parametro celular |
| celular | Não         | Telefone | -                                              |

###### RETORNO

```php
Array(1) {
    ['success'] = Boolean(1) true
}
```


---------------------------------------------------------------


### Transações / Comprovante

> Envia comprovante do pagamento para o comprador via e-mail e SMS

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

###### URL

widepay.com/api/transacoes/comprovante

###### PARAMETROS

| Campos  | Obrigatório | Tipo     | Observações                                    |
| ------- | ----------- | -------- | ---------------------------------------------- |
| id      | Sim         | String   | -                                              |
| email   | Sim         | E-mail   | Obrigatório se não existir o parametro celular |
| celular | Não         | Telefone | -                                              |

###### RETORNO

```php
Array(1) {
    ['success'] = Boolean(1) true
}
```


---------------------------------------------------------------


### Transações / Cancelar

> Cancela a transação

`Autenticação obrigatória usando os parametros ws-conta e ws-token`

###### URL

widepay.com/api/transacoes/cancelar

###### PARAMETROS

| Campos | Obrigatório | Tipo   | Observações       |
| ------ | ----------- | ------ | ----------------- |
| id     | Sim         | String | Pode ser múltiplo |

###### RETORNO

```php
Array(2) {
    ['success'] = Boolean(1) true
    ['total'] = Integer(1) 1
}
```


---------------------------------------------------------------


### Transações / Notificação

> Retorna dados transação referente a um disparo de alteração de status

###### URL

widepay.com/api/transacoes/notificacao

###### PARAMETROS

| Campos | Obrigatório | Tipo   | Observações |
| ------ | ----------- | ------ | ----------- |
| id     | Sim         | String | -           |

###### RETORNO

```php
Array(2) {
    ['success'] = Boolean(1) true
    ['transacao'] => Array(16) {
        ['id'] = String(16) 2b1197bb86714ab1
        ['tipo'] = String(6) Boleto
        ['cliente'] => Array(13) {
            ['pessoa'] = String(7) Física
            ['nome'] = String(14) Lays Pontarolo
            ['cpf'] = NULL(0) null
            ['cnpj'] = NULL(0) null
            ['email'] = NULL(0) null
            ['celular'] = NULL(0) null
            ['rua'] = NULL(0) null
            ['numero'] = NULL(0) null
            ['complemento'] = NULL(0) null
            ['bairro'] = NULL(0) null
            ['cep'] = NULL(0) null
            ['cidade'] = NULL(0) null
            ['estado'] = NULL(0) null
        }
        ['itens'] => Array(1) {
            ['0'] => Array(4) {
                ['descricao'] = String(7) Produto
                ['valor'] = Integer(2) 50
                ['quantidade'] = String(1) 1
                ['desconto'] = Integer(1) 0
            }
        }
        ['desconto'] = NULL(0) null
        ['valor'] = String(5) 50.00
        ['identificador'] = NULL(0) null
        ['notificacao'] = NULL(0) null
        ['redirecionamento'] = NULL(0) null
        ['vencimento'] = String(10) 2015-10-10
        ['criacao'] = String(19) 2015-08-19 15:40:09
        ['status'] = String(10) Compensada
        ['cancelamento'] = NULL(0) null
        ['pagamento'] => Array(4) {
            ['data'] = String(10) 2015-08-10
            ['valor'] = Integer(2) 50
            ['tarifa'] = Double/Float(4) 1.95
            ['disponivel'] => Array(2) {
                ['data'] = String(10) 2015-08-13
                ['valor'] = Double/Float(5) 48.05
            }
        }
        ['historico'] => Array(2) {
            ['0'] => Array(2) {
                ['status'] = String(20) Aguardando pagamento
                ['data'] = String(19) 2015-08-19 15:40:09
            }
            ['1'] => Array(2) {
                ['status'] = String(10) Compensada
                ['data'] = String(19) 2015-08-19 15:56:14
            }
        }
        ['boleto'] => Array(6) {
            ['beneficiario'] = String(7) Almeida
            ['banco'] = String(3) 033
            ['agencia'] = String(4) 4582
            ['codigo'] = String(7) 7109288
            ['carteira'] = String(3) 102
            ['numero'] = String(3) 262
        }
    }
}
```



## Gerando Carnês

...

## Gerando Assinaturas

...

## Recebendo Notificações

...