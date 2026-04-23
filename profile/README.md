<div align="center">

# 🌵 Mandacá App

**Plataforma mobile para gerenciamento e conexão de comunidades.**

[![Frontend](https://img.shields.io/badge/Frontend-React%20Native%20%2B%20Expo-blue?logo=expo)](https://github.com/Mandaca-App/mandaca-frontend)
[![Backend](https://img.shields.io/badge/Backend-FastAPI%20%2B%20Python-green?logo=fastapi)](https://github.com/Mandaca-App/mandaca-backend)
[![License](https://img.shields.io/badge/License-MIT-yellow)](https://github.com/Mandaca-App/mandaca-backend/blob/dev/LICENSE)

</div>

---

## 📖 Sobre o Projeto

O **Mandacá** é uma aplicação mobile desenvolvida para conectar e facilitar o gerenciamento de comunidades. O projeto é composto por duas camadas principais: um aplicativo mobile em React Native e uma API REST em Python/FastAPI, integradas ao banco de dados gerenciado pelo Supabase.

---

## 🏗️ Arquitetura

```
┌─────────────────────────────────────┐
│        📱 Aplicativo Mobile         │
│  React Native + Expo (iOS/Android)  │
└────────────────┬────────────────────┘
                 │ HTTP / REST
┌────────────────▼────────────────────┐
│            🔌 API REST              │
│       FastAPI (Python 3.10+)        │
└────────────────┬────────────────────┘
                 │ SQL (via Supabase)
┌────────────────▼────────────────────┐
│         🗄️ Banco de Dados           │
│        Supabase (PostgreSQL)        │
└─────────────────────────────────────┘
```

---

## 📦 Repositórios

| Repositório | Descrição | Tecnologias |
|---|---|---|
| [mandaca-frontend](https://github.com/Mandaca-App/mandaca-frontend) | Aplicativo mobile multiplataforma (iOS & Android) | React Native · Expo · TypeScript · NativeWind |
| [mandaca-backend](https://github.com/Mandaca-App/mandaca-backend) | API REST com documentação automática e migrações | Python · FastAPI · Supabase · Docker · Alembic |

---

## 🛠️ Stack Tecnológica

### 📱 Frontend

| Tecnologia | Descrição |
|---|---|
| [React Native](https://reactnative.dev/) | Framework para aplicativos mobile multiplataforma |
| [Expo](https://expo.dev/) | Plataforma e toolchain para React Native |
| [TypeScript](https://www.typescriptlang.org/) | Tipagem estática para JavaScript |
| [NativeWind](https://www.nativewind.dev/) | Tailwind CSS para React Native |
| [Node.js](https://nodejs.org/) | Ambiente de execução para ferramentas de build |

### ⚙️ Backend

| Tecnologia | Descrição |
|---|---|
| [Python 3.10+](https://www.python.org/) | Linguagem principal do backend |
| [FastAPI](https://fastapi.tiangolo.com/) | Framework web moderno e de alta performance |
| [Supabase](https://supabase.com/) | Banco de dados PostgreSQL gerenciado |
| [Alembic](https://alembic.sqlalchemy.org/) | Migrações de banco de dados |
| [Docker](https://www.docker.com/) | Conteinerização e orquestração do ambiente |

---

## 🚀 Início Rápido

### Pré-requisitos

- [Node.js](https://nodejs.org) (LTS) e npm
- [Python 3.10+](https://www.python.org/) e pip
- [Git](https://git-scm.com)
- [Docker](https://www.docker.com/) (para o backend)
- [Expo Go](https://expo.dev/client) no celular (para testar o app)

### 📱 Rodando o Frontend

```bash
# Clone o repositório
git clone https://github.com/Mandaca-App/mandaca-frontend.git
cd mandaca-frontend

# Instale as dependências
npm install

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env com as configurações necessárias

# Inicie o servidor de desenvolvimento
npx expo start
```

Abra o **Expo Go** no celular e escaneie o QR Code exibido no terminal.

### ⚙️ Rodando o Backend

```bash
# Clone o repositório
git clone https://github.com/Mandaca-App/mandaca-backend.git
cd mandaca-backend

# Crie e ative o ambiente virtual
python -m venv .venv
source .venv/bin/activate       # Linux / macOS
# .\.venv\Scripts\Activate.ps1  # Windows (PowerShell)

# Instale as dependências
pip install -r requirements.txt

# Configure as variáveis de ambiente
cp .env.example .env
# Edite o .env com as credenciais do banco e demais configurações

# Suba o banco de dados
docker compose up db -d

# Aplique as migrações
alembic upgrade head

# Inicie a API
uvicorn app.main:app --reload
```

A documentação interativa da API estará disponível em `http://localhost:8000/docs`.

---

## 🤝 Contribuindo

Contribuições são bem-vindas! Siga o fluxo abaixo:

1. Abra uma **issue** descrevendo a mudança ou bug.
2. Crie uma branch a partir da branch de desenvolvimento:
   - `feature/nome-da-funcionalidade` para novas funcionalidades.
   - `fix/nome-do-bug` para correções.
3. Faça suas alterações e adicione testes quando aplicável.
4. Abra um **Pull Request** com descrição clara e referência à issue.

---

## 📄 Licença

Este projeto está licenciado sob a licença **MIT** — veja o arquivo [LICENSE](https://github.com/Mandaca-App/mandaca-backend/blob/dev/LICENSE) para mais detalhes.

