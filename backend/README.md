# Backend — Tripper

API REST do projeto Tripper (NestJS + TypeScript + Prisma).

## Estado atual

Backend limpo e pronto para desenvolvimento. Estrutura base com:
- **Auth** e **Users** (estrutura pronta para implementação)
- **Prisma** + PostgreSQL
- **Swagger** em `/api/docs`
- **Health check** em `/api/v1/health`

## Como rodar

**Pré-requisitos:** Node.js 18+, Docker (PostgreSQL).

1. Instalar dependências:
   ```bash
   npm install
   ```

2. Subir PostgreSQL:
   ```bash
   docker compose up -d
   ```

3. Copiar variáveis de ambiente:
   ```bash
   cp .env.example .env
   ```

4. Gerar cliente Prisma e aplicar migrations:
   ```bash
   npm run prisma:generate
   npm run prisma:migrate
   ```

5. Iniciar a API em modo desenvolvimento:
   ```bash
   npm run start:dev
   ```

- **API:** http://localhost:3000/api/v1  
- **Health:** http://localhost:3000/api/v1/health  
- **Swagger:** http://localhost:3000/api/docs  

Porta padrão: `3000` (alterável via `PORT` no `.env`).

## Estrutura (src/)

```
src/
├── app.module.ts
├── app.controller.ts
├── main.ts
├── prisma/           # PrismaService
└── modules/
    ├── auth/
    └── users/
```

## Banco de dados (PostgreSQL via Docker)

```bash
docker compose up -d
```

- **Host:** localhost  
- **Porta:** 5432  
- **Banco:** tripper  
- **Usuário:** tripper  
- **Senha:** tripper_dev  

Connection string:
```
postgresql://tripper:tripper_dev@localhost:5432/tripper
```

Para parar: `docker compose down`. Os volumes persistem os dados.
