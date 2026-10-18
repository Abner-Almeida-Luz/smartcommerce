# Ambiente de Desenvolvimento — SmartCommerce

Registro do ambiente local usado no projeto. Atualizado em: 2026-10-18.

## SO e ferramentas

| Ferramenta           | Versão instalada                     | Versão alvo | Papel no projeto                                                                                                    |
| -------------------- | ------------------------------------ | ----------- | ------------------------------------------------------------------------------------------------------------------- |
| **Windows**          | 11 (amd64, family windows)           | —           | SO de desenvolvimento                                                                                               |
| **Java (JDK)**       | 21.0.6 LTS (Oracle)                  | 21 LTS      | Roda o backend Spring Boot que expõe a API REST                                                                     |
| **Maven**            | 3.9.16                               | 3.9+        | Gerencia dependências e constrói o backend (compila, testa, empacota em `.jar`)                                     |
| **Node.js**          | 24.21.0                              | 20+ LTS     | Roda o frontend React + TypeScript (build, dev server)                                                              |
| **npm**              | 11.17.0                              | —           | Gerenciador de pacotes do Node; instala dependências **e executa scripts** (`npm run dev`, `npm run build`)         |
| **Python**           | (não instalado — adiado para Fase 6) | 3.12        | Rodará o serviço de IA em FastAPI                                                                                   |
| **Docker**           | 29.7.2                               | 24+         | Roda containers isolados (Postgres, Redis, serviço de IA) sem instalar nada no SO                                   |
| **Docker Compose**   | v5.4.0                               | —           | Orquestra **vários** containers descritos em um único `docker-compose.yml`, com um comando (`docker compose up -d`) |
| **Git**              | 2.49.0.windows.1                     | 2.40+       | Versiona o código localmente (ferramenta instalada no SO)                                                           |
| **GitHub**           | —                                    | —           | Serviço web que hospeda o repositório Git remoto (não confundir com Git)                                            |
| **IntelliJ IDEA CE** | (a instalar/instalado)               | última      | IDE do backend Java, com Spring Initializr integrado                                                                |
| **VS Code**          | (instalado)                          | última      | IDE do frontend e do Python; editor de documentação                                                                 |

## Decisões

- **Python adiado para a Fase 6.** Só será necessário quando o serviço de IA começar. Instalar agora seria ruído.
- **Node 24 LTS** (em vez de 20) — versão LTS mais recente, compatível com Vite 5+ e o ecossistema React atual.
- **Projetos em `C:\Projects`** — fora do OneDrive. O OneDrive sincroniza `.git/`, `target/` e `node_modules/`, causando locks, lentidão e corrupção de repositório.
- **Versões fixas** (nunca `latest`) — reprodutibilidade. Outra pessoa (ou eu, em outro PC) consegue reproduzir o ambiente sabendo as versões exatas.

## Comandos de verificação

```powershell
java -version         # deve mostrar "21.x.x LTS"
mvn -version          # deve mostrar "Apache Maven 3.9.x"
node -v               # deve mostrar "v24.x.x"
npm -v                # deve mostrar "11.x.x"
docker --version      # deve mostrar "Docker version 29.x.x"
docker compose version # deve mostrar "Docker Compose version v5.x.x"
git --version         # deve mostrar "git version 2.4x.x"
```
