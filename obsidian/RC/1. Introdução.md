### Internet

É uma rede de redes. 
Consiste em redes locais conectadas a um ISP (Internete Service Provider). As redes privadas são denominadas _Intranets_.

### Protocolo

Define um formato e ordem de mensagens enviadas e recebida e também ações.

![[Pasted image 20231118112456.png]]


#### Residencial Acess: Point to point

__Modem__: Can't surf and phone at the same time e not always on. Analog. Connection to ISP.
__DSL__: Digital subscriber line.
__Cable Modem__: HFC (Hubrid Fiber Coaxial) Casa partilha acesso ao router.

### Meios de Transmissão

##### Meio Físico

__Data__ (packs de bits): propagam entre transmissores e recetores.
__Physical Link__: O que há entre esses transmissores e recetores.

2 tipos de physical media:
__Guided/ WIRED__: em cobre, fibra ou coaxials.
__Unguided/ WIRELESS__: prop freely.

__Cobre__: RJ-45. Diferentes categorias:
- Categoria 3 - Cabos de telefone e rede até 10Mbps.
- Categoria 5 - Até 100Mbps.
- Categoria 6 - Até 1Gbps
- Categoria 7 - Até 10Gbps ou 100Gbps, se distância < que 15m.

__Cabos Coaxiais__: Bastante isolados, evitam enterferências eletromagnéticas.

__Fibra Ótica__: Alta velocidade. Não afetada por interferências ou frequências. Muito frágil.

##### Meio Wireless

É bidirecional e usa antenas. 
Usam-se APs( _Acess Points_ ) para transmitir sinal de rede.
Problemas de uso apenas wireless:

- __Reflexão__ -  Enviado em muitos sentidos e um sinal pode ir parar ao mesmo sítio que outro. Se acontecer isto pode haver ruído ou cancelamento.
- __Obstrução por Objetos__ - Objetos como metal podem absorver diminuindo a intensidade.
- __Interferência__ - Rádios, micro-ondas, etc podem também interferir.



**Modelo cliente/servidor:** O _host_ do cliente faz um pedido e recebe um serviço de um servidor, que se encontra sempre ligado, como por exemplo um _browser_ no lado do cliente e um servidor _web_.

**Modelo _peer to peer_:** Existe um uso mínimo ou inexistente de servidores dedicados, como é, por exemplo, o caso do Skype e do BitTorrent.

#### Circuit Switching

Os recursos da rede divididos em partes alocada, havendo um canal para cada host. Não há partilha de recursos.
A largura de banda pode ser divida em frequências (FDM) ou ao longo do tempo (TDM).

###### FDM (Frequency division multiplexer)

Divisão feita na frequência.
Usam-se vários canais/frequências para a mesma fibra ótica/cabo. Cada um usa uma das frequências
![[Pasted image 20231118121058.png]]

###### TDM (Time division multiplexer)

Divisão feita no tempo.
Cada host pode usar a fibra durante um específico tempo.
![[Pasted image 20231118121233.png]]
Desvantagens: o aluguer de um canal exclusivo é caro. É um canal pequeno e não tem tanta performance.

#### Packet Switching

Em vez de dividir os recursos da rede, estes são partilhados e a comunicação é feita em pacotes. Cada pacote utiliza o tamanho total da largura de banda e seja qual for o recurso quando necessário. Um host pode ter o canal todo para ele caso não existam outros.

Sistema de encaminhamento da internet é feito de maneira a que ada pacota possa ser enviado por caminhos diferentes. Pode ter problemas:

- A procura pode exceder rescursos disponíveis.
- Pode haver pacotes à espera de outros na fila ou perdas (_Congestion_).
- Cada pacote por ser recebido na totalidade antes de ser encaminhado (_Store and forward_).

###### Store and Forward

Em cada link, o pacote tem que chegar por inteiro ao router antes de ser transmitido o próximo link.
![[Pasted image 20231118123912.png]]
O router precisa de receber o pacote todo:

- para verificar se houve erros na transmissão
- para calcular qual o melhor caminho por onde reencaminhar já que pode haver caminhos congestionados.

Para calcular o tempo que um pacote demora a chegar ao seu destino tem que se somar o tempo de propagação e o tempo de transmissão.

O tempo de transmissão é calculado a partir da velocidade de transmissão e o tamanho do pacote.
O tempo de propagação é calculado a partir da velocidade a que um sinal viaja e a distância entre 2 pontos.

O tempo de propagação não muda se mudarem os tamanhos dos pacotes ou o número de pacotes a transmitir.

__Transmission delay__:
- _R_ link bandwith (bps)
- _L_ packet length (bits)
- Time to send bits into link = L/R

__Propagation delay__:
- _d_ length of physical link
- _s_ propagation speed in medium
- Propagation delay = d/s

__Nodal delay__:
d nodal = d proc + d queue + d trans + d prop

dproc: processing delay
dqueue: depends on congestion
dtrans: L/R
dprop: d/s

__Queueing delay__:
- _R_ link bandwith
- _L_ packet length
- _a_ average packet arrival rate
- Traffic intesity = L.a/R
- Se = 0, average queueing delay small.
- Se = 1, delay very big.
- Se > 1, more work arriving than can be serviced.
#### Arquitetura em Camadas
Cada camada fornece um serviço às camadas de cima.

#### Packet Loss

Queue buffer anterior tem capacidade finita.
Um pacote que chega a uma fila que já está cheia é perdido.
Um pacote perdido é retransmitido.

#### Throughput

(Bits/time unit) at which bits are transferred between sender and receiver.

#### Layers

Cada layer implementa um serviço. Através de internal-layer actions. Relying on services provided by layer below.

__Protocol__: Regras seguidas entre duas peer enteties, assegurando o sucesso da data exchange.
__Service__: Each layer oferece um serviço de layer abaixo e usa serviços feitos pelo layer abaixo.

__Peer enteties__ do mesmo layer executam distributed algorithm.
__Protocols__ definem as regras de comunicação entre peer enteties.

###### Service Interface
Especifica quais serviços são oferecidos pelo layer n para o layer n+1.

##### Internet Protocol Stack

- __Application__ - suport network apps
- __Transport__ - process-process data transf (TCP / UDP)
- __Network__ - reencaminhamento  de datagrams da origem ao destino (IP)
- __Link__ - transferência de dados entre elementos de rede vizinhos (wifi, PPP)
- __Física__ - Bits no cabo.



