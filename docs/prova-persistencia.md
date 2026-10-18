# Prova de persistência — Postgres

## Passo 1: criar dados antes do down

**Entrada** — `docker exec -it smart-postgres psql -U smart -d smartcommerce`

```sql
CREATE TABLE produto (
  id SERIAL PRIMARY KEY,
  nome TEXT NOT NULL,
  preco NUMERIC(10,2) NOT NULL
);

INSERT INTO produto (nome, preco) VALUES
  ('Caneca', 29.90),
  ('Camiseta', 59.90),
  ('Caneta', 9.90);

SELECT * FROM produto;
Saída

text
CREATE TABLE
INSERT 0 3
 id |   nome   | preco
----+----------+-------
  1 | Caneca   | 29.90
  2 | Camiseta | 59.90
  3 | Caneta   |  9.90
(3 rows)
Passo 2: down + up
Entrada

powershell
docker compose down
docker compose ps
docker compose up -d
docker compose ps
Saída

text
[+] down 2/2
 ✔ Container smart-postgres      Removed
 ✔ Network smartcommerce_default Removed

NAME      IMAGE     COMMAND   SERVICE   CREATED   STATUS    PORTS
(vazio)

[+] up 2/2
 ✔ Network smartcommerce_default Created
 ✔ Container smart-postgres      Started

NAME             IMAGE         STATUS                    PORTS
smart-postgres   postgres:16   Up (healthy)              0.0.0.0:5432->5432/tcp
Passo 3: dados depois do up
Entrada

powershell
docker exec -it smart-postgres psql -U smart -d smartcommerce -c "SELECT * FROM produto;"
Saída

text
 id |   nome   | preco
----+----------+-------
  1 | Caneca   | 29.90
  2 | Camiseta | 59.90
  3 | Caneta   |  9.90
(3 rows)
Conclusão
Os dados sobreviveram porque o volume nomeado pgdata está mapeado em
/var/lib/postgresql/data do container. docker compose down remove containers
mas preserva volumes nomeados; só down -v remove os dados.
```
