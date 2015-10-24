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
* **cpf**: campo opcional
* **email**: campo opcional
* **telefone**: campo obrigatóro
* **pontos**: campo obrigatório, quantidade de pontos a ser trocada

#### Observações
Os atributos CPF e E-mail não são obrigatórios na troca de pontos, entretanto, um email será enviado ao gerente da loja com a seguinte mensagem:

_"Caro <gerente_da_loja>,_

_Informamos que o operador <nome_do_usuario> da loja <nome_da_loja> realizou a troca de pontos por benefício para o(a) cliente <cliente_nome_e_telefone> sem completar os seguintes dados cadastrais: <CPF/EMAIL>_

_Kiskadi"_


Alguns possíveis erros no retorno do JSON
* "CPF inválido"
* "Email inválido"
* "Telefone inválido"
* "Nome da loja não encontrado"
* "Os pontos não são suficientes para esse benefício"