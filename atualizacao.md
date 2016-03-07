### Atualização dos dados de um cliente
O recurso /api/v1/atualizacao é utilizado para atualizar os dados de um determinado cliente. Todos os atributos são descritos na tabela que segue os exemplos.

#### Métodos suportados

**PUT/POST** - Atualiza os dados de um cliente selecionado

##### Exemplos
```
# Envio
{
    "loja": "Bemtevi",
    "nomeDaLoja": "Loja Shopping",
    "cliente": {
        "nome": "Felipe Gentil",
        "telefone": "16991546201"
    },
    "alterar": {
        "cpf": "18117526085",
        "dataNascimento": "01/01/1970",
        "cep": "14801-309",
        "cidade": "São Paulo",
        "endereco": "Rua Doutor César",
        "uf": "SP",
        "numero": "421",
        "complemento": "ap 122",
        "avisoEmail": false,
        "avisoSMS": false
    }
}

# Resposta
{
  "loja": "Kiskadi Store",
  "respostaAtualizacao": {
    "status": "Sucesso",
    "mensagem": "Cliente atualizado com sucesso",
    "consumidor": {
      "kiskadi_id": "1",
      "nome": "Felipe Gentil",
      "cpf": "18117526085",
      "telefone": "16991546201"
      "dataNascimento": "1970-01-01",
      "email": "felipeapicriacao01@gmail.com",
      "endereco": "Rua Doutor César",
      "cep": "14801-309",
      "cidade": "São Paulo",
      "uf": "SP",
      "number": "421",
      "complemento": "ap 122",
      "avisoEmail": false,
      "avisoSms": true,
      "pontosAtuais": "1600.0"
    }
  }
}
```

```
# Envio
{
    "loja": "Bemtevi",
    "nomeDaLoja": "Loja Shopping",
    "cliente": {
        "kiskadi_id": "1",
    },
    "alterar": {
        "cpf": "18117526085",
        "dataNascimento": "01/01/1970",
        "cep": "14801-309",
        "cidade": "São Paulo",
        "endereco": "Rua Doutor César",
        "uf": "SP",
        "numero": "421",
        "complemento": "ap 122",
        "avisoEmail": false,
        "avisoSMS": false
    }
}

# Resposta
{
  "loja": "Kiskadi Store",
  "respostaAtualizacao": {
    "status": "Sucesso",
    "mensagem": "Cliente atualizado com sucesso",
    "consumidor": {
      "kiskadi_id": "1",
      "nome": "Felipe Gentil",
      "cpf": "18117526085",
      "telefone": "16991546201"
      "dataNascimento": "1970-01-01",
      "email": "felipeapicriacao01@gmail.com",
      "endereco": "Rua Doutor César",
      "cep": "14801-309",
      "cidade": "São Paulo",
      "uf": "SP",
      "number": "421",
      "complemento": "ap 122",
      "avisoEmail": false,
      "avisoSms": true,
      "pontosAtuais": "1600.0"
    }
  }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "nomeDaLoja": "Matriz",
    "cliente": {
        "telefone": "1199990101"
    },
    "alterar": {
        "cpf": "61182163556",
        "dataNascimento": "01/01/1980",
        "cep": "14801-309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP",
        "numero": "400",
        "complemento": "ap 123",
        "avisoEmail": false,
        "avisoSMS": false
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaAtualizacao": {
        "status": "Sucesso",
        "mensagem": "Cliente criado com sucesso",
        "consumidor": {
            "kiskadi_id": "4",
            "nome": null,
            "cpf": "61182163556",
            "telefone": "1199990101",
            "dataNascimento": "1980-01-01",
            "email": null,
            "endereco": "Rua Maria Janasi Biagioni",
            "cep": "14801-309",
            "cidade": "Araraquara",
            "uf": "SP",
            "number": "400",
            "complemento": "ap 123",
            "avisoEmail": false,
            "avisoSms": null,
            "pontosAtuais": "0.0"
        }
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "nomeDaLoja": "Matriz",
    "cliente": {
        "nome": "João"
    },
    "alterar": {
        "dataNascimento": "01/01/1980",
        "cep": "14801-309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP"
    }
}

# Resposta
{
  "loja": "Kiskadi Store",
  "respostaAtualizacao": {
    "status": "Erro",
    "mensagem": "Cliente não encontrado",
    "consumidor": {}
  }
}
```

#### Obrigatoriedade dos campos
* **loja**: campo obrigatório com o nome da loja cadastrada no Kiskadi FID.
* **nomeDaLoja**: campo opcional com o nome da loja cadastrada no Kiskadi FID, caso esse parâmetro não seja enviado, a loja será atribuída à loja do consumidor, ou seja, onde ele foi cadastrado pela primeira vez.
* **cliente**: campo obrigatório, recebe um json com os dados necessários para localizar um cliente, podendo ser TELEFONE, CPF, EMAIL ou KISKADI_ID (o último, que em caso de presença, será utilizado como chave primária na busca pelo cliente)
* **alterar**: campo obrigatório, recebe um json com os dados necessários para atualizar o cliente do json anterior, podendo ser _NOME, TELEFONE, CPF, EMAIL, DATANASCIMENTO, CEP, CIDADE, ENDERECO, UF, NUMERO, COMPLEMENTO, AVISOEMAIL e AVISOSMS_.
* Dentro do _json_ *cliente*, CPF, TELEFONE e EMAIL são campos opcionais, mas é OBRIGATÓRIO a presença de pelo menos um desses ou do identificador KISKADI_ID, caso contrário o sistema não encontrará o cliente e nem será capaz de criar um novo.

#### Observações
* O atributo **cliente** representa todos os dados atualizados com o KiskadiFID do cliente selecionado.
* Caso o cliente não seja encontrado, seguindo o padrão do lançamento de pontos, a API usará os atributos enviados para criar o consumidor, evitando uma chamada extra na consulta do cliente antes de alterá-lo. Uma vez criado, a próxima chamada, quando necessário, encontrará o cliente e alterará os seus dados.