# Arquitetura do Laboratório de SOC - Vértice Consultoria

## 1. Introdução e Objetivo


Este documento descreve a arquitetura e os componentes do ambiente de laboratório criado para simular as operações de um Security Operations Center (SOC) para a rede da Vértice Consultoria. O objetivo deste laboratório é práticar e documentar a implementação de ferramentas de monitoramento, detecção e resposta a incidentes de segurança em um ambiente controlado que simula a infraestrutura da empresa.

## 2. Componentes do Laboratório

O ambiente é construído utilizando o Oracle VirtualBox e é composto pelas seguintes máquinas virtuais (VMs):

| Hostname  | Sistema Operacional     | Função Principal                         | Endereço IP (Plano) | RAM / CPU (Sugerido) |
| --------- | ----------------------- | ---------------------------------------- | ------------------- | -------------------- |
| SRV-DC01  | Windows Server 2022     | Controlador de Domínio (AD DS), DNS      | `192.168.56.10`     | 2 GB / 2 CPUs        |
| WKS-ENT01 | Windows 10 Enterprise   | Estação de Trabalho do Usuário           | DHCP / Dinâmico     | 2 GB / 2 CPUs        |
| SRV-SEC01 | Ubuntu Server 22.04 LTS | Servidor de Segurança (SIEM/IDS)         | `192.168.56.100`    | 4 GB / 2 CPUs        |

## 3. Arquitetura de Rede

Todas as máquinas virtuais são configuradas para operar em uma **"Rede Interna"** do VirtualBox chamada `soc-net`. Isso cria um ambiente de laboratório isolado ("bolha"), onde as máquinas podem se comunicar entre si, mas não têm acesso direto à rede do hospedeiro ou à internet (após a fase de instalação).

O servidor **SRV-DC01** atua como o servidor DNS para a rede, garantindo que as máquinas possam se resolver pelo nome dentro do domínio `vertice.local`.

## 4. Fluxo de Dados e Alertas

O fluxo de monitoramento foi desenhado para centralizar a visibilidade de segurança na VM **SRV-SEC01**, que atua como nosso servidor SIEM e IDS.

```ascii
+---------------------------------+      +--------------------------------+
|       SRV-DC01 (Win Server)     |      |    WKS-ENT01 (Win 10)          |
|        IP: 192.168.56.10        |      |      IP: DHCP                  |
|                                 |      |                                |
| [ Wazuh Agent ]-----------------|----->| [ Wazuh Agent ]----------------|----->+
+---------------------------------+      +--------------------------------+      |
                                                                                 |
           |                                                                     |
           | <--- Todo o tráfego de rede passa por aqui ---> |                   |
           |                                                                     |
           v                                                                     |
+--------------------------------------------------------------------------------+
|                                SRV-SEC01 (Ubuntu Server)                       |
|                                  IP: 192.168.56.100                            |
|                                                                                |
|    +------------------+      +------------------------------------------+      |
|    | [ Snort IDS ]    |----->|             [ Wazuh Server ]             |      |
|    | (Analisa a Rede) |      | (Coleta, Analisa e Alerta os Logs)       | <----+
|    +------------------+      +------------------------------------------+      |
|                                                                                |
+--------------------------------------------------------------------------------+