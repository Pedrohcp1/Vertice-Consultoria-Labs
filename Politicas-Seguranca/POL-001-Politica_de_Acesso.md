# Política de acesso da Vértice Consultoria

| Propriedade          | Valor                             |
| --------------------- | --------------------------------- |
| **ID do Documento** | POL-001                           |
| **Título** | Política de Controle de Acesso    |
| **Versão** | 1.0                               |
| **Status** | Rascunho                          |
| **Data de Aprovação** | (15/07/2025)                      |
| **Proprietário** | Departamento de TI / Segurança    |

## 1. Objetivo

O objetivo desta política é estabelecer as diretrizes e os padrões para a concessão, gerenciamento e revogação de acesso aos sistemas de informação, dados e recursos da Vértice Consultoria, garantindo que apenas pessoas autorizadas tenham acesso às informações necessárias para realizar suas funções.

---
## 2. Escopo

Esta política se aplica a todos os colaboradores, funcionários em tempo integral, meio período, estagiários, prestadores de serviço e terceiros (coletivamente denominados "Usuários") da Vértice Consultoria.

Ela abrange o acesso a todos os sistemas de informação, redes, aplicativos (SaaS, PaaS, IaaS), bancos de dados e dados de propriedade ou gerenciados pela Vértice Consultoria, independentemente do local de acesso (escritório, remoto, etc.).

---
## 3. Papéis e Responsabilidades

* **Proprietário do Sistema/Informação (System/Information Owner):**
    * Geralmente um diretor ou gerente de área (ex: Diretor Financeiro para o sistema financeiro).
    * É o responsável final pela informação. Define quem deve ter acesso aos dados e classifica a sensibilidade da informação. Não é um papel técnico.

* **Administrador do Sistema (System Administrator):**
    * A equipe de TI ou o profissional responsável pela configuração técnica do sistema (ex: a "Vértice Consultoria").
    * Implementa os controles de acesso conforme definido pelo Proprietário do Sistema. Realiza a criação de contas, atribuição de permissões e manutenção técnica.

* **Usuário Final (End User):**
    * Qualquer colaborador que utiliza o sistema para realizar seu trabalho.
    * É responsável por usar seu acesso de forma segura, proteger sua senha e seguir as políticas da empresa.

* **Auditor:**
    * Responsável por revisar e verificar se os acessos concedidos estão de acordo com as políticas e se os controles estão funcionando como esperado.
    * Tipicamente, possui acesso de "apenas leitura" (read-only) aos logs de acesso e configurações do sistema para não interferir na operação. Pode ser um papel interno (Controles Internos) ou externo (auditoria independente).

---
## 4. Diretrizes para Concessão de Acesso

Todo acesso aos recursos da Vértice Consultoria deve seguir as seguintes diretrizes fundamentais:

* **Princípio do Menor Privilégio (PoLP - Principle of Least Privilege):**
    * A cada usuário será concedido o nível mínimo de permissões e acesso estritamente necessário para o desempenho de suas funções. O acesso "por padrão" é negado.

* **Necessidade de Saber (Need-to-Know):**
    * O acesso a informações específicas só será concedido se houver uma necessidade de negócio legítima e documentada para tal.

* **Processo de Aprovação Formal:**
    * Nenhum acesso será concedido sem um registro de solicitação e a aprovação formal do **Proprietário do Sistema/Informação** relevante.

* **Revisão Periódica de Acessos:**
    * As permissões de acesso de todos os usuários devem ser revisadas em intervalos regulares (no mínimo, anualmente) e imediatamente após qualquer mudança de função, promoção ou término de contrato.

* **Segregação de Funções (Segregation of Duties - SoD):**
    * Funções críticas devem ser segregadas para evitar que um único indivíduo tenha controle excessivo sobre um processo, reduzindo o risco de fraude ou erro.

* **Acesso para Contas Não-Humanas (Contas de Serviço):**
    * Contas utilizadas por aplicações e scripts devem ter suas senhas gerenciadas de forma segura (ex: cofres de senhas), suas permissões devem ser extremamente restritas ao escopo de sua função e devem ser revisadas com maior frequência.

---
## 5. Procedimentos de Gerenciamento de Acesso

O ciclo de vida do acesso de um usuário (solicitação, aprovação, concessão e revogação) seguirá os procedimentos formais descritos abaixo.

* **5.1. Solicitação e Aprovação:**
    * Toda necessidade de um novo acesso ou alteração de um acesso existente deve ser formalizada através de uma solicitação no sistema de chamados da TI, iniciada pelo gestor direto do usuário.
    * A solicitação deve conter a justificativa de negócio, os sistemas envolvidos e o nível de permissão desejado.
    * A aprovação da solicitação é de responsabilidade do **Proprietário do Sistema/Informação**, que avaliará se o pedido está de acordo com o Princípio do Menor Privilégio e a Necessidade de Saber.

* **5.2. Concessão e Implementação:**
    * Após o recebimento da aprovação formal, o **Administrador do Sistema** (Equipe de TI) será responsável por criar ou modificar as permissões do usuário.
    * O acesso concedido deve ser exatamente o que foi aprovado, nem mais, nem menos. Toda concessão deve ser registrada no chamado para fins de auditoria.

* **5.3. Revisão e Recertificação:**
    * Conforme a diretriz de Revisão Periódica, os **Proprietários de Sistema** receberão, no mínimo anualmente, um relatório de todos os usuários com acesso aos seus respectivos sistemas.
    * É de responsabilidade do Proprietário revisar e "recertificar" a necessidade de cada acesso, solicitando a remoção dos que não são mais necessários.

* **5.4. Revogação de Acesso:**
    * O processo de revogação de acesso é iniciado automaticamente pelo departamento de RH durante o processo de desligamento de um colaborador.
    * Todo o acesso do usuário aos sistemas da Vértice Consultoria deve ser removido pelo **Administrador do Sistema** no máximo até o final do último dia de trabalho do colaborador.

---
## 6. Consequências do Não Cumprimento

A violação de qualquer diretriz estabelecida nesta política por parte de um colaborador ou prestador de serviço será tratada com seriedade. Ações disciplinares podem ser aplicadas de acordo com a gravidade da violação, em conformidade com as políticas do departamento de Recursos Humanos e a legislação vigente, podendo incluir advertência verbal ou escrita, suspensão, ou término do contrato de trabalho/serviço.

---
## 7. Revisão e Manutenção da Política

Esta política será revisada anualmente, ou sempre que ocorrerem mudanças significativas no ambiente de negócios ou tecnológico que impactem a gestão de acessos. A responsabilidade pela revisão e atualização do documento é do **Proprietário** definido no cabeçalho desta política.