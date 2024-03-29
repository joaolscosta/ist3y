**Sustentabilidade** -> para o tempo de vide de um codigo, temos de ser capazes de responder a mundanças (dependencias, tecnologias, etc)

O propósito de engenharia de software é desenvolver código que faça os clientes atingir objetivos.

## Git

```js
# copia o repositório para o ambiente local
git clone <repo-url.git>

# Mostra o historico dos nós
git log [--graph] [--oneline]

# Criar ramo
git checkout -b <nome-do-branch>

# Verificar o que mudou
git status

# Adiciona as modificações a area 'staged' -> sera colocada no commit
git add <ficheiro> <ficheiro> ... <ou . para tudo>

# Guarda as mudanças na base de dados do git
git commit -m "<mensagem>"

# Envia as mudanças locais a base de dados remota
git push

# Recebe as mudanças da base de dados remota
git pull
```
### Agile Software Engeneering Methods

___Plan-driven development___ envolvido em sistemas long-lifetime.
Rigoroso e controlado software.
Mas não suporta o rápido desenvolvimento de software já que é muito delicado e envolve muitos _overheads_.

- ***Incremental Development (feature oriented)***
O desenvolvimento de produto é focado em __features__ em que se faz algo ao utilizador.
Com este tipo de desenvolvimento dá-se prioridade às features mais importantes para serem implementadas primeiro.

- ***Customer Involvement*** ***(new requeriments and sys interactions)***
Os clientes estão envolvidos durante o processo de desenvolvimento.
Prioriza os novos requerimentos de sistema e avalia as interações com o sistema.

- ***Embrace Change*** 
É esperado que os requerimentos de sistema mudem e o design que acompanhe também essas mudanças.

- ***Incremental delivery*** 
Software desenvolvido em incrementos que os clientes prentendem o que querem em cada um deles.

- ***Maintain Simplicity***
Simplicidade no desenvolvimento de software e no seu processo e sempre que possível ter mais trabalho ativo para eliminar complexidade.

- ***People not process***
Reconhecer as skills da equipa. Os developers terem a sua liberdade para fazerem o que querem.

### Agile Techniques

***User storie*** - cenário experenciado pelo user.
Estes são capturados em ___storie cards___.

Template:
__As a__ userType, __i want__ someGoal __so that__ someReason.

Pode haver um __Acceptance Criteria__ que por ponrtos especifica melhor.


- ___Test-driven development___ (escrever testes primeiro)
Novo código não parte o anterior. Não se deve mexer nele.

- ___Refactoring___
Melhorar estrutura, leitura e eficiência. Assim que se encontrar por onde melhorar, melhorar.

# SCRUM

Tem uma framework para organizar e planear.

__Product Owner__: Equipa focada no produto invés de outros interesses menos relevantes ao trabalho.

__ScrumMaster__: Guia a equipa de uma maneira efetiva de como usar o Scrum. É um coach e não um project manager.

## Key Scrum Practices

- __Product Backlog__: to-do list de items a serem implementados antes de serem atualizados antes de cada sprint.
- __TimeBoxed sprints__: Tempo fixo (2-4x por semana) de tarefas do product backlog.
- __Self-organizing teams__: Equipas trabalham por si e discutem issues e fazem decisões by consensus.

![[Pasted image 20240326172757.png]]

O __product backlog__ é o mais prioritário.

__Sprints__:  Períodos fixos em que novas features têm que ser desenvolvidas e entregues.

Durante as sprints, existem daily meetings (Scrums) para ver o progresso e atualizar a lista to-do.

Estas sprints produzem um __shippable product increment__.

1. Sprint Planning (Decidir stories e tasks)
2. Sprint Execution
3. Sprint Review

## Agile Activities

Não se sugerem nos scrums mas devemos:

- fazer testes próprios para testar o que desenvolvemos.
- procurar fazer integração no código existente e por vir.

__Validation Testing__: testes para mostrar que o software está completo.
__Defect Testing__: Para descobrir erros. Um teste de sucesso aqui é um que dá erro no sistema e aí vê-se o defeito.

__Verification__: Software corresponder à sua especificação.
__Validation__: O software tem que fazer o que o cliente pretende.

# Inspections and Testing

![[Pasted image 20240326174015.png]]

__Software Inspections__: preocupada com a análise static para descobrir problemas.
__Software Testing__: preocupada em observar o comportamento do sistema.

Estas duas são complementares.

- __Static__ - reviews e inspections.
- __Dynamic__ - tests.

## Continuos Integration (CI)

Importante para large systems em que novas features não partam as anteriores.  












