# 📄 `README.md` (versão final)

````markdown
# SmartCommerce

E-commerce full-stack com Spring Boot (Java), React + TypeScript e serviço de IA em Python.

## Stack

- **Backend:** Java 21, Spring Boot 3, PostgreSQL
- **Frontend:** React 18, TypeScript, Vite
- **IA:** Python 3.12, FastAPI (fase 6)

## Como rodar o banco de dados

Requisitos: Docker Desktop rodando.

```bash
docker compose up -d
O Postgres estará acessível em localhost:5432:

Campo	Valor
Database	smartcommerce
User	smart
Password	smart
Verificar estado:

bash
docker compose ps
Deve mostrar smart-postgres com estado healthy.

Inspecionar via terminal (psql dentro do container):

bash
docker exec -it smart-postgres psql -U smart -d smartcommerce
Para parar (mantendo os dados):

bash
docker compose stop
Para remover os containers (mantendo os dados):

bash
docker compose down
Para apagar TUDO, incluindo dados: ⚠️

bash
docker compose down -v
Como rodar o backend
(instruções virão na fase 1)

Como rodar o frontend
(instruções virão na fase 5)

Documentação adicional
docs/ambiente.md — versões e decisões do ambiente

docs/prova-persistencia.md — evidência da persistência do Postgres
```
````
