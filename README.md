# 🎗️ Sistema de Gestão de Pacientes - Rede de Combate ao Câncer (RCC)

![Python](https://img.shields.io/badge/Python-3.8+-blue?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-3.0.0-black?logo=flask&logoColor=white)
![Oracle](https://img.shields.io/badge/Oracle_ORDS-API_REST-red?logo=oracle&logoColor=white)
![Status](https://img.shields.io/badge/Status-Em_Desenvolvimento-success)

## 📋 Sobre o Projeto

O **Sistema de Gestão RCC** é uma aplicação web dedicada a otimizar o acompanhamento e cuidado de pacientes oncológicos. Desenvolvido para centralizar informações cruciais, o sistema permite que a equipe da Rede de Combate ao Câncer gerencie desde dados cadastrais básicos até históricos complexos de tratamentos e serviços prestados de forma ágil e segura.

A aplicação consome uma API RESTful provida pelo **Oracle ORDS**, garantindo que as regras de negócio do banco de dados estejam desacopladas da interface web.

### ✨ Principais Funcionalidades

* **Gestão de Pacientes:** Cadastro, leitura, atualização e exclusão (CRUD) de dados pessoais e de contato.
* **Prontuário e Histórico Médico:** Registro detalhado de diagnósticos, tratamentos em andamento, medicamentos de uso contínuo e alergias.
* **Controle de Serviços Prestados:** Histórico de todos os serviços e assistências fornecidas pela instituição a cada paciente.
* **Integração REST:** Comunicação assíncrona e segura com o banco de dados Oracle via API.

---

## 🚀 Tecnologias e Stack

As versões das dependências principais do projeto são:
* **Flask 3.0.0** - Framework web principal.
* **Requests 2.31.0** - Cliente HTTP para consumo da API Oracle ORDS.
* **Werkzeug 3.0.1** - Biblioteca WSGI utilitária para o Flask.
* **python-dotenv 1.0.0** - Gerenciamento de variáveis de ambiente.
* **Jinja2** - Engine de renderização de templates HTML.

---

## 🏗️ Arquitetura do Projeto

O projeto utiliza o padrão **Application Factory** (`create_app`) e **Blueprints**, o que garante alta escalabilidade, facilitando a adição de novos módulos no futuro sem quebrar o código existente.

```text
gestao-rcc/
│
├── app/                          # Core da aplicação
│   ├── __init__.py               # Factory de inicialização (create_app)
│   ├── models/                   # Lógica de negócio e estrutura de dados
│   │   ├── __init__.py
│   │   └── pessoa.py             # Classe/Modelo de mapeamento de Pessoa
│   └── routes/                   # Controladores (Blueprints)
│       ├── __init__.py
│       └── pessoa_routes.py      # Endpoints para CRUD de pacientes e serviços
│
├── templates/                    # Telas renderizadas pelo Jinja2
│   ├── base.html                 # Estrutura matriz (Header, Footer, Nav)
│   ├── listar.html               # Datatable de pacientes cadastrados
│   ├── novo.html                 # Formulário de entrada de paciente
│   ├── editar.html               # Formulário de atualização
│   ├── detalhes.html             # Visão 360º do paciente e seu prontuário
│   └── novo_servico.html         # Formulário de registro de novos serviços
│
├── static/                       # Assets estáticos
│   └── style.css                 # Folhas de estilo customizadas
│
├── config.py                     # Central de configurações dinâmicas
├── run.py                        # Entrypoint para ambiente de desenvolvimento
├── requirements.txt              # Mapeamento de dependências
├── .env                          # Variáveis sensíveis de ambiente (NÃO VERSIONAR)
└── .gitignore                    # Regras de exclusão do Git
