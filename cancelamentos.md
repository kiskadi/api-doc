### Cancelamento de lançamento ou troca
O recurso /api/v1/cancelamentos é utilizado para cancelar um lançamento ou troca previamente efetuados. Todos os atributos são descritos na tabela que segue os exemplos.

#### Métodos suportados
**PUT** - Cancela um lançamento ou troca previamente registrado

##### Exemplos
```
# Envio
{
    "loja": "Kiskadi Store",
    "cancelamento": {
        "nomeDaLoja": "Matriz",
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101",
        "voucher": "23452"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaCancelamento": {
        "status": "SUCESSO",
        "mensagem": "Voucher 28512 cancelado com sucesso",
        "pontosAtuais": "800",
        "todosPontos": "805"
    }
}
```

```
# Envio
{
    "loja": "Kiskadi Store",
    "cancelamento": {
        "nomeDaLoja": "Matriz",
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101",
        "voucher": "23452"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaCancelamento": {
        "status": "ERRO",
        "mensagem": "O voucher não corresponde a nenhum lançamento ou troca deste cliente",
        "pontosAtuais": "100",
        "todosPontos": "110"
    }
}
```

```
# Envio
# Envio
{
    "loja": "Kiskadi Store",
    "cancelamento": {
        "nomeDaLoja": "Matriz",
        "nome": "João da Silva",
        "cpf": "37281920111",
        "email": "joaodasilva@email.com",
        "telefone": "5199999101",
        "voucher": "23452"
    }
}

# Resposta
{
    "loja": "Kiskadi Store",
    "respostaCancelamento": {
        "status": "ERRO",
        "mensagem": "Este lançamento ou troca já está cancelado",
        "pontosAtuais": "",
        "todosPontos": "110"
    }
}
```

#### Obrigatoriedade dos campos
* **loja**: campo obrigatório com o nome da loja cadastrada no Kiskadi FID.
* **nomeDaLoja**: campo opcional com o nome da loja cadastrada no Kiskadi FID, caso esse parâmetro não seja enviado, a loja será atribuída à loja do consumidor, ou seja, onde ele foi cadastrado pela primeira vez.
* **nome**: campo opcional
* **cpf**, **telefone** e **email**: é obrigatório a presença de pelo menos um para que o cliente seja confirmado com o voucher
* **voucher**: campo obrigatório

#### Observações
* O atributo **pontosAtuais** representa a quantidade de pontos atual do cliente caso o cancelamento tenha sido feito com sucesso.
*  O atributo **todosPontos** representa a quantidade total de pontos do cliente, incluindo lançamentos que não foram contabilizados ainda, ou seja, que só vão começar a valer a partir de uma determinada data.