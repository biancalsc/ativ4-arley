
# 🛡️ CSRF – Demonstração de Ataque e Mitigação

Este projeto tem como objetivo demonstrar, de forma prática, a vulnerabilidade Cross-Site Request Forgery (CSRF) em aplicações web. A estrutura do projeto está dividida em dois servidores:
- `server-vitima`: aplicação vulnerável que simula funcionalidades reais de um sistema web (login, alteração de senha, cadastro de contatos);
- `server-ataque`: aplicação controlada pelo atacante, utilizada para forjar requisições maliciosas contra o sistema vítima.

## 📁 Estrutura do projeto
```
├── server-vitima/
│   ├── public/
│   │   └── login.html
│   ├── src/
│   │   ├── routes/
│   │   │   ├── db.ts
│   │   │   └── index.ts
│   │   ├── comandos.sql
│   │   └── index.ts
│   ├── package.json
│   └── tsconfig.json
│
└── server-ataque/
    ├── public/
    │   ├── csrf-get-attack.html
    │   ├── csrf-post-attack-seguro.html
    │   └── csrf-post-attack.html
    ├── src/
    │   └── index.ts
    ├── package.json
    └── tsconfig.json
```

## ▶️ Como executar o projeto

### 1. Instalando as dependências

cd server/server-vitima
npm install
cd ../server-ataque
npm install


### 2. Configurando o Banco de Dados PostgreSQL
- Crie um banco de dados chamado `bdaula` no PostgreSQL;
- Atualize o arquivo `.env` com os dados corretos de acesso ao banco;

### 3. Criando as tabelas
- Execute os comandos SQL presentes no arquivo `server-vitima/src/comandos.sql`;

### 4. Configurando os subdomínios
- Edite o arquivo `hosts` no seu sistema operacional:
  - Windows: `C:\Windows\System32\drivers\etc\hosts`
  - Linux/macOS: `/etc/hosts`
- Adicione as seguintes linhas:
```
127.0.0.1   vitima.local
127.0.0.1   atacante.local
```
- O servidor vítima roda em `http://vitima.local:3001`
- O servidor ataque roda em `http://atacante.local:3002`

### 5. Iniciando os servidores
Em cada pasta (`server-vitima` e `server-ataque`), execute:
```bash
npm start
# ou em ambiente de desenvolvimento
npm run dev
```
