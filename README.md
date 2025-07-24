# Vértice Consultoria Labs - Ambiente de Estudo de Segurança e IAM

![Status: Em Andamento](https://img.shields.io/badge/status-em%20andamento-yellow)
![Tecnologia: PowerShell](https://img.shields.io/badge/PowerShell-5.1-blue)
![Tecnologia: Active Directory](https://img.shields.io/badge/Active%20Directory-Windows%20Server-blueviolet)

> Este repositório é um projeto de portfólio contínuo, desenhado para simular e documentar a infraestrutura de TI e o programa de Segurança da Informação de uma empresa fictícia, a "Vértice Consultoria".

O objetivo principal deste projeto é aplicar e demonstrar conhecimentos práticos seguindo a filosofia do **Profissional em T**:

* **A Barra Horizontal (—):** Conhecimento amplo sobre diversos domínios da Segurança da Informação (Redes, Blue Team, GRC, etc.).
* **A Barra Vertical (|):** Conhecimento profundo e especializado em **Gestão de Identidade e Acesso (IAM)**.

---

## 1. O Cenário: Vértice Consultoria

Para dar contexto a todos os artefatos aqui presentes, foi definido o seguinte perfil de empresa:

* **Empresa:** Vértice Consultoria
* **Porte:** Pequena para Média Empresa (~50 funcionários), em fase de crescimento.
* **Setor:** Consultoria de Gestão de Patrimônio para clientes de alta renda.
* **Principal Risco:** Proteção e privacidade de dados financeiros e pessoais extremamente sensíveis.
* **Ambiente Tecnológico:** Híbrido, com um Active Directory (AD) local para gestão de identidades e uso de serviços em nuvem (Microsoft 365) para produtividade.

---

## 2. Estrutura do Repositório

* `📁 Politicas-Seguranca/`
    * Contém os documentos de Governança, Risco e Conformidade (GRC). É a base teórica que guia as implementações técnicas.
    * **POL-001:** Política de Controle de Acesso.
    * **POL-002:** Política de Uso Aceitável (PUA/AUP).

* `📁 IAM-Scripts/`
    * (Em planejamento) Scripts de automação em PowerShell para tarefas de IAM, como onboarding e offboarding de funcionários.

* `📁 GPO-Lab/`
    * (Em planejamento) Documentação e evidências da implementação de Políticas de Grupo (GPOs) para reforçar as políticas de segurança no Active Directory.

* `📁 Lab-BlueTeam/`
    * (Em planejamento) Artefatos e documentação dos estudos práticos de Blue Team e SOC, incluindo a implementação de ferramentas como Wazuh, Suricata e Snort em ambiente de laboratório.

---

## 3. Tecnologias e Ferramentas

Este projeto utiliza ou planeja utilizar as seguintes tecnologias:

* **Sistemas Operacionais:** Windows Server, Windows 10/11 Enterprise, Linux (Ubuntu Server).
* **Virtualização:** Oracle VirtualBox.
* **Serviços de Diretório:** Microsoft Active Directory Domain Services.
* **Automação:** PowerShell.
* **Segurança (Blue Team):** Wazuh (SIEM/XDR), Suricata/Snort (IDS/IPS).
* **Documentação:** Markdown.

---

## 4. Roadmap do Projeto

- [x] Definição do Perfil da Empresa Vértice Consultoria
- [x] Criação da Política de Controle de Acesso (POL-001)
- [x] Criação da Política de Uso Aceitável (AUP) (POL-002)
- [ ] Criação da Política de Classificação da Informação (POL-003)
- [ ] **(Blue Team)** Criação do procedimento de Monitoramento de Rede com IDS/IPS
- [ ] **(Blue Team)** Implementação do laboratório com Suricata e Wazuh
- [ ] **(IAM)** Desenvolvimento de script de Onboarding/Offboarding em PowerShell

---

## 5. Contato

* **Autor:** Pedro Henrique
* **LinkedIn:** www.linkedin.com/in/pedro-henrique-si
