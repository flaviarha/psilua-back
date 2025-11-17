# Backend Projeto-Psilua

Projeto backend para a aplicação PsiLua — API em Python para gerenciamento de pacientes, psicólogos, atendimentos e relatórios.

## Descrição

Este repositório contém a API do servidor (FastAPI) responsável por autenticação, gestão de pacientes, psicólogos, agendamentos, geração de relatórios e serviços de ML de apoio.

Estrutura principal:

- `main.py` — ponto de entrada da aplicação.
- `core/` — configuração do banco de dados e inicialização.
- `models/` — modelos de dados (ORM).
- `routers/` — endpoints organizados por recurso (auth, patients, appointments, etc.).
- `schemas/` — Pydantic schemas para validação.
- `services/` — lógica de negócio reutilizável (autenticação, relatório, ML).
- `seed_data.py` — script para popular dados iniciais (uso em desenvolvimento).

## Pré-requisitos

- Python 3.10+ (recomendado). 
- `pip` para instalar dependências.

Instale dependências:

```powershell
pip install -r requirements.txt
```

## Variáveis de ambiente

Crie um arquivo `.env` na raiz (ou configure variáveis no seu ambiente). Exemplo de variáveis esperadas:

- `DATABASE_URL` — URL de conexão com o banco (ex: `sqlite:///./db.sqlite3` ou PostgreSQL).
- `SECRET_KEY` — chave para assinatura de tokens JWT.
- `ACCESS_TOKEN_EXPIRE_MINUTES` — tempo de expiração do token.

Atualize os valores conforme seu ambiente de desenvolvimento/produção.

## Executando a aplicação (desenvolvimento)

Execute com `uvicorn` (com recarregamento automático):

```powershell
uvicorn main:app --reload --host 0.0.0.0 --port 8000
```

Ou, se preferir rodar via Python:

```powershell
python .\main.py
```

Depois de subir, a API normalmente ficará disponível em `http://localhost:8000`. Se a aplicação usar FastAPI, a documentação interativa estará em `http://localhost:8000/docs`.

## Endpoints principais

Os `routers` estão em `routers/`. Resumo dos módulos já presentes:

- `auth.py` — endpoints de registro, login e refresh de tokens.
- `patients.py` — CRUD de pacientes.
- `psychologists.py` — CRUD de psicólogos.
- `appointments.py` — agendamento e gerenciamento de atendimentos.
- `reports.py` — geração de relatórios.
- `requests.py` — endpoints auxiliares para requisições específicas.
- `ml_analysis.py` — rotas relacionadas a análises/serviços de ML.

Exemplo de uso (login):

```bash
curl -X POST "http://localhost:8000/auth/login" -H "Content-Type: application/json" -d '{"username":"user","password":"pass"}'
```

Substitua o caminho conforme definido no `routers/auth.py`.

## Banco de dados

Configuração em `core/database.py`. Por padrão o projeto pode usar SQLite para desenvolvimento; para produção, configure `DATABASE_URL` para PostgreSQL ou outra solução suportada.

## Seed e testes rápidos

- Para popular dados de exemplo: `python .\seed_data.py`.
- Testes rápidos/execução de scripts de verificação: `python .\test.py`.

## Estrutura de desenvolvimento

- Coloque lógica de negócio reaproveitável em `services/`.
- Validação e contratos de request/response em `schemas/`.
- Modelos e mapeamento ORM em `models/`.

## Contribuição

1. Fork do repositório.
2. Crie uma branch: `git checkout -b feature/minha-feature`.
3. Faça commits claros e pequenos.
4. Abra um Pull Request descrevendo a mudança.

## Contato

Para dúvidas, abra uma issue ou contacte o mantenedor do repositório.

https://github.com/flaviarha/psilua-back
---

