# ☁️ Serviços de Armazenamento AWS – Amazon S3 e Amazon Glacier

## 📘 Introdução

O armazenamento em nuvem é um dos pilares da AWS.
Os serviços **Amazon S3** e **Amazon Glacier** fornecem soluções escaláveis, seguras e econômicas para armazenar desde dados de acesso frequente até arquivos de arquivamento de longo prazo.

Este documento reúne anotações sobre o funcionamento, características e casos de uso de ambos os serviços.

---

## 🧱 Amazon S3 (Simple Storage Service)

### 🧠 O que é o Amazon S3?

O **Amazon S3** é um serviço de **armazenamento de objetos** na nuvem, ideal para **armazenar, organizar e recuperar grandes volumes de dados** de forma **segura, escalável e durável**.

Cada arquivo armazenado é chamado de **objeto**, e cada conjunto de objetos fica dentro de um **bucket** (um contêiner com nome globalmente único).

---

### ⚙️ Características Principais

* **Armazenamento de Objetos:** Cada arquivo é armazenado com metadados e um identificador único.
* **Buckets:** Contêineres onde os objetos são organizados.
* **Escalabilidade:** Capacidade quase ilimitada de armazenamento.
* **Durabilidade:** Projetado para **99,999999999% (11 noves)** de durabilidade.
* **Disponibilidade:** 99,99% em múltiplas zonas de disponibilidade.
* **Segurança:**

  * Criptografia **em repouso e em trânsito**.
  * Controle de acesso granular via **IAM Policies** e **Access Control Lists (ACLs)**.

---

### 🧩 Classes de Armazenamento

| Classe                                 | Descrição                                                                   | Caso de Uso                               |
| -------------------------------------- | --------------------------------------------------------------------------- | ----------------------------------------- |
| **S3 Standard**                        | Acesso frequente, alta durabilidade e baixa latência                        | Sites, arquivos ativos, backups recentes  |
| **S3 Intelligent-Tiering**             | Move automaticamente objetos entre classes com base na frequência de acesso | Dados com padrões de acesso imprevisíveis |
| **S3 Standard-IA (Infrequent Access)** | Dados acessados ocasionalmente                                              | Backups e logs                            |
| **S3 Glacier**                         | Armazenamento de longo prazo e baixo custo                                  | Arquivos raramente acessados              |
| **S3 Glacier Deep Archive**            | Menor custo e maior tempo de recuperação                                    | Arquivamento de longo prazo               |
| **S3 One Zone-IA**                     | Armazenamento em uma única zona de disponibilidade                          | Dados não críticos                        |

---

### 🔒 Políticas de Acesso

* As políticas do S3 controlam quem pode acessar ou modificar dados.
* São escritas em formato **JSON**, definindo permissões detalhadas.
* Integração com o **IAM (Identity and Access Management)** permite criar políticas para buckets e objetos.
* Exemplo: política para **tornar um bucket público** ou restringir acesso a um **usuário específico**.

> ⚠️ *Evite tornar buckets públicos sem necessidade; isso pode expor dados sensíveis.*

---

### 💡 Vantagens do Amazon S3

* Alta durabilidade e segurança.
* Integração com vários serviços AWS (EC2, Lambda, CloudFront).
* Armazenamento ilimitado.
* Custo ajustável com base na classe de armazenamento.
* Ideal para aplicações web, backups e Big Data.

---

## ❄️ Amazon Glacier – Armazenamento de Longo Prazo

### 🧠 O que é o Amazon Glacier?

O **Amazon Glacier** (agora parte das classes do S3) oferece **armazenamento de baixo custo** para dados que **não precisam ser acessados com frequência**.
É ideal para **arquivamento** e **retenção de longo prazo**, mantendo a mesma durabilidade e segurança do S3.

---

### ⚙️ Características Principais

* Pertence à família de **classes do Amazon S3**.
* Ideal para armazenar dados que são acessados **após dias ou meses**.
* Projetado para **reduzir custos** de armazenamento.
* Mantém **99,999999999%** de durabilidade, assim como o S3.
* Recuperação de dados **entre 3 a 5 horas** (S3 Glacier) ou até **12 horas** (S3 Glacier Deep Archive).

---

### 🧩 Casos de Uso

* Armazenamento de arquivos digitais antigos.
* Dados científicos e históricos.
* Arquivamento de informações médicas e de conformidade regulatória.
* Backup de longo prazo de logs e relatórios empresariais.

---

### 💰 Preços e Duração

| Classe                      | Tempo mínimo de armazenamento | Tempo de recuperação | Custo aproximado |
| --------------------------- | ----------------------------- | -------------------- | ---------------- |
| **S3 Glacier**              | 90 dias                       | 3 a 5 horas          | US$ 0,01/GB      |
| **S3 Glacier Deep Archive** | 180 dias                      | até 12 horas         | US$ 0,004/GB     |

> 💡 *Os dados arquivados podem ser restaurados sob demanda conforme necessidade operacional.*

---

### 🚛 AWS Snow Family (Transferência de Grandes Volumes)

Para empresas que precisam transferir grandes volumes (terabytes ou petabytes) para o S3 ou Glacier, a AWS oferece a **Snow Family**:

| Serviço               | Descrição                                                      | Capacidade                            |
| --------------------- | -------------------------------------------------------------- | ------------------------------------- |
| **AWS Snowball**      | Dispositivo físico para migração de dados locais para a nuvem. | Até 80 TB                             |
| **AWS Snowball Edge** | Permite processamento local e transporte rápido de dados.      | Alta velocidade via transporte físico |
| **AWS Snowmobile**    | Caminhão de transporte de dados para cargas de até 100 PB.     | 100 Petabytes                         |

> 🚀 *Esses serviços eliminam dependência de conexão de internet para grandes migrações.*

---

## 🧾 Comparativo: S3 x Glacier

| Característica        | **Amazon S3**           | **Amazon Glacier**                 |
| --------------------- | ----------------------- | ---------------------------------- |
| Tipo de armazenamento | Objeto                  | Arquivo (frio)                     |
| Acesso                | Frequente / imediato    | Raro / agendado                    |
| Tempo de recuperação  | Imediato                | 3 a 12 horas                       |
| Custo                 | Médio                   | Muito baixo                        |
| Uso ideal             | Sites, backups ativos   | Arquivos antigos, logs, compliance |
| Integração            | EC2, CloudFront, Lambda | S3 Lifecycle, Snow Family          |

---

## 💬 Insight Final

Os serviços **Amazon S3** e **Amazon Glacier** formam a base do armazenamento na AWS:

* O **S3** garante **acesso rápido e confiável** aos dados do dia a dia.
* O **Glacier** complementa com **armazenamento de baixo custo e longa retenção**.

> 🧠 *Dominar o ciclo de vida entre S3 e Glacier é fundamental para otimizar custos e manter dados seguros e acessíveis a longo prazo.*
