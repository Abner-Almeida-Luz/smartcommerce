# Comandos do dia a dia

## Docker

```powershell
docker compose up -d          # sobe tudo
docker compose ps             # estado
docker compose logs -f        # logs
docker compose down           # para (mantém dados)
Git
powershell
git status                    # o que mudou
git checkout -b feat/nome     # nova branch
git add .                     # adicionar
git commit -m "feat: ..."     # commitar
git push                      # enviar
git log --oneline             # histórico
Postgres no container
powershell
docker exec -it smart-postgres psql -U smart -d smartcommerce        # sessão
docker exec smart-postgres psql -U smart -d smartcommerce -c "SQL"   # 1 query
```
