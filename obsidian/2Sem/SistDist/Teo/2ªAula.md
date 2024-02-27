## Relógios Físicos

Mesmo que no mesmo instante os mesmos relógios tenham o mesmo valor, com o passar do tempo apresentam diferenças chamadas ___skew___.
Daí precisar-mos de sincronização.

Sincronização:

1. ler relógios
2. aplicar função/algoritmo para ler outro nó estimar o tempo a que se quer colocar (moda, média)
3. podemos considerar relógios melhores apenas se tivermos info disso
4. amortização/convergência

Para se corrigir dois relógios se um estiver mais atrasado que o outro, ele não se corrige imediatamente, amortiza-se:

![[amortização]]

Um relógio pode até receber uma mensagem antes mas para sincronização tem uma hora mais tarde em que de facto envia a mensagem:

![[later time]]

#### Sincronização Interna

Podem estar sincronizados entre si mas desfasados para o exterior. Arranjam forma dentro de se orientar.

Onde __não existe__ tolerância a faltas.
Cada processo lê o valor de todos os outros processos, aplica-se função e atrasa-se ou adianta-se.

Onde __existe__ tolerância a faltas.
Temos que descobrir como escolher que valores considerar.

#### Sincronização Externa

Quando 1 ou mais nós têm acesso ao tempo real.

Onde __não existe__ tolerância a faltas.
Um processo acessa ao UTC para outros processos lerem esse relógio e atrasarem-se ou adiantarem-se para se acertarem.

Onde __existe__ tolerância a faltas.
Se _f_ processos falharem e fornecerem valores errados de relógio, configuram-se _2f+1_ processos com acesso ao _UTC_, outros processos lêem o valor de relógio desses processos e descartam-se os _f_ mais altos e mais baixos. Escolhem-se os de sobra.

### Leitura Remota de Relógios

Tentar descobrir os tempos dos outros relógios já é tramado.
Existem incertezas.

![[2ªAula 2024-02-21 21.06.44.excalidraw]]

`Mensagem de resposta = Message Delay = t4 - t3`

P1 estima valor de relógio do P2 no instante t4 é `X + Message Delay`.

O problema é que não que consegue saber ao certo t3 então vai haver um erro
### Relógio de Lamport

Lógico.
Não reflete tempo real mas sim a ordem dos eventos.
Atribui a cada evento um carimbo de tempo (inteiro). Assim um evento A precede B em que o tempo de A é menor que B.

Se um relógio der trigger no tempo 30. O próximo será num tempo obrigatoriamente posterior a esse.

1. Cada processo com contador local.
2. Quando envia ou recebe mensagem incrementa.
3. Antes de enviar mensagem um processo cola o seu contador à mensagem e é escolhido o maior contador entre os dois mais um.

A ordem pode não ser a correta ao longo do tempo.


## Algoritmo de Cristian

Processo cliente p ajusta o seu relógio para `x + Tround/2`.
Erro de +- (Tround-2min)/2.
Se valor de min muito pequeno considera-se zero.

![[Pasted image 20240221211747.png]]


1. **Cliente solicita tempo**: O cliente envia uma solicitação ao servidor pedindo o tempo atual.
    
2. **Servidor responde**: O servidor responde à solicitação, enviando seu tempo atual de volta ao cliente.
    
3. **Cliente calcula diferença**: O cliente registra o tempo que enviou a solicitação e o tempo que recebeu a resposta. Ele calcula a diferença entre esses tempos para estimar o atraso da comunicação.
    
4. **Sincronização do relógio**: O cliente ajusta seu relógio local somando metade da diferença calculada ao tempo recebido do servidor.
    
5. **Limitações**: O algoritmo assume que o atraso de comunicação é simétrico e constante, o que pode não ser sempre o caso em redes reais.

#### Resumindo:

O servidor deve escolher o relógio com menor RTT para ter melhor precisão.

O valor com que deve acertar é `tempo + RTT/2`.

A precisão é `RTT / 2`.

Se soubermos o tempo mínimo de envio de uma mensagem `(RTT/2) - tempoMinimo`.

## Algoritmo de Berkely

Sincronização interna.
Servidor mestre lê valores dos escravos (usa _round trip time_ para estimar valores).
Obtém média dos valores.
Envia os ajustes para cada um dos escravos.
Se mestre falha elege-se um novo.

## Programa Idempotente

Se o aplicarmos várias vezes ao mesmo estado inicial obtermos sempre o mesmo estado final.


# _Network Time Protocol_ - NTP

Permite clientes da internet sincronizarem os seus relógios com o UTC.
Tem robustez e é escalável dada a redundância dos caminhos.

![[2ªAula 2024-02-21 21.27.32.excalidraw]]

Nível 1 - é o servidor primário ligado à UTC.
Nível 2 - servidores secundários sincronizados com o primeiro.
Nível 3 - pcs pessoais.

Um pc que perca a ligação ao UTC fica secundário.
Um pc que perca ligação ao seu primário procura outro.

__Multicast (rede LAN)__: Servidor faz LAN para outros servidores que se ajustam com um dado delay.

__Invocação Remota (Cristian)__: Servidor aceita pedidos de outros. Responde com tempo atual.

__Simétrica__: Pares de servidores trocam mensagens que contêm info sobre o tempo. Para maior precisão. É aqui que acontece a cena de a mensagem ser enviada x tempo mais tarde para sincronização.

# Relógios Lógicos

# Relógios Vetoriais

1. Cada processo com vetor de relógio inicializados a zero com o tamanho do número de processos.
2. Cada vez que se manda ou recebe mensagem o seu relógio incrementa.
3. Antes de mandar mensagem, atualiza o seu vetor, colando à mensagem.
4. Quando o outro recebe a mensagem, atualiza o seu relógio comparando a mensagem recebida e o seu vetor.









