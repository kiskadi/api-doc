KiskadiAPI
==========

### Introdução

A API do Kiskadi FID permite que as lojas troquem informações de lançamento e troca de pontos de forma rápida, simples e segura.

Nossa API é construida seguindo os princípios arquiteturais RESTful, o que, além de prover uma plataforma robusta e escalável, torna a integração muito mais simples e intuitiva do que os modelos tradicionais de integração de sistemas distribuídos, como SOAP e XML-RPC.

### Autenticação

Todas as URLs referenciadas neste documento utilizam autenticação.
O método de autenticação utilizado é HTTP Basic Access Authentication. Isto significa que suas credenciais serão solicitadas em todas as requisições.
Sessões não são utilizadas nas requisições. Clique aqui para mais informações sobre autenticação HTTP Basic.

### Content-Type

Em todos os recursos da API do Kiskadi FID utilizamos o Content-type: application/json; charset=utf-8. Se algum recurso
específico utilizar outro formato este será especificado na documentação do mesmo.

_Requisições cujo conteúdo não for codificado em UTF-8 serão rejeitadas com status 400 Bad Request_

### Versionamento

A API possui um versionamento embutido nas suas URLs. Elas seguem a forma:  _/api/<versão>/<nome_da_api>_. Este documento descreve a versão **v1** da API. Futuras versões serão eventualmente criadas com a evolução da API.

#### Recursos
* [Lançamento automático de pontos](lancamentos.md)
* [Consulta de pontos para um determinado cliente](pontos.md)
* [Troca automática de pontos](trocas.md)
* [Cancelamento de lançamento ou troca](cancelamentos.md)
* [Atualização de dados de cliente](atualizacao.md)
* [Erros api/v1](errors.md)
* [Criação de cliente sem lançamento de pontos](criacao.md)