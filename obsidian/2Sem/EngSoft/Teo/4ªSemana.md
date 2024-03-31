Quais são as qualidades de um bom design?

- __High cohesion__: responsabilidade individual de um bom design. Aumenta a localidade de mudança.
- __Low coupling__: reduz dependências entre modulos.


# Design Patterns

### Command Design Patterns

Encapsola uma solicitação como um objeto, assim permitindo que paremetrize clientes com solicitações diferentes, log ou de queue, e permite também desfazer operações.

Coupling:
- quem invoca é independente do comando 
- o cliente sabe o comando
- fácil de ter novos tipos de comando
Cohesion:
- comandos concretos que têm todas as operaçõe associadas com o controlo da operação.

O invocador tem ligação fraca com os comandos concretos.

### The template method design pattern

Define o esqueleto de um programa para um algoritmo numa operação, adiando alguns passos de subclasses. Permite redefinir certos passos de um algoritmo sem mudar a estrutura dele.

Coupling:
- Existe um forte coupling entre as subclasses e superclasse porque seguem o algoritmo (abstração).
Cohesion:
- a superclasse é coesiva no contexto que é necessário.

As classes têm ligação forte entre elas.
Possibilita a partilha de código entre super e sub.
Super tem coesão elevada.

### State Design pattern

O padrão oferece elevada coesão nas responsabilidades de cada estado.
Encapsolar objetos baseado no seu estado.
É uma boa maneira de corrigir runtime sem ter que mudar o seu comportamento e reordenar as suas condições.

### Composite Design pattern

Descreve um grupo de objetcts que são tratados da mesma maneira como uma só instância do mesmo tipo de objeto.
Objetivo é compor em três estruturas para representar partes de hierárquias.

Isto permite aos clientes tratamento individual de objetos e compolos uniformemente com os outros.

## Lei de Deméter

Evita dependências excessivas entre partes do sistema.

## Princípio da Segregação de Interfaces

Interfaces devem ser ajustadas ao clientes que a usam e não genéricas para todos para não haver coisas desncessárias.

## Princípio da inversão de dependências

Módulos de alto nível aqui não dependem dos de baixo nível.
Ambos dependem de abstrações.

## Princípio de substituição de Liskov

Objetos de uma classe devem podem ser substituídos por objetos de suas subclasses sem afetar a integridade do sistema.


