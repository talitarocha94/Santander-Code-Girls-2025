# 🧭 Gerenciamento e Governança na AWS

## 📘 Introdução

A governança e o gerenciamento na AWS são fundamentais para garantir **segurança, monitoramento, auditoria e controle de acesso** aos recursos em nuvem.
Nesta etapa, você aprendeu a utilizar ferramentas que fortalecem a **visibilidade operacional**, **auditoria de ações** e **gestão de permissões**.

Os principais serviços e recursos abordados foram:

* **Amazon CloudWatch**
* **AWS CloudTrail**
* **AWS Identity and Access Management (IAM)**
* **AWS Policies e Roles**

---

## ☁️ Amazon CloudWatch

### 🧠 O que é o CloudWatch?

O **Amazon CloudWatch** é o serviço de **monitoramento e observabilidade** da AWS.
Ele coleta e analisa **métricas, logs e eventos em tempo real**, permitindo visualizar a performance e o estado dos recursos da sua conta.

> 💡 *CloudWatch é o “painel de controle” da sua infraestrutura AWS.*

---

### ⚙️ Principais Funcionalidades

* **Coleta de métricas:** monitora uso de CPU, memória, tráfego de rede e armazenamento.
* **Dashboards personalizados:** cria painéis para exibir métricas e KPIs da sua aplicação.
* **Alarmes e notificações:** envia alertas automáticos ou executa ações quando um limite é ultrapassado.
* **Eventos do sistema (CloudWatch Events):** detecta mudanças em instâncias EC2, buckets S3 e outros recursos.
* **Logs centralizados:** registra logs de aplicações e serviços para análise detalhada.

---

### 💼 Casos de Uso

* Monitorar **instâncias EC2**, **bancos RDS** e **funções Lambda**.
* Criar **alertas automáticos** para sobrecarga de CPU.
* Integrar com **SNS** para envio de notificações.
* Acionar **funções Lambda** para automação de respostas.

> 🧠 *Com o CloudWatch, você tem visibilidade total do desempenho e integridade do seu ambiente AWS.*

---

## 🔍 AWS CloudTrail

### 🧩 O que é o CloudTrail?

O **AWS CloudTrail** é o serviço responsável por **auditar e registrar todas as ações realizadas na conta AWS**.
Ele monitora atividades feitas via **Console, CLI e APIs**, gerando logs detalhados de cada operação.

> 📚 *CloudTrail é o “histórico de auditoria” da AWS — ele mostra quem fez o quê, quando e de onde.*

---

### ⚙️ Principais Características

* **Auditoria completa:** registra todas as chamadas de API e eventos administrativos.
* **Governança e conformidade:** ajuda a atender normas como ISO, GDPR e SOC.
* **Detecção de atividades suspeitas:** permite identificar acessos indevidos.
* **Integração com CloudWatch:** para criar alarmes baseados em eventos registrados.

---

### 🧩 Diferença entre CloudWatch e CloudTrail

| Serviço        | Função Principal                       | Tipo de Dados                        |
| -------------- | -------------------------------------- | ------------------------------------ |
| **CloudWatch** | Monitora métricas e logs em tempo real | Desempenho e status operacional      |
| **CloudTrail** | Registra atividades e auditorias       | Histórico de ações e APIs executadas |

> 💬 *CloudWatch mostra o que está acontecendo agora; CloudTrail mostra o que já aconteceu.*

---

## 🔐 AWS Identity and Access Management (IAM)

### 🧠 O que é o IAM?

O **AWS Identity and Access Management (IAM)** é o serviço responsável por **gerenciar identidades e controlar o acesso** aos recursos da AWS.
Ele permite criar **usuários, grupos, funções (roles)** e aplicar **políticas (policies)** com permissões específicas.

---

### ⚙️ Principais Recursos

* **Usuários:** identidades individuais com credenciais de acesso.
* **Grupos:** conjuntos de usuários com políticas compartilhadas.
* **Funções (Roles):** permissões temporárias atribuídas a serviços ou usuários externos.
* **Policies:** documentos JSON que definem as permissões de cada identidade.

---

### 🧱 Boas Práticas

* **Princípio do menor privilégio:** conceder apenas as permissões necessárias.
* **Uso de MFA (Multi-Factor Authentication):** aumenta a segurança da conta.
* **Evitar uso da conta root:** reservar apenas para configurações iniciais.
* **Rotação de credenciais:** atualizar senhas e chaves periodicamente.

---

## 🧾 AWS Policies e Roles

### 🧩 O que são Policies?

As **Policies (políticas)** são **documentos JSON** que definem **permissões de acesso** para usuários, grupos ou roles.
Elas especificam **quais ações** podem ser realizadas e **em quais recursos** da AWS.

> 💬 *Uma Policy é o “contrato de acesso” entre o usuário e a AWS.*

---

### ⚙️ Tipos de Policies

| Tipo                               | Descrição                                                |
| ---------------------------------- | -------------------------------------------------------- |
| **Managed Policies (Gerenciadas)** | Criadas e mantidas pela AWS, prontas para uso.           |
| **Customer Managed Policies**      | Criadas manualmente pelo administrador.                  |
| **Inline Policies**                | Atribuídas diretamente a um usuário ou grupo específico. |

---

### 🧱 Estrutura de uma Policy (Exemplo JSON)

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "ListObjectsInBucket",
      "Effect": "Allow",
      "Action": ["s3:ListBucket"],
      "Resource": ["arn:aws:s3:::bucket-name"]
    },
    {
      "Sid": "AllObjectActions",
      "Effect": "Allow",
      "Action": "s3:*Object",
      "Resource": ["arn:aws:s3:::bucket-name/*"]
    }
  ]
}
```

---

### 🧩 O que são Roles?

As **Roles (funções)** permitem delegar permissões temporárias para serviços AWS, aplicações ou usuários externos (ex: uma função do **EC2** acessando o **S3**).

**Usos Comuns:**

* Permitir que uma função Lambda acesse um bucket S3.
* Atribuir permissões a instâncias EC2.
* Autorizar integrações entre contas AWS.

---

## 🧩 Resumo Geral

| Serviço              | Função Principal                     | Finalidade                  |
| -------------------- | ------------------------------------ | --------------------------- |
| **CloudWatch**       | Monitoramento de métricas e logs     | Observabilidade e automação |
| **CloudTrail**       | Registro de eventos e auditoria      | Governança e conformidade   |
| **IAM**              | Controle de identidades e permissões | Segurança e acesso          |
| **Policies e Roles** | Definição e delegação de permissões  | Gestão granular de acesso   |

---

## 💬 Insight Final

Com esses serviços, você domina a **camada de governança e controle da AWS** — o coração da segurança e confiabilidade na nuvem.

* 🔎 **CloudWatch**: monitora a performance.
* 🧾 **CloudTrail**: audita ações e acessos.
* 🔐 **IAM + Policies/Roles**: define quem pode fazer o quê, e com qual nível de permissão.

> 🧠 *Gerenciar é proteger. Na AWS, o controle vem da observação, da auditoria e da aplicação rigorosa de políticas de acesso.*
