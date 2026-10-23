# 🔧 Sistema de Oficina Mecânica — SAEP / SENAI

Sistema web desenvolvido para gerenciamento de uma oficina mecânica, seguindo as orientações do projeto proposto no SAEP / SENAI.

O sistema permite realizar o gerenciamento de **usuários, clientes, veículos e agendamentos de serviços**, utilizando banco de dados MySQL e uma aplicação web desenvolvida em Python com Flask.

---

## 📌 Objetivo do Projeto

O objetivo do projeto é desenvolver um sistema para auxiliar no controle das atividades de uma oficina mecânica.

A aplicação permite:

- 🔐 Realizar login de funcionários;
- 👥 Cadastrar e gerenciar clientes;
- 🚗 Cadastrar e gerenciar veículos;
- 📅 Cadastrar e alterar agendamentos;
- 🗄️ Armazenar os dados em banco de dados MySQL;
- 🔒 Utilizar Bcrypt para proteção de senhas e dados sensíveis;
- 🌐 Disponibilizar uma interface web para utilização do sistema.

---

## 🛠️ Tecnologias Utilizadas

O projeto utiliza as seguintes tecnologias:

- **Python**
- **Flask**
- **MySQL**
- **Bcrypt**
- **HTML5**
- **CSS3**
- **JavaScript**

As versões definidas na guia são:

```text
Flask==3.0.3
mysql-connector-python==8.4.0
bcrypt==4.1.3
Werkzeug==3.0.3
```

---

## 📁 Estrutura do Projeto

A estrutura principal definida pela guia é:

```text
oficina_mecanica/
│
├── saep_db.sql
│
└── sistema/
    ├── app.py
    ├── banco.py
    ├── autenticacao.py
    ├── clientes.py
    ├── veiculos.py
    ├── agendamento.py
    ├── rotas.py
    ├── requirements.txt
    │
    ├── templates/
    │   ├── base.html
    │   ├── login.html
    │   ├── dashboard.html
    │   ├── clientes.html
    │   ├── veiculos.html
    │   └── agendamentos.html
    │
    └── static/
        ├── css/
        │   └── style.css
        │
        └── js/
            └── main.js
```

---

# 🚀 Fases do Desenvolvimento

## Fase 0 — Estrutura de Pastas

Foi criada a estrutura principal do projeto, contendo a pasta `sistema`, os templates HTML e os arquivos estáticos de CSS e JavaScript.

---

## Fase 1 — Ambiente Python

Foi configurado um ambiente virtual para manter as dependências do projeto isoladas.

As principais bibliotecas utilizadas são:

- Flask;
- MySQL Connector;
- Bcrypt;
- Werkzeug.

---

## Fase 2 — Banco de Dados

O banco de dados utilizado pelo projeto é o **MySQL**.

O arquivo:

```text
saep_db.sql
```

é responsável pela criação do banco `saep_db` e suas tabelas.

As principais tabelas são:

- `usuarios`
- `clientes`
- `veiculos`
- `agendamentos`

O banco utiliza relacionamentos entre clientes, veículos e agendamentos.

---

## Fase 3 — Conexão com o Banco

O arquivo:

```text
sistema/banco.py
```

é responsável pela conexão da aplicação Python com o banco de dados MySQL.

Também existe um teste de conexão para verificar se o banco está funcionando corretamente.

---

## Fase 4 — Autenticação

O arquivo:

```text
sistema/autenticacao.py
```

é responsável pelo sistema de login.

As senhas são protegidas utilizando **Bcrypt**.

O sistema também possui controle de sessão para impedir que usuários não autenticados acessem as páginas internas.

---

## Fase 5 — Clientes

O módulo:

```text
sistema/clientes.py
```

é responsável pelo gerenciamento dos clientes.

Entre as regras do projeto está a validação do CPF considerando **11 dígitos**.

O CPF também possui tratamento de proteção utilizando Bcrypt, conforme a regra de proteção de dados indicada na guia.

O módulo permite:

- Cadastrar clientes;
- Listar clientes;
- Pesquisar clientes;
- Editar clientes;
- Excluir clientes.

---

## Fase 6 — Veículos

O arquivo:

```text
sistema/veiculos.py
```

gerencia os veículos cadastrados.

Cada veículo deve obrigatoriamente estar relacionado a um cliente.

São armazenadas informações como:

- Placa;
- Marca;
- Modelo;
- Ano;
- Cor;
- Quilometragem.

O banco utiliza uma chave estrangeira para relacionar o veículo ao cliente.

---

## Fase 7 — Agendamentos

O arquivo:

```text
sistema/agendamento.py
```

é responsável pelos serviços agendados.

Os agendamentos são apresentados em ordem cronológica e possuem informações relacionadas ao cliente e ao veículo.

O sistema também permite alterar a data de um agendamento já cadastrado, salvando a alteração no banco de dados. 

---

## Fase 8 — Rotas

O arquivo:

```text
sistema/rotas.py
```

é responsável por conectar as funcionalidades do sistema às páginas web.

Entre as rotas estão:

```text
/login
/logout
/dashboard
/clientes
/veiculos
/agendamentos
```

O módulo também controla a autenticação e a validade da sessão do usuário. 

---

## Fase 9 — Aplicação Flask

O arquivo principal da aplicação é:

```text
sistema/app.py
```

Ele cria a aplicação Flask, configura a chave da sessão e registra as rotas.

A guia determina um tempo de expiração da sessão de **15 minutos**.

Para iniciar o sistema:

```cmd
python sistema\app.py
```

Quando o servidor estiver funcionando, será disponibilizado:

```text
http://127.0.0.1:5000
```

---

## Fase 10 — Interface

A interface do sistema utiliza:

- HTML5;
- CSS3;
- JavaScript puro.

Os arquivos HTML ficam dentro de:

```text
sistema/templates/
```

Os arquivos CSS ficam em:

```text
sistema/static/css/
```

E os arquivos JavaScript ficam em:

```text
sistema/static/js/
```

O arquivo `base.html` funciona como estrutura principal das páginas, apresentando o usuário conectado, navegação e botão de logout.

---

# 🔐 Usuários para Teste

O banco possui usuários cadastrados para testar o sistema.

### Administrador

```text
Login: admin
Senha: admin123
```

### Mecânico

```text
Login: mecanico
Senha: senha123
```

### Recepção

```text
Login: recepcao
Senha: rec123
```

Esses usuários fazem parte dos dados iniciais definidos no banco do projeto.

---

# ▶️ Como Executar o Projeto

## 1. Abrir o terminal

Abra o CMD ou o terminal integrado do VS Code.

Entre na pasta principal do projeto:

```cmd
cd caminho\da\pasta\oficina_mecanica
```

## 2. Ativar o ambiente virtual

No Windows:

```cmd
venv\Scripts\activate
```

## 3. Instalar as dependências

```cmd
pip install -r sistema\requirements.txt
```

## 4. Configurar o banco de dados

Execute o arquivo:

```text
saep_db.sql
```

no MySQL para criar o banco e as tabelas.

## 5. Testar a conexão

Execute:

```cmd
python sistema\banco.py
```

Se a conexão estiver funcionando, será apresentada uma mensagem de sucesso.

## 6. Iniciar o sistema

Execute:

```cmd
python sistema\app.py
```

Depois abra no navegador:

```text
http://127.0.0.1:5000
```

---

# 🧪 Testes do Sistema

A guia possui uma etapa final destinada à validação das regras do sistema.

Devem ser testados:

### Login

- Senha incorreta deve impedir o acesso;
- `admin / admin123` deve permitir a entrada;
- O usuário conectado deve aparecer na interface;
- O logout deve retornar para a tela de login.

### Clientes

- CPF com quantidade incorreta de dígitos deve ser bloqueado;
- CPF com 11 dígitos deve ser aceito;
- Deve ser possível pesquisar clientes;
- Deve ser possível editar clientes.

### Veículos

- Deve ser possível cadastrar veículos;
- O cliente deve ser obrigatório;
- Deve ser possível editar veículos.

### Agendamentos

- Os agendamentos devem aparecer organizados por data;
- Deve ser possível alterar a data;
- A alteração deve ser salva no banco de dados.

---

# 🎯 Resultado Esperado

Ao final do projeto, deve existir uma aplicação web funcional para gerenciamento de uma oficina mecânica.

O sistema deve permitir que funcionários autenticados gerenciem clientes, veículos e agendamentos, utilizando uma interface web integrada a um banco de dados MySQL.

---

## 👨‍💻 Projeto Acadêmico

**Projeto:** Sistema de Oficina Mecânica  
**Programa:** SAEP / SENAI  
**Tecnologias:** Python, Flask, MySQL, Bcrypt, HTML5, CSS3 e JavaScript

---

## 📚 Referência

Projeto desenvolvido seguindo a **Guia Definitiva Passo a Passo & Linha a Linha — Desenvolvimento do Sistema para Oficina Mecânica (SAEP / SENAI)**, que organiza o desenvolvimento em 12 fases, da criação da estrutura até os testes e validação das regras de negócio.
