# ☁️ Redes na AWS – Anotações

## 📘 Introdução

Este documento reúne anotações sobre os principais componentes de rede utilizados na AWS, abordando conceitos essenciais de **Subnet**, **Security Groups** e **Route 53**.
Esses recursos fazem parte do **Amazon VPC (Virtual Private Cloud)**, permitindo que o usuário controle a estrutura de rede, segurança e resolução de nomes dentro da nuvem AWS.

---

## 🌐 Amazon Subnet

### 🧩 O que é uma Subnet?

Uma **Subnet** (sub-rede) é uma **faixa de endereços IP** dentro de uma **VPC (Virtual Private Cloud)**.
Ela define uma **seção lógica da rede** onde os recursos da AWS — como **instâncias EC2** — são criados e organizados.

Cada Subnet:

* Reside **inteiramente dentro de uma zona de disponibilidade (AZ)**;
* É usada para **segmentar a rede** (ex: separar recursos públicos e privados);
* Pode hospedar instâncias e outros recursos específicos da AWS.

> 💡 *Exemplo:* você pode criar uma subnet pública para servidores web e outra privada para bancos de dados.

---

### ⚙️ Função e Integração

* Dentro das Subnets, criamos os **Security Groups (SGs)** — responsáveis por controlar o tráfego de rede.
* É nelas que definimos **protocolos, portas e IPs** que podem acessar ou ser acessados pelos recursos (via **Inbound** e **Outbound Rules**).

> 🔐 *Inbound Rules:* controlam o tráfego que **entra** no recurso.
> 🚀 *Outbound Rules:* controlam o tráfego que **sai** do recurso.

---

## 🔒 Amazon Security Group

### 🧠 O que é um Security Group?

Um **Security Group (SG)** é um **firewall virtual** que controla o tráfego de entrada e saída das instâncias EC2 e outros recursos dentro de uma VPC.

Ele define **regras de acesso** baseadas em:

* **Portas** (ex: 22 para SSH, 80 para HTTP, 443 para HTTPS);
* **Protocolos** (ex: TCP, UDP, ICMP);
* **Endereços IP de origem/destino**.

---

### ⚙️ Principais Funcionalidades

* Permite configurar **regras de entrada (Inbound)** e **saída (Outbound)** específicas.
* Define **quem pode acessar** a instância (ex: acesso SSH de um IP autorizado).
* É **stateful**, ou seja, se o tráfego de entrada for permitido, o retorno é automaticamente liberado.
* Pode ser **associado a uma ou mais instâncias EC2**.

> 💬 *Exemplo:* um Security Group pode liberar acesso RDP (porta 3389) para um servidor Windows e SSH (porta 22) para um servidor Linux.

---

### 💡 Boas Práticas

* **Restringir acessos** apenas a IPs e portas necessárias.
* **Evitar o uso de 0.0.0.0/0** em regras de entrada — isso expõe o recurso à internet.
* Criar **SGs separados por função** (ex: web, banco de dados, aplicação).
* Revisar e atualizar regras periodicamente.

---

## 🌍 Amazon Route 53

### 🧭 O que é o Route 53?

O **Amazon Route 53** é o serviço de **DNS (Domain Name System)** da AWS.
Ele realiza a **conversão de nomes de domínio** em endereços IP, permitindo que usuários acessem recursos na nuvem de forma simples e segura.

> 💡 *Exemplo:* traduz o domínio `www.exemplo.com` para o IP público de uma instância EC2 ou balanceador de carga.

---

### ⚙️ Funções Principais

* **Resolução de nomes DNS** dentro e fora da AWS;
* **Gerenciamento de tráfego** e **roteamento inteligente** entre regiões ou zonas;
* **Alta disponibilidade** e **baixa latência**;
* Integração com serviços como **CloudFront**, **Elastic Load Balancer (ELB)** e **API Gateway**.

---

### 🧱 Tipos de Registros Suportados

| Tipo      | Descrição                                                   |
| --------- | ----------------------------------------------------------- |
| **A**     | Associa um nome de domínio a um endereço IPv4.              |
| **AAAA**  | Associa um domínio a um endereço IPv6.                      |
| **CNAME** | Redireciona um nome para outro domínio.                     |
| **MX**    | Define servidores de e-mail do domínio.                     |
| **NS**    | Lista os servidores DNS autorizados.                        |
| **TXT**   | Armazena informações de texto (ex: verificação de domínio). |

---

### 💡 Benefícios

* Totalmente **gerenciado pela AWS**.
* Permite **balancear tráfego globalmente**.
* Integra-se facilmente com **recursos EC2, S3 e CloudFront**.
* Altamente **escalável e seguro**.

---

## 🧩 Resumo Geral

| Serviço                   | Função Principal                               | Tipo              |
| ------------------------- | ---------------------------------------------- | ----------------- |
| **Amazon Subnet**         | Segmenta a rede dentro da VPC                  | Estrutura de Rede |
| **Amazon Security Group** | Controla tráfego de entrada e saída (firewall) | Segurança         |
| **Amazon Route 53**       | Converte domínios em IPs e roteia tráfego      | DNS / Roteamento  |

---

# ☁️ Distribuição e Balanceamento na AWS – Anotações

## 📘 Introdução

Este documento reúne anotações sobre os serviços **Amazon CloudFront** e **Amazon Elastic Load Balancer (ELB)**.
Ambos fazem parte da camada de **distribuição e desempenho da rede AWS**, garantindo **alta disponibilidade**, **baixa latência** e **experiência otimizada para o usuário final**.

---

## 🌍 Amazon CloudFront

### 🧩 O que é o CloudFront?

O **Amazon CloudFront** é o **serviço de Content Delivery Network (CDN)** da AWS.
Ele permite a **entrega rápida e segura de conteúdo** (como sites, vídeos, sistemas e documentos) a usuários em todo o mundo, **reduzindo a latência** e melhorando a performance da aplicação.

---

### ⚙️ Como o CloudFront Funciona

* O conteúdo é distribuído através de **Edge Locations** — servidores localizados estrategicamente em diversas regiões do mundo.
* Quando um usuário faz uma solicitação (por exemplo, acessa um site hospedado no S3 ou EC2), o **CloudFront** direciona o pedido para o **ponto de presença mais próximo**, garantindo maior velocidade.
* Se o conteúdo já estiver em cache no Edge Location, ele é entregue imediatamente, sem precisar acessar o servidor de origem.

> 💡 *Edge Locations reduzem o tempo de resposta e melhoram a experiência do usuário em aplicações globais.*

---

### 🚀 Principais Benefícios

* **Distribuição global de conteúdo** com baixa latência.
* **Integração com Amazon S3, EC2, Route 53 e Load Balancer.**
* **Suporte a HTTPS**, oferecendo segurança e criptografia ponta a ponta.
* **Escalabilidade automática** — adapta-se ao volume de tráfego.
* **Cache inteligente**, reduzindo carga no servidor de origem.

---

### 💡 Cenários de Uso

* Hospedagem de **sites estáticos e dinâmicos** com distribuição global.
* **Streaming de vídeo e áudio** com baixa latência.
* Distribuição de **aplicações web e APIs** com alta performance.
* Integração com **AWS Shield e WAF** para segurança contra ataques DDoS.

---

### 🧭 Resumo do CloudFront

| Característica   | Descrição                                   |
| ---------------- | ------------------------------------------- |
| Tipo de serviço  | Content Delivery Network (CDN)              |
| Função principal | Entrega rápida de conteúdo globalmente      |
| Ponto-chave      | Edge Locations                              |
| Benefício        | Redução de latência e aumento de desempenho |
| Integração       | S3, EC2, Route 53, WAF, Shield              |

---

## ⚖️ Amazon Elastic Load Balancer (ELB)

### 🧩 O que é o ELB?

O **Elastic Load Balancer** é um serviço que **distribui automaticamente o tráfego de rede** entre múltiplas instâncias EC2 ou outros recursos AWS.
Seu objetivo é **otimizar o desempenho**, **melhorar a disponibilidade** e **evitar sobrecarga** em um único servidor.

> 💬 *Em outras palavras, o ELB atua como o “porteiro inteligente” do ambiente AWS, decidindo para onde enviar cada solicitação de usuário.*

---

### ⚙️ Como Funciona

* Recebe o tráfego de entrada (HTTP, HTTPS, TCP, UDP).
* Encaminha as solicitações para instâncias EC2 disponíveis com base em regras definidas.
* Detecta automaticamente falhas e remove instâncias inativas do balanceamento.
* Pode operar em múltiplas zonas de disponibilidade (AZs) para garantir alta disponibilidade.

---

### 🧱 Tipos de Load Balancer

| Tipo                                | Descrição                                                                        | Uso Ideal                                                         |
| ----------------------------------- | -------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| **Application Load Balancer (ALB)** | Gerencia tráfego HTTP/HTTPS com regras avançadas (URLs, cabeçalhos, cookies).    | Aplicações web modernas e APIs REST.                              |
| **Network Load Balancer (NLB)**     | Gerencia tráfego TCP/UDP a nível de rede, com baixa latência e alta performance. | Aplicações de alto desempenho e jogos online.                     |
| **Gateway Load Balancer (GLB)**     | Combina balanceamento e segurança (firewalls, IDS/IPS).                          | Ambientes que precisam de inspeção de tráfego e proteção de rede. |
| **Classic Load Balancer (CLB)**     | Balanceador legado para tráfego HTTP/HTTPS e TCP.                                | Aplicações antigas e compatibilidade com versões anteriores.      |

---

### 🚀 Benefícios do ELB

* **Alta disponibilidade e redundância** entre zonas de disponibilidade.
* **Escalabilidade automática** de acordo com o volume de tráfego.
* **Integração com Auto Scaling Groups** e **Route 53**.
* **Monitoramento via Amazon CloudWatch**.
* **Distribuição inteligente de carga** com base em regras e desempenho.

---

### 💡 Cenários de Uso

* Aplicações web com múltiplas instâncias EC2.
* Ambientes híbridos (AWS + local) com alta disponibilidade.
* Distribuição de tráfego entre regiões e data centers.
* Integração com
