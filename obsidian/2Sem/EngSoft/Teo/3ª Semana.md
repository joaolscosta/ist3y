# Testing Strategies

- __Partition Testing__
- __Guideline-based testing__: usa guidelines para escolher quais testes. Estas são reflexo de experiências anteriores. Que testes são bons para descobrir erros.

Exemplos:

- Escolher inputs que dêem erro.
- Inputs que encham buffers.
- Repetir o mesmo input diversas vezes.
- Forçar inputs errados a dar certo.

# Code Coverage

Percentagem de quanto código fonte é usado para dado teste.

Um programa com maior cobertura de testes tem mais do seu código fonte executado o que te uma menor chance de conter software bugs de software não identificados.

White-box testing.

- __Statement coverage__: cada statement tem que ser executado pelo menos uma vez. Se numm if entra nos dois sitios.
- __Branch Coverage__: Se para testes diferentes num if numa vez entra por um lado e noutra vez entra por outro.
- __Condition Coverage__: Todas as variaveis no if são consideradas em diferentes iterações como true ou false.
- __Path coverage__: Que caminhos se podem fazer se considerarmos as variáveis true e false em diferentes iterações.

## Structured Basis Testing

É um Path coverage.

``Número de independent paths = número de decisions + 1``

## Object Testing

Testa sequências de métodos, vários unit testing.

Importância distinguir entre __modal__ e __non-modal__.

Os internal states impactam na modal apenas.

Este teste foca nas modais.

## Component Testing

Faz-se esta depois do Unit e do Object.

Testa a interação entre interfaces de diferentes componentes.

Tem então como objetivo encontrar falhas na interface.

### Interface Errors

- __Interface misuse__: uma componente chama outra componente e dá erro na interface por parametros numa ordem errada.
- __Interface misunderstanding__: uma componente assume coisas erradas.
- __Timing errors__: duas componentes terem timings diferentes e out-of-date data acessada.

### Approaches

Podemos testar todas juntas (__big bang integration__) ou incrementando (__bottom-up__ ou __top-down__).

![[Pasted image 20240329224724.png]]

# 5ªAula

## TDD Refactoring

Testes antes do code.
Desenvolve-se incrementally com um teste para esse incremento.

Beneficios:

__code coverage__: um teste pelo menos para cada cena escrita.
__Regression Testing__: teste para verificar que as funcionalidades já existentes não se estragam.
## Litter-Pickup Refactoring

## Comprehension Refactoring

## Preparatory Refactoring

## Planned Refactoring

Num projeto de refactorização de longa duração, a ultima coisa a fazer é remover o código obsoleto. Deve-se primeiro garantir uma boa cobertura de testes. Serve entre outras coisas para reduzir complexidade e melhorar legibilidade.








