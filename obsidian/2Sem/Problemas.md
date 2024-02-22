
1.
UDP na camada de transporte: eficiente e usado na comnicação 1 para n mas não garante fiabilidade e pacotes podem ser perdidos, duplicados ou reordenados.

2.
Características de um canal de comunicação de um socket do tipo stream: canal com ligação (é isto que quer dizer stream, estabelece ligação antes de enviar ou receber dados), bidirecional, fiável, etc.

3.
Bro

4.
1000 porque a semântica é que é oferecido pelo menos uma vez.

5.
increment

7.

__SOAP__: 
- XML
- específicação rígida das mensagens
- pode ser usado sobre diferentes protocolos de transporte
- menos flexível mas é consistente

__REST__:
- arquitetura leve e flexível
- não mantém states entre solicitações
- menos formal

__gRPC__:
- HTTP2
- usa Protocol Buffers (protobuf) para definir mensagens
- suporta streaming bidirecional
- pode ser usado sobre HTTPS para garantir confiabilidade, autenticidade e integridade.
- formato mais eficiente que Web Services em JSON
- serviço de nomes -> DNS

10.
mensagens e funções romotas em _protobuf_ para o RPC da questão 4.

```JSON
message requestIncrementar {
	int32 incremento = 1;
}

message replyIncrementar {
}

message requestNumPessoas {
}

message replyNumPessoas {
	int32 = resultado = 1;
}

service praia {
	rpc incrementar(requestIncrementar) returns (replyIncrementar);
	rpc obter_num_pessoas(requestNumPessoas) returns (replyNumPessoas);
}
```

11.
Tempo de propagação + RTT não?
A solução está a considerar só o tempo de propagação.

12.
O C que está no meio continua com esse tempo e os outros somam e subtraem para ficarem com o tempo do C.

13.
Ajustes que os processos fazem e os seus erros.

R1.2:
220 + ((216-200)/2) - 216 = +12
erro = ((216-200)/2) = +-8 (enviado - pedido / 2)

14.
pior caso = 8 + 7 = 15

15.
É melhor ter um processo mestre.

16.
Relógios vetoriais, A é concorrente com B.

17.
[3,1]

18.
?

19.
?

20.



