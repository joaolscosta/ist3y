## Template View

Renderiza informação para HTML por _embedding markers_ in a HTML page.

# FrontController

Controller que gere todos os pedidos para o Web site.

Não duplica os comportamentos comuns. (segurança exemplo)

O handler pode ser estático ou dinâmico.

O handler e os comandos fazem parte do controller. Os comandos escolhem em que view usam a response.

Simplifica a configuração do webserver já que contém o handler invés de muitos Page Controllers.


# Remote Façade

Fornece uma fachada para objetos mais detalhados com o objetivo de melhorar a sua eficiência ao operar sobre uma rede de computadores

Fine-grained objects são bons a lidar com lógica complexa.

Chamadas interprocessos são ordens de magnitude mais caras que in-process.

Acess e Transactional Control são geridas por esta.

## Data Transfer Object

Um objeto que tem data e passa por processos para reduzir número de chamadas de métodos.

Não é um object, é um _data object_.

Precisam de ser serialized mas algumas já suportam (REST (JSON))