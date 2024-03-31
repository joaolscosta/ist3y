![[Pasted image 20240331195211.png]]
# Domain Logic

Uses cases para o exemplo do banco:

- Transferir dinheiro
- Saldo do cliente

Como implementar:

- Transaction Script (TS)
- Domain model (DM)

#### TS

Um procedimento para cada use case.
Acesso direto à DB ou acess layer.
Cada TS é indepependente e corresponde a uma transação.

Depois de programarmos percebemos:

- Difícil de se reutilizar.
- Código duplicado.
- Depende muito da estrutura da DB.

Isto é basicamente usar a DB.
Organiza business logic em procedimentos que um único pedido.

#### DM

Cada objeto tem uma parte do domain logic.

Isto é usar classes e objetos delas.
Tem o comportamento e data.

- Mais reutilizável
- Mais estável

Mas tem problemas como:

- data acess
- objetos persistentes
- um método não corresponde a uma transação

#### Table Module

Uma instância única que orienta o business logic para todas as linhas de uma table or view.
# Services

1 serviço = 1 transação

# Data Acess

Data Source Architectural Patters:

- Table Data Gateway
- Row Data Gateway
- Active Record
- Data Mapper

### Table Data gateway

Um objeto que atua como _Gateway_ para uma _databse table_.
Uma instância gere todas as linhas de uma tabela.

Localiza todo o código SQL para a sua classe.
Não tem uma interface de objetos-orientados.

### Row Data Gateway

Um objeto atua como _gateway_ para um único record na data.
Apenas uma instância por row.

Localiza o código SQL na propria classe e tem uma interface de objetos-orientados mas não contém domain logic.

### Active Record

Um objeto que envolve uma linha numa table ou view encapsola o acesso à database e adiciona o domain logic à data.

### Data Mapper

Uma camada de Mappers movem data entre os objetos e a database enquanto os guardam independentemente uns dos outros.

Código SQL separado do domain logic que tem um object-oriented interface que conem business logic e permite mappings diferentes entre estruturas de objetos e da estrutura da database.

# Unit of Work

Tem uma lista de objetos afetados pela _business transaction_ e coordenadas que escrevem as diferenças e resolução de problemas de concorrência.


# Identity Map

Assegura que cada objeto seja carregado apenas uma vez guardando todos os objetos carregados num map.

# Lazy Load

Um objeto não contem toda a data mas sabe como obtê-la.

A inicialização é a null.

# Virtual Proxy

VP de um objeto é carregar o objeto real.

# Value Holder

Wraps the real object.

# Ghost

É o objeto real mas num estado parcial.


