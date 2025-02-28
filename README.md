# Modelo de Banco de Dados para Sistema de Oficina Mecânica

## Descrição

Este modelo de banco de dados foi desenvolvido para um sistema de gerenciamento de oficina mecânica. Ele abrange as principais entidades e seus relacionamentos, permitindo o controle eficiente de clientes, veículos, mecânicos, serviços, peças e pagamentos.

## Diagrama Entidade-Relacionamento (DER)

![OficinaMecanica](https://github.com/user-attachments/assets/ca674d6c-db68-4352-8c04-f83a95fa1752)

## Tabelas

### Cliente

| Coluna | Tipo | Descrição |
|---|---|---|
| idCliente | INT | Identificador único do cliente (Chave Primária) |
| Nome | VARCHAR(45) | Nome completo do cliente |
| Endereço | VARCHAR(45) | Endereço do cliente |
| Celular | VARCHAR(45) | Número de celular do cliente |

### Veículo

| Coluna | Tipo | Descrição |
|---|---|---|
| idVeículo | INT | Identificador único do veículo (Chave Primária) |
| Fabricante | VARCHAR(45) | Fabricante do veículo |
| Modelo | VARCHAR(45) | Modelo do veículo |
| Ano | VARCHAR(45) | Ano de fabricação do veículo |
| Placa | VARCHAR(45) | Placa do veículo |
| Cliente_idCliente | INT | Chave estrangeira referenciando a tabela Cliente |

### Mecânico

| Coluna | Tipo | Descrição |
|---|---|---|
| idMecânico | INT | Identificador único do mecânico (Chave Primária) |
| Matrícula | VARCHAR(45) | Matrícula do mecânico |
| Nome | VARCHAR(45) | Nome completo do mecânico |
| Endereço | VARCHAR(45) | Endereço do mecânico |
| Especialidade | VARCHAR(45) | Especialidade do mecânico |

### Equipe

| Coluna | Tipo | Descrição |
|---|---|---|
| OrdemServiço_idOrdemServiço | INT | Chave estrangeira referenciando a tabela OrdemServiço |
| Mecânico_idMecanico | INT | Chave estrangeira referenciando a tabela Mecânico |

### OrdemServiço

| Coluna | Tipo | Descrição |
|---|---|---|
| idOrdemServiço | INT | Identificador único da ordem de serviço (Chave Primária) |
| Número | INT | Número da ordem de serviço |
| DataEmissão | DATETIME | Data de emissão da ordem de serviço |
| DataEntregaPrevista | DATE | Data prevista para entrega do veículo |
| ValorTotal | VARCHAR(45) | Valor total da ordem de serviço |
| Status | VARCHAR(45) | Status da ordem de serviço |
| Autorizado | VARCHAR(45) | Indica se a ordem de serviço foi autorizada |
| Veículo_idVeículo | INT | Chave estrangeira referenciando a tabela Veículo |
| Veículo_Cliente_idCliente | INT | Chave estrangeira referenciando a tabela Cliente |

### PeçaUsada

| Coluna | Tipo | Descrição |
|---|---|---|
| idPeçaUsada | INT | Identificador único da peça usada (Chave Primária) |
| Peça_idPeça | INT | Chave estrangeira referenciando a tabela Peça |
| OrdemServiço_idOrdemServiço | INT | Chave estrangeira referenciando a tabela OrdemServiço |
| Quantidade | INT | Quantidade de peças usadas |
| Preço | DECIMAL(10.2) | Preço total das peças usadas |

### Peça

| Coluna | Tipo | Descrição |
|---|---|---|
| idPeça | INT | Identificador único da peça (Chave Primária) |
| Nome | VARCHAR(45) | Nome da peça |
| Descrição | MEDIUMTEXT | Descrição da peça |
| Preço | DECIMAL(10.2) | Preço da peça |
| QuantidadeEstoque | INT | Quantidade em estoque da peça |

### Pagamento

| Coluna | Tipo | Descrição |
|---|---|---|
| idPagamento | INT | Identificador único do pagamento (Chave Primária) |
| Veículo_idVeículo | INT | Chave estrangeira referenciando a tabela Veículo |
| OrdemServiço_idOrdemServiço | INT | Chave estrangeira referenciando a tabela OrdemServiço |
| OrdemServiço_Veículo_idCliente | INT | Chave estrangeira referenciando a tabela Cliente |
| Data | DATETIME | Data do pagamento |
| ValorTotal | DECIMAL(10.2) | Valor total do pagamento |
| Metodo_de_Pagamento | VARCHAR(45) | Método de pagamento utilizado |

### Serviço

| Coluna | Tipo | Descrição |
|---|---|---|
| idServiço | INT | Identificador único do serviço (Chave Primária) |
| MãoDeObra_idMãoDeObra | INT | Chave estrangeira referenciando a tabela MãoDeObra |
| OrdemServiço_idOrdemServiço | INT | Chave estrangeira referenciando a tabela OrdemServiço |
| Serviços | VARCHAR(45) | Nome do serviço |
| Status | VARCHAR(45) | Status do serviço |

### MãoDeObra

| Coluna | Tipo | Descrição |
|---|---|---|
| idMãoDeObra | INT | Identificador único da mão de obra (Chave Primária) |
| Descrição | MEDIUMTEXT | Descrição da mão de obra |
| Preço | DECIMAL(10.2) | Preço da mão de obra |

## Relacionamentos

* Um Cliente pode ter vários Veículos.
* Um Mecânico pode participar de várias Equipes.
* Uma OrdemServiço pode ter várias PeçasUsadas e vários Serviços.
* Uma Peça pode ser usada em várias PeçasUsadas.
* Um Veículo pode ter vários Pagamentos.
* Um Serviço utiliza uma MãoDeObra.

## Instruções de Uso

1.  Crie um banco de dados com o nome desejado.
2.  Execute o script SQL para criar as tabelas e seus relacionamentos.
3.  Insira os dados de exemplo para testar o sistema.

## Contribuição

Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue ou enviar um pull request.

## Licença

Este projeto está licenciado sob a [Licença MIT](https://opensource.org/licenses/MIT).
