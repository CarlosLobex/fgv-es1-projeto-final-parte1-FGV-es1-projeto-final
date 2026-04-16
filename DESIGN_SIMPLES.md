# Design Simples no ESM Forum — Análise do Backend

## Introdução

O princípio de **Design Simples** é uma das práticas centrais do Extreme Programming (XP). Um código segue design simples quando:

1. Passa em todos os testes
2. Não possui lógica duplicada
3. Expressa claramente a intenção do programador
4. Possui o menor número possível de classes e métodos

Associado a isso está o princípio **YAGNI** (*You Aren't Gonna Need It*): não implemente algo antes de precisar. Código especulativo adiciona complexidade sem agregar valor imediato.

---

## 1. Aspectos que Seguem o Princípio de Design Simples

### 1.1 Rotas diretas e sem abstração desnecessária (`routes/perguntas.js`)

O backend do ESM Forum define rotas RESTful de forma direta, sem camadas de abstração intermediárias (como repositórios ou services) que não seriam necessárias para um sistema de escopo didático.

**Exemplo típico da estrutura encontrada:**

```js
// routes/perguntas.js

router.get('/', (req, res) => {
  db.all('SELECT * FROM perguntas ORDER BY id DESC', [], (err, rows) => {
    if (err) return res.status(500).json({ error: err.message });
    res.json(rows);
  });
});

router.post('/', (req, res) => {
  const { titulo, corpo, autor } = req.body;
  db.run(
    'INSERT INTO perguntas (titulo, corpo, autor) VALUES (?, ?, ?)',
    [titulo, corpo, autor],
    function (err) {
      if (err) return res.status(500).json({ error: err.message });
      res.json({ id: this.lastID });
    }
  );
});
```

**Por que isso é design simples?**
- Cada rota faz exatamente uma coisa
- Não há classes `PerguntaRepository`, `PerguntaService` ou `PerguntaController` separadas — o que seria YAGNI para um sistema desse porte
- O código é legível e compreensível sem conhecimento prévio da arquitetura

---

### 1.2 Sem autenticação complexa (YAGNI aplicado)

O sistema não implementa autenticação por token (JWT), sessões ou OAuth. O campo `autor` é simplesmente uma string passada diretamente no corpo da requisição.

```js
// Exemplo de inserção sem autenticação
const { titulo, corpo, autor } = req.body;
```

**Análise:** Como o objetivo do sistema é didático e não há requisito de segurança real, não implementar autenticação é uma aplicação direta de YAGNI. Adicionar JWT, middleware de autenticação e tabela de usuários seria código especulativo.

---

### 1.3 Banco de dados SQLite sem ORM (`routes/respostas.js`)

O sistema usa queries SQL diretamente, sem ORM (Sequelize, Prisma, TypeORM). Isso elimina uma camada de abstração desnecessária para o escopo do projeto.

```js
// routes/respostas.js
router.get('/:pergunta_id', (req, res) => {
  const { pergunta_id } = req.params;
  db.all(
    'SELECT * FROM respostas WHERE pergunta_id = ? ORDER BY id ASC',
    [pergunta_id],
    (err, rows) => {
      if (err) return res.status(500).json({ error: err.message });
      res.json(rows);
    }
  );
});
```

**Por que isso é design simples?**
- ORMs adicionam configuração, migrações e abstrações que não se justificam para 2–3 tabelas simples
- As queries são legíveis diretamente no código da rota
- Menos dependências no `package.json`

---

## 2. Oportunidades de Simplificação

### 2.1 Tratamento de erro repetido

Em diversas rotas, o bloco de tratamento de erro é idêntico:

```js
if (err) return res.status(500).json({ error: err.message });
```

Embora pequeno, esse padrão se repete em cada callback de banco. Uma simplificação possível seria extrair um helper:

```js
// Antes (repetido em cada rota)
if (err) return res.status(500).json({ error: err.message });

// Depois (helper reutilizável)
function handleDbError(err, res) {
  if (err) {
    res.status(500).json({ error: err.message });
    return true;
  }
  return false;
}

// Uso nas rotas
if (handleDbError(err, res)) return;
```

> **Nota:** Esta refatoração mantém o design simples e elimina duplicação — sem adicionar complexidade desnecessária.

### 2.2 Validação de entrada ausente

As rotas não validam se os campos obrigatórios foram enviados:

```js
// Situação atual — sem validação
const { titulo, corpo, autor } = req.body;
db.run('INSERT INTO perguntas ...', [titulo, corpo, autor], ...)

// Com validação mínima (melhoria simples)
const { titulo, corpo, autor } = req.body;
if (!titulo || !corpo || !autor) {
  return res.status(400).json({ error: 'Campos obrigatórios ausentes' });
}
```

Esta não é uma oportunidade de *design simples*, mas de **robustez mínima** — e pode ser implementada com poucas linhas sem violar YAGNI.

---

## 3. Conclusão

O backend do ESM Forum demonstra bom alinhamento com os princípios de design simples e YAGNI: rotas diretas, sem abstrações prematuras, banco de dados simples e código com intenção clara. As oportunidades de melhoria identificadas são pontuais e não comprometem a qualidade geral do projeto.

---

*Documento preparado para o Projeto Final de Engenharia de Software — Parte 1.*
