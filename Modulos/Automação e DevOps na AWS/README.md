# ⚙️ Automação e DevOps na AWS

## 📘 Introdução

Nesta etapa da formação **AWS Cloud Foundations**, aprendi a importância da **automação e da cultura DevOps** dentro da AWS.
O foco principal foi entender **como simplificar tarefas**, **automatizar processos** e **integrar desenvolvimento e operações (Dev + Ops)** usando ferramentas que tornam o ciclo de entrega de software mais rápido, seguro e eficiente.

---

## 🤖 Automatizando Tarefas na AWS

### 🧠 O que é Automação na AWS?

A automação é a base da eficiência em nuvem.
Ela permite **executar tarefas repetitivas de forma consistente**, reduzindo erros humanos, economizando tempo e otimizando recursos.

> 💡 *Automatizar é transformar processos manuais em fluxos inteligentes e reproduzíveis.*

---

### ⚙️ Ferramentas Principais de Automação

| Ferramenta              | Descrição                                                                     | Uso Ideal                                            |
| ----------------------- | ----------------------------------------------------------------------------- | ---------------------------------------------------- |
| **AWS CloudFormation**  | Criação e gerenciamento de infraestrutura como código (IaC) usando JSON/YAML. | Provisionamento e replicação de ambientes AWS.       |
| **AWS Lambda**          | Execução de código sem servidor (serverless).                                 | Responder a eventos automaticamente.                 |
| **AWS CodePipeline**    | Automação de pipelines CI/CD.                                                 | Entrega contínua de software.                        |
| **AWS Systems Manager** | Automação de tarefas operacionais e manutenção de instâncias.                 | Gerenciamento de patches e comandos em larga escala. |
| **AWS Step Functions**  | Criação de fluxos automatizados entre serviços AWS.                           | Orquestração de processos complexos.                 |

---

### 🧩 Formas de Automação

1. **Infraestrutura como Código (IaC):**
   Usar ferramentas como **CloudFormation** ou **Terraform** para criar recursos de forma declarativa.
2. **Scripts e CLI:**
   Utilizar a **AWS CLI** para executar comandos automatizados (ex: iniciar instâncias EC2 ou criar buckets S3).
3. **SDKs (Software Development Kits):**
   Criar automações personalizadas com linguagens como **Python (Boto3)**, **JavaScript** ou **Java**.

---

### 🚀 Benefícios da Automação

* Redução de erros manuais.
* Aumento da eficiência operacional.
* Escalabilidade em processos complexos.
* Agilidade na criação e atualização de infraestrutura.

---

## 🧱 Criação de Recursos com Terraform

### 🧠 O que é o Terraform?

O **Terraform** é uma ferramenta de **Infraestrutura como Código (IaC)** desenvolvida pela **HashiCorp**, usada para **definir, provisionar e gerenciar infraestrutura** em múltiplos provedores, incluindo a AWS.

> 💬 *Com o Terraform, é possível criar toda a infraestrutura AWS usando código, de forma automatizada e replicável.*

---

### ⚙️ O que é possível fazer com o Terraform na AWS

* Criar e gerenciar recursos (EC2, VPCs, S3, RDS, Lambda, etc.).
* Automatizar mudanças em larga escala com segurança.
* Controlar dependências entre recursos.
* Versionar e reverter alterações facilmente.

---

### 💡 AWS Local com LocalStack

O **LocalStack** permite **simular a AWS localmente**, ideal para testes e aprendizado.

* Criado pela **Atlantis Software**, suporta diversos serviços AWS.
* Possui versões **open-source** e **pro**.
* Permite criar, testar e destruir recursos localmente antes de aplicá-los na nuvem real.

📍 **Comandos básicos:**

* Subir ambiente local (`localstack start`).
* Criar infraestrutura com IaC.
* Testar APIs com Postman.
* Destruir e recriar recursos de forma automatizada.

---

## 🧩 O que é DevOps

### 🧠 Conceito

O **DevOps** é uma metodologia que une **desenvolvimento (Dev)** e **operações (Ops)** com o objetivo de **entregar software de forma rápida, segura e contínua**.

> 💡 *DevOps é 50% automação e 50% colaboração.*

---

### ⚙️ Princípios-Chave do DevOps

1. **Colaboração** – Desenvolvedores e equipes de operação trabalham juntos.
2. **Automação** – Reduz falhas humanas e acelera entregas.
3. **Melhoria contínua** – Monitoramento e aprendizado constante.
4. **Foco no cliente** – Entregar valor de forma ágil.
5. **Crie com o fim em mente** – Planejar desde o início para o ambiente final.

---

### 💼 Benefícios do DevOps

* Entregas mais rápidas e seguras.
* Redução de falhas em produção.
* Recuperação rápida em caso de erros.
* Melhor colaboração entre times.

---

## ☁️ DevOps na AWS

### ⚙️ Ferramentas AWS para DevOps

| Ferramenta             | Função                                              |
| ---------------------- | --------------------------------------------------- |
| **AWS CodeCommit**     | Repositório Git gerenciado para controle de versão. |
| **AWS CodeBuild**      | Compila e testa o código automaticamente.           |
| **AWS CodeDeploy**     | Automatiza implantações de aplicações.              |
| **AWS CodePipeline**   | Cria e gerencia pipelines CI/CD.                    |
| **AWS CloudFormation** | Cria infraestrutura como código (IaC).              |
| **Amazon CloudWatch**  | Monitora logs e métricas das aplicações.            |
| **AWS IAM**            | Garante segurança e controle de permissões.         |

---

### 🔄 Pipeline CI/CD na AWS

**CI/CD (Continuous Integration / Continuous Deployment)** é o coração do DevOps.
Ele automatiza desde o envio do código até a entrega em produção.

📍 **Etapas Típicas de um Pipeline AWS:**

1. **Commit do Código** → GitHub / CodeCommit
2. **Build e Testes** → CodeBuild
3. **Implantação** → CodeDeploy
4. **Monitoramento** → CloudWatch

> 💬 *Esse fluxo garante entregas consistentes, ágeis e seguras.*

---

### 🧩 Integração com Outras Ferramentas

* **AWS Systems Manager OpsCenter:** registro e acompanhamento de tickets.
* **CodePipeline Manual Approval:** etapas de aprovação manual antes do deploy.
* **CloudTrail:** auditoria e rastreabilidade de ações no pipeline.
* **CodeDeploy Reports:** histórico de versões e implantações.

---

## 🧰 Ferramentas Externas de Apoio ao DevOps

| Ferramenta             | Função                                                     |
| ---------------------- | ---------------------------------------------------------- |
| **Ansible**            | Gerenciamento de configurações e provisionamento via YAML. |
| **Terraform**          | Provisionamento e versionamento de infraestrutura.         |
| **AWS CloudFormation** | Criação e replicação de ambientes AWS via IaC.             |

> 💡 *Essas ferramentas trazem a cultura DevOps para a prática, tornando a automação mais simples e previsível.*

---

## 💬 Insight Final

Com esse módulo, aprendi a **automatizar tarefas**, **gerenciar infraestrutura como código** e **aplicar o conceito de DevOps dentro da AWS**.
Hoje entendo como **cada ferramenta** se conecta para criar um fluxo de trabalho **automatizado, colaborativo e eficiente**, que reduz falhas e acelera entregas.

> 🧠 *Automação + Colaboração = Eficiência e Inovação na Nuvem.*
