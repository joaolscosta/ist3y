
Sistema usas várias máquinas __concorrentes__ para prestar um serviço ao mesmo tempo.
Maior escalonamento que seviços.
Garante replicação, se um falha outros continuam.

2 maneiras de programar sistemas concorrentes:

1. __Troca de Mensagens__: Geralmente por _remote procedure call_.
2. __Partilha de Memória__: Um ponto de memória é partilhado.

Geralmente o utilizador não vê as mensagens e sim o espaço partilhado de memória.

## _Remote Procedure Call - RPC_


> [!NOTE] Definição
> Comunicação entre processos que permite a um programa de um PC chamar um procedimento em outro espaço de endereçamento.
>  

Basicamente chamar uma função que vai ser executada em outro servidor. 
Permite que um aplicativo chame procedimentos ou métodos em outro aplicativo remoto como se fossem locais.

## _Interface Definition Language - IDL

Define comunicação entre cliente e servidor.
No caso do gRPC a linguagem é ___Protobuf___.

```protobuf
program counter {
	version c_version {
		void limpa(void) = 0,
		void mc(int) = 1,
		int consulta(void) = 2, // o numero define o indice do metodo
	} = 1
} = 45484
```
É como se fosse um .h e todos os clientes e servidores têm que usar o mesmo formato.

## SD e Concorrência Centralizada

As coisas podem falhar como nunca ser recebido algo enviado e como se resolve?

Uma das soluções é o código de melhor esforço que só envia e não quer saber se chega ou não. (usado para coisas menos importantes)

Outra solução é enviar pelo menos uma veze usar _timeouts_.

A última solução é enviar apenas uma vez mas com identificadores _UID_ nos pedidos e o servidor guarda a resposta aquele pedido (_log_)

## Serviço de Nomes - _nameserver_

Envia-se uma _string_ `www.exemplo.com` e recebe-se um `IP`. ___DNS__ é um exemplo.

### _Load Balancing_

Escolher dos servidores qual vai responder ao pedido.
Pode escolher-se um ao calhas ou escolher o mais próximo ao usuário de modo a reduzir a latência.

## DNS

Resolve um nome através de uma resolução iterativa ou recursiva.

Em cada organização existe um servidor que faz a resolução e guarda os dados.
Funciona como cache e pode gerar problemas de coerência.

Usa nomes hierárquicos.












