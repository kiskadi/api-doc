### Identificação dos clientes

O Kiskadi pode receber uma série de atributos para identificar um cliente.
São eles:
* **kiskadi_id**: identificação numérica única de um cliente no Kiskadi
* **cpf**: CPF do cliente
* **email**: Email do cliente
* **telefone**: Telefone do cliente

O Kiskadi determina qual o cliente está sendo referenciado pela API usando estes atributos na seguinte ordem de prioridade:

1. kiskadi_id
2. cpf
3. email
4. telefone

Ou seja, se a chamada de API contiver CPF e telefone do cliente, o Kiskadi usará o CPF para encontrar o cliente no cadastro.
Caso não seja encontrado um cliente com este CPF no cadastro, o telefone será usado.

É importante ressaltar que, ao contrário dos anteriores, o telefone não é um atributo que garante unicidade no cadastro da Kiskadi, portanto os usuários da API devem dar preferência aos outros atributos na identificação do cliente.
Se a identificação for feita pelo telefone, corre-se o risco do cliente seleciona não ser o pretendido.
