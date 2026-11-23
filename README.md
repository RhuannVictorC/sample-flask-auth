🔐 Sample Flask Auth

<p align="center">
<strong>API REST de autenticação e gerenciamento de usuários com Python, Flask e MySQL.</strong>
</p>

<p align="center">
<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
<img src="https://img.shields.io/badge/Flask-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask"/>
<img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white" alt="MySQL"/>
<img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" alt="Docker"/>
<img src="https://img.shields.io/badge/Bcrypt-Security-orange?style=for-the-badge" alt="Bcrypt"/>
</p>

📌 Sobre o projeto

O Sample Flask Auth é uma API REST desenvolvida em Python utilizando Flask, com o objetivo de implementar um sistema de autenticação e gerenciamento de usuários.

O projeto utiliza Flask-Login para gerenciamento de sessões, Bcrypt para hash de senhas e MySQL como banco de dados relacional, integrado através do Flask-SQLAlchemy.

Além da autenticação, a aplicação possui controle de acesso baseado em papéis (Role-Based Access Control), diferenciando usuários comuns de administradores.

🚀 Funcionalidades
Cadastro de usuários.
Autenticação utilizando usuário e senha.
Hash de senhas utilizando Bcrypt no cadastro.
Gerenciamento de sessões com Flask-Login.
Logout de usuários autenticados.
Consulta de informações de usuários.
Atualização de senha.
Exclusão de usuários.
Controle de permissões por perfil (admin e user).
Integração com banco de dados MySQL.
🛠️ Tecnologias utilizadas
Tecnologia	Utilização
Python	Linguagem principal
Flask	Framework para construção da API
Flask-Login	Gerenciamento de autenticação e sessões
Flask-SQLAlchemy	ORM para interação com o banco
MySQL	Banco de dados relacional
Bcrypt	Hash e verificação de senhas
Docker Compose	Inicialização do banco de dados
📂 Estrutura do projeto
text
sample-flask-auth/
│
├── models/
│   └── user.py
│
├── app.py
├── database.py
├── docker-compose.yml
├── requirements.txt
└── README.md

⚙️ Como executar o projeto
Pré-requisitos

Antes de começar, você precisará ter instalado:

Python
Docker
Docker Compose
Git
1. Clone o repositório
bash
git clone https://github.com/RhuannVictorC/sample-flask-auth.git


Entre na pasta do projeto:

bash
cd sample-flask-auth

2. Crie um ambiente virtual
bash
python -m venv venv


Ative o ambiente virtual:

Windows:

bash
venv\Scripts\activate


Linux / macOS:

bash
source venv/bin/activate

3. Instale as dependências
bash
pip install -r requirements.txt

4. Inicialize o banco de dados

Utilize o Docker Compose para iniciar o MySQL:

bash
docker compose up -d db


Aguarde o banco de dados estar pronto para receber conexões.

Configuração atual do banco:

Configuração	Valor
Host	127.0.0.1
Porta	3306
Database	flask-crud
Usuário	root
Senha	admin123
Essas são as configurações presentes atualmente no código e no Docker Compose. Altere-as antes de utilizar o projeto em um ambiente real.
5. Crie as tabelas

Com o banco disponível, execute:

bash
python -c "from app import app, db; app.app_context().push(); db.create_all()"

6. Execute a aplicação
bash
python app.py


A API estará disponível em:

text
http://127.0.0.1:5000

📡 Endpoints da API
Método	Endpoint	Descrição	Autenticação
POST	/user	Cadastrar usuário	Não
POST	/login	Autenticar usuário	Não
GET	/logout	Encerrar sessão	Sim
GET	/user/<id_user>	Consultar usuário	Sim
PUT	/user/<id_user>	Atualizar senha	Sim
DELETE	/user/<id_user>	Excluir usuário	Sim, admin
Exemplos de utilização

1. Cadastro de usuário

POST /user

json
{
  "username": "usuario",
  "password": "senha123"
}


2. Login

POST /login

json
{
  "username": "usuario",
  "password": "senha123"
}


Resposta esperada:

json
{
  "message": "Autenticação realizada com sucesso."
}


3. Consultar usuário

GET /user/1

Resposta esperada:

json
{
  "username": "usuario"
}


4. Atualizar senha

PUT /user/1

json
{
  "password": "nova_senha123"
}


5. Logout

GET /logout

Resposta esperada:

json
{
  "message": "Logout realizado com sucesso!"
}

As rotas protegidas utilizam a sessão gerenciada pelo Flask-Login. Portanto, o cliente HTTP precisa preservar os cookies recebidos durante o login.
🔑 Controle de permissões

A aplicação possui dois níveis de acesso:

Perfil	Permissões
user	Consultar usuários e atualizar a própria senha
admin	Possui permissões adicionais, incluindo exclusão de usuários

O cadastro de novos usuários atribui automaticamente o perfil user.

🔒 Segurança

O projeto utiliza Bcrypt para proteger as senhas durante o cadastro e Flask-Login para controlar as sessões autenticadas.

Atenção: antes de utilizar a aplicação em produção, alguns pontos precisam ser aprimorados:

Armazenar a SECRET_KEY em variável de ambiente.
Remover credenciais fixas do código-fonte.
Aplicar hash Bcrypt também na atualização de senhas.
Validar melhor os dados recebidos pela API.
Configurar HTTPS e cookies seguros.
Revisar as permissões e os controles de acesso.
📚 Objetivo

Este projeto foi desenvolvido com o propósito de praticar e demonstrar conceitos de desenvolvimento backend com Python, incluindo:

Construção de APIs REST.
Autenticação e gerenciamento de sessões.
Persistência de dados com ORM.
Criptografia de senhas com hash.
Controle de acesso baseado em papéis.
Containerização de serviços com Docker.
👨‍💻 Autor

Rhuann Victor

GitHub: @RhuannVictorC
