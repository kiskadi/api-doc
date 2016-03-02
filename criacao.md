### Criação de cliente sem lançamento de pontos
O recurso /api/v1/criacao é utilizado para criar um cliente sem que seja realizado um lançamento de pontos.. Todos os atributos são descritos na tabela que segue os exemplos.

#### Métodos suportados
**POST** - Cria um cliente novo sem lançamento de pontos

##### Exemplos
```
# Envio
{
    "loja": "Bemtevi",
    "nomeDaLoja": "Loja Shopping",
    "cliente": {
        "nome": "Felipe API Criação 01",
        "telefone": "1699880001",
        "cpf": "66229255855",
        "email": "felipeapicriacao01@gmail.com",
        "dataNascimento": "01/01/1999",
        "cep": "14801309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP",
        "numero": "463",
        "complemento": "Ap 122",
        "avisoEmail": true,
        "avisoSms": true,
        "ativo": true
    }
}

# Resposta
{
    "loja": "Bemtevi",
    "respostaCriacao": {
        "status": "Sucesso",
        "mensagem": "Cliente criado com sucesso"
    },
    "consumidor": {
        "kiskadi_id": "123",
        "nome": "Felipe API Criação 01",
        "telefone": "1699880001",
        "cpf": "66229255855",
        "email": "felipeapicriacao01@gmail.com",
        "dataNascimento": "01/01/1999",
        "cep": "14801309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP",
        "numero": "463",
        "complemento": "Ap 122",
        "avisoEmail": true,
        "avisoSms": true,
        "ativo": true
    }
}
```

```
# Envio
{
    "loja": "Bemtevi",
    "nomeDaLoja": "Loja Shopping",
    "cliente": {
        "nome": "Felipe API Criação 01",
        "cep": "14801309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP",
        "numero": "463",
        "complemento": "Ap 122",
        "avisoEmail": true,
        "avisoSms": true,
        "ativo": true
    }
}

# Resposta
{
    "loja": "Bemtevi",
    "respostaCriacao": {
        "status": "Erro",
        "mensagem": "Parâmetros inválidos para criar cliente"
    },
    "consumidor": {}
}
```

```
# Envio
{
    "loja": "Bemtevi",
    "nomeDaLoja": "Loja Shopping",
    "cliente": {
        "nome": "Felipe API Criação 01",
        "telefone": "1699880001",
        "cpf": "66229255855",
        "email": "felipeapicriacao01@gmail.com",
        "dataNascimento": "01/01/1999",
        "cep": "14801309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP",
        "numero": "463",
        "complemento": "Ap 122",
        "avisoEmail": true,
        "avisoSms": true,
        "ativo": true
    }
}

# Resposta
{
    "loja": "Bemtevi",
    "respostaCriacao": {
        "status": "Erro",
        "mensagem": "Cliente já cadastrado"
    },
    "consumidor": {
        "kiskadi_id": "123",
        "nome": "Felipe API Criação 01",
        "telefone": "1699880001",
        "cpf": "66229255855",
        "email": "felipeapicriacao01@gmail.com",
        "dataNascimento": "01/01/1999",
        "cep": "14801309",
        "cidade": "Araraquara",
        "endereco": "Rua Maria Janasi Biagioni",
        "uf": "SP",
        "numero": "463",
        "complemento": "Ap 122",
        "avisoEmail": true,
        "avisoSms": true,
        "ativo": true
    }
}
```

#### Obrigatoriedade dos campos
* **loja**: campo obrigatório com o nome da loja cadastrada no Kiskadi FID.
* **nomeDaLoja**: campo opcional com o nome da loja cadastrada no Kiskadi FID, caso esse parâmetro não seja enviado, a loja será atribuída à loja do consumidor, ou seja, onde ele foi cadastrado pela primeira vez.
* **cliente**: campo obrigatório, recebe um json com os dados necessários para localizar um cliente, podendo ser TELEFONE, CPF ou EMAIL

#### Observações
* Dentro do _json_ *cliente*, CPF, telefone e email são campos opcionais, mas é OBRIGATÓRIO a presença de pelo menos um desses, caso contrário o sistema não encontrará o cliente e nem será capaz de criar um novo.