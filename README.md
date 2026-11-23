Sample Flask Auth

API de autenticação e gerenciamento de usuários desenvolvida com Python, Flask e MySQL.

Sobre

O Sample Flask Auth é uma aplicação backend desenvolvida com Flask que implementa mecanismos de autenticação, gerenciamento de usuários e controle de acesso.

O projeto foi estruturado com foco na organização das responsabilidades, integração com banco de dados relacional e aplicação de conceitos fundamentais de segurança no desenvolvimento de APIs.

Tecnologias
Python e Flask: desenvolvimento da aplicação e disponibilização dos endpoints.
Flask-Login: gerenciamento de autenticação e sessões.
Flask-SQLAlchemy: comunicação e persistência de dados.
MySQL: armazenamento das informações dos usuários.
Bcrypt: proteção de senhas por meio de hash.
Docker Compose: configuração e inicialização do banco de dados.
Funcionalidades
Cadastro e gerenciamento de usuários.
Autenticação e encerramento de sessões.
Consulta de informações de usuários autenticados.
Atualização de senhas.
Controle de permissões por perfil de acesso (admin e user).
Integração com banco de dados MySQL.
Arquitetura

A aplicação possui uma estrutura modular, separando a lógica principal, a configuração do banco de dados e os modelos de entidades.

Arquivo	Responsabilidade
app.py	Inicialização da aplicação e definição das rotas
database.py	Configuração da conexão com o banco de dados
models/user.py	Modelo e estrutura dos usuários
docker-compose.yml	Configuração dos serviços em containers
requirements.txt	Dependências do projeto
Funcionamento

O fluxo de autenticação é baseado em sessões gerenciadas pelo Flask-Login.

Cadastro: o usuário informa suas credenciais, que são processadas e armazenadas no banco de dados.
Autenticação: as credenciais são verificadas e, quando válidas, uma sessão é iniciada.
Autorização: as rotas protegidas verificam a autenticação e as permissões do usuário.
Gerenciamento: usuários autorizados podem consultar, atualizar ou excluir registros conforme seu nível de acesso.
Logout: a sessão autenticada é encerrada.
Executando o projeto
Requisitos
Python instalado.
Docker e Docker Compose.
Git.
Instalação

Clone o repositório, instale as dependências e inicialize o banco de dados:

bash
git clone https://github.com/RhuannVictorC/sample-flask-auth.git
cd sample-flask-auth
pip install -r requirements.txt
docker compose up -d db


Após configurar o ambiente e inicializar as tabelas, execute a aplicação:

bash
python app.py


A aplicação estará disponível localmente em http://127.0.0.1:5000.

Exemplos de utilização

As principais operações disponibilizadas pela API são:

Método	Endpoint	Operação
POST	/user	Cadastro
POST	/login	Autenticação
GET	/logout	Encerramento da sessão
GET	/user/<id_user>	Consulta de usuário
PUT	/user/<id_user>	Atualização de senha
DELETE	/user/<id_user>	Exclusão de usuário

As requisições de cadastro e autenticação recebem as credenciais do usuário em formato JSON.

Exemplo de cadastro:

json
{
  "username": "usuario",
  "password": "senha"
}


As operações protegidas exigem uma sessão autenticada e respeitam as permissões associadas ao perfil do usuário.

Considerações de segurança

O projeto utiliza Bcrypt no cadastro de senhas e Flask-Login para gerenciamento de sessões.

Para utilização em ambientes de produção, recomenda-se aprimorar o gerenciamento de credenciais, proteger a chave secreta da aplicação, aplicar hash também na atualização de senhas e revisar as configurações de segurança das sessões.

Autor

Rhuann Victor

GitHub

Projeto desenvolvido para estudo e aplicação prática de conceitos de desenvolvimento backend, autenticação e gerenciamento de usuários com Python.
