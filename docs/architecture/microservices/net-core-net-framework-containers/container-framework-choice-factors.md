---
title: Tabela de decisões. Estruturas .NET a serem usadas para o Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Tabela de decisões, estruturas .NET a serem usadas para o Docker
ms.date: 09/11/2018
ms.openlocfilehash: 0087d80c2d949daf14e1edd773dd310f47c508a9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039672"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela de decisões: estruturas .NET a serem usadas para o Docker

A tabela de decisão a seguir resume se deve-se usar o .NET Framework ou o .NET Core. Lembre-se de que, para contêineres Linux, são necessários hosts do Docker baseados em Linux (VMs ou servidores) e de que, para contêineres do Windows, são necessários hosts do Docker baseados em Windows Server (VMs ou servidores).

> [!IMPORTANT]
> Os computadores de desenvolvimento executarão um host Docker, seja Linux ou Windows. Microsserviços relacionados que você deseja executar e testar em conjunto em uma solução precisarão ser executados na mesma plataforma de contêiner.

| Arquitetura/tipo de aplicativo | Contêineres do Linux | Contêineres do Windows |
|-------------------------|------------------|--------------------|
| Microsserviços em contêineres | .NET Core | .NET Core |
| Aplicativo monolítico | .NET Core | .NET Framework <br/> .NET Core |
| Melhores desempenho e escalabilidade da categoria | .NET Core | .NET Core |
| Migração do aplicativo herdado do Windows Server ("campo-marrom") para contêineres | -- | .NET Framework |
| Novo desenvolvimento baseado em contêiner ("campo-verde") | .NET Core | .NET Core |
| ASP.NET Core | .NET Core | .NET Core (recomendado) <br/> .NET Framework |
| ASP.NET 4 (MVC 5, API Web 2 e Web Forms) | -- | .NET Framework |
| Serviços SignalR | .NET Core 2.1 ou versão posterior | .NET Framework <br/> .NET Core 2.1 ou versão posterior |
| WCF, WF e outras estruturas herdadas | WCF no .NET Core (somente biblioteca de cliente) | .NET Framework <br/> WCF no .NET Core (somente biblioteca de cliente) |
| Consumo de serviços do Azure | .NET Core <br/> (eventualmente todos os serviços do Azure fornecerão SDKs do cliente para o .NET Core) | .NET Framework <br/> .NET Core <br/> (eventualmente todos os serviços do Azure fornecerão SDKs do cliente para o .NET Core) |

>[!div class="step-by-step"]
>[Anterior](net-framework-container-scenarios.md)
>[Próximo](net-container-os-targets.md)
