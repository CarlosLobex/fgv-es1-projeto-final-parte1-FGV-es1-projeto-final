# Instalação e Configuração do Ambiente — ESM Forum

## Pré-requisitos

Os repositórios do projeto foram desenvolvidos com **Node.js 18**. Usar outra versão pode causar erros na instalação dos pacotes. Por isso, é obrigatório usar um gerenciador de versões do Node.

---

## 1. Fork dos Repositórios

Acesse os repositórios originais no GitHub e clique em **Fork** para criar sua cópia pessoal:

- **Backend:** [https://github.com/mtov/esmforum](https://github.com/mtov/esmforum)
- **Frontend:** [https://github.com/mtov/esmforum-react](https://github.com/mtov/esmforum-react)

Após realizar o fork, clone os seus repositórios localmente:

```bash
# Clone o backend
git clone https://github.com/<seu-usuario>/esmforum.git

# Clone o frontend
git clone https://github.com/<seu-usuario>/esmforum-react.git
```

---

## 2. Instale um Gerenciador de Versões do Node

### Opção A — fnm (recomendado, funciona em Windows, Mac e Linux)

**Windows** (via winget, no PowerShell ou Terminal):
```powershell
winget install Schniz.fnm
```
Feche e reabra o terminal após a instalação. Depois, adicione ao seu perfil do PowerShell (`notepad $PROFILE`):
```powershell
fnm env --use-on-cd | Out-String | Invoke-Expression
```

**macOS** (via Homebrew):
```bash
brew install fnm
```
Adicione ao seu `~/.zshrc` (ou `~/.bashrc`):
```bash
eval "$(fnm env --use-on-cd)"
```

**Linux** (via script oficial):
```bash
curl -fsSL https://fnm.vercel.app/install | bash
```
Adicione ao seu `~/.bashrc` (ou `~/.zshrc`):
```bash
eval "$(fnm env --use-on-cd)"
```
Após editar o arquivo de perfil, reinicie o terminal ou execute `source ~/.bashrc`.

---

### Opção B — nvm (Mac e Linux)

```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
```
Reinicie o terminal após a instalação (o script já configura o perfil automaticamente).

---

## 3. Instale e Ative o Node 18

Execute nos terminais de backend e frontend:

**Com fnm:**
```bash
fnm install 18
fnm use 18
```

**Com nvm:**
```bash
nvm install 18
nvm use 18
```

Confirme a versão ativa:
```bash
node --version
# Deve exibir algo como v18.x.x
```

---

## 4. Configure o Backend (esmforum)

```bash
cd esmforum

# Use npm ci (não npm install) para usar os pacotes travados
npm ci

# Inicie o servidor
node server.js
```

O backend estará disponível em: **http://localhost:5000**

> Deixe este terminal aberto enquanto usa o sistema.

---

## 5. Configure o Frontend (esmforum-react)

Abra um **novo terminal** e execute:

```bash
cd esmforum-react

# Certifique-se de que o Node 18 está ativo também aqui
fnm use 18   # ou: nvm use 18

npm ci

npm start
```

O frontend abrirá automaticamente em: **http://localhost:3000**

---

## 6. Resumo Rápido

| Passo | Comando |
|---|---|
| Ativar Node 18 (fnm) | `fnm install 18 && fnm use 18` |
| Ativar Node 18 (nvm) | `nvm install 18 && nvm use 18` |
| Instalar dependências | `npm ci` |
| Rodar backend | `node server.js` |
| Rodar frontend | `npm start` |

---

## 7. Problemas Comuns

| Problema | Solução |
|---|---|
| `fnm` não reconhecido após instalação no Windows | Feche e reabra o terminal. Verifique se o winget concluiu sem erros e se o perfil do PowerShell foi configurado |
| Erro `EBADENGINE` ou falha no `npm ci` | Verifique a versão com `node --version`. Se diferente de v18, execute `fnm use 18` (ou `nvm use 18`) novamente |
| Frontend não conecta ao backend | Confirme que o backend está rodando (`node server.js`) em outro terminal antes de iniciar o frontend |

---

*Documentação preparada para o Projeto Final de Engenharia de Software — Parte 1.*
