# 🗄️ SQL vs NoSQL: O Papel dos Bancos de Dados na Engenharia de Dados

Este repositório documenta os conceitos, definições e insights sobre o uso de Bancos de Dados Relacionais (SQL) e Não Relacionais (NoSQL) sob a ótica da Engenharia de Dados. O objetivo é compreender quando, como e por que utilizar cada paradigma na construção de arquiteturas de dados escaláveis e eficientes.

## 📌 1. Bancos de Dados Relacionais (SQL)

Os bancos de dados relacionais organizam os dados em tabelas (linhas e colunas) com esquemas rigidamente definidos. Eles utilizam a linguagem padrão ANSI SQL para consultas e manipulação.

### Conceitos-Chave
* **ACID (Atomicidade, Consistência, Isolamento, Durabilidade):** Garantem que as transações sejam processadas de forma confiável e segura. Se uma parte da transação falhar, toda a transação falha (Rollback).
* **Schema-on-Write:** A estrutura do dado (tabelas, tipos de dados, restrições) deve ser definida *antes* da inserção do dado.
* **Normalização:** Processo de estruturação de um banco de dados para reduzir a redundância de dados e melhorar a integridade.

### O Papel na Engenharia de Dados
* **Data Warehouses:** Ferramentas baseadas em relacionamentos são a espinha dorsal de armazéns de dados estruturados para Business Intelligence (BI).
* **Casos de Uso Práticos:** Armazenamento de transações financeiras, cadastros de clientes, históricos de pedidos e dados de ERPs. Devido à garantia ACID, são cruciais quando a precisão matemática e a consistência absoluta são inegociáveis.

---

## 📌 2. Bancos de Dados Não Relacionais (NoSQL)

Surgiram para resolver problemas de escalabilidade horizontal e flexibilidade que os bancos SQL tradicionais tinham dificuldade em lidar na era do Big Data.

### Conceitos-Chave
* **Teorema CAP:** Em sistemas distribuídos, você só pode garantir duas das três propriedades simultaneamente: Consistência (Consistency), Disponibilidade (Availability) e Tolerância ao Particionamento (Partition tolerance).
* **BASE (Basically Available, Soft state, Eventual consistency):** Foca na disponibilidade e permite que o sistema fique temporariamente inconsistente, desde que alcance a consistência eventualmente.
* **Schema-on-Read:** Os dados podem ser ingeridos sem uma estrutura pré-definida. A estrutura é aplicada apenas no momento em que o dado é lido/consultado.

### Principais Tipos de NoSQL
1. **Chave-Valor (Key-Value):** Alta velocidade para leituras simples (ex: Redis, DynamoDB).
2. **Documentos:** Armazenam dados em formato JSON/BSON, ideais para estruturas flexíveis (ex: MongoDB).
3. **Grafos:** Focados em relacionamentos complexos entre entidades (ex: Neo4j).
4. **Colunares (Wide-Column):** Otimizados para leitura e gravação rápida em grandes volumes de dados (ex: Cassandra, HBase).

### O Papel na Engenharia de Dados
* **Ingestão Massiva:** Engenheiros utilizam NoSQL para lidar com os 3 V's do Big Data (Volume, Variedade e Velocidade).
* **Casos de Uso Práticos:** Captura de logs em tempo real, armazenamento de dados de redes sociais, catálogos de produtos dinâmicos, IoT (Internet das Coisas) e sistemas de recomendação.

---

## ⚖️ 3. Tabela Comparativa: SQL vs NoSQL

| Característica | Bancos Relacionais (SQL) | Bancos Não Relacionais (NoSQL) |
| :--- | :--- | :--- |
| **Estrutura** | Tabelas, Linhas e Colunas | Chave-valor, Documentos, Grafos, Colunares |
| **Esquema** | Rígido (Schema-on-Write) | Flexível / Dinâmico (Schema-on-Read) |
| **Escalabilidade**| Vertical (Aumentar CPU/RAM do servidor) | Horizontal (Adicionar mais servidores/nós) |
| **Garantias** | Transações ACID | Foco no Teorema CAP e modelo BASE |
| **Consultas** | Padrão SQL (Queries com JOINs) | APIs específicas, linguagens próprias do BD |
| **Cenário Ideal** | Dados estruturados, integridade crítica | Big Data, dados não estruturados, alta velocidade |

---

## 🚀 4. A Visão do Engenheiro de Dados: Polyglot Persistence

O papel do Engenheiro de Dados não é escolher um lado como "o melhor", mas sim arquitetar soluções poliglotas (**Polyglot Persistence**). Um pipeline de dados moderno geralmente utiliza ambos os mundos:

1. **Ingestão (Data Lake / Raw Zone):** Um banco NoSQL ou Storage de Objetos recebe o fluxo massivo e não estruturado de logs e eventos brutos.
2. **Processamento e Transformação (ETL/ELT):** O pipeline processa e limpa esses dados.
3. **Serviço (Data Warehouse / Serving Zone):** Os dados refinados são estruturados e carregados em bancos relacionais ou colunares para que Cientistas de Dados e Analistas de BI possam consumi-los com eficiência utilizando SQL.

---
*Desafio resolvido como parte do portfólio de estudos em Engenharia de Dados.*
