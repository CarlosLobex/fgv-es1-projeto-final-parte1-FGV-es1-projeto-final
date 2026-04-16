# Pair Programming no ESM Forum

## Introdução

**Pair Programming** é uma prática do Extreme Programming (XP) em que dois desenvolvedores trabalham juntos em um único computador. Um assume o papel de **driver** (quem escreve o código) e o outro de **navigator** (quem revisa, questiona e pensa estrategicamente). Os papéis se alternam regularmente.

Os benefícios incluem: detecção precoce de bugs, difusão de conhecimento entre a equipe, melhor qualidade do design e maior comprometimento com boas práticas.

---

## 1. Contexto: Projeto Individual

Este projeto está sendo desenvolvido individualmente. Portanto, a seguir será descrito como o pair programming **seria aplicado** caso houvesse um par disponível, conforme solicitado pelo professor.

---

## 2. Estratégia de Aplicação

### 2.1 Ferramenta Principal: VS Code Live Share

A ferramenta escolhida seria o **[VS Code Live Share](https://visualstudio.microsoft.com/pt-br/services/live-share/)**, por ser:

- Integrada ao editor mais utilizado no projeto
- Gratuita e de fácil configuração
- Capaz de compartilhar terminal, servidor local e edição em tempo real
- Compatível com extensões como ESLint e Prettier, mantendo a qualidade do código durante a sessão

### 2.2 Ferramenta de Comunicação: Discord

Para comunicação de voz durante as sessões seria utilizado o **Discord**, com as seguintes configurações:

- Canal de voz dedicado ao projeto
- Compartilhamento de tela como alternativa ao Live Share
- Chat para trocar links, snippets e referências durante o desenvolvimento

---

## 3. Rotação de Papéis

A rotação seria feita a cada **25–30 minutos**, seguindo a técnica Pomodoro adaptada:

| Ciclo | Driver | Navigator | Duração |
|---|---|---|---|
| 1 | Desenvolvedor A | Desenvolvedor B | 25 min |
| Pausa | — | — | 5 min |
| 2 | Desenvolvedor B | Desenvolvedor A | 25 min |
| Pausa | — | — | 5 min |
| 3 | Desenvolvedor A | Desenvolvedor B | 25 min |

**Responsabilidades de cada papel:**

**Driver:**
- Escreve o código ativamente
- Verbaliza o raciocínio em voz alta
- Foca na implementação linha a linha

**Navigator:**
- Revisa o código em tempo real
- Identifica possíveis erros e casos de borda
- Pensa na estratégia maior (arquitetura, padrões, YAGNI)
- Consulta documentação quando necessário

---

## 4. Aplicação por Funcionalidade

| Funcionalidade | Abordagem Sugerida |
|---|---|
| Busca por palavra-chave | Navigator pesquisa a query SQL com `LIKE`, Driver implementa a rota e testa no Insomnia |
| Categorização (tags) | Navigator projeta o modelo de dados (nova tabela ou campo), Driver implementa migration e rotas |
| Sistema de votação | Driver implementa endpoint de upvote/downvote, Navigator valida lógica de negócio (votos duplicados) |
| Perfil de usuário | Navigator rastreia dependências com outras features, Driver implementa queries de histórico |
| Notificações | Navigator pesquisa estratégias (polling vs. websocket), Driver implementa a solução mais simples |

---

## 5. Adaptação Individual (Contexto Atual)

Como o projeto é individual, as práticas de pair programming são adaptadas da seguinte forma:

- **Revisão de código própria:** após cada funcionalidade, o código é revisado com uma pausa de pelo menos 30 minutos antes de fazer o commit — simulando o olhar externo do navigator.
- **Checklist de navigator:** antes de cada commit, é verificado: a funcionalidade passa nos testes? Há duplicação de código? O design está simples? Existe código especulativo (YAGNI)?
- **Commits atômicos:** cada commit representa uma unidade lógica de trabalho, facilitando a revisão posterior.

---

## 6. Referências

- BECK, Kent; ANDRES, Cynthia. *Extreme Programming Explained: Embrace Change*. 2. ed. Addison-Wesley, 2004.
- VALENTE, Marco Tulio. *Engenharia de Software Moderna*. Cap. 2 — Extreme Programming.

---

*Documento preparado para o Projeto Final de Engenharia de Software — Parte 1.*
