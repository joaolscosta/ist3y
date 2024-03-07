# Teorema CAP

1. Coerência (consistency)
2. Disponibilidade (availability)
3. Tolerância a partições de rede (partition-tolerance)

É impossível ter-se as três, só se conseguem ter duas.

# Propagação Epidémica (_Gossip_)

Sistema em que tenta replicar processos da form menos coordenada possível:

- Cada processo contacta outro e envia atualizações para outros nós (_gossip_).
- Vantagem de ser totalmente descentralizado e bom balanceamento de carga.

Considerem-se três réplicas, R1, R2, e R3 e uma aplicação para
preparar slides de forma cooperativa.
• Na réplica R1 um cliente executa “criar círculo”, e esta actualização é
propagada para R2
• Na réplica R2 um cliente executa a operação “pintar círculo” que é propagada
para R3
• A réplica R3 recebe “pintar círculo” antes de ter recebido a operação “criar
círculo”. Isto pode gerar um erro.

# Suportar clientes móveis

- ___Read-your-writes___ - cliente após escrebveu pode ler o que escreveu e não algo já atualizado.
- ___Monotonic reads___ - basicamente quando um cliente faz uma leitura, todos os dados que ler depois vão ser iguais ou mais recentes.
- ___Writes Follow Reads___ - garante os dados mais recentes escritos.
- ___Monotonic writes___ - quando um cliente faz uma escrita, os outros clientes quando receberem mais escritas deste vão ser sempre escritas mais recentes.


# Lazy Replication

Operações de escrita são propagadas em segundo plano de forma assíncrona para as réplicas.

___Batching___: divididas em lotes antes de serem replicadas.
__Assincronia__: Escritas enviadas de maneira assíncrona e não tem que se esperar pela confirmação para continuar a executar operações.
__Replicação Incremental__: Em vez de replicar todo o nó replica-se apenas o que foi incrementado.

# _Gossip Architeture_

Sacrifica a coerência mas:

- Mesmo que o cliente aceda a diferentes réplicas, assegura _monotonic reads_.
- Respeita ordem: se houve uma modificação em _m2_ que dependa de _m1_, executa _m1_ sempre primeiro.

# Algoritmo: interação cliente-réplica

1. Cada cliente tem uma _timestamp_ vetorial _prev_. É um vetor de inteiros, umpor réplica que é a última versão do cliente.
2. Cada pedido a uma réplica, cliente envia (pedido, _prev_)
3. Réplica responde com (reposta, _new_). _New_ é o estado da réplica retornado e se a réplica estiver atrasada, espera até se atualizar.
4. Cliente atualiza _prev_ com _new_ se maior.


## _Update Log_

Cliente pode receber uma modificação mas ainda estar a receber ou à espera de receber modificações cauais então a modificação não é estável. É necessário manter o _update_ até que todas as modificações sejam recebidas.

## Pedidos de leitura

Réplica verifica se _prev_ < _timestamp_:

- se sim retorna ambos os valores.
- se não fica pendente.

## Modificações

Para cada moficação que um gestor de réplicas recebe:

- Se não for duplicada, acrescenta ao _log_.
- Atualiza a sua _timestamp_.
- assim que _prev_<_timestamp_ executa a modificação.


## Garantias

Read-your-Writes: 
- session update -> write
- session check -> read

# Bayou

Operações são codificadas e têm uma ordem.
Cancelam as operações que venham numa ordem diferente aplicando uma função de recociliação.

