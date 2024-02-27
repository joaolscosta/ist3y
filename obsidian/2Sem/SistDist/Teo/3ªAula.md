# Exclusão Mútua

Vários processos usam os mesmos recursos e tem que se escolher qual processo deve aceder à vez a esses recursos.

## Solução Centralizada (cliente-servidor)

1. Aqui existe um mestre que coordena o acesso a recursos compartilhados.
2. Qualquer processo que queira aceder ao conteúdo compartilhado tem que fazer o pedido (envio de uma chave) ao mestre.
3. O mestre decide a ordem com que acedem. Pode ser o primeiro a pedir é o primeiro que o tem ou então tem regras mais específicas para a ordem. Este acesso acontece sempre à vez.
4. Quando termina de usar notifica o mestre para que mande vir o próximo ou seja, envia a chave ao metre para este enviar para o próximo cliente.
5. O mestre pode falhar e aí o sistema bloqueia e elege-se um novo.


## Solução Descentralizada
### Algoritmo de _Ricart y Agrawala_

1. Cada processo tem duas variáveis (uma para guardar o processo que solicitou o pedido, uma _timestamp_ e outra para as respostas de outros pedidos)
2. Quando um processo quer aceder a um dado recurso,  envia mensagem a todos os processos com o seu _timestamp_.
3. Quando um processo recebe uma mensagem compara os _timestamps_. Se na altura que recebe já não quer o dado recurso passa logo ao próximo, caso contrário regista na lista de respostas.
4. Quando já recebeu todas as respostas pode conceder acesso ao recurso (enviar a chave diretamente a outro processo) ou aceder ele se o seu _timestamp_ for menor que todos os outros dos outros processos.
5. Quando termina de usar, informa todos os outros processos para que atualizem os seus estados.

## Solução P2P
Não existe nenhum líder, todos os processos processos colaboram.

## Algoritmo de Maekawa

1. Processos organizados em grafo. Cada nó representa um processo e as arestas são os processos que podem aceder ao conteúdo partilhado. Não pode haver nós sem ligações.
2. A cada nó é atribuído um conjunto de controlo de acesso (subconjunto de nós chamado __quóruns__). Assim cada processo tem acesso a outro processo que tem acesso a outro processo evitando bloqueios.
3. Quando um processo quer aceder a um recurso partilhado pede acesso a todos os processos daquele conjunto de controlo de acesso.
4. Só pode aceder quando receber confirmação de todos os nós que fizerem parte do conjunto de controlo de acesso.
5. No fim larga e notifica todos do conjunto de controlo de acesso.

Assim não há um processo que receba todos os pedidos, distribui carga.
Um processo pode pertencer a mais de um quórum.

__Propriedade fundamental__:
Qualquer par de quóruns intercepta em pelo menos um processo, logo 2 pedidos
concorrentes nunca conseguem, cada um, receber os votos de quóruns inteiros.

## Falhas:

- __Centralizada__: não tolera a falha do coordenador,mas tolera falha de cliente que não detenha nem tenha pedido o token
- ___Ricart&Agrawala___: não toleram a falha de qualquer processo
- ___Maekawa___: tolera a falha dos processos que não esteja no quórum
