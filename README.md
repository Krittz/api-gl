# 🐐 Backend da Plataforma AgroTech

Este é o backend de uma aplicação agropecuária moderna, desenvolvida em **Go** com o framework **Gin**, seguindo princípios de arquitetura limpa e segurança robusta com **JWT via cookies HTTP-only**.

---

## 🛠️ Tecnologias Utilizadas

| Categoria         | Tecnologias                                |
|------------------|---------------------------------------------|
| **Linguagem**     | [Go](https://golang.org/)                  |
| **Framework**     | [Gin](https://gin-gonic.com/)              |
| **Banco de Dados**| [MySQL](https://www.mysql.com/)            |
| **Autenticação**  | JWT + Cookies HTTP-only                    |
| **PDF**           | [go-wkhtmltopdf](https://github.com/SebastiaanKlippert/go-wkhtmltopdf) |
| **Excel**         | [excelize](https://github.com/qax-os/excelize) |

---

## 📐 Estrutura do Projeto

A aplicação é organizada em camadas, seguindo princípios de **separação de responsabilidades**, **escalabilidade** e **testabilidade**:

```
/internal
│
├── /domain
│   ├── /entities       → Structs que representam os modelos do negócio (ex.: User, Animal)
│   ├── /dto            → Objetos de transferência de dados (entrada/saída)
│
├── /repository         → Interface e implementação de acesso ao banco de dados (SQLx)
│
├── /service            → Lógica de negócio e validações
│
├── /handler            → Endpoints HTTP e controllers
│
├── /middleware         → Autenticação JWT, logging, CORS etc.
│
├── /util               → Funções auxiliares, helpers e ferramentas
│
├── /report             → Geração de relatórios em PDF e Excel
│
└── /tests              → Testes unitários, de integração e mocks
```

---

## 🔐 Autenticação Segura

- Tokens JWT gerados no login.
- Armazenamento via **cookies HTTP-only**, evitando exposição ao JavaScript.
- Sem uso de `localStorage` ou `sessionStorage`.
- Todos os endpoints protegidos validam o token presente no cookie.

---

## 👤 Endpoints de Usuário (Módulo Inicial)

| Método | Rota              | Descrição                            |
|--------|-------------------|--------------------------------------|
| `POST` | `/auth/register`  | Cadastro de novos usuários           |
| `POST` | `/auth/login`     | Autenticação e retorno do JWT        |
| `GET`  | `/users/me`       | Retorna os dados do usuário logado   |

---

## 🧪 Validações

As validações são rigorosas e seguem boas práticas tanto em segurança quanto em integridade de dados:

- **Backend**
  - E-mail único
  - Senha forte (mínimo de caracteres, letras, números e símbolos)
  - Dados obrigatórios
- **Frontend**
  - Validações básicas para evitar requisições desnecessárias

---

## 📊 Exportação de Relatórios

A API permite exportação de dados diretamente do backend, com suporte aos formatos:

- **PDF** via `go-wkhtmltopdf` (HTML + CSS para visual profissional)
- **Excel** via `excelize` (planilhas com múltiplas abas e formatações)

---

## 🧱 Módulos Planejados

Além do módulo de **usuários**, serão implementados:

- **Animais** (cadastro, evolução, saúde)
- **Propriedades** (registro de fazendas e áreas)
- **Produção** (controle de leite, carne, etc.)
- **Financeiro** (custos, receitas, relatórios mensais)

---

## 📌 Observações

- A aplicação utiliza **SQL puro com SQLx**, sem ORM, para máxima performance e controle.
- A estrutura é preparada para expansão com suporte futuro a **multi-tenant** e **multi-linguagem**.
- Suporte completo a testes automatizados e integração contínua planejados para próxima fase.

---

## 🚀 Como Executar Localmente

```bash
# Clone o repositório
git clone https://github.com/krittz/api-gl.git
cd api-gl

# Crie o arquivo .env com as variáveis de conexão

# Execute a aplicação
go run cmd/server/main.go
```

---

## 🧑‍💻 Autor & Coautoria

**Desenvolvido por:** Cristian Alves Silva  


---

## 📬 Contato

📧 contato@kodificar.com.br  
🌐 https://kodificar.com.br

---

> Projeto em constante evolução. Contribuições são bem-vindas!