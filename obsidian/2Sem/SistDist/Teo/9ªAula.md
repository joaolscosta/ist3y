# Difusão atómica usando consenso


> [!NOTE] O que pretende?
> Que todas as operaçẽos se executem ou que nenhuma se execute.


# Máquina de Estados Replicada

Clientes usam difusão atómica para enviar pedidos para todas as réplicas.

Réplicas receberem todas pela mesma ordem e processam pela difusão atómica.

Réplicas respondem aos clientes.

# Sincronia na Vista com Consenso

Mudança da vista Vi para Vi+1:

- Recolher todas as mensagens entregues na vista vi.
- Propor um tuplo: vi+1 = <memebros de vi+1, conjunto de mensgaens entregues em vi>.
- Esperar resultado do consenso.
- Entregar mensagens em falta.
- Entregar nova vista.

1. Cada processo pi tem um registo hi de todas as mensagens que já entregou numa dada vista.
2. Quandos se inicia a mudança de vista de vi para vi+1, uma mensagem "view-change (saídas, entradas)" é enviada para todos os processos da vista vi.
3. Quando um processo recebe a "view-change" párade entregar novas mensagens, inicia vi+1= vi-saídas+entradas, inicia hj a null para todos os processos pj e envia hi para todos os processos na vi+1.
4. Cada processo recebe todos os valores de hj de todos os processos pj na vi.

5. Se um processo pi não recebe hj de um processo pj, suspeita que pj falhou, retira pj da vi+1 e coloca hj={}.
6. Quando pi tem todos os valores de hj <> null (isto é, se já recebeu hj de pj ou se assume que pj falhou) define o conjunto de mensagem a entregar M-Vi como a união de todos os hj recebidos e inicia o consenso propondo <Vi+1, M Vi>-
7. O resultado do consenso define a nova vista e o conjunto de mensagens a entregar na vista anterior.

