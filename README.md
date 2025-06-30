# 💻 Gerenciamento de Máquinas Virtuais no Microsoft Azure

Repositório criado como parte do **Desafio Prático da DIO** sobre **implantação e gerenciamento de máquinas virtuais (VMs)** no Microsoft Azure.

> 🌐 Este repositório contém **resumos**, **anotações** e **dicas práticas** que podem ser usados como material de apoio para estudos e futuras implementações.

---

## 📌 Objetivos do Desafio

- Implantar máquinas virtuais no Azure
- Gerenciar recursos associados à VM (como discos)
- Desanexar discos de dados de forma segura
- Documentar os processos técnicos de forma clara e reutilizável

---

## 📁 Estrutura do Repositório
~~~
.
├── README.md # Documentação principal do desafio
├── /images # Capturas de tela das etapas (opcional)
└── comandos.md # Comandos práticos usados na CLI (opcional)
~~~

---

## 🚀 Etapas Realizadas

### 1. Criação de Máquina Virtual (VM)

- **Sistema operacional**: Windows Server 2022 ou Ubuntu 20.04 LTS
- **Tamanho**: Standard_B1s (para fins de teste)
- **Rede**: IP público + NSG com porta RDP (Windows) ou SSH (Linux)
- **Autenticação**: usuário/senha ou chave SSH

🔧 **Dica**: Ative o desligamento automático na VM para evitar custos desnecessários.

---

### 2. Adição de Disco de Dados

- Acesse a VM no portal > Discos > "+ Adicionar disco"
- Escolha:
  - **Nome do disco**
  - Tipo (HDD ou SSD padrão)
  - Tamanho (ex: 32 GB)
- Após anexar, entre na VM:
  - No **Windows**, inicialize o disco no Gerenciador de Disco
  - No **Linux**, use `lsblk`, `mkfs`, `mount`

---

### 3. Desanexar Disco da Máquina Virtual

- **Via Portal**:
  - VM > Discos > Selecione o disco > Clique em “Desanexar”
- **Via CLI**:
  ```bash
  az vm disk detach --resource-group MeuGrupo --vm-name MinhaVM --name NomeDoDisco
⚠️ Importante: Verifique se o disco não está sendo usado ativamente antes da desanexação.

## 🛠️ Comandos úteis (Azure CLI)
# Criar uma VM simples
~~~
az vm create \
  --resource-group MeuGrupo \
  --name MinhaVM \
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
~~~
# Criar um disco de dados
~~~
az disk create \
  --resource-group MeuGrupo \
  --name MeuDisco \
  --size-gb 32 \
  --sku Standard_LRS
~~~
# Anexar disco à VM
~~~
az vm disk attach \
  --resource-group MeuGrupo \
  --vm-name MinhaVM \
  --name MeuDisco
~~~
# Desanexar disco da VM
~~~
az vm disk detach \
  --resource-group MeuGrupo \
  --vm-name MinhaVM \
  --name MeuDisco
~~~
## 📚 Referências
[Documentação oficial – Máquinas Virtuais no Azure] (https://learn.microsoft.com/pt-br/azure/virtual-machines/)

[DIO – Formação Azure AZ-104] (https://web.dio.me/track/microsoft-az-104-certification))

[Guia Markdown GitHub] (https://guides.github.com/features/mastering-markdown/)

## ✍️ Autora
Feito por Enaile Lopes
💼 [LinkedIn] (https://www.linkedin.com/in/enailelopes/)
💻 [GitHub] (https://github.com/Nai-nailinha/) 
