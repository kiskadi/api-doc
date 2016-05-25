### Troca automática de pontos
O recurso /api/v1/trocas é utilizado para enviar um registro de troca de pontos para o Kiskadi FID. Todos os atributos são descritos na tabela que segue o exemplo.

#### Métodos suportados
**POST** - Realiza a troca de pontos por um benefício

#### Exemplos
```
# Envio
{
    "loja": "Kiskadi Store",
    "troca": {
        "nomeDaLoja": "Matriz",
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101",
        "pontos": "100"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaTroca": {
        "status": "Sucesso",
        "mensagem": "Pontos trocados com sucesso",
        "voucher": "3958",
        "pontosAtuais": "75",
        "todosPontos": "100",
        "descontoTotal": "75",
        "desconto": "10"
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "troca": {
        "cpf": "37281920111",
        "pontos": "100"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaTroca": {
        "status": "Sucesso",
        "mensagem": "Pontos trocados com sucesso",
        "voucher": "3958",
        "pontosAtuais": "50",
        "todosPontos": "100",
        "descontoTotal": "5",
        "desconto": "5"
    }
}

```

```
# Envio
{
    "loja": "Kiskadi Store",
    "troca": {
        "nomeDaLoja": "Matriz",
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101",
        "pontos": "1000"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaTroca": {
        "status": "Erro",
        "pontos": "Os pontos não são suficientes para esse benefício",
        "voucher": "3958",
        "pontosAtuais": "100",
        "todosPontos": "110",
        "descontoTotal": "100",
        "desconto": ""
    }
}

```

#### Obrigaroriedade dos campos
* **loja**: campo obrigatório com o nome da loja cadastrada no Kiskadi FID.
* **troca**: campo obrigatório, recebe um json com dados da transação
* **nomeDaLoja**: campo obrigatório com o nome da filial
* **nome**: campo opcional
* **cpf**: [campo opcional](identificacao_do_cliente.md)
* **email**: [campo opcional](identificacao_do_cliente.md)
* **telefone**: [campo opcional](identificacao_do_cliente.md)
* **kiskadi_id**: [campo opcional](identificacao_do_cliente.md)
* **aniversario**: campo opcional
* **pontos**: campo obrigatório, quantidade de pontos a ser trocada

#### Observações
Cada loja decide um conjunto de atributos cuja presença no cadastro é obrigatória para a troca de pontos, entre CPF, Email e Data de aniversário.
Além destes, o Nome e o Telefone precisam estar no cadastro para trocas serem bem-sucedidas.

Estes atributos não precisam estar na chamada da API de troca, mas já devem estar presentes no cadastro do cliente no Kiskadi.
Caso o cadastro do cliente não tenha todos os dados obrigatórios, a troca falhará e a mensagem de erro retornada pela API indicará qual(is) atributo(s) precisam ser preenchidos.

Alguns possíveis erros no retorno do JSON
* "CPF inválido"
* "Email inválido"
* "Telefone inválido"
* "Nome da loja não encontrado"
* "Os pontos não são suficientes para esse benefício"
* "Falha ao trocar pontos (Para efetuar trocas o cliente deve possuir email preenchido(s))"
