# Departamento de Controle de RH

Sistema completo para gestão e controle de recursos humanos, desenvolvido com arquitetura moderna separando backend e frontend.

## 📋 Sobre o Projeto

O **Departamento de Controle de RH** é uma solução completa para gerenciamento de recursos humanos, permitindo o controle de colaboradores, departamentos, cargos, férias, folha de pagamento e muito mais. O sistema foi desenvolvido com foco em escalabilidade, segurança e facilidade de uso.

## 🚀 Tecnologias Utilizadas

### Backend

- **PHP 8.x**
- **CodeIgniter 4** - Framework PHP para desenvolvimento da API REST
- **MySQL 8.x** - Banco de dados relacional
- **JWT** - Autenticação via tokens

### Frontend

- **ReactJS 18.x**
- **React Router** - Gerenciamento de rotas
- **Axios** - Requisições HTTP
- **React Hook Form** - Gerenciamento de formulários
- **Tailwind CSS** - Estilização

## ✨ Funcionalidades

- ✅ Autenticação e autorização de usuários
- ✅ Cadastro e gestão de colaboradores
- ✅ Controle de departamentos e cargos
- ✅ Gestão de férias e licenças
- ✅ Controle de ponto eletrônico
- ✅ Folha de pagamento
- ✅ Relatórios e dashboards
- ✅ Gestão de benefícios
- ✅ Controle de documentos
- ✅ Histórico de alterações

## 📦 Pré-requisitos

Antes de começar, certifique-se de ter instalado:

- **PHP >= 8.0**
- **Composer**
- **MySQL >= 8.0**
- **Node.js >= 16.x**
- **npm ou yarn**

## 🔧 Instalação

### Backend (API)

1. Clone o repositório:

```bash
git clone https://github.com/seu-usuario/dep_controller-main.git
cd dep_controller-main
```

2. Navegue até a pasta do backend:

```bash
cd backend
```

3. Instale as dependências do PHP:

```bash
composer install
```

4. Configure o arquivo de ambiente:

```bash
cp env .env
```

5. Edite o arquivo `.env` com suas configurações:

```env
# Database
database.default.hostname = localhost
database.default.database = dep_controller
database.default.username = seu_usuario
database.default.password = sua_senha
database.default.DBDriver = MySQLi

# JWT
JWT_SECRET_KEY = sua_chave_secreta_aqui
JWT_TIME_TO_LIVE = 3600
```

6. Execute as migrations:

```bash
php spark migrate
```

7. Execute os seeders (opcional):

```bash
php spark db:seed DatabaseSeeder
```

8. Inicie o servidor:

```bash
php spark serve
```

O backend estará disponível em `http://localhost:8080`

### Frontend (React)

1. Navegue até a pasta do frontend:

```bash
cd frontend
```

2. Instale as dependências:

```bash
npm install
# ou
yarn install
```

3. Configure as variáveis de ambiente:

```bash
cp .env.example .env
```

4. Edite o arquivo `.env`:

```env
REACT_APP_API_URL=http://localhost:8080/api
```

5. Inicie o servidor de desenvolvimento:

```bash
npm start
# ou
yarn start
```

O frontend estará disponível em `http://localhost:3000`

## 📁 Estrutura do Projeto

```
dep_controller-main/
├── backend/
│   ├── app/
│   │   ├── Config/
│   │   ├── Controllers/
│   │   ├── Models/
│   │   ├── Filters/
│   │   └── Database/
│   │       ├── Migrations/
│   │       └── Seeds/
│   ├── public/
│   ├── writable/
│   └── .env
│
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── contexts/
│   │   ├── hooks/
│   │   ├── utils/
│   │   └── App.js
│   ├── package.json
│   └── .env
│
└── README.md
```

## 🔌 Principais Endpoints da API

### Autenticação

```
POST   /api/auth/login          - Login
POST   /api/auth/logout         - Logout
POST   /api/auth/refresh        - Renovar token
GET    /api/auth/me             - Dados do usuário logado
```

### Colaboradores

```
GET    /api/colaboradores       - Listar colaboradores
GET    /api/colaboradores/:id   - Detalhes do colaborador
POST   /api/colaboradores       - Criar colaborador
PUT    /api/colaboradores/:id   - Atualizar colaborador
DELETE /api/colaboradores/:id   - Remover colaborador
```

### Departamentos

```
GET    /api/departamentos       - Listar departamentos
GET    /api/departamentos/:id   - Detalhes do departamento
POST   /api/departamentos       - Criar departamento
PUT    /api/departamentos/:id   - Atualizar departamento
DELETE /api/departamentos/:id   - Remover departamento
```

### Cargos

```
GET    /api/cargos              - Listar cargos
GET    /api/cargos/:id          - Detalhes do cargo
POST   /api/cargos              - Criar cargo
PUT    /api/cargos/:id          - Atualizar cargo
DELETE /api/cargos/:id          - Remover cargo
```

### Férias

```
GET    /api/ferias              - Listar férias
GET    /api/ferias/:id          - Detalhes de férias
POST   /api/ferias              - Solicitar férias
PUT    /api/ferias/:id          - Atualizar férias
DELETE /api/ferias/:id          - Cancelar férias
```

### Ponto Eletrônico

```
GET    /api/ponto               - Listar registros de ponto
POST   /api/ponto/registrar     - Registrar ponto
GET    /api/ponto/relatorio     - Relatório de ponto
```

## 🎯 Como Usar

1. **Acesse o sistema**: Abra o navegador em `http://localhost:3000`
2. **Faça login**: Use as credenciais padrão (ou crie um usuário)
3. **Navegue pelos módulos**: Dashboard, Colaboradores, Departamentos, etc.
4. **Gerencie os dados**: Cadastre, edite e visualize informações do RH

## 🔐 Autenticação

O sistema utiliza **JWT (JSON Web Tokens)** para autenticação. Após o login bem-sucedido, um token é gerado e deve ser enviado no header de todas as requisições protegidas:

```
Authorization: Bearer {seu_token_aqui}
```

## 🗄️ Banco de Dados

O sistema utiliza MySQL. O schema do banco é criado automaticamente através das migrations do CodeIgniter.

### Principais Tabelas

- `usuarios` - Dados de acesso ao sistema
- `colaboradores` - Informações dos colaboradores
- `departamentos` - Departamentos da empresa
- `cargos` - Cargos disponíveis
- `ferias` - Controle de férias
- `ponto` - Registros de ponto eletrônico
- `folha_pagamento` - Dados da folha de pagamento

## 🧪 Testes

### Backend

```bash
cd backend
./vendor/bin/phpunit
```

### Frontend

```bash
cd frontend
npm test
# ou
yarn test
```

## 📝 Variáveis de Ambiente

### Backend (.env)

```env
app.baseURL = 'http://localhost:8080'
database.default.hostname = localhost
database.default.database = dep_controller
database.default.username = root
database.default.password =
JWT_SECRET_KEY = sua_chave_secreta
```

### Frontend (.env)

```env
REACT_APP_API_URL=http://localhost:8080/api
REACT_APP_NAME=Departamento de Controle de RH
```

## 🤝 Contribuindo

Contribuições são sempre bem-vindas! Para contribuir:

1. Faça um fork do projeto
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## 📄 Licença

Este projeto está sob a licença MIT. Veja o arquivo [LICENSE](LICENSE) para mais detalhes.

## 👨‍💻 Autor

Desenvolvido com ❤️ para facilitar a gestão de Recursos Humanos.

## 📞 Suporte

Para dúvidas e suporte, abra uma issue no repositório ou entre em contato através do email: suporte@exemplo.com

---

**Departamento de Controle de RH** - Gestão Inteligente de Recursos Humanos
