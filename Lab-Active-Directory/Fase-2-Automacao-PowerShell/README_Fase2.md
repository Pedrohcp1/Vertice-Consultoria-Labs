# Projeto de Laboratório: Infraestrutura Vértice Consultoria

Este projeto demonstra a criação e o gerenciamento de uma infraestrutura de TI completa baseada em Windows Server e Active Directory. Ele está sendo construído em fases para abranger diferentes competências.

---

## 🌳 Fases do Projeto

### ✅ Fase 1: Fundação do Active Directory (Concluída)
* **Descrição:** Instalação e configuração de um Controlador de Domínio, DNS, estrutura de OUs, usuários e implementação de Políticas de Grupo (GPOs) para padronização e segurança.
* **Habilidades Demonstradas:** Windows Server, AD DS, DNS, Group Policy Management, Troubleshooting.
* **[Ver Detalhes e Screenshots da Fase 1](#fase-1-detalhes)**

### ✅ Fase 2: Automação com PowerShell (Concluída)
* **Descrição:** Desenvolvimento de um script para automatizar a criação de novos usuários em massa a partir de um arquivo CSV, alocando-os dinamicamente em suas respectivas OUs.
* **Habilidades Demonstradas:** PowerShell Scripting, Automação de Tarefas, Manipulação de Dados (CSV).
* **[Ver Detalhes e Screenshots da Fase 2](#fase-2-detalhes)**

### 🔜 Fase 3: Servidor de Arquivos e Permissões (Próximos Passos)
* **Objetivo:** Configurar um servidor de arquivos com pastas departamentais e permissões de segurança NTFS específicas para cada grupo, garantindo que cada departamento acesse apenas seus próprios dados.

---

## <a name="fase-1-detalhes"></a> Fase 1: Detalhes da Fundação do AD

## 1. Visão Geral do Projeto
Neste projeto, foi simulada a criação e configuração de uma infraestrutura de Active Directory do zero para uma empresa fictícia de consultoria financeira, a "Vértice Consultoria". O objetivo foi implementar e demonstrar habilidades essenciais em administração de servidores Windows Server, incluindo a estruturação de um domínio, gerenciamento de usuários e aplicação de Políticas de Grupo (GPOs) para padronização e segurança.

## 2. Ambiente do Laboratório
* **Software de Virtualização:** Oracle VM VirtualBox
* **Controlador de Domínio (DC):** Windows Server 2022 Standard (SRV-DC01)
* **Máquina Cliente:** Windows 10 Enterprise (WKS-W10-01)
* **Rede:** Rede Interna Virtual com o range de IP 192.168.100.x

## 3. Etapas Executadas

### 3.1. Configuração do Domínio

A criação do ambiente começou com a preparação do servidor principal, seguida pela instalação dos serviços necessários e, finalmente, a configuração do domínio.

Preparação do Servidor

O processo iniciou-se com uma instalação limpa do sistema operacional Windows Server 2022 na máquina virtual SRV-DC01. Como pré-requisito fundamental para um Controlador de Domínio, a primeira configuração crítica realizada foi a definição de um endereço de IP estático (192.168.100.10). Essa etapa garante que o servidor sempre seja encontrado no mesmo "endereço" na rede, o que é vital para o serviço de DNS que será instalado posteriormente.

![image](https://github.com/user-attachments/assets/38073098-09a4-4a80-8750-58ff289a0404)

*Figura 1: Tela de configuração do IPV4 no Windows após a adição do IP estático.*

Instalação das Funções (Roles)

Utilizando o "Gerenciador do Servidor" (Server Manager), foi iniciado o assistente para "Adicionar Funções e Recursos". Foram selecionadas as duas funções essenciais para este projeto:

Active Directory Domain Services (AD DS): O serviço principal, responsável por criar e gerenciar o domínio, autenticar usuários e computadores, e aplicar políticas.

Servidor DNS: O serviço de "catálogo telefônico" da rede, indispensável para que os computadores consigam localizar o controlador de domínio e outros recursos pelo nome.

![Captura de tela 2025-07-02 193237](https://github.com/user-attachments/assets/89ede6d9-65f7-4784-a9d1-360342ebe94f)

*Figura 2: Demonstra quais ferramentas instalei no servidor para conclusão deste laboratório.*

Promoção a Controlador de Domínio

Após a instalação das funções, a etapa final foi a configuração pós-instalação, onde o servidor foi "promovido" a Controlador de Domínio. As decisões chave nesta fase foram:

Criação de uma nova floresta: Estabelecendo a "Vértice Consultoria" como uma organização completamente nova no Active Directory.

Definição do nome do domínio raiz: Foi escolhido o nome verticeconsultoria.local, utilizando o sufixo .local como boa prática de mercado para domínios internos que não são expostos à internet.

Configuração da senha do DSRM: Definição de uma senha segura para o Modo de Restauração dos Serviços de Diretório, um passo crucial para planos de recuperação de desastres.

![Captura de tela 2025-07-02 195210](https://github.com/user-attachments/assets/29374851-1811-4c34-a668-af88642453e2)

*Figura 3: Tela final com todas as configurações escolhidas por mim para este servidor.*

Após a reinicialização automática, o servidor passou a operar como o Controlador de Domínio principal da rede.

![Captura de tela 2025-07-04 144447](https://github.com/user-attachments/assets/5b6b97a2-8a25-4ac4-a792-ef263d52b031)
*Figura 4: Tela de login do Windows Server após a promoção, já mostrando o domínio VERTICECONSULTORIA.*

### 3.2. Estrutura Organizacional
* Criação de Unidades Organizacionais (OUs) para espelhar a estrutura da empresa:
    * `Diretoria`
    * `Consultores`
    * `Administrativo`
    * `TI`
  
![image](https://github.com/user-attachments/assets/a1cdaef3-9a4b-41ba-833f-4915ac963e61)

*Figura 5: Em destaque Unidades Organizacionais (departamentos) criados para a Vértice Consultoria*

* Criação de usuários de teste (`carla.moura`, `bruno.costa`) e alocação em suas respectivas OUs.

![image](https://github.com/user-attachments/assets/8fb5424f-b48f-406c-af2e-e6083a128805)

*Figura 6: Na imagem a criação do perfil da diretora Carla Moura.*

### 3.3. Implementação de Políticas de Grupo (GPOs)
Foram implementadas duas políticas principais para demonstrar o gerenciamento centralizado:

* **GPO de Padronização (`GPO - Padronizacao Desktop`):**
    * **Escopo:** Aplicada a todo o domínio.
    * **Ação:** Define um papel de parede de bloqueio padrão da empresa para todos os usuários.
    * **Resultado:** Login com qualquer usuário do domínio resulta na aplicação do wallpaper padrão.
  
![image](https://github.com/user-attachments/assets/dc6c5b46-055c-46e8-9237-0b24b80451d4)
*Figura 7: Tela de bloqueio da Vértice Consultoria.*

* **GPO de Segurança (`GPO - Restricoes Consultores`):**
    * **Escopo:** Aplicada apenas à OU `Consultores`.
    * **Ação:** Proíbe o acesso ao Painel de Controle para os usuários deste departamento.
    * **Resultado:** Usuários na OU `Consultores` recebem "acesso negado" ao tentar abrir o Painel de Controle, enquanto usuários de outras OUs (como `Diretoria`) mantêm o acesso normal.

![image](https://github.com/user-attachments/assets/7d3806dd-1e53-4038-b9f3-b63ca1e48626)
*Figura 8: Acesso negado ao painel de controle ao consultor.*

## 4. Desafios e Apredizados
Durante a execução do projeto, surgiram desafios práticos como a recuperação de uma senha de administrador utilizando o Modo de Restauração dos Serviços de Diretório (DSRM) e a solução de problemas de permissões em pastas compartilhadas para a aplicação de GPOs. Esses desafios foram fundamentais para solidificar o conhecimento em recuperação de desastres e diagnóstico de problemas em um ambiente de rede Windows.

## 5. Conclusão 
Este laboratório prático solidificou conhecimentos em administração de redes Windows, desde a instalação básica até a aplicação de políticas de segurança direcionadas. A principal competência demonstrada é a capacidade de criar um ambiente de TI organizado, seguro e gerenciado de forma centralizada e eficiente.


---

## <a name="fase-2-detalhes"></a> Fase 2: Detalhes da Automação com PowerShell

## 1. Objetivo

O processo manual de criação de novos usuários ("onboarding") em uma empresa é demorado e suscetível a erros. O objetivo desta fase foi desenvolver uma solução automatizada para provisionar novas contas de usuário no Active Directory de forma rápida, padronizada e eficiente.

## 2. Componentes da Solução

Para alcançar este objetivo, a solução foi dividida em dois componentes principais:

* **Fonte de Dados (`novos_funcionarios.csv`):** Foi criado um arquivo no formato CSV para servir como a fonte de dados padronizada, contendo as informações essenciais de cada novo colaborador (Nome, Sobrenome, Departamento, Cargo). Esta abordagem permite que o departamento de RH, por exemplo, preencha uma planilha simples que servirá de entrada para a automação.

* **Script de Automação (`criar_usuarios.ps1`):** O coração da automação é um script desenvolvido em PowerShell. Este script é responsável por ler os dados do arquivo CSV e interagir diretamente com o Active Directory para executar as tarefas de criação de contas.

![image](https://github.com/user-attachments/assets/ec424635-70f0-4636-9657-8fad5f14ea76)

Figura 1: Arquivo "novos_funcionários.cvs" criado no bloco de notas.

## 3. Detalhes da Implementação do Script

O script foi projetado para seguir uma lógica clara e robusta:

1.  **Importação de Dados:** Utilizando o cmdlet `Import-Csv`, o script inicia importando os dados do arquivo `.csv`, transformando cada linha em um objeto estruturado.
2.  **Loop de Processamento:** Através de um loop `foreach`, o script itera sobre cada registro (cada futuro funcionário) que foi importado do CSV, garantindo que a mesma sequência de ações seja aplicada a todos.
3.  **Criação Dinâmica do Usuário:** Para cada funcionário na lista, o cmdlet `New-ADUser` é utilizado para criar a conta no Active Directory. Os parâmetros são preenchidos dinamicamente com as informações do funcionário atual no loop.
4.  **Alocação na OU Correta:** O parâmetro `-Path` do comando `New-ADUser` utiliza a informação da coluna "Departamento" do CSV para alocar o novo usuário automaticamente na Unidade Organizacional (OU) correta, garantindo a organização do AD.
5.  **Configuração de Segurança:** Seguindo as melhores práticas, o script define uma senha inicial padrão e ativa a opção `-ChangePasswordAtLogon $true`, forçando o usuário a criar sua própria senha no primeiro login.

![Captura de tela 2025-07-08 084222](https://github.com/user-attachments/assets/ae954fee-dbe4-441d-80fa-3b32b0d0d1a6)

Figura 2: Script de criação de funcionários executado com êxito no Power Shell ISE.

## 4. Resultados e Benefícios

A execução do script resultou na criação bem-sucedida de 4 novos usuários em seus respectivos departamentos em menos de 5 segundos. Os principais benefícios alcançados são a drástica redução do tempo de trabalho, a eliminação de erros de digitação e a garantia de que todos os novos usuários são criados seguindo um padrão consistente.

![image](https://github.com/user-attachments/assets/233222db-71ad-426a-b986-16ee928fdccd)

Figura 3: Novos funcionários foram adicionados ao seus departamentos no Active Directory.




