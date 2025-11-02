# ⚙️ AWS Lambda Function – Anotações

## 📘 Introdução

O **AWS Lambda** é um serviço baseado no modelo **Serverless**, onde **não há necessidade de gerenciar servidores**.
Com ele, é possível executar código sob demanda, em resposta a eventos, **sem se preocupar com infraestrutura**, escalabilidade ou provisionamento de máquinas.

---

## ☁️ O Conceito de Serverless

“Serverless” **não significa ausência de servidores**, mas sim que **o gerenciamento é feito automaticamente pela AWS**.
O desenvolvedor foca apenas na **lógica do código**, enquanto a AWS cuida da execução, escalabilidade e cobrança.
O modelo **Serverless** traz simplicidade, redução de custos e alta escalabilidade.

### 🧩 Serviços AWS Serverless

* AWS **Lambda**
* **Amazon S3**
* **Amazon DynamoDB**
* **AWS Cognito**
* **Amazon API Gateway**
* **Amazon SNS / SQS**
* **AWS Kinesis**
* **Amazon Aurora Serverless**

> 💡 *Em todos esses serviços, o usuário não precisa criar, configurar nem manter servidores ativos.*

---

## ⚖️ Diferença: EC2 x Lambda

| Característica | **Amazon EC2**                                      | **AWS Lambda**                       |
| -------------- | --------------------------------------------------- | ------------------------------------ |
| Modelo         | Infraestrutura tradicional (IaaS)                   | Serverless (FaaS)                    |
| Gerenciamento  | Usuário gerencia servidor, sistema e escalabilidade | AWS gerencia tudo automaticamente    |
| Cobrança       | Por tempo de instância ativa (por hora)             | Por execução (número de requisições) |
| Escalabilidade | Manual ou com Auto Scaling                          | Automática                           |
| Uso ideal      | Aplicações de longa duração                         | Funções curtas, eventos e automações |

> 🧠 *Lambda é ideal para executar funções pequenas e pontuais, enquanto EC2 é indicado para aplicações contínuas.*

---

## 💡 Benefícios do AWS Lambda

* **Custo eficiente:** paga-se apenas pelo tempo de execução e número de requisições.
* **Free Tier:** 1 milhão de requisições gratuitas por mês.
* **Escalabilidade automática:** aumenta ou reduz a capacidade conforme a demanda.
* **Integração nativa com serviços AWS:** S3, DynamoDB, SNS, API Gateway etc.
* **Suporte a várias linguagens:** Python, Node.js, Java, Go, Ruby, .NET, entre outras.
* **Sem necessidade de manter infraestrutura.**

**Valores (estimativa):**

* Primeiros **1 milhão de requisições grátis**.
* Após isso, **US$ 0,20 por milhão de requisições**.
* Depois, **US$ 0,02 por requisição adicional.**

---

## 🧪 Hands On – Criando uma Lambda Function

1. Acesse o console AWS → **Lambda → Create Function**.
2. Escolha **“Author from scratch”**.
3. Defina nome, runtime (ex: Python, Node.js) e permissões (role IAM).
4. No editor embutido, adicione o código (exemplo: *Hello World*).
5. Clique em **Deploy → Test**.

**Exemplo de código simples (Python):**

```python
def lambda_handler(event, context):
    return {
        'statusCode': 200,
        'body': 'Hello from AWS Lambda!'
    }
```

**Referências oficiais:**

* [AWS Getting Started – Run Serverless Code](https://aws.amazon.com/pt/getting-started/hands-on/run-serverless-code/)
* [Documentação AWS Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html)

---

## 💬 Resumo e Insight

O **AWS Lambda** representa a essência da computação em nuvem moderna:

> *“Focar no código, e não na infraestrutura.”*

Com ele, é possível construir soluções completas integrando serviços **Serverless** (S3, DynamoDB, API Gateway, Cognito etc.), eliminando a necessidade de administrar servidores.
Isso torna as aplicações mais **ágeis, escaláveis e econômicas**, ideais para **microserviços, automações e APIs modernas**.
