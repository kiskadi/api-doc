### Consulta de pontos para um determinado cliente
O recurso /api/v1/pontos é utilizado para fazer uma consulta da quantidade de pontos para um determinado cliente.

#### Métodos suportados

**GET/POST** - Consulta a quantidade de pontos de um determinado cliente.

##### Exemplos

```
# Envio
{
    "loja": "Kiskadi Store",
    "cliente": {
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaPontos": {
        "status": "Sucesso",
        "mensagem": "200",
        "desconto": "10",
        "consumidor": {
            "kiskadi_id": "123",
            "nome": "Felipe Gentil",
            "telefone": "1699990101",
            "cpf": "18117526085",
            "email": "felipe@gentil.com",
            "dataNascimento": "01/01/1970",
            "cep": "14801-309",
            "cidade": "São Paulo",
            "endereco": "Rua Doutor César",
            "uf": "SP",
            "numero": "421",
            "complemento": "ap 122",
            "avisoEmail": false,
            "avisoSMS": false,
            "pontosAtuais": "100"
        }
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "cliente": {
        "cpf": "37281920111"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaPontos": {
        "status": "Sucesso",
        "mensagem": "200",
        "desconto": "10",
        "consumidor": {
            "kiskadi_id": "123",
            "nome": "Felipe Gentil",
            "telefone": "1699990101",
            "cpf": "18117526085",
            "email": "felipe@gentil.com",
            "dataNascimento": "01/01/1970",
            "cep": "14801-309",
            "cidade": "São Paulo",
            "endereco": "Rua Doutor César",
            "uf": "SP",
            "numero": "421",
            "complemento": "ap 122",
            "avisoEmail": false,
            "avisoSMS": false,
            "pontosAtuais": "100"
        }
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "cliente": {
        "kiskadi_id": "123"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaPontos": {
        "status": "Sucesso",
        "mensagem": "200",
        "desconto": "10",
        "consumidor": {
            "kiskadi_id": "123",
            "nome": "Felipe Gentil",
            "telefone": "1699990101",
            "cpf": "18117526085",
            "email": "felipe@gentil.com",
            "dataNascimento": "01/01/1970",
            "cep": "14801-309",
            "cidade": "São Paulo",
            "endereco": "Rua Doutor César",
            "uf": "SP",
            "numero": "421",
            "complemento": "ap 122",
            "avisoEmail": false,
            "avisoSMS": false,
            "pontosAtuais": "100"
        }
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store II",
    "cliente": {
        "email": "joaodasilva@email.com",
        "telefone": "5199999101"
    }
}

# Resposta
{
    "loja": "Kiskadi Store II",
    "respostaPontos": {
        "status": "Erro",
        "mensagem": "Loja não encontrada",
        "desconto": "",
        "consumidor": {}
    }
}
```

#### Obrigatoriedade dos campos

* **loja**: campo obrigatório com o nome da loja cadastrada no Kiskadi FID.
* **cliente**: campo obrigatório, recebe parâmetros com informações do cliente
* **nome**: campo opcional
* **cpf**: [campo opcional](identificacao_do_cliente.md)
* **email**: [campo opcional](identificacao_do_cliente.md)
* **telefone**: [campo opcional](identificacao_do_cliente.md)
* **kiskadi_id**: [campo opcional](identificacao_do_cliente.md)

#### Observações

Alguns possíveis erros no retorno do JSON
* "Cliente não encontrado"
* "Loja não encontrara"
* "Usuário não autenticado para essa loja"
