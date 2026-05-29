```markdown
# 🏥 Sistema de Gestão RCC (Rede de Combate ao Câncer)

O **Sistema de Gestão RCC** é uma plataforma web desenvolvida em Python e Flask projetada para centralizar, automatizar e otimizar o acompanhamento assistencial e o prontuário de pacientes integrados à Rede de Combate ao Câncer[cite: 1]. O sistema substitui registros manuais por uma interface digital segura, permitindo o controle de cadastros, o histórico de atendimentos e a concessão de serviços e insumos médicos ou sociais[cite: 1].

---

## 🗺️ Mapa do Aplicativo (Fluxo de Navegação e Rotas)

O ecossistema de telas e o fluxo de permissões do aplicativo foram projetados de forma modular, separando a lógica de acesso do gerenciamento operacional dos pacientes[cite: 1]:


```

```
              ┌────────────────────────┐
              │     ponto de entrada   │
              │        (run.py)        │
              └───────────┬────────────┘
                          │
                          ▼
              ┌────────────────────────┐
              │        /login          │ ◄── Tela de Autenticação (templates/login.html)
              └───────────┬────────────┘
                          │
                          ▼ (Acesso Autorizado)
              ┌────────────────────────┐
              │        /listar         │ ◄── Painel Central / Busca de Pacientes (templates/listar.html)
              └───────────┬────────────┘
                          │
     ┌────────────────────┼────────────────────┐
     ▼                    ▼                    ▼

```

┌────────────────┐   ┌────────────────┐   ┌────────────────┐
│     /novo      │   │ /detalhes/ │   │  /editar/  │
│                │   │                │   │                │
│ Formulário de  │   │ Prontuário     │   │ Atualização e  │
│ cadastro de    │   │ completo e     │   │ correção de    │
│ novos pacientes│   │ histórico do   │   │ dados do       │
│ (templates/    │   │ paciente       │   │ paciente       │
│ novo.html)     │   │ (templates/    │   │ editar.html)   │
└────────────────┘   │ detalhes.html) │   └────────────────┘
└────────┬───────┘
│
▼
┌────────────────┐
│ /novo_servico  │
│                │
│ Registro de    │
│ novos auxílios/│
│ insumos        │
│ (templates/    │
│ novo_servico.h)│
└────────────────┘

```

### Detalhamento das Interfaces:
* **`/login` (`login.html`)**: Interface de segurança para controle de sessão e autenticação de usuários autorizados na plataforma[cite: 1].
* **`/listar` (`listar.html`)**: Painel principal que exibe a listagem geral das pessoas assistidas, servindo como o hub de busca central do sistema[cite: 1].
* **`/novo` (`novo.html`)**: Formulário estruturado para a inserção unificada de novos pacientes no banco de dados[cite: 1].
* **`/detalhes/<id>` (`detalhes.html`)**: Prontuário individualizado onde é possível visualizar dados cadastrais profundos e a linha do tempo de atendimentos do paciente[cite: 1].
* **`/editar/<id>` (`editar.html`)**: Tela dedicada à manutenção, correção de inconsistências e atualização de dados de cadastros preexistentes[cite: 1].
* **`/novo_servico` (`novo_servico.html`)**: Módulo de lançamento para associar novos atendimentos, medicamentos ou a entrega de cestas assistenciais diretamente ao histórico do paciente[cite: 1].

---

## 🛠️ Stack Tecnológica e Arquitetura

* **Back-end**: Python 3 e Flask Framework, utilizando o padrão de *Application Factory* para inicialização controlada do ecossistema[cite: 1].
* **Front-end**: Criação de interfaces limpas e responsivas utilizando HTML5 estruturado através do motor de renderização Jinja2 e folhas de estilo CSS3 customizadas[cite: 1].
* **Modularização (Blueprints)**: Divisão clara e isolada de responsabilidades de rotas entre o fluxo de autenticação (`auth_routes.py`) e as operações de gerenciamento de pacientes (`pessoa_routes.py`)[cite: 1].
* **Modelagem de Dados**: Abstração lógica das entidades do sistema centralizada em modelos orientados a objetos (`app/models/pessoa.py`)[cite: 1].

---

## 📁 Estrutura de Arquivos do Repositório

```text
gestao-rcc/
├── app/
│   ├── __init__.py          # Configuração do Application Factory do Flask
│   ├── models/
│   │   ├── __init__.py
│   │   └── pessoa.py        # Modelo lógico da entidade Paciente/Pessoa
│   └── routes/
│       ├── __init__.py
│       ├── auth_routes.py   # Gerenciamento de rotas de login, logout e sessão
│       └── pessoa_routes.py # Controle do CRUD de pacientes e vínculo de serviços
├── config.py                # Definições gerais de ambiente e chaves do sistema
├── docs/                    # Documentação de Engenharia e Metodologia do projeto
│   ├── evidences/           # Registros de versionamento e artefatos físicos do ciclo Git
│   ├── planning/            # Arquivos de Backlog, Visão do Projeto e Roadmap
│   └── workflow/            # Organização do time, fluxos de Kanban e Gantt
├── static/
│   └── style.css            # Estilização visual unificada e customizada do sistema
├── templates/               # Views em HTML renderizadas dinamicamente via Jinja2
├── requirements.txt         # Arquivo de dependências e bibliotecas Python
└── run.py                   # Script de execução principal do servidor web

```

---

## 🚀 Novos Updates (Recursos Recentes)

O projeto evoluiu significativamente em sua arquitetura interna e organização metodológica, com a implementação dos seguintes recursos:

* **Separação por Blueprints**: A arquitetura de rotas foi completamente desacoplada, dividindo o escopo de segurança (`auth_routes`) das regras de negócio operacionais (`pessoa_routes`), eliminando arquivos de código inflados e de difícil manutenção.


* **Rastreabilidade de Alterações**: Criação de telas completas para o ciclo CRUD, incluindo visualização detalhada de prontuário (`detalhes.html`) e edição dinâmica (`editar.html`).


* **Módulo de Lançamento de Serviços**: Inclusão do fluxo de cadastro de novos serviços (`novo_servico.html`), permitindo que a instituição registre a entrega de insumos e assistência de forma individualizada na ficha do paciente.


* **Governança Técnica e Repositório `/docs**`: Estruturação de uma pasta de documentação completa contendo guias de fluxo de trabalho para desenvolvimento vs. produção, organização de equipes, relatórios de participação no ciclo Git e planejamento visual.



---

## 🔮 O Futuro do Aplicativo (Roadmap & Próximos Passos)

O planejamento estratégico do sistema de "caiobraz-cmd/gestao-rcc" está estruturado para expansões em ciclos incrementais contínuos, utilizando os parâmetros definidos nos documentos de planejamento interno (`roadmap.md` e `backlog.md`):

### Próximas Implementações Técnicas:

1. **Conexão Direta com Banco de Dados de Produção**: Integração e mapeamento completo das tabelas lógicas diretamente em banco de dados relacional estável, superando a fase de dados locais.


2. **Sistema Automatizado de Alertas Assistenciais**: Desenvolvimento de um mecanismo inteligente para monitorar o intervalo de tempo desde a última assistência prestada (ex: controle de entrega mensal de insumos/cestas básicas). O sistema emitirá alertas visuais automáticos caso o paciente esteja elegível para um novo recebimento.


3. **Módulo de Relatórios e Auditoria (LGPD)**: Geração de relatórios gerenciais consolidados em PDF/CSV para prestação de contas da ONG e implementação de registros de logs de auditoria interna para assegurar a proteção de dados sensíveis de saúde dos pacientes.


4. **Pipeline de CI/CD e Deploy**: Configuração de rotinas automáticas de testes e publicação do aplicativo em servidores de nuvem para acesso externo seguro pelos colaboradores da Rede de Combate ao Câncer.



---

## ⚙️ Instalação e Execução Local

1. Clone o repositório em sua máquina local:



```bash
   git clone [https://github.com/seu-usuario/gestao-rcc.git](https://github.com/seu-usuario/gestao-rcc.git)
   cd gestao-rcc

```

2. Crie e ative um ambiente virtual isolado (`venv`):



```bash
   python -m venv venv
   source venv/bin/activate  # No Windows utilize: venv\Scripts\activate

```

3. Instale todas as dependências exigidas pelo projeto:



```bash
   pip install -r requirements.txt

```

4. Certifique-se de configurar as variáveis contidas no arquivo `config.py` e inicialize o servidor de desenvolvimento:



```bash
   python run.py

```

5. Acesse o sistema através do seu navegador no endereço: `http://127.0.0.1:5000`.



```

```
