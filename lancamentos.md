### Lançamento automático de pontos
O recurso /api/v1/lancamentos é utilizado no lançamento de pontos para um determinado cliente. Caso o cliente não exista na base de dados, ele será criado com a pontuação devidamente lançada automaticamente.

#### Métodos suportados

**POST** - Cria um ou mais consumidores e lança pontos automaticamente.

##### Exemplos
```
# Envio
{
  "loja": "Kiskadi Store",
  "lancamento": {
      "nomeDaLoja": "Matriz",
      "nome": "João da Silva",
      "cpf": "37281920111",
      "email": "joaodasilva@email.com",
      "telefone": "5199999101",
      "aniversario": "10/12",
      "dataHora": "12/01/2014 09:35",
      "valorDaCompra": "21,30",
      "numeroDoDocumento": "43675",
      "nomeVendedor": "Machado de Assis"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaLancamento": {
        "resposta": "SUCESSO",
        "mensagem": "Consumidor criado e pontos lançados com sucesso",
        "voucher": "3958",
        "descontoUltimoLancamento": "2",
        "pontosAtuais": "100",
        "todosPontos": "120",
        "desconto": "10"
    }
}

```

```
# Envio
{
    "loja": "Kiskadi Store",
    "lancamento": {
        "nomeDaLoja": "Matriz",
        "dataHora": "14/01/2014 09:35",
        "valorDaCompra": "91,50",
        "numeroDoDocumento": "43676"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaLancamento": {
        "resposta": "ERRO",
        "mensagem": "Telefone é obrigatório para o lancamento de pontos",
        "voucher": "",
        "descontoUltimoLancamento": "",
        "pontosAtuais": "100",
        "todosPontos": "110",
        "desconto": "10"
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "lancamento": {
        "nomeDaLoja": "Matriz",
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101",
        "aniversario": "7/11/1988",
        "dataHora": "12/01/2014 09:35",
        "valorDaCompra": "21,30",
        "numeroDoDocumento": "43675",
        "nomeVendedor": "Machado de Assis"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaLancamento": {
        "resposta": "SUCESSO",
        "mensagem": "Consumidor já existente e pontos lançados com sucesso",
        "voucher": "3959",
        "descontoUltimoLancamento": "3",
        "pontosAtuais": "100",
        "todosPontos": "110",
        "desconto": "10"
    }
}
```

#### Obrigatoriedade dos campos
* **loja**: campo obrigatório com o nome da loja cadastrada no Kiskadi FID.
* **lancamentos**: campo obrigatório, recebe um json com dados da transação
* **nomeDaLoja**: campo obrigatório com o nome da filial
* **nome**: campo opcional
* **cpf**: campo opcional
* **email**: campo opcional
* **telefone**: campo obrigatório *
* **aniversario**: campo opcional, formato "dia/mês" ou "dia/mês/ano"
* **dataHora**: campo obrigatório com a data e hora da transação
* **valorDaCompra**: campo obrigatório com o valor total da compra
* **numeroDoDocumento**: campo opcional
* **nomeVendedor**: campo opcional, representa o vendedor que realizou a venda
* **cpf**: Texto
* **dataNascimento**: Data
* **cep**: Texto - Campo opctional
* **cidade**: Texto - Campo opctional
* **endereco**: Texto - Campo opctional
* **uf**: Texto - Campo opctional
* **numero**: Texto - Campo opctional
* **complemento**: Texto - Campo opctional
* **avisoEmail**: true | false - Campo opctional (default: true)
* **avisoSMS**: true | false - Campo op (default: true)
* **ativo**: true | false - Campo opcional (default: true)

#### Observações

O atributo **desconto** representa o desconto atual do cliente baseado em seus pontos, não somente da troca realizada na requisição recente. **descontoUltimoLancamento** é o desconto, calculado igualmente descrito acima, mas relacionado somente ao lançamento realizado durante a requisição. **voucher** representa o ID único da transação que representa a troca de pontos, será utilizado para cancelar uma troca de pontos. O atributo **pontosAtuais** representa a quantidade de pontos atual do cliente caso o cancelamento tenha sido feito com sucesso. O valor de **todosPontos** representa a quantidade total de pontos do cliente, incluindo lançamentos que não foram contabilizados ainda, ou seja, que só vão começar a valer a partir de uma determinada data.


Alguns possíveis erros no retorno do JSON
* "CPF inválido"
* "Email inválido"
* "Telefone inválido"
* "Nome da loja não encontrado"