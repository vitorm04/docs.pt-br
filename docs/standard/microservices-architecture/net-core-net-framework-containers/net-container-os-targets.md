---
title: "Qual sistema operacional de destino com contêineres do .NET"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Qual sistema operacional de destino com contêineres do .NET"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a>Qual sistema operacional de destino com contêineres do .NET

Dada a diversidade de sistemas operacionais com suporte pelo Docker e as diferenças entre o .NET Framework e o .NET Core, você deve ter como destino um sistema operacional específico e versões específicas, dependendo da estrutura que você está usando. 

Para Windows, você pode usar o Windows Server Core ou Nano Server do Windows. Essas versões do Windows fornecem características diferentes (IIS no Windows Server Core em comparação com um servidor de web auto-hospedado como Kestrel no Nano Server) que podem ser necessários para o .NET Framework ou .NET Core, respectivamente. 

Para o Linux, várias distribuições estão disponíveis e com suporte oficial imagens Docker .NET (como Debian).

Figura 3-1, você verá a versão do SO possíveis dependendo do .NET framework usada.

![](./media/image1.png)

**Figura 3-1.** Sistemas operacionais para o destino dependendo de versões do .NET framework

Você também pode criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição de Linux diferente ou onde quer uma imagem com as versões não fornecidas pela Microsoft. Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework e Windows Server Core, que é um cenário não tão comuns para Docker tradicional.

Quando você adiciona o nome da imagem ao seu arquivo de Dockerfile, você pode selecionar o sistema operacional e versão de acordo com a marca que você usa, como nos exemplos a seguir:

-   Microsoft /**dotnet:2.0.0-tempo de execução-jessie**

        .NET Core 2.0 runtime-only on Linux

-   Microsoft /**dotnet:2.0.0-tempo de execução-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   Microsoft /**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[Anterior] (contêiner-estrutura-escolha-factors.md) [Avançar] (oficial-net-docker-images.md)
