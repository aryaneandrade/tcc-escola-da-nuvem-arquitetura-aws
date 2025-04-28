# 📚 TCC - Evolução da Arquitetura de E-commerce com Foco em Confiabilidade e Recuperação de Desastres

Em 2024, concluí uma etapa significativa na **Escola da Nuvem** com a entrega e apresentação do Trabalho de Conclusão de Curso (TCC). Este trabalho teve como objetivo a evolução de uma arquitetura de e-commerce, priorizando os aspectos de **Alta Disponibilidade** e **Recuperação de Desastres**, empregando as melhores práticas fornecidas pela **Amazon Web Services (AWS)**. 

A arquitetura proposta foi desenvolvida para assegurar alta disponibilidade, resiliência e recuperação eficiente diante de possíveis falhas. A seguir, é apresentada a descrição detalhada da evolução da arquitetura do sistema, que passou de uma solução simples para uma abordagem robusta e altamente disponível.

---

## 🔹 Evolução da Arquitetura AWS para Alta Disponibilidade e Recuperação de Desastres

### Arquitetura Anterior

A **arquitetura anterior** do sistema era simplificada, com diversos pontos de falha que comprometiam a continuidade operacional e a resiliência da infraestrutura:

- **Infraestrutura de uma única região:** A arquitetura operava exclusivamente na região **Northern Virginia**.
- **Uso de uma única Zona de Disponibilidade (AZ):** O sistema estava restrito à **Availability Zone A**, o que impedia a redundância e a recuperação rápida em caso de falha.
- **Rede básica:** A rede era composta por uma **VPC** com apenas uma **subnet pública** e uma **subnet privada**.
- **Instância EC2 única:** A arquitetura contava com uma única instância **EC2** na **subnet pública**, sem estratégias de escalabilidade ou redundância.
- **Conectividade limitada:** A única forma de acesso à internet era através de um único **Internet Gateway**.

Essa configuração apresentava falhas críticas, pois não oferecia redundância em múltiplos níveis, comprometendo a disponibilidade e a continuidade do serviço.

#### Imagem 2 - Arquitetura Anterior
![Arquitetura Anterior](arquitetura-anterior.jpeg)

---

### Arquitetura Atual

A **arquitetura otimizada** foi projetada para resolver as limitações da configuração anterior, implementando soluções avançadas de **alta disponibilidade** e **recuperação de desastres**:

#### Multi-Região e Multi-AZ

- **Região Primária:** Localizada em **Northern Virginia**, com duas **Zonas de Disponibilidade (AZ1 e AZ2)**, garantindo maior resiliência e continuidade operacional.
- **Região Secundária (Disaster Recovery - DR):** A região de **Ohio** foi designada como a região de **Recuperação de Desastres (DR)**, permitindo a replicação de dados e failover em caso de falhas na região primária.

#### Sistema de Failover Automático

- **Route 53:** Implementação de **DNS inteligente**, permitindo a recuperação automática dos serviços em caso de falha.
- **Monitoramento ativo/inativo:** Sistema de monitoramento entre as regiões para garantir que a região ativa seja sempre a mais saudável.

#### Componentes da Arquitetura

- **VPCs** em ambas as regiões, com configuração de subnets públicas e privadas para segmentação e segurança.
- **Internet Gateways** e **NAT Gateways** para garantir a conectividade externa e a segurança da comunicação interna.
- **Load Balancers** para distribuição de tráfego entre as instâncias **EC2**, assegurando maior performance e escalabilidade.
- **Auto Scaling Group** na região primária, permitindo ajuste dinâmico da capacidade computacional conforme a demanda.

#### Armazenamento e Banco de Dados

- **Amazon S3** para armazenamento de objetos, com replicação entre regiões para garantir a integridade e disponibilidade dos dados.
- **Amazon RDS Multi-AZ** para alta disponibilidade de bancos de dados dentro da região primária, com **replicação Cross-Region** para a região de DR, assegurando a recuperação dos dados em caso de falhas.

#### Monitoramento e Gerenciamento

- **Amazon CloudWatch** para monitoramento de métricas e logs.
- **Amazon SNS** para notificações e alertas em tempo real.
- **AWS Config** para controle de configurações e garantias de conformidade.
- **AWS CloudFormation** para a definição e gestão da infraestrutura como código, assegurando a automação e a consistência dos recursos.
- **AWS IAM** para gerenciamento de identidade e controle de acesso.

#### Imagem 1 - Arquitetura Otimizada
![Arquitetura Otimizada](arquitetura-otimizada.jpeg)

---

## 🔹 Principais Melhorias

A evolução da arquitetura proporcionou diversas melhorias significativas, com foco em redundância, escalabilidade e recuperação rápida:

- **Eliminação de pontos únicos de falha**, por meio de redundância em múltiplas zonas e regiões.
- **Recuperação automática de desastres**, utilizando o **Route 53** para failover entre regiões.
- **Elasticidade da infraestrutura**, implementando **Auto Scaling** para ajustamento dinâmico da capacidade de acordo com a carga.
- **Replicação de dados** entre zonas e regiões, garantindo a integridade e disponibilidade dos dados em cenários de falha.
- **Sistema de monitoramento abrangente**, com **CloudWatch**, **SNS** e **AWS Config**, para identificar problemas de forma proativa e garantir a continuidade do serviço.

---

## 🛠️ Ferramentas e Serviços Utilizados

- **Amazon EC2** – Para computação escalável e elástica.
- **Amazon RDS** – Banco de dados com alta disponibilidade e replicação.
- **Amazon S3** – Armazenamento seguro e replicado.
- **Amazon Route 53** – Gerenciamento de DNS e failover entre regiões.
- **AWS CloudFormation** – Infraestrutura como código para automação e consistência.
- **AWS Config** – Monitoramento e conformidade das configurações de recursos.
- **AWS IAM** – Gerenciamento de identidade e controle de acesso.

---

## 🎯 Objetivos do TCC

- Garantir **alta disponibilidade** e **resiliência** dos serviços.
- Assegurar **recuperação rápida** em caso de desastres ou falhas.
- Automatizar a infraestrutura, utilizando as melhores práticas recomendadas pela **AWS**.

---

## 💡 Aprendizados

A evolução arquitetural realizada no TCC proporcionou uma compreensão mais profunda sobre como estruturar soluções resilientes em ambientes de missão crítica. A implementação de recursos como **CloudFormation**, **Route 53** e **AWS Config** foi fundamental para garantir a escalabilidade, a segurança e a automação da infraestrutura, além de possibilitar a recuperação rápida em caso de falhas significativas.

---

Este repositório contém toda a documentação referente ao TCC, incluindo a evolução da arquitetura proposta, os detalhes dos serviços utilizados e as práticas adotadas durante o desenvolvimento.
