### Erros api/v1
O recurso /api/v1/errors é utilizado para inserir um erro de comunicação com a KiskadiAPI. Todos os atributos são descritos na tabela que segue os exemplos.

#### Métodos suportados

** POST ** - Cria um registro de erro retornado pela KiskadiAPI

#### Exemplos

```
# Envio
{
    "api_error": {
        "json_input": "{teste}",
        "json_output": "{error}",
        "status": "422",
        "date": "01/01/2015",
        "method": "teste",
        "vendor": "Kiskadi Store",
        "branch": "Matriz"
    }
}

# Resposta
{
    "message": "Sucesso",
    "error": ""
}
```

```
# Envio
{
    "api_error": {
        "json_input": "",
        "json_output": "{error}",
        "status": "422",
        "date": "01/01/2015",
        "method": "teste",
        "vendor": "Kiskadi Store",
        "branch": "Matriz"
    }
}

# Resposta
{
    "message": "Erro",
    "error": "Json input não pode ficar em branco"
}
```

#### Descrição de atributos
* **json_input**: Json de entrada da requisição que apresentou erro
* **json_output**: Mensagem de resposta da KiskadiAPI da requisição
* **status**: Status recebido da KiskadiAPI (ex: 422, 404, 500)
* **date**: Data da requisição (ex: 01/05/2015 23:00:35)
* **method**: Método utilizado (ex: pontos, atualizacao, cancelamento)
* **vendor**: Nome da loja (ex: Maria Xica, Bonneterie, Loja Kiskadi)
* **branch**: Nome da filial (ex: Shopping Iguatemi, Matriz)

#### Observações
* Campos obrigatórios: _json_input_ e _json_output_
* A principal motivação dessa rota é servir de feedback dos integradores na intenção de melhorar sempre a KiskadiAPI, não é de maneira nenhuma obrigatório o uso desse método para que a aplicação funcione.