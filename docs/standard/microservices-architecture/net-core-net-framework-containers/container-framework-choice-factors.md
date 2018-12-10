---
title: Tabela de decisões. Estruturas .NET a serem usadas para o Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Tabela de decisões, estruturas .NET a serem usadas para o Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: 8044e3064ac372750c174d8b47c3f7a63d6bbd0b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149049"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela de decisões: estruturas .NET a serem usadas para o Docker

A tabela de decisão a seguir resume se deve-se usar o .NET Framework ou o .NET Core. Lembre-se de que, para contêineres Linux, são necessários hosts do Docker baseados em Linux (VMs ou servidores) e de que, para contêineres do Windows, são necessários hosts do Docker baseados em Windows Server (VMs ou servidores).

> [!IMPORTANT]
> Os computadores de desenvolvimento executarão um host Docker, seja Linux ou Windows. Microsserviços relacionados que você deseja executar e testar em conjunto em uma solução precisarão ser executados na mesma plataforma de contêiner.

<table>
<thead>
<tr class="header">
<th><strong>Arquitetura/tipo de aplicativo</strong></th>
<th><strong>Contêineres do Linux</strong></th>
<th><strong>Contêineres do Windows</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Microsserviços em contêineres</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Aplicativo monolítico</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>Melhores desempenho e escalabilidade da categoria</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Migração do aplicativo herdado do Windows Server ("campo-marrom") para contêineres</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>Novo desenvolvimento baseado em contêiner ("campo-verde")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (recomendado)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5, API Web 2 e Web Forms)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>Serviços SignalR</td>
<td>.NET Core 2.1 ou versão posterior</td>
<td><p>.NET Framework</p>
<p>.NET Core 2.1 ou versão posterior</p></td>
</tr>
<tr class="odd">
<td>WCF, WF e outras estruturas herdadas</td>
<td>WCF no .NET Core (somente a biblioteca de clientes WCF)</td>
<td><p>.NET Framework</p>
<p>WCF no .NET Core (somente a biblioteca de clientes WCF)</p></td>
</tr>
<tr class="even">
<td>Consumo de serviços do Azure</td>
<td><p>.NET Core</p>
<p>(eventualmente todos os serviços do Azure fornecerão SDKs do cliente para o .NET Core)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(eventualmente todos os serviços do Azure fornecerão SDKs do cliente para o .NET Core)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[Anterior](net-framework-container-scenarios.md)
>[Próximo](net-container-os-targets.md)