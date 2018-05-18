---
title: Tabela de decisões. Estruturas .NET a serem usadas para o Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Tabela de decisões, estruturas .NET a serem usadas para o Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0e384fabca88d8ad6f93ae626140fb3d5dcaf971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela de decisões: estruturas .NET a serem usadas para o Docker

A seguir, há um resumo se deve ser usado o .NET Framework ou o .NET Core e contêineres Linux ou do Windows. Lembre-se de que, para contêineres Linux, são necessários hosts do Docker baseados em Linux (VMs ou servidores) e de que, para contêineres do Windows, são necessários hosts do Docker baseados em Windows Server (VMs ou servidores).

Há vários recursos do seu aplicativo que afetam sua decisão. Você deve avaliar a importância desses recursos ao tomar essa decisão.

> [!IMPORTANT]
> Os computadores de desenvolvimento executarão um host Docker, seja Linux ou Windows. Microsserviços relacionados que você deseja executar e testar em conjunto em uma solução precisarão ser executados na mesma plataforma de contêiner.

* A opção de arquitetura de aplicativo é **Microsserviços em contêineres**.
    - Sua opção de implementação do .NET deve ser *.NET Core*.
    - A opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
* A opção de arquitetura de aplicativo é um **aplicativo monolítico**.
    - A opção de implementação do .NET pode ser *.NET Core* ou *.NET Framework*.
    - Se você tiver escolhido *.NET Core*, a opção de plataforma de contêiner poderá ser *contêineres Linux* ou *contêineres do Windows*.
    - Se você tiver escolhido *.NET Framework*, sua opção de plataforma de contêiner deverá ser *contêineres do Windows*.
* Seu aplicativo é um **novo desenvolvimento baseado em contêiner ("campo-verde")**.
    - Sua opção de implementação do .NET deve ser *.NET Core*.
    - A opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
* Seu aplicativo é uma **migração do aplicativo herdado do Windows Server ("campo-marrom") para contêineres**
    - A opção de implementação do .NET é *.NET Framework* com base na dependência de estrutura.
    - A opção de plataforma de contêiner deve ser *contêineres do Windows* devido à dependência do .NET Framework.
* A meta de design do seu aplicativo é **o melhor desempenho e escalabilidade da categoria**.
    - Sua opção de implementação do .NET deve ser *.NET Core*.
    - A opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
* Você criou seu aplicativo usando o **ASP.NET Core**.
    - Sua opção de implementação do .NET deve ser *.NET Core*.
    - Será possível usar a implementação do *.NET Framework* se você tiver outras dependências de estrutura.
    - Se você tiver escolhido *.NET Core*, a opção de plataforma de contêiner poderá ser *contêineres Linux* ou *contêineres do Windows*.
    - Se você tiver escolhido *.NET Framework*, sua opção de plataforma de contêiner deverá ser *contêineres do Windows*.
* Você criou seu aplicativo usando o **ASP.NET 4 (MVC 5, API Web 2 e Web Forms)**.
    - A opção de implementação do .NET é *.NET Framework* com base na dependência de estrutura.
    - A opção de plataforma de contêiner deve ser *contêineres do Windows* devido à dependência do .NET Framework.
* Seu aplicativo usa os **serviços SignalR**.
    - Sua opção de implementação do .NET pode ser *.NET Framework* ou *.NET Core 2.1 (quando lançado) ou posterior*.
    - Sua opção de plataforma de contêiner deverá ser *contêineres do Windows* se você tiver escolhido a implementação de SignalR no .NET Framework.
    - Sua opção de plataforma de contêiner poderá ser contêineres Linux ou contêineres do Windows se você tiver escolhido a implementação de SignalR no .NET Core 2.1 ou posterior (quando lançado).  
    - Quando os **serviços SignalR** são executados no *.NET Core*, é possível usar *contêineres Linux ou contêineres do Windows*.
* Seu aplicativo usa **WCF, WF e outras estruturas herdadas**.
    - A opção de implementação do .NET é *.NET Framework* ou *.NET Core (em nossos planos para um lançamento futuro)*.
    - A opção de plataforma de contêiner deve ser *contêineres do Windows* devido à dependência do .NET Framework.
* Seu aplicativo envolve **Consumo de serviços do Azure**.
    - Sua opção de implementação do .NET é *.NET Framework* ou *.NET Core (eventualmente, todos os serviços do Azure fornecerão SDKs de cliente para o .NET Core)*.
    - Sua opção de plataforma de contêiner deverá ser *contêineres do Windows* se você usar APIs de cliente do .NET Framework.
    - Se você usar APIs de cliente disponíveis para *.NET Core*, também será possível escolher entre *contêineres Linux e contêineres do Windows*.

>[!div class="step-by-step"]
[Anterior] (net-framework-container-scenarios.md) [Próximo] (net-container-os-targets.md)
