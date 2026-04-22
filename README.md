# 🚀 Azure MySQL + Power BI | Integração e Transformação de Dados

![Power BI](https://img.shields.io/badge/Power%20BI-Data%20Analysis-yellow)
![Azure](https://img.shields.io/badge/Azure-Cloud-blue)
![MySQL](https://img.shields.io/badge/MySQL-Database-orange)
![Status](https://img.shields.io/badge/Status-Concluído-success)

---

## 📌 Descrição do Projeto

Projeto prático com foco na criação, integração e transformação de dados utilizando **MySQL no Azure** e **Power BI**.

O objetivo principal foi construir um pipeline de dados completo, desde a criação do banco até o tratamento e preparação dos dados para análise (ETL).

> ⚠️ Este projeto não contempla a criação de dashboards, tendo como foco a modelagem, integração e transformação de dados.

---

## 🎯 Etapas do Projeto

### 🔹 1. Criação da instância no Azure
- Criação de um servidor MySQL no Microsoft Azure
- Configuração de acesso e firewall
- Conexão via Azure Cloud Shell e MySQL Workbench

---

### 🔹 2. Criação do banco de dados
- Criação do schema `azure_company`
- Implementação das tabelas com:
  - Chaves primárias
  - Chaves estrangeiras
  - Constraints
- Inserção dos dados respeitando integridade referencial

📁 Scripts disponíveis:
- `sql/create_database.sql`
- `sql/insert_data.sql`

---

### 🔹 3. Integração com Power BI
- Conexão do Power BI Desktop com banco MySQL no Azure
- Utilização do conector nativo MySQL
- Importação das tabelas para o Power Query

---

### 🔹 4. Transformação dos dados (ETL)

As transformações foram realizadas no **Power Query**, incluindo:

### ✔️ Tratamento inicial
- Verificação de cabeçalhos e tipos de dados
- Ajuste de colunas numéricas (Salary e Hours)
- Identificação de valores nulos

---

### ✔️ Análise de dados faltantes
- Identificação de colaboradores sem gerente (`Super_ssn`)
- Validação de departamentos com gerente
- Tratamento de inconsistências

---

### ✔️ Separação de colunas
- Coluna `Address` foi dividida em:
  - Número
  - Rua
  - Cidade
  - Estado

---

### ✔️ Mesclagem de tabelas (Merge)

#### 📌 O que é mesclar?
Mesclar consultas é o processo de combinar tabelas com base em colunas relacionadas, semelhante a um **JOIN no SQL**.

---

### ✔️ Aplicação da mescla

Foi realizada a mescla entre:
- `employee` (base principal)
- `departament`

🔗 Chaves utilizadas:
- `employee.Dno`
- `departament.Dnumber`

📌 Tipo de junção:
- **Externa esquerda (Left Join)**

➡️ Mantém todos os colaboradores, mesmo sem correspondência

---

### ❗ Por que usar mesclar e não combinar?

- **Mesclar (Merge):** junta tabelas lado a lado (JOIN)
- **Combinar (Append):** empilha tabelas (UNION)

👉 Neste caso, era necessário enriquecer os dados dos colaboradores, não empilhar dados.

---

### ✔️ Expansão de dados
- Expansão da coluna mesclada para trazer o nome do departamento (`Dname`)

---

### ✔️ Limpeza de dados
- Remoção de colunas desnecessárias
- Padronização dos dados

---

### ✔️ Junção colaborador x gerente
- Relacionamento entre colaborador e gerente utilizando `Super_ssn`
- Estrutura similar a **Self Join**

---

### ✔️ Criação de colunas derivadas

- Nome completo do colaborador:
  - Mescla de `Fname` + `Lname`

---

### ✔️ Modelagem para futuro (Star Schema)

- Criação de combinação única:
  - **Departamento + Localização**

➡️ Facilita modelagem dimensional futura

---

## 🛠️ Tecnologias Utilizadas

- Microsoft Azure (MySQL Flexible Server)
- MySQL
- Power BI Desktop
- Power Query (ETL)

---

## 📂 Estrutura do Repositório

```text
azure-mysql-powerbi-data-integration/
│
├── transformacao-dados.pbix
├── sql/
│   ├── create_database.sql
│   └── insert_data.sql
└── README.md
```

---

## 📌 Considerações Finais

Este projeto demonstra habilidades em:

- Modelagem de banco de dados
- SQL e integridade referencial
- Integração com serviços em nuvem (Azure)
- Processos de ETL com Power BI
- Transformação e preparação de dados para análise

---

## 💡 Próximos passos (evolução do projeto)

- Criação de modelo estrela (Star Schema)
- Desenvolvimento de dashboards no Power BI
- Publicação no Power BI Service
- Análises com KPIs

---

## 👩‍💻 Autora

**Jamile Alves Serra**

Projeto desenvolvido como desafio prático da DIO (Digital Innovation One), abordando criação de banco de dados no Azure, integração com Power BI e processos de ETL.
