# Replicação

### Tolerância a faltas

Duas técnicas:
para trás.
para a frente.

## Para trás:

- Com um algoritmo guarda-se o estado num momento em que seja adequado.
- Quando um ou mais processos falham, estes são relançados.
- Os novos processos lêem o último estado guardado e recomeçam a partir desse último - estado.
- Chama-se ___checkpoint-recovery___.

> [!NOTE] Basicamente
> Os estados guardados pelos vários processos que falharam devem estar
mutuamente coerentes.

## Para a frente:

- Várias réplicas do processo.
- Quando uma réplica é alterada todas as outras também o têm de ser.
- Se uma réplica falha os clientes podem usar outra réplica.

> [!NOTE] Basic
> Os estado das réplicas que sobrevivem devem estar mútuamente coerentes.

#### Estrutura de dados:

- Registo - Algoritmo ABD
- Espaço de tuplos - Xu-Liskov

# Primário-Secundário:

1. Um processo é eleito como primário (se um prikmário falha é eleito outro primário)
2. Clientes enviam pedidos ao primário.
3. Para cada pedido, primário: executa o pedido, propaga estado para secundários e espera confirmação, responde ao cliente e vê próximo pedido.

Suporta operações não deterministas (lider decide o resultado)
Se líder reproduz valor errado é propagado para as outras réplicas.

# Replicação de Máquina de Estados

1. Clientes enviam pedidos a todas as réplicas
2. Todos os pedidos são ordenados por ordem total
3. Todas as réplicas replicam os mesmos pedidos pela mesma ordem.

Se produzir um valor errado não afeta as outras réplicas.
Operações Deterministas.

# Abstrações para a construção de sistemas replicados

### Canais Perfeitos













