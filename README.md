# 📱 Telecommunication System (JAVA)

Este repositório contém um sistema de simulação de uma operadora de telecomunicações desenvolvido em **Java**. O projeto foca-se na gestão de clientes, diferentes tipos de contas (pré-pago e pós-pago) e cálculo de faturação, aplicando conceitos fundamentais de **Programação Orientada a Objetos (POO)**.

## 📋 Sobre o Projeto

O objetivo deste sistema é demonstrar a lógica de negócio de uma empresa de telecomunicações. Permite ao administrador gerir a base de dados de clientes e simular operações diárias como chamadas e carregamentos de saldo.

**Conceitos aplicados:**
* **Abstração e Encapsulamento:** Proteção de dados sensíveis e definição de modelos.
* **Herança e Polimorfismo:** Diferenciação entre tipos de clientes e serviços.
* **Collections:** Uso de Listas e Maps para armazenamento de dados em memória.

## 🚀 Funcionalidades

* **Gestão de Clientes:** Adicionar, visualizar e remover clientes.
* **Tipos de Conta:**
    * *Pré-pago:* Requer carregamento de saldo para efetuar operações.
    * *Pós-pago:* As despesas são acumuladas numa fatura mensal.
* **Simulação de Serviços:**
    * Chamadas de voz (Custo calculado por duração).
    * Envio de SMS.
    * Consumo de Internet/Dados.
* **Faturação:** Geração de relatórios de custos e saldo atual.

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Java (JDK 8+)
* **IDE Sugerido:** IntelliJ IDEA, Eclipse ou NetBeans
* **Controlo de Versão:** Git

## 📂 Estrutura do Projeto

A estrutura de pastas segue o padrão convencional de projetos Java:

```text
src/
├── main/           # Classe principal (Main/Menu)
├── model/          # Classes de modelo (Cliente, Fatura, Servico)
├── service/        # Lógica de negócio e operações
└── utils/          # Utilitários auxiliares
