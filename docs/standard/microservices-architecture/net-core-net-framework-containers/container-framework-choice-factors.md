---
title: "Tabela de decisão. Versões do .NET Framework a ser usado para Docker"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Tabela de decisão, .NET Framework a ser usado para Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>Tabela de decisão: versões do .NET Framework a ser usado para Docker

A seguir resume se deseja usar contêineres do .NET Framework ou .NET Core e Windows ou Linux. Lembre-se de que, para contêineres do Linux, você precisa de hosts de Docker baseados em Linux (máquinas virtuais ou servidores) e para contêineres do Windows precisam do Windows Server com base em hosts de Docker (máquinas virtuais ou servidores).

Há vários recursos do aplicativo que afetam sua decisão. Você deve avaliar a importância desses recursos ao tomar essa decisão.

> [!IMPORTANT]
> As máquinas de desenvolvimento executará um host Docker, Linux ou Windows. Microservices relacionados que você deseja executar e testar juntos em uma única solução será necessário executar na mesma plataforma do contêiner.

* A opção de arquitetura de aplicativo é **Microservices em contêineres**.
    - A opção de implementação do .NET deve ser *.NET Core*.
    - Opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
* A opção de arquitetura de aplicativo é um **aplicativo monolítico**.
    - A opção de implementação do .NET pode ser *.NET Core* ou *do .NET Framework*.
    - Se você tiver escolhido *.NET Core*, sua opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
    - Se você tiver escolhido *do .NET Framework*, sua escolha de plataforma do contêiner deve ser *contêineres do Windows*.
* Seu aplicativo é um **novo desenvolvimento baseado em contêiner ("verde-field")**.
    - A opção de implementação do .NET deve ser *.NET Core*.
    - Opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
* Seu aplicativo é um **migração de aplicativo herdado ("brown-field") do Windows Server para contêineres**
    - A opção de implementação do .NET é *do .NET Framework* com base na dependência de estrutura.
    - Sua escolha de plataforma do contêiner deve ser *contêineres do Windows* devido a dependência do .NET Framework.
* Meta de design do seu aplicativo é **em melhor desempenho e escalabilidade**.
    - A opção de implementação do .NET deve ser *.NET Core*.
    - Opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
* Você criou seu aplicativo usando **ASP.NET Core**.
    - A opção de implementação do .NET deve ser *.NET Core*.
    - Você pode usar o *do .NET Framework* implementação, se você tiver outras dependências de estrutura.
    - Se você tiver escolhido *.NET Core*, sua opção de plataforma de contêiner pode ser *contêineres Linux* ou *contêineres do Windows*.
    - Se você tiver escolhido *do .NET Framework*, sua escolha de plataforma do contêiner deve ser *contêineres do Windows*.
* Você criou seu aplicativo usando **ASP.NET 4 (5 do MVC, API Web 2 e Web Forms)**.
    - A opção de implementação do .NET é *do .NET Framework* com base na dependência de estrutura.
    - Sua escolha de plataforma do contêiner deve ser *contêineres do Windows* devido a dependência do .NET Framework.
* Seu aplicativo usa **serviços SignalR**.
    - A opção de implementação do .NET pode ser *do .NET Framework*, ou *.NET Core 2.1 (quando liberado) ou posterior*.
    - Sua escolha de plataforma do contêiner deve ser *contêineres do Windows* se você escolher a implementação de SignalR no .NET Framework.
    - Opção de plataforma de contêiner pode ser Linux contêineres ou contêineres do Windows se você escolher a implementação de SignalR no .NET Core 2.1 ou posterior (quando liberado).  
    - Quando **serviços SignalR** executados em *.NET Core*, você pode usar *Linux contêineres ou contêineres do Windows*.
* Seu aplicativo usa **WCF, WF e outras estruturas herdadas**.
    - A opção de implementação do .NET é *do .NET Framework*, ou *.NET Core (em nossos planos para uma versão futura)*.
    - Sua escolha de plataforma do contêiner deve ser *contêineres do Windows* devido a dependência do .NET Framework.
* Seu aplicativo envolver **serviços de consumo do Azure**.
    - A opção de implementação do .NET é *do .NET Framework*, ou *.NET Core (o Azure, eventualmente, todos os serviços fornecerá SDKs de cliente para .NET Core)*.
    - Sua escolha de plataforma do contêiner deve ser *contêineres do Windows* se você usar APIs de cliente do .NET Framework.
    - Se você usar APIs disponíveis para o cliente *.NET Core*, você também pode escolher entre *Linux contêineres e Windows*.

>[!div class="step-by-step"]
[Anterior] (net-framework-contêiner-scenarios.md) [Avançar] (net-contêiner-os-targets.md)
