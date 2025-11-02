# 🗄️ Bancos de Dados na AWS – Anotações

## 📘 Introdução

A AWS oferece soluções de **banco de dados gerenciados** que permitem ao usuário focar no desenvolvimento e na lógica das aplicações, deixando para a AWS tarefas como **provisionamento, backup, monitoramento e escalabilidade**.

Os dois principais serviços estudados neste módulo são:

* **Amazon RDS** (Relacional)
* **Amazon DynamoDB** (NoSQL)

---

## 🧩 Amazon RDS (Relational Database Service)

### 🧠 O que é o Amazon RDS?

O **Amazon RDS (Relational Database Service)** é um serviço de **banco de dados relacional gerenciado**.
Ele facilita a criação, operação e escalabilidade de bancos de dados relacionais na nuvem, com **alta disponibilidade e automação de tarefas administrativas**.

**Principais características:**

* Criação de bancos em minutos.
* Flexibilidade para escolher mecanismos de banco de dados.
* Escalabilidade vertical e horizontal.
* Backups automatizados e monitoramento integrado.

---

### ⚙️ Benefícios

* ✅ **Fácil de gerenciar:** reduz a complexidade da administração de bancos de dados.
* ⚙️ **Automação de tarefas:** backups, atualizações e patches automáticos.
* 🚀 **Rápida implantação:** bancos prontos em poucos minutos.
* 💪 **Desempenho otimizado:** recursos ajustáveis conforme demanda.
* 🧩 **Flexibilidade e customização:** escolha do motor e configuração.
* 💰 **Gerenciamento de custos:** paga-se apenas pelo uso.

---

### ⚠️ Pontos de Atenção

* 💸 Custos variáveis conforme o tipo de instância e armazenamento.
* 🧩 Complexidade maior em cenários avançados (integrações e migrações).

---

### 💼 Casos de Uso

* **Aplicativos Web e Mobile:** banco escalável e seguro para armazenamento de dados de usuários.
* **Aplicações Empresariais:** ideal para grandes sistemas corporativos que exigem confiabilidade e performance.

---

### 🧱 Tipos de Bancos Suportados pelo Amazon RDS

| Tipo                     | Descrição                                                                                      |
| ------------------------ | ---------------------------------------------------------------------------------------------- |
| **Amazon Aurora**        | Compatível com MySQL e PostgreSQL; até 5x mais rápido que MySQL e com custo reduzido.          |
| **Oracle**               | Suporte completo a Oracle Database, com opção BYOL (Bring Your Own License).                   |
| **Microsoft SQL Server** | Compatível com ferramentas nativas do SQL Server.                                              |
| **MySQL**                | Banco relacional open source amplamente utilizado na web.                                      |
| **PostgreSQL**           | Sistema objeto-relacional poderoso e extensível.                                               |
| **MariaDB**              | Compatível com MySQL, sendo uma alternativa open source desenvolvida pelos criadores do MySQL. |

---

## ⚡ Amazon DynamoDB

### 🧠 O que é o DynamoDB?

O **Amazon DynamoDB** é um **banco de dados NoSQL totalmente gerenciado** que oferece **alta performance, baixa latência e escalabilidade automática**.
É ideal para aplicações que exigem resposta em tempo real e trabalham com **dados não estruturados ou semiestruturados**.

> 💡 *Diferente do RDS, o DynamoDB não usa tabelas relacionais, mas sim tabelas baseadas em chaves e valores (Key-Value).*

---

### ⚙️ Principais Recursos

* **Totalmente gerenciado:** a AWS lida com servidores, particionamento e replicação.
* **Escalabilidade automática:** ajusta automaticamente capacidade de leitura e gravação.
* **Baixa latência:** tempo de resposta em milissegundos.
* **Alta disponibilidade:** dados replicados automaticamente em múltiplas zonas de disponibilidade.
* **Integração nativa** com Lambda, API Gateway e CloudWatch.

---

### 🧾 Exemplo de Estrutura

Uma tabela chamada **Clientes** pode ter uma **chave primária** `CustomerID`, que é usada para otimizar as consultas e garantir desempenho consistente.

---

### 💼 Casos de Uso

| Empresa     | Aplicação                                                          |
| ----------- | ------------------------------------------------------------------ |
| **Airbnb**  | Armazenamento e processamento de dados de reservas e propriedades. |
| **Lyft**    | Gerenciamento de dados de usuários e viagens em tempo real.        |
| **Netflix** | Armazenamento de histórico de visualização e dados de clientes.    |
| **Samsung** | Diversas aplicações internas e externas em grande escala.          |
| **Dropbox** | Gerenciamento de metadados e operações de arquivos.                |

---

### 🧩 Hands-On (Exemplo Prático)

1. Instalar o **AWS CLI** conforme o sistema operacional.
2. Criar um **usuário programático** no IAM e baixar o arquivo `.csv` com chaves de acesso.
3. Configurar a CLI com o comando:

   ```bash
   aws configure
   ```
4. Executar comandos para criar e gerenciar tabelas DynamoDB via CLI.

> 📚 **Documentação oficial:**
> [AWS CLI – Getting Started](https://docs.aws.amazon.com/pt_br/cli/latest/userguide/getting-started-install.html)

---

## 🧩 Comparativo: RDS x DynamoDB

| Característica | **Amazon RDS**                      | **Amazon DynamoDB**                    |
| -------------- | ----------------------------------- | -------------------------------------- |
| Tipo de banco  | Relacional (SQL)                    | Não relacional (NoSQL)                 |
| Estrutura      | Tabelas, colunas e relacionamentos  | Tabelas baseadas em chave-valor        |
| Escalabilidade | Vertical e limitada                 | Automática e ilimitada                 |
| Latência       | Milissegundos, depende da instância | Milissegundos consistentes             |
| Casos de uso   | Aplicações tradicionais e ERP       | Aplicações de tempo real e alta escala |
| Gerenciamento  | Semi-gerenciado                     | Totalmente gerenciado                  |

---

# 💾 Estratégias de Backup e Recuperação de Dados na AWS

## 📘 Introdução

O **backup de dados** é uma das funções mais essenciais de **proteção e continuidade de negócios** em ambientes de TI.
Na AWS, existem diversas ferramentas e boas práticas para **garantir segurança, disponibilidade e recuperação rápida** em caso de falhas, desastres ou incidentes.

---

## 🧠 O que é Backup de Dados?

Um **backup** é uma cópia dos dados, configurações ou aplicações armazenada separadamente do original.

### 💡 Importância

* Evita **perda de informações** causadas por falhas, desastres naturais ou erros humanos.
* Garante **continuidade operacional** e **reduz custos** de interrupção.
* Permite **recuperar sistemas rapidamente** em caso de falhas.
* Atende a **requisitos de auditoria e conformidade**.

> 🔐 *Backup é a linha de defesa contra falhas inevitáveis. Ter backup é essencial; testá-lo é obrigatório.*

---

## 🧩 Etapas para Definir uma Estratégia de Backup

### **1. Avaliação e Planejamento**

* **Identificar dados críticos:** determine quais dados precisam ser protegidos.
* **Definir RPO e RTO:**

  * **RPO (Recovery Point Objective):** quanto de perda de dados é aceitável entre backups (ex: diário, semanal).
  * **RTO (Recovery Time Objective):** tempo máximo aceitável que o sistema pode ficar fora do ar antes da recuperação.

> 📊 *RPO está ligado aos dados; RTO, ao tempo de recuperação.*

---

### **2. Seleção de Serviços AWS**

Os principais serviços AWS para backup e recuperação incluem:

* **Amazon S3:** armazenamento confiável e escalável para cópias de segurança.
* **AWS Backup:** gerenciamento centralizado e automação de backups em múltiplos serviços.
* **Amazon RDS Automated Backups e Snapshots:** backups automáticos e manuais de bancos relacionais.
* **Amazon DynamoDB On-Demand Backup (PITR):** backups sob demanda e recuperação contínua de tabelas NoSQL.

> 💡 *Com o AWS Backup, é possível aplicar políticas de backup em diversos serviços com poucos cliques.*

---

### **3. Implementação da Estratégia de Backup**

* **Backups Regulares:** configure **backups automáticos diários** para dados críticos.
* **Backups Incrementais:** armazene apenas alterações desde o último backup para otimizar espaço.
* **Cópias em Múltiplas Regiões:** use **replicação entre regiões (cross-region replication)** para garantir resiliência.
* **Automação e Monitoramento:**

  * Utilize **AWS Lambda** para automatizar execuções.
  * Monitore status e falhas com **Amazon CloudWatch**.

---

### **4. Recuperação e Teste**

* **Documentar planos de recuperação** detalhados para diferentes tipos de falhas.
* **Realizar testes periódicos** de restauração de backup para validar integridade e desempenho.
* **Backup Drill:** simular cenários de desastres para testar o plano de recuperação.

> 🧠 *Um plano de backup só é confiável se já foi testado.*

---

### **5. Segurança e Conformidade**

* **Criptografia de Dados:**

  * Em trânsito: TLS.
  * Em repouso: S3 Server-Side Encryption, RDS Encryption.
* **Controle de Acesso:** use políticas **IAM** para restringir acesso a backups apenas a usuários autorizados.
* **Auditoria e Logs:** utilize **AWS CloudTrail** para registrar ações e garantir conformidade regulatória.

> 🧩 *Segurança de dados começa com controle de acesso e termina com rastreabilidade completa.*

---

### **6. Custo e Otimização**

* Use **AWS Cost Explorer** para monitorar e otimizar gastos com armazenamento de backups.
* Aplique **políticas de ciclo de vida (Lifecycle Policies)** no S3 para mover dados antigos para classes mais baratas (ex: *S3 Glacier*).
* Balanceie frequência e retenção dos backups para adequar custo-benefício.

---

## ⚙️ Ferramentas e Serviços Recomendados

| Serviço                              | Função                                                | Caso de Uso                               |
| ------------------------------------ | ----------------------------------------------------- | ----------------------------------------- |
| **AWS Backup**                       | Centraliza e automatiza backups em múltiplos serviços | Ambientes híbridos e multi-serviço        |
| **Amazon S3**                        | Armazena backups de longo prazo                       | Dados críticos e replicação entre regiões |
| **RDS Automated Backups**            | Backups e restauração de bancos relacionais           | Aplicações transacionais                  |
| **DynamoDB On-Demand Backup (PITR)** | Recuperação contínua de tabelas NoSQL                 | Aplicações em tempo real                  |
| **AWS Lambda + CloudWatch**          | Automação e monitoramento de processos                | Agendamento e alertas automáticos         |

---

## 💬 Conclusão e Boas Práticas

* **Automatize tudo:** elimine a dependência de processos manuais.
* **Monitore constantemente:** utilize CloudWatch e CloudTrail.
* **Teste frequentemente:** garanta que o plano realmente funcione.
* **Use múltiplas regiões:** nunca mantenha backups no mesmo local do dado original.
* **Gerencie custos:** use políticas de ciclo de vida e classes de armazenamento inteligentes.

> 💡 *Na AWS, uma boa estratégia de backup é aquela que você nunca precisará usar — mas que está pronta para quando precisar.*

---

