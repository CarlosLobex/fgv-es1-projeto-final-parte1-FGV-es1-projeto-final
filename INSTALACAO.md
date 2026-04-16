# Instalação e Configuração do Ambiente — ESM Forum

## Pré-requisitos

Antes de começar, certifique-se de ter instalado em sua máquina:

- [Node.js](https://nodejs.org/) v18 ou superior
- [npm](https://www.npmjs.com/) v9 ou superior
- [Git](https://git-scm.com/)

---

## 1. Fork dos Repositórios

Acesse os repositórios originais no GitHub e clique em **Fork** para criar sua cópia pessoal:

- **Backend:** [https://github.com/mtov/esmforum](https://github.com/mtov/esmforum)
- **Frontend:** [https://github.com/mtov/esmforum-react](https://github.com/mtov/esmforum-react)

Após realizar o fork, clone os seus repositórios localmente:

```bash
# Clone o backend
git clone https://github.com/CarlosLobex/esmforum.git

# Clone o frontend
git clone https://github.com/CarlosLobex/esmforum-react.git
```

---

## 2. Configuração do Backend

```bash
# Entre na pasta do backend
cd esmforum

# Instale as dependências
npm install

# Execute o servidor em modo desenvolvimento
npm start
```

O servidor backend será iniciado em: **http://localhost:3000**

> O banco de dados SQLite será criado automaticamente na primeira execução, com dados de exemplo já populados.

---

## 3. Configuração do Frontend

Abra um **novo terminal** e execute:

```bash
# Entre na pasta do frontend
cd esmforum-react

# Instale as dependências
npm install

# Execute o servidor de desenvolvimento
npm start
```

O frontend será iniciado em: **http://localhost:3001**

> O frontend se comunicará automaticamente com o backend na porta 3000. Certifique-se de que ambos os servidores estejam rodando simultaneamente.

---

## 4. Verificação do Ambiente

Com ambos os servidores rodando, acesse no navegador:

```
http://localhost:3001
```

Você deverá visualizar a interface do ESM Forum com a lista de perguntas cadastradas.

---

## 5. Estrutura dos Repositórios

### Backend (`esmforum`)

```
esmforum/
├── src/
│   ├── routes/
│   │   ├── perguntas.js   # Rotas CRUD de perguntas
│   │   └── respostas.js   # Rotas CRUD de respostas
│   ├── db.js              # Configuração do banco SQLite
│   └── app.js             # Configuração do Express
├── package.json
└── README.md
```

### Frontend (`esmforum-react`)

```
esmforum-react/
├── src/
│   ├── components/        # Componentes React
│   ├── pages/             # Páginas da aplicação
│   └── App.js             # Componente raiz
├── package.json
└── README.md
```

---

## 6. Problemas Comuns

| Problema | Solução |
|---|---|
| Porta 3000 já em uso | Encerre o processo que usa a porta: `npx kill-port 3000` |
| Módulos não encontrados | Delete `node_modules` e rode `npm install` novamente |
| CORS bloqueado | Confirme que o backend está rodando antes de iniciar o frontend |
| Banco corrompido | Delete o arquivo `.db` na raiz do backend e reinicie |

---

## 7. Comandos Úteis

```bash
# Verificar versão do Node
node --version

# Verificar versão do npm
npm --version

# Rodar testes do backend (se disponíveis)
npm test
```

---

*Documentação preparada para o Projeto Final de Engenharia de Software — Parte 1.*
