# Cortes Coerentes
##### Capturar um estado global de um SD

É útil para:
- guardar o estado de forma a recomeçar a aplicação em caso de falha.
- verificar interbloqueios.
- verificar se foram violadas propriedades.

É chato porque os relógios não estão todos sincronizados então não existe um tempo global.

O estado da aplicação tem:
- estado de cada processo;
- possíveis mensagens em trânsito.

> [!DEFINITION] Definição
> Corte é coerente se para cada evento o corte inclui todos os eventos que acontecem __antes__ desse evento.

# Eleição de Líder

## Bully

Processos com maior hierárquia tendem a assumir a liderança.

1. Cada processos com SD está sempre a monitorizar os outros. Se um processo detetar que líder falhou, inicia eleições.
2. Quando deteta isso manda uma mensagem de eleição para todos os processos com _ID_ mais alto do que ele.
3. Os processos que têm _ID_ mais alto que o que mandou a mensagem respondem com _OK_. Se um processo não receber _OK_ dentro de um dado período de tempo, assume que é o candidato com a maior hieráriquia e declara-se líder.
4. Quando se declara notifica todos os processos e estes atualizam as suas listas de líders.

![[Pasted image 20240227215758.png]]

# Tentar guardaro estado global sem parar o sistema?

Partimos do princípio que:

- processos não falham.
- rede garante entrega ordenada (FIFO).
- qualquer processo pode inciar um _snapshot global_ a qulquer momneto guardadndo o seu estado local.

__Quando um processo guarda o seu estado__ -> envia um marcador a todos os outros processos. Depois de enviar marcadores a todos os processos pode continuar a enviar e receber mensagens.

__Quando um processo recebe uma mensagem de um marcado__ -> se este processo ainda não guardou o seu estado, então guardar o seu estado local.

# NÃO ENTENDO SLIDE 26 E 27 dos slides do TAGUS

# Algoritmo de _Chandy-Lamport_

Parte-se do princípio que:
- não há falhas dos canais de comunicação e dos processos.
- canais unidirecionais, ordem FIFO.

Qualquer processo pode iniciar um _snapshot global_ a qualquer momento.
Durante o _snapshot_ __podem__ continuar a mandar e receber mensagens.

Aqui diferente do anterior, o __estado do canal também é guardado__.

Para um dado canal (unidirecional), se o recetor salvaguardou o seu estado local __antes__ do emissor ter feito o mesmo, __é necessário salvaguardar as mensagens recebidas nesse canal entre os dois instantes__.

Nenhum processo decide que termina.
Todos os processos vão receber um marcador (no máximo N-1) e gravar o seu estado.

Mais tarde um servidor central pode obter os estados locais coerentes para construir o _snapshot global_.




