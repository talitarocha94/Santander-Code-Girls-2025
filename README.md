# 💻 Santander Code Girls 2025
**Um curso voltado para computação em nuvem utilizando a AWS**

## 🌐 Primeiros Passos na AWS

### 🔒 1. Ativação da Autenticação Multifator (MFA)

A **autenticação multifator (MFA)** adiciona uma camada extra de segurança à conta raiz (root). Ela exige um segundo fator de verificação — geralmente um código temporário gerado por um aplicativo como **Google Authenticator** ou **Authy** — além da senha.

**Etapas:**

1. Acessar o console da AWS com o usuário root.
2. Ir até **IAM → Dashboard → Ativar MFA**.
3. Escolher o tipo de MFA (virtual app, chave física, etc).
4. Escanear o QR Code e confirmar com dois códigos consecutivos.

> ✅ **Boa prática:** nunca usar o usuário root para tarefas diárias; utilize-o apenas para configurações administrativas iniciais.

---

### 👥 2. Criação de Usuários IAM

Após proteger a conta root, o próximo passo é criar **usuários individuais** no IAM (*Identity and Access Management*).
Cada pessoa ou sistema que precisa acessar a AWS deve ter seu próprio usuário — evitando o compartilhamento de credenciais.

**Etapas:**

1. Acessar o console **IAM → Users → Add user**.
2. Definir nome de usuário e tipo de acesso:

   * **Acesso ao console da AWS** (para login via navegador).
   * **Acesso programático** (para uso via CLI ou SDK).
3. Criar senhas temporárias para novos usuários.

> 🔑 **Dica:** ative a opção *“Usuário deve redefinir senha no primeiro acesso”*.

---

### 🧩 3. Criação de Grupos IAM

Os **grupos** permitem organizar usuários que compartilham funções semelhantes, facilitando o controle de permissões.

**Exemplo:**

* **Administradores:** acesso total à conta AWS.
* **Desenvolvedores:** acesso a EC2, S3 e CloudWatch.
* **Financeiro:** acesso apenas a relatórios de cobrança (Billing).

**Etapas:**

1. Ir até **IAM → Groups → Create group**.
2. Escolher um nome para o grupo.
3. Anexar políticas de permissão adequadas (ex: *AdministratorAccess*, *AmazonEC2FullAccess*).
4. Adicionar usuários ao grupo.

> 🧠 **Benefício:** em vez de configurar permissões usuário por usuário, basta ajustar as políticas do grupo — todos os membros recebem automaticamente as atualizações.

---

### 🧾 4. Políticas de Acesso

As **políticas IAM** definem o que um usuário, grupo ou função pode ou não fazer na AWS.

**Tipos de políticas:**

* **Gerenciadas pela AWS:** prontas para uso (ex: *AmazonS3ReadOnlyAccess*).
* **Gerenciadas pelo cliente:** criadas pelo próprio usuário para necessidades específicas.
* **Em linha (inline):** anexadas diretamente a um único usuário ou grupo.

> ⚖️ **Boa prática:** aplicar o **princípio do menor privilégio**, concedendo apenas as permissões necessárias para cada função.

---

## ☁️ Computação em Nuvem com EC2

### ⚙️ 1. O que é EC2?

O **Amazon EC2 (Elastic Compute Cloud)** é um serviço que permite criar e executar **servidores virtuais (instâncias)** sob demanda, com total controle sobre sistema operacional, rede e armazenamento. Em resumo, o EC2 representa **máquinas virtuais na nuvem**.

---

### 🧩 2. Principais Componentes

* **Instância:** servidor virtual executando na nuvem.
* **AMI (Amazon Machine Image):** imagem base usada para inicializar uma instância.
* **Tipos de Instância:** diferentes combinações de CPU, memória e rede (ex: *t2.micro*, *t3.medium*).
* **EBS (Elastic Block Store):** armazenamento persistente das instâncias EC2.
* **Security Groups:** regras de firewall que controlam tráfego de entrada e saída.
* **Key Pair:** conjunto de chaves para acesso seguro via SSH.

---

## ⚙️ Otimização de Recursos na AWS

Gerenciar instâncias e serviços na AWS envolve **eficiência, desempenho e economia**. Abaixo, estão as principais boas práticas para otimizar custos e recursos.

### 💰 1. Utilize o AWS Free Tier

Use recursos **gratuitos** sempre que possível: instâncias *t2.micro* ou *t3.micro*, buckets S3 pequenos, Lambda, DynamoDB e CloudWatch dentro dos limites do Free Tier.

> 🧠 **Dica:** monitore o uso — o Free Tier tem limites e pode gerar cobranças.

---

### 💤 2. Pare ou Exclua Instâncias Não Utilizadas

Desligue ou exclua instâncias EC2 inativas para evitar custos.

> ✅ **Boa prática:** configure **CloudWatch Alarms** para identificar instâncias ociosas.

---

### 🧾 3. Monitore Custos com AWS Billing e Budgets

Crie alertas e acompanhe gastos pelo **AWS Budgets**. Configure notificações por e-mail quando o custo ultrapassar um valor definido.

> 💡 **Insight:** acompanhar custos desde o início evita surpresas e incentiva o uso consciente.

---

### 🧮 4. Escolha Tipos de Instância Adequados

Selecione tipos de instância conforme a carga:

* **t2.micro / t3.micro:** testes e pequenos ambientes.
* **m5 / m6g:** equilíbrio entre CPU e memória.
* **c5 / c6g:** intensivas em CPU.
* **r5 / r6g:** aplicações que exigem muita memória.

> 🔍 **Dica:** use o **AWS Instance Type Selector** para comparar custos e desempenho.

---

### 🧰 5. Use Auto Scaling

O **Auto Scaling** ajusta automaticamente o número de instâncias EC2 conforme a demanda, garantindo economia e disponibilidade.

**Benefícios:** escalabilidade automática, redução de custos e alta disponibilidade.

---

### 💾 6. Gerencie o Armazenamento com Eficiência

Otimize custos com **EBS** e **S3**:

* Use **EBS gp3** (melhor custo-benefício).
* Exclua **snapshots antigos**.
* Configure **S3 Lifecycle** para mover arquivos antigos para o **Glacier**.

---

### 🧩 7. AWS Trusted Advisor

Ferramenta que recomenda melhorias em: **custos, desempenho, segurança, tolerância a falhas e limites de serviço**.

> 💬 Exemplo: sugerir exclusão de instâncias subutilizadas ou volumes EBS não conectados.

---

### 🔐 8. Evite Sobrecarga de Permissões

Use **políticas de menor privilégio**, remova **chaves antigas** e revise periodicamente usuários e grupos.

---

### 🧠 9. Automatize Tarefas Rotineiras

Use **AWS Lambda**, **CloudFormation** ou **Systems Manager** para automatizar desligamentos, backups e manutenções.

> 🧩 Exemplo: função Lambda para desligar instâncias fora do horário comercial.

---

### 🚀 10. Use Tags para Organização

As **tags** ajudam a controlar custos e identificar recursos.
Exemplo:

```
Project: AppMobile
Environment: Test
Owner: IgorRocha
```

---

## ⚖️ Escalabilidade de Recursos

A escalabilidade permite **aumentar ou reduzir** recursos conforme a demanda, garantindo desempenho e economia.

### 📈 1. Escalabilidade Vertical

Aumenta os recursos de uma única instância (CPU, RAM, armazenamento).

> Exemplo: trocar *t2.micro* (1 GB RAM) por *t3.medium* (4 GB RAM).

**Vantagens:** simples de aplicar, ideal para apps monolíticas.
**Desvantagens:** há limite físico, requer reinício e custo mais alto.

---

### ⚙️ 2. Escalabilidade Horizontal

Adiciona ou remove múltiplas instâncias para dividir carga de trabalho.

> Exemplo: usar **Load Balancer + Auto Scaling Group**.

**Vantagens:** alta disponibilidade e custo ajustável.
**Desvantagens:** arquitetura mais complexa, exige aplicações distribuídas.

---

## 💾 Armazenamento na AWS

### 🧱 Amazon EBS (Elastic Block Store)

Fornece **armazenamento em blocos** persistente anexado a instâncias EC2, funcionando como um **HD virtual**.

**Boas práticas:**

* Excluir volumes não usados.
* Fazer **snapshots regulares**.
* Preferir **volumes gp3**.

---

### ☁️ Amazon S3 (Simple Storage Service)

Serviço de **armazenamento de objetos** escalável e durável para arquivos, backups e mídias.

**Boas práticas:**

* Habilitar **versionamento** e **MFA Delete**.
* Usar **regras de ciclo de vida** para arquivamento.
* Evitar **buckets públicos**.
* Integrar com **CloudFront** para performance.

---

### ⚖️ Comparativo: EBS x S3

| Característica | EBS                                  | S3                       |
| -------------- | ------------------------------------ | ------------------------ |
| Tipo           | Bloco                                | Objeto                   |
| Persistência   | Vinculado à instância EC2            | Independente             |
| Escalabilidade | Limitada                             | Altamente escalável      |
| Uso            | Sistema operacional, bancos de dados | Backups, arquivos, mídia |
| Custo          | Por volume/IOPS                      | Por GB/mês e requisições |

---
