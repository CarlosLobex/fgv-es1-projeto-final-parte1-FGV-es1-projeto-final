# Planejamento do Processo de Desenvolvimento — ESM Forum

## Processo Escolhido: Kanban

---

## 1. Justificativa da Escolha

Para o desenvolvimento das novas funcionalidades do ESM Forum, optou-se pelo **Kanban** em vez do Scrum. A seguir, estão as razões fundamentadas nos conceitos de processos ágeis:

### 1.1 Características do Kanban

O Kanban é um método ágil baseado no **fluxo contínuo de trabalho**, com foco na visualização do processo e na limitação do trabalho em progresso (WIP — *Work In Progress*). Seus pilares são:

- **Visualização do fluxo:** todo o trabalho é representado em um quadro com colunas que refletem o estado atual de cada item.
- **Limitação de WIP:** restringe-se o número de tarefas simultâneas por coluna, evitando sobrecarga e gargalos.
- **Gestão do fluxo:** o time monitora e otimiza continuamente o tempo de ciclo de cada tarefa.
- **Melhoria contínua:** o processo é ajustado progressivamente com base no que é observado no quadro.

Diferentemente do Scrum, o Kanban **não utiliza sprints com duração fixa**, iterações com reuniões obrigatórias (daily, review, retrospectiva) nem papéis definidos (Scrum Master, Product Owner). O trabalho é puxado conforme a capacidade da equipe.

### 1.2 Por que Kanban é adequado para este projeto?

| Critério | Justificativa |
|---|---|
| **Tamanho da equipe** | Projeto individual (ou dupla), sem necessidade de coordenação complexa de papéis como no Scrum |
| **Natureza das tarefas** | As 5 funcionalidades têm escopo bem definido e podem ser desenvolvidas de forma independente, sem agrupamento forçado em sprints |
| **Flexibilidade** | O prazo é fixo (3 semanas), mas a ordem de execução pode ser ajustada conforme a complexidade encontrada durante o desenvolvimento |
| **Ausência de cadência rígida** | Sem reuniões de planejamento de sprint ou retrospectivas formais, o Kanban se adapta melhor ao contexto acadêmico individual |
| **Rastreabilidade** | O GitHub Projects com Kanban permite visualizar exatamente o status de cada funcionalidade a qualquer momento |

> Em contraste, o Scrum seria mais adequado para **equipes maiores** com entregas frequentes aos stakeholders e necessidade de cerimônias formais de alinhamento — o que não se aplica a este contexto.

---

## 2. Estrutura do Board Kanban no GitHub Projects

O board foi configurado com as seguintes colunas:

### Colunas

| Coluna | Descrição | Limite WIP |
|---|---|---|
| **Backlog** | Funcionalidades planejadas ainda não iniciadas | Sem limite |
| **Em Andamento** | Funcionalidades ativamente sendo desenvolvidas | Máx. 2 |
| **Em Revisão** | Código finalizado aguardando revisão e testes | Máx. 2 |
| **Concluído** | Funcionalidades finalizadas, testadas e documentadas | Sem limite |

### Fluxo de Trabalho

```
Backlog → Em Andamento → Em Revisão → Concluído
```

Um card só avança para a próxima coluna quando todos os critérios de aceitação da coluna atual forem satisfeitos.

---

## 3. Cards das Funcionalidades (Priorizados)

Os cards foram priorizados com base em três critérios:
1. **Valor para o usuário** — impacto direto na experiência de uso
2. **Complexidade técnica** — esforço necessário de implementação
3. **Dependências** — se a funcionalidade depende de outra para funcionar

| Prioridade | Funcionalidade | Justificativa |
|---|---|---|
| 🥇 1 | **Busca de perguntas por palavra-chave** | Alta utilidade imediata; baixa complexidade; não depende de outras features |
| 🥈 2 | **Categorização de perguntas (tags)** | Organiza o conteúdo; impacto transversal nas demais funcionalidades |
| 🥉 3 | **Sistema de votação (upvote/downvote)** | Engajamento dos usuários; requer ajustes no modelo de dados |
| 4 | **Perfil de usuário com histórico** | Alta complexidade; requer autenticação e queries mais elaboradas |
| 5 | **Notificação de novas respostas** | Maior complexidade técnica; pode ser implementado após as demais |

---

## 4. Referências Conceituais

- VALENTE, Marco Tulio. *Engenharia de Software Moderna*. Cap. 2 — Processos de Desenvolvimento de Software.
- ANDERSON, David J. *Kanban: Successful Evolutionary Change for Your Technology Business*. Blue Hole Press, 2010.

---

*Documento preparado para o Projeto Final de Engenharia de Software — Parte 1.*
