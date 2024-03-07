
Se duas operações partilham alguma parte do tempo em que estão a ser executadas são __concorrentes__, senão são anteriores ou posteriores.

Um sistema replicado diz-se __linearizável__ se:
- se _op1_ acontece antes de _op2_ em tempo real então em virtual _op1_ aparece sempre antes.
- todos os clientes leem as mesmas leituras

# Registos
Ler escrever. Muitos podem ler mas so um escreve.


### Atomic
É equivalalente à linearizabilidade. As escritas e leituras ocorrem num ponto entre o inicio e fim da operação.

### Regular
Se uma leitura anão for concorrente com escrita, lê último valor escrito.
Se sim lê ultimo ou esse.

### Safe
Se for concorrente pode lançar um valor arbitrário.

## Continuando

Cada processo tem uma cópia do registo.
Cada registo tem um tuplo: <valor, versão>

# ABD

__Atomicidade__: Se estiverem a acontecer várias transações ou acontecem todas ou nenhuma porque são isoladas.
__Consistência__: Os dados têm que ter sempre os mesmos estados ou se precisarem de mudar têm que continuar coerentes.
__Durablidade__: Permanência dos dados.

## Registo Regular (só com um escritor)

Escrita:

1. W incrementa número da versão e envia tuplo para todos os processos.
2. Ao receberem, atualualizam a cópia do registo (se a versão for superior) e envia confirmação.
3. Acaba esta escrita quando receber maioria.

Leitura:

1. O leitor envia mensagem a todos a pedir o tuplo mais recente.
2. Cada um envia.
3. Quando receber maioria retorna o mais recente e atualiza-se caso necessário.

# Espaço de Tuplos

Aqui pode haver várias cópias do mesmo tuplo.
Uma escrita é `take` e `put`.

O `take` é sincronizado e bloqueante, requer um `compare-and-swap`.

Tolerância a faltas tem uma filiação que mantém o grupo de réplicas. Quando uma falha a filiação do grupo é alterada.

# Xu-Liskov
Tolerância a falhas forte.
Operações executadas de maneira consistente para todos os nós.

1. Tem uma ordem sequencial que deve ser respeitada.
2. Se uma opA precede opB num nó, para todos os outros têm  que saber disto mesmo que opB se execute primeiro.
![[Pasted image 20240307111828.png]]

