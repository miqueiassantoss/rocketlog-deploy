<h1 align="center"> RocketLog API </h1>

<p align="center">
  API RESTful para gestão logística e rastreamento de entregas, desenvolvida com tecnologias modernas como Prisma ORM e Docker.
</p>

<p align="center">
  <a href="#-tecnologias">Tecnologias</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-funcionalidades">Funcionalidades</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-rotas">Rotas</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#-como-rodar">Como Rodar</a>&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;
  <a href="#memo-licença">Licença</a>
</p>

<p align="center">
  <img alt="License" src="https://img.shields.io/static/v1?label=license&message=MIT&color=49AA26&labelColor=000000">
</p>

## 🚀 Tecnologias

Este projeto utiliza uma stack robusta para aplicações escaláveis:

- **[Node.js](https://nodejs.org/)** & **[TypeScript](https://www.typescriptlang.org/)**
- **[Express](https://expressjs.com/)** (Framework Web)
- **[Prisma ORM](https://www.prisma.io/)** (Database Mapping e Migrations)
- **[PostgreSQL](https://www.postgresql.org/)** (Banco de Dados Relacional via Docker)
- **[Jest](https://jestjs.io/)** & **[Supertest](https://www.npmjs.com/package/supertest)** (Testes Automatizados E2E)
- **[Zod](https://zod.dev/)** (Validação de Schema)

## 💻 Sobre o Projeto

O **RocketLog** é um sistema de controle de encomendas. Ele permite que administradores cadastrem entregas, e que entregadores atualizem o status dessas entregas, gerando um histórico (log) de cada movimentação.

### Regras de Negócio e Segurança (RBAC)
O sistema implementa controle de acesso baseado em cargos:
- **ADMIN:** Pode cadastrar entregadores e novas encomendas.
- **DELIVERYMAN:** Pode visualizar suas entregas e atualizar o status (Retirada/Entregue).
- **CUSTOMER:** Pode visualizar o status de suas encomendas.

## 🗄 Modelagem de Dados (Prisma)

O banco de dados possui as seguintes entidades principais:
- `User`: Usuários do sistema (Admin, Entregador, Cliente).
- `Delivery`: A encomenda em si, contendo status atual.
- `DeliveryLog`: Histórico de atualizações de uma entrega.

## 📍 Rotas da API

### Autenticação
- `POST /sessions`: Login de usuário (Retorna JWT).
- `POST /users`: Cadastro de novos usuários.

### Entregas
- `POST /deliveries`: Cadastra nova entrega (Admin).
- `GET /deliveries`: Lista entregas (com filtros).
- `PATCH /deliveries/:id/status`: Atualiza o status da entrega (Ex: `PICKED`, `DELIVERED`).

## 🎲 Como Rodar

### Pré-requisitos
Você precisa ter o **Docker** e o **Node.js** instalados.

```bash
# 1. Clone o repositório
$ git clone [https://github.com/miqueiassantoss/rocketlog-deploy.git](https://github.com/miqueiassantoss/rocketlog-deploy.git)

# 2. Acesse a pasta
$ cd rocketlog-deploy

# 3. Instale as dependências
$ npm install

# 4. Crie o arquivo .env baseado no exemplo
$ cp .env.example .env

# 5. Suba o banco de dados com Docker
$ docker-compose up -d

# 6. Rode as migrations do Prisma
$ npx prisma migrate dev

# 7. Inicie o servidor
$ npm run dev
```

# Rodando testes
$ npm test

## 📝 Licença

Esse projeto está sob a licença MIT.

---

<p align="center">
  Feito por <a href="https://github.com/miqueiassantoss">Miqueias Santos</a>
</p>
