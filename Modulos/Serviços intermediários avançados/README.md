# ⚙️ Serviços Intermediários e Avançados na AWS

## 📘 Introdução

Este documento apresenta anotações sobre os serviços intermediários e avançados da AWS, fundamentais para a **automação, escalabilidade e comunicação entre aplicações modernas**.

Os principais serviços abordados são:

* **AWS Lambda** – Computação Serverless
* **Amazon SNS e SQS** – Mensageria e Notificações
* **Amazon ECS e EKS** – Orquestração e Gerenciamento de Containers

---

## 🧩 AWS Lambda

### 🧠 O que é o AWS Lambda?

O **AWS Lambda** é um serviço de **computação serverless** que executa código em resposta a eventos, sem a necessidade de gerenciar servidores.
Ele cuida automaticamente da **infraestrutura, escalabilidade, provisionamento e monitoramento**, permitindo que o desenvolvedor foque apenas no código.

> 💡 *Lambda é a base do paradigma Serverless: você escreve o código, e a AWS executa sob demanda.*

---

### ⚙️ Principais Características

* **Execução sob demanda:** o código é executado apenas quando acionado por um evento.
* **Custo eficiente:** paga-se apenas pelo tempo de execução (US$ 0,20 por 1 milhão de solicitações).
* **Escalonamento automático:** ajusta-se automaticamente ao volume de eventos recebidos.
* **Alta disponibilidade:** infraestrutura gerenciada pela AWS com redundância integrada.
* **Integração nativa:** com serviços como S3, DynamoDB, SNS, SQS, API Gateway, CloudWatch e Step Functions.

---

### 🚀 Benefícios

* Reduz custos de infraestrutura.
* Elimina a necessidade de manutenção de servidores.
* Facilita a criação de aplicações **event-driven** (baseadas em eventos).
* Aumenta a agilidade de desenvolvimento e a inovação.

> 📚 *Ideal para microsserviços, automações e processamento de eventos em tempo real.*

---

## 📡 Amazon SNS (Simple Notification Service)

### 🧩 O que é o SNS?

O **Amazon SNS** é um serviço de **mensageria assíncrona** e **notificação distribuída**, permitindo que diferentes sistemas e aplicações troquem mensagens de forma escalável e desacoplada.

Ele segue o modelo **Publisher/Subscriber**, onde:

* O **Publisher (publicador)** envia mensagens para um **Tópico (Topic)**.
* Os **Subscribers (assinantes)** recebem essas mensagens via e-mail, SMS, HTTP/S, Lambda, ou outros serviços AWS.

---

### ⚙️ Tipos de Tópicos

| Tipo                          | Descrição                                                         | Uso Ideal                                                 |
| ----------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------- |
| **Standard**                  | Alta taxa de publicação, entrega eventual, sem garantia de ordem. | Notificações rápidas e massivas (ex: alertas, marketing). |
| **FIFO (First-In-First-Out)** | Garante ordem e entrega única das mensagens (300 publicações/s).  | Processos críticos que exigem sequência e consistência.   |

---

### 💡 Benefícios

* Entrega rápida de notificações para múltiplos destinos.
* Integração com **Lambda**, **SQS** e **CloudWatch Alarms**.
* Comunicação instantânea entre sistemas distribuídos.
* Alta disponibilidade e segurança com controle de acesso via **IAM Policies**.

> 💬 *Use SNS para enviar notificações em tempo real para usuários ou aplicações.*

---

## 📨 Amazon SQS (Simple Queue Service)

### 🧠 O que é o SQS?

O **Amazon SQS** é um serviço de **fila de mensagens** que permite comunicação assíncrona entre sistemas e microsserviços.
Ele **desacopla componentes** de uma aplicação, garantindo processamento ordenado e confiável de mensagens.

---

### ⚙️ Tipos de Filas

| Tipo               | Descrição                                      | Uso Ideal                                         |
| ------------------ | ---------------------------------------------- | ------------------------------------------------- |
| **Standard Queue** | Alta taxa de transferência e entrega eventual. | Processamento de tarefas paralelas.               |
| **FIFO Queue**     | Ordem garantida e entrega única.               | Processos sensíveis à sequência, como transações. |

---

### 🔄 Funcionamento

* O **Producer (produtor)** envia mensagens à fila.
* O **Consumer (consumidor)** lê e processa as mensagens.
* Após o processamento, a mensagem é removida.
* Durante o consumo, a mensagem fica **invisível** para outros consumidores por um tempo limite (Visibility Timeout).

> 🧠 *SQS suaviza picos de tráfego e garante processamento consistente, mesmo com falhas temporárias.*

---

### ⚖️ SNS x SQS

| Aspecto   | **Amazon SNS**                        | **Amazon SQS**                                 |
| --------- | ------------------------------------- | ---------------------------------------------- |
| Padrão    | Publicação/Assinatura (Pub/Sub)       | Fila de Mensagens                              |
| Entrega   | Push (envio automático)               | Pull (consumidor busca a mensagem)             |
| Ordem     | Opcional (FIFO)                       | Garantida em filas FIFO                        |
| Uso Ideal | Notificações para usuários e sistemas | Comunicação entre sistemas e serviços internos |

---

## 🐳 Amazon ECS (Elastic Container Service)

### 🧩 O que é o ECS?

O **Amazon ECS** é um serviço de **orquestração de containers** altamente escalável e gerenciado pela AWS.
Ele permite executar, escalar e gerenciar containers **Docker** de forma simplificada, eliminando a necessidade de configurar clusters manualmente.

---

### ⚙️ Funcionamento

* Cada container é definido em uma **Task Definition**.
* As tarefas são executadas em um **Cluster ECS**, que pode usar **EC2 Instances** ou **AWS Fargate** (sem servidor).
* O **ECS Service** mantém o número desejado de tarefas ativas e distribui carga automaticamente.

---

### 💡 Benefícios

* Gerenciamento automatizado de containers Docker.
* Integração com **Load Balancer, IAM, CloudWatch e ECR (Elastic Container Registry)**.
* Suporte a **Fargate**, permitindo execução totalmente serverless.
* Ideal para **microserviços e aplicações escaláveis**.

> ⚙️ *O ECS simplifica o ciclo de vida dos containers, da implantação ao monitoramento.*

---

## ☸️ Amazon EKS (Elastic Kubernetes Service)

### 🧠 O que é o EKS?

O **Amazon EKS** é um serviço gerenciado que facilita a execução do **Kubernetes** na AWS, sem a necessidade de configurar manualmente nós e controladores.
Ele é compatível com qualquer aplicação Kubernetes padrão, o que permite migração fácil de workloads on-premises para a nuvem.

---

### ⚙️ Características Principais

* **Gerenciamento automático do plano de controle (Control Plane)**.
* **Escalabilidade horizontal e vertical** de clusters.
* **Integração com IAM**, **VPC**, **ECR** e **CloudWatch**.
* **Alta compatibilidade** com aplicações Kubernetes open source.

---

### 🚀 Benefícios

* Totalmente gerenciado e compatível com Kubernetes upstream.
* Execução de workloads híbridas (on-premises + AWS).
* Escalonamento automático de pods e nós.
* Redução de custos e simplificação operacional.

> 💡 *Use o EKS para ambientes que exigem portabilidade e flexibilidade Kubernetes nativa.*

---

## 🔍 ECS x EKS

| Característica    | **Amazon ECS**               | **Amazon EKS**                       |
| ----------------- | ---------------------------- | ------------------------------------ |
| Orquestrador      | Proprietário AWS             | Kubernetes                           |
| Facilidade de uso | Mais simples e nativo da AWS | Mais flexível, porém mais complexo   |
| Integração        | Profunda com serviços AWS    | Compatível com múltiplas plataformas |
| Ideal para        | Apps nativas AWS e Fargate   | Workloads Kubernetes e híbridas      |

---

## 💬 Insight Final

Esses serviços formam a base para aplicações **modernas, escaláveis e desacopladas** na AWS:

* **Lambda:** processamento de eventos sem servidor.
* **SNS/SQS:** comunicação entre sistemas.
* **ECS/EKS:** gerenciamento e orquestração de containers.

> 🧠 *Dominar esses serviços é essencial para quem deseja construir arquiteturas cloud-native robustas e eficientes.*
