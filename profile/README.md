<div align="center">

# Mandacá App

**Plataforma HCD para conectar turistas a microempreendedores gastronômicos no interior de Pernambuco.**

[![Frontend](https://img.shields.io/badge/Frontend-React%20Native%20%2B%20Expo-blue?logo=expo)](https://github.com/Mandaca-App/mandaca-frontend)
[![Backend](https://img.shields.io/badge/Backend-FastAPI%20%2B%20Python-green?logo=fastapi)](https://github.com/Mandaca-App/mandaca-backend)
[![License](https://img.shields.io/badge/License-MIT-yellow)](https://github.com/Mandaca-App/mandaca-backend/blob/dev/LICENSE)

</div>

---

## Ambientes de Deploy

| Ambiente | URL | Quando atualiza |
|---|---|---|
| Backend Staging | https://mandaca-backend-staging.onrender.com/docs | A cada push em `dev` |
| Backend Production | https://mandaca-backend-production.onrender.com/docs | Release semanal (domingos 05h) |
| Frontend Web Production | https://mandaca-frontend-production.onrender.com | Release semanal (domingos 05h) |

> Os servicos rodam no free tier do Render. A primeira requisicao apos um periodo de inatividade pode levar ate 1 minuto (cold start). As subsequentes sao normais.

---

## Instalar o App Android

O APK de preview e gerado automaticamente todo domingo e publicado com um link permanente. Nao e necessario compilar nada localmente.

**Download direto:**
```
https://github.com/Mandaca-App/mandaca-frontend/releases/latest/download/mandaca-preview.apk
```

**Como instalar:**
1. Acesse o link acima no celular Android e baixe o APK
2. Abra o arquivo baixado (se solicitado, habilite *Instalar apps de fontes desconhecidas* nas configuracoes)
3. Conclua a instalacao normalmente
4. O app ja aponta para o backend de producao

O app e compativel com Android arm64-v8a. Para ver o historico de builds e releases anteriores: [Releases do Frontend](https://github.com/Mandaca-App/mandaca-frontend/releases)

---

## Pipeline de Releases

Todo **domingo as 05h00 (Recife, UTC-3)** os dois pipelines disparam automaticamente:

**Backend**
- Verifica se a branch `dev` tem commits novos em relacao a `main`
- Se sim: cria PR de `dev -> main`, aguarda o CI passar (lint + testes + cobertura) e faz o merge automaticamente
- Apos o merge: cria tag SemVer e publica GitHub Release com changelog dos PRs da semana

**Frontend Android**
- Le o arquivo `VERSION` na raiz do repositorio
- Dispara um build EAS no Expo (perfil `preview`, APK arm64)
- Aguarda a conclusao do build (~5-10 min)
- Baixa o APK e publica GitHub Release com tag SemVer, APK anexado e links de producao

### Versionamento SemVer

Ambos os repositorios usam um arquivo `VERSION` na raiz para controle de versao:

| Tipo | Regra | Exemplo |
|---|---|---|
| PATCH | Auto-incrementado pelo workflow se nenhum bump manual foi feito na semana | `0.1.0` -> `0.1.1` |
| MINOR | Bump manual pelo dev ao entregar uma feature nova (editar `VERSION` antes do domingo) | `0.1.x` -> `0.2.0` |
| MAJOR | Bump manual ao atingir estabilidade de API ou breaking change | `0.x.x` -> `1.0.0` |

As versoes `0.x.x` representam o periodo beta da plataforma. O PATCH reseta para `0` sempre que MINOR ou MAJOR sobe.

---

## Sobre o Projeto

O **Mandacá** é uma aplicação mobile com foco em Human-Centered Design (HCD), desenvolvida para dar visibilidade a microempreendedores gastronômicos do interior de Pernambuco e conectá-los a turistas da região. O projeto prioriza alta acessibilidade, incluindo suporte a IA e Text-to-Speech.

---

## Arquitetura

```
┌─────────────────────────────────────┐
│        Aplicativo Mobile            │
│  React Native + Expo (iOS/Android)  │
└────────────────┬────────────────────┘
                 │ HTTP / REST
┌────────────────▼────────────────────┐
│            API REST                 │
│       FastAPI (Python 3.10+)        │
└────────────────┬────────────────────┘
                 │ SQL (via Supabase)
┌────────────────▼────────────────────┐
│         Banco de Dados              │
│        Supabase (PostgreSQL)        │
└─────────────────────────────────────┘
```

---

## Repositórios

| Repositório | Descrição | Tecnologias |
|---|---|---|
| [mandaca-frontend](https://github.com/Mandaca-App/mandaca-frontend) | Aplicativo mobile multiplataforma (iOS & Android) | React Native · Expo · TypeScript · NativeWind |
| [mandaca-backend](https://github.com/Mandaca-App/mandaca-backend) | API REST com documentação automática e migrações | Python · FastAPI · Supabase · Docker · Alembic |

---

## Stack Tecnológica

### Frontend

| Tecnologia | Descrição |
|---|---|
| [React Native](https://reactnative.dev/) | Framework para aplicativos mobile multiplataforma |
| [Expo](https://expo.dev/) | Plataforma e toolchain para React Native |
| [TypeScript](https://www.typescriptlang.org/) | Tipagem estática para JavaScript |
| [NativeWind](https://www.nativewind.dev/) | Tailwind CSS para React Native |

### Backend

| Tecnologia | Descrição |
|---|---|
| [Python 3.10+](https://www.python.org/) | Linguagem principal do backend |
| [FastAPI](https://fastapi.tiangolo.com/) | Framework web moderno e de alta performance |
| [Supabase](https://supabase.com/) | Banco de dados PostgreSQL gerenciado |
| [Alembic](https://alembic.sqlalchemy.org/) | Migrações de banco de dados |
| [Docker](https://www.docker.com/) | Conteinerização e orquestração do ambiente |

---

## Início Rápido

### Pré-requisitos

- [Node.js](https://nodejs.org) (LTS) e npm
- [Python 3.10+](https://www.python.org/) e pip
- [Git](https://git-scm.com)
- [Docker](https://www.docker.com/) (para o backend)

### Rodando o Frontend

```bash
git clone https://github.com/Mandaca-App/mandaca-frontend.git
cd mandaca-frontend
npm install
cp .env.example .env
# Edite o .env com as configurações necessárias
npx expo start
```

Abra o **Expo Go** no celular e escaneie o QR Code exibido no terminal.

### Rodando o Backend

```bash
git clone https://github.com/Mandaca-App/mandaca-backend.git
cd mandaca-backend
python -m venv .venv
source .venv/bin/activate  # Linux / macOS
pip install -r requirements.txt
cp .env.example .env
# Edite o .env com as credenciais do banco e demais configurações
alembic upgrade head
uvicorn app.main:app --reload
```

A documentação interativa da API estará disponível em `http://localhost:8000/docs`.

---

## Contribuindo

1. Crie uma branch a partir de `dev` (backend) ou `develop` (frontend) seguindo o padrão `feature/SCRUM-ID-descricao`
2. Faça suas alterações com commits atômicos no formato `SCRUM-ID tipo: mensagem`
3. Abra um Pull Request com descrição clara referenciando o ticket do Jira
4. Aguarde a revisão e aprovação de ao menos 1 reviewer

---

## Licença

Este projeto está licenciado sob a licença **MIT** — veja o arquivo [LICENSE](https://github.com/Mandaca-App/mandaca-backend/blob/dev/LICENSE) para mais detalhes.
