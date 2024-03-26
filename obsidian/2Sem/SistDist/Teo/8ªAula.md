# Consenso


> [!NOTE] Conceito
> Para N processos cada um decide um input e todos decidem um output. O valor decidido é um dos propostos e é escolhido aleatoriamente.

# Floodset
 
Se _pi_ não recebe o valor de um processo _pj_ no turno _n_ então _pj_ falhou e não participa nos próximos turnos.

1. Todos os nós começam com  um conjunto vazio de valores para o consenso.
2. Quando um nó tem um valor a propor ele envia para todos os outros nós no sistema e cada mensagem é marcada com o número de sequência para indicar a ordem.
3. Quando um nó recebe uma mensagem mete no conjunto de valores propostos se ainda não estiver lá. Envia mensagem a todos os outros com o tempo em que recebeu mensagem.
4. Se receber uma mensagem para um valor que já foi decidido descarta a mensagem, caso contrário mantém e dá o valor como decidido quando receber a mensagem de todos os outros nós para esse valor.
5. Depois do nós ser decidido pode ser considerado como valor final de consenso.

### Problemas:

#### Coerência Interativa

Cada processo pi propõe um valor input_i. Todos os processos decidem o mesmo valor.
Ou v[i] = input_i ou null.





