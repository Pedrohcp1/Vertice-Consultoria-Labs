# Arquitetura do Laborat�rio de SOC - V�rtice Consultoria

## 1. Introdu��o e Objetivo


Este documento descreve a arquitetura e os componentes do ambiente de laborat�rio criado para simular as opera��es de um Security Operations Center (SOC) para a rede da V�rtice Consultoria. O objetivo deste laborat�rio � pr�ticar e documentar a implementa��o de ferramentas de monitoramento, detec��o e resposta a incidentes de seguran�a em um ambiente controlado que simula a infraestrutura da empresa.

## 2. Componentes do Laborat�rio

O ambiente � constru�do utilizando o Oracle VirtualBox e � composto pelas seguintes m�quinas virtuais (VMs):

| Hostname  | Sistema Operacional     | Fun��o Principal                         | Endere�o IP (Plano) | RAM / CPU (Sugerido) |
| --------- | ----------------------- | ---------------------------------------- | ------------------- | -------------------- |
| SRV-DC01  | Windows Server 2022     | Controlador de Dom�nio (AD DS), DNS      | `192.168.56.10`     | 2 GB / 2 CPUs        |
| WKS-ENT01 | Windows 10 Enterprise   | Esta��o de Trabalho do Usu�rio           | DHCP / Din�mico     | 2 GB / 2 CPUs        |
| SRV-SEC01 | Ubuntu Server 22.04 LTS | Servidor de Seguran�a (SIEM/IDS)         | `192.168.56.100`    | 4 GB / 2 CPUs        |

## 3. Arquitetura de Rede

Todas as m�quinas virtuais s�o configuradas para operar em uma **"Rede Interna"** do VirtualBox chamada `soc-net`. Isso cria um ambiente de laborat�rio isolado ("bolha"), onde as m�quinas podem se comunicar entre si, mas n�o t�m acesso direto � rede do hospedeiro ou � internet (ap�s a fase de instala��o).

O servidor **SRV-DC01** atua como o servidor DNS para a rede, garantindo que as m�quinas possam se resolver pelo nome dentro do dom�nio `vertice.local`.

## 4. Fluxo de Dados e Alertas

O fluxo de monitoramento foi desenhado para centralizar a visibilidade de seguran�a na VM **SRV-SEC01**, que atua como nosso servidor SIEM e IDS.

```ascii
+---------------------------------+      +--------------------------------+
|       SRV-DC01 (Win Server)     |      |    WKS-ENT01 (Win 10)          |
|        IP: 192.168.56.10        |      |      IP: DHCP                  |
|                                 |      |                                |
| [ Wazuh Agent ]-----------------|----->| [ Wazuh Agent ]----------------|----->+
+---------------------------------+      +--------------------------------+      |
                                                                                 |
           |                                                                     |
           | <--- Todo o tr�fego de rede passa por aqui ---> |                   |
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