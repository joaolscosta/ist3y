O que é arquitetura de software:
- High level desing for the stakeholders.

Porque precisamos de Archichetural Patterns?
- Restringem o número de possíveis forms.

# MVC - Model-View-Controller

Separa a aprensentação e interação da data do sistema.
Este sistema é constituído por 3 componentes lógicos que interagem entre eles.

1. O compoenente Model gere a data do sistema e as operações dessa data.
2. O componente View define como a data é apresentada.
3. O componente Controller gere a interação (cliques) e passa a informação aos outros dois.

Usa-se isto quando há multiplos pontos de vista de interação ou quando ainda existem elementos desconhecidos.

Vantagens:
- Data pode mudar independentemente da sua representação.

Desvantagens:
- Pode envolver código a mais e mais complexidade,.

# Layered Architecture

Organiza o sistema em camadas relacionadas com as funcionalidades de cada camada.
Uma camada dispõe serviços à camada superior.
Então as camadas mais em baixo são core services.

Usa-se quando existem muitas equipas a trabalhar no mesmo sistema

Vantagens:
- Permite mudar completamente uma camada continuando com a mesma interface.
- Pode haver uma redundância positiva por exemplo na autenticação em que todos verificam isso.

Desvantagens:
- Pode haver problema de performance já que tem que acontecer este acesso de estar a ir às camadas mais abaixo.

# Reposotory

Toda a data é tratada numa central que é acedida pelos componentes.
Os componentes não interagem diretamente uns com os outros, vão à central.

Vantagens:
- componentes podem ser independentes já que não precisam de ter contato umas com as outras.
- uma alteração numa componente é propagada a todas.

Desvantagens:
- se a central falha já era.
- ineficiente já que tem que haver estes caminhos.


# Client-Server

Organizado em serviços e cada um tem um server.
Clientes são os utilizadores desses serviços e usam os servers para os acessarem.

Vantagens:
- Servers podem ser distribuídos na rede.

Desvantagens:
- Cada serviço que falhe já era por completo.
- Ineficiente talvez.

# Pipe and Filter

Cada componente tem um tipo de data (filter).
A data flui de um componente para outro processo (pipe).

Vantagens:
- Reutulizável e fácil leitura.

Desvatagens:
- Tem que haver parse e unparse para correponder aos tipos de datas.
- Isto aumenta o overhead e torna dificil reutilizar.



