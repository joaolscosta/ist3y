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

Existe um primário que está a trabalhar e secundários que estão em _standby_ à espera que o primário falhe para um deles continuar no mesmo estado e não perder informação.

> [!NOTE] Basicamente
> Os estados guardados pelos vários processos que falharam devem estar
mutuamente coerentes.

## Para a frente:

- Várias réplicas do processo.
- Quando uma réplica é alterada todas as outras também o têm de ser.
- Se uma réplica falha os clientes podem usar outra réplica.

Aqui todas as réplicas estão a trabalhar. Trabalham em simultâneo e distribui-se a carga. As solicitações chegam a todas as réplicas e combinadas respondem.


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

Garantem a entrega de mensagens ordenadas.

Retransmitem uma mensagem até que seja confirmada pelo destinatário.
Usam-se _ids_ e não se entregam mensagens com _id_ inferior a uma que já tenha sido entregue.

#### Difusão Fiável

Ou todos os destinatários recebem ou nenhum recebe.

Existe a __regular__ e a __uniforme__.

###### Regular

- Mensagem _m_ enviada para processos { _p1, p2, ..., pn_ } de um destes processos.
- Validade: se processo _pi_ envia _m_ então entregará mais tarde.
- Não-duplicação: nenhuma mensagem _m_ é entregue mais do que uma vez.
- _Não-criação_: se uma mensagem é entregue então foi enviada por um processo correto.
- Acordo: Se um processo correto entrega a mensagem então todos os processos corretos também a entregarão.

1. Emissor envia mensagem usando canais perfeitos para todos os membros do grupo.
2. Quando um outro recebe entrega-a à aplicação e reenvia para todos os membros do grupo.


> [!NOTE] Resumindo
> Um nó envia a mensagem a todos os outros nós de um dado grupo. Os que já receberam mensagem reenviam a mensagem para os que não receberam e continua este processoa até que todos recebam.


#### Difusão Fiável Uniforme

Só muda:

- Acordo: Se um processo entrega mensagem então todos os processos corretos enviam.

1. Emissor envia mensagem usando os canais perfeitos para todos os membros do grupo.
2. Quando um outro recebe reenvia para todos os outros.
3. Quando um receber a mensagem _m_ de _f_ membros entrega a mensagem à aplicação.

- _f < N/2_


> [!NOTE] Resumindo
> Nesta é o mesmo processo mas em vez de ser apenas de um dado grupo é para todo o sistema.


#### Difusão Atómica

- Se uma réplica recebe o pedido todas as réplicas recebem o pedido.
- Todas as réplicas recebem os pedidos pela mesma ordem.

# Algoritmos em caso de Falhas

### Ordem total baseada em sequenciador

- Mensagens enviadas para todas as réplicas usando um algoritmo de difusão fiável.
- Uma das réplicas é eleita líder, decide a ordem e envia esta info para as réplicas restantes.
- Quando existe uma falha por exemplo do líder pode acontecer um __estado incoerente__ (mensagens não ordenadas pelo líder, etc).

# Sincronia na Vista

> [!NOTE] Informalmente
> Permite mudar a filiação de um grupo de processos de uma orma que facilita a tolerância a faltas.

- Podem ser adicionados novos membtos a um grupo de processos.
- Um pode sair voluntariamente ou ser expulso caso falhe.

Exemplo:
• V1 = {p1, p2, p3}
• V2 = {p1, p2, p3, p4}
• V3 = {p1, p2, p3, p4, p5}
• V4 = {p2, p3, p4, p5}

Um processo é __correto__ se faz parte da lista _vi_ e da lista _vi+1_.

Se uma mensagem m é entregue à aplicação depois da vista Vi ser
entregue e antes da vista Vi+1 ser entregue, a mensagem m diz-se
que foi entregue na vista Vi.


#### Difusão Fiável Síncrona na vista

- Se um processo correto _p_ na vista _Vi_ envia uma mensagem _m_ na vista _Vi_,
então _m_ é entregue a _p_ na vista _Vi_
- Se um processo entrega uma mensagem m na vista Vi, todos os processos
correctos da vista Vi entregam m na vista Vi



> [!DEFINITION] Corolário
> Dois processos que entregam a vista Vi e a vista Vi+1 entregam exactamente o
mesmo conjunto de mensagens na vista Vi.



- Para mudar a vista é necessário obrigar as aplicações interromper temporariamente a transmissão de mensagens de forma a que o conjunto de mensagens a entregar na vista seja finito
- Para além disso, é necessário executar um algoritmo de coordenação para garantir que todos os processos correctos chegam a acordo sobre:
- Qual a composição da próxima vista
- Qual o conjunto de mensagens a entregar antes de mudar a vista


# Primário-secundário (agora concretizado)

Réplicas usam sincronia na vista para lidar com falha do primário:
• Quando o primário p, algum tempo depois será entregue nova vista sem p
• Quando nova vista é entregue e o anterior primário não consta nela, os restantes processos elegem o novo primário
• Pode ser o primeiro membro da nova vista
• Ou podemos usar outro algoritmo de eleição de líder
• O novo primário anuncia o seu endereço num serviço de nomes (para que os clientes o descubram)
Primário usa difusão fiável uniforme síncrona na vista para propagar novos estados aos secundários
• Só reponde ao cliente quando a uniformidade está garantida

# Replicação de máquina de estados (agora concretizado)

- Processos usam sincronia na vista
- Clientes usam difusão atómica síncrona na vista para enviar pedidos
para todas as réplicas