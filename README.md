# 📌 Projeto Conceitual - Oficina Mecânica (Modelo ER)

Este repositório contém o **modelo conceitual** (diagrama entidade-relacionamento) para um sistema de controle e gerenciamento de ordens de serviço em uma oficina mecânica.  
O projeto foi desenvolvido a partir da narrativa fornecida no desafio, transformando as informações em **entidades, relacionamentos e atributos** para modelagem de dados.

---

## 🎯 Objetivo
Criar um **esquema conceitual** que represente o contexto de uma oficina mecânica, com base nos requisitos narrados, de forma a permitir a futura implementação do sistema.

---

## 📖 Narrativa
- Clientes levam veículos à oficina mecânica para consertos ou revisões periódicas.  
- Cada veículo é designado a uma equipe de mecânicos que identifica os serviços necessários e preenche uma **Ordem de Serviço (OS)** com a data de entrega.  
- O valor de cada serviço é calculado com base em uma tabela de referência de mão de obra.  
- O valor das peças também compõe o valor total da OS.  
- O cliente autoriza a execução antes do início dos serviços.  
- A mesma equipe avalia e executa os serviços.  
- Mecânicos possuem código, nome, endereço e especialidade.  
- Cada OS possui: número, data de emissão, valor total, status e data de conclusão.

---

## 🗂 Entidades e Atributos

### **Cliente**
- `id_cliente` (PK)  
- nome  
- endereço  
- telefone  
- e-mail  

### **Veículo**
- `id_veiculo` (PK)  
- placa  
- modelo  
- ano  
- cor  
- `id_cliente` (FK)  

### **Mecânico**
- `id_mecanico` (PK)  
- código  
- nome  
- endereço  
- especialidade  

### **Equipe**
- `id_equipe` (PK)  
- nome_equipe  

### **Equipe_Mecânico** (Relacionamento N:N)
- `id_equipe` (FK)  
- `id_mecanico` (FK)  

### **Ordem_de_Serviço**
- `id_os` (PK)  
- número_os  
- data_emissão  
- data_entrega  
- valor_total  
- status  
- `id_veiculo` (FK)  
- `id_equipe` (FK)  

### **Serviço**
- `id_servico` (PK)  
- descrição  
- valor_mao_de_obra  

### **Peça**
- `id_peca` (PK)  
- descrição  
- valor  

### **OS_Serviço** (Relacionamento N:N)
- `id_os` (FK)  
- `id_servico` (FK)  
- quantidade  

### **OS_Peça** (Relacionamento N:N)
- `id_os` (FK)  
- `id_peca` (FK)  
- quantidade  

---

## 🔗 Relacionamentos
- Cliente **1:N** Veículo  
- Veículo **1:N** Ordem_de_Serviço  
- Equipe **1:N** Ordem_de_Serviço  
- Equipe **N:N** Mecânico (via Equipe_Mecânico)  
- Ordem_de_Serviço **N:N** Serviço (via OS_Serviço)  
- Ordem_de_Serviço **N:N** Peça (via OS_Peça)  

---

## 📊 Diagrama Conceitual
![Diagrama ER](diagrama_oficina.png)  
*(O arquivo `diagrama_oficina.png` está neste repositório e contém o modelo conceitual visual do sistema.)*

---
