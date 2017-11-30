---
title: Diretrizes gerais
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Diretrizes gerais"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 22dea926e77079e4f543934613ced13a28b2dae6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="general-guidance"></a>Diretrizes gerais

Esta seção fornece um resumo de quando escolher .NET Core ou do .NET Framework. Podemos fornecer mais detalhes sobre essas opções nas seções a seguir.

Você deve usar o .NET Core com contêineres do Windows, ou Linux para o aplicativo de servidor em contêineres do Docker quando:

-   Você tiver necessidades de plataforma cruzada. Por exemplo, você deseja usar ambos os contêineres do Windows e Linux.

-   A arquitetura do aplicativo é baseada em microservices.

-   Você precisa iniciar contêineres rápida e desejar uma superfície pequena por contêiner para obter melhor densidade ou mais contêineres por unidade de hardware para reduzir os custos.

Em resumo, quando você cria novos aplicativos .NET em contêineres, você deve considerar o núcleo do .NET como a opção padrão. Ela tem muitos benefícios e se ajuste melhor com o estilo de trabalho e filosofia de contêineres.

Um benefício adicional de usar o .NET Core é que você pode executar as versões do .NET lado a lado para aplicativos no mesmo computador. Esse benefício é mais importante para servidores ou máquinas virtuais que não usam contêineres, como contêineres isolar as versões do .NET que o aplicativo precisa. (Desde que eles sejam compatíveis com o sistema operacional subjacente.)

Você deve usar o .NET Framework, com contêineres do Windows para o aplicativo de servidor em contêineres do Docker quando:

-   Seu aplicativo usa o .NET Framework e tem dependências fortes no Windows.

-   Você precisa usar APIs do Windows que não são suportados pelo .NET Core.

-   Você precisa usar bibliotecas .NET de terceiros ou pacotes do NuGet que não estão disponíveis para o .NET Core.

Usando o .NET Framework no Docker pode melhorar sua experiência de implantação, minimizar os problemas de implantação. Isso [ *cenário "comparar e deslocar"* ](https://aka.ms/liftandshiftwithcontainersebook) é importante para aplicativos herdados que foram desenvolvidos originalmente com o .NET Framework tradicionais, como formulários da Web do ASP.NET, MVC web WCF (ou aplicativos de containerizing Serviços do Windows Communication Foundation).

### <a name="additional-resources"></a>Recursos adicionais

-   **livro eletrônico: modernizar aplicativos existentes do .NET Framework com o Azure e os contêineres do Windows**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **Aplicativos de exemplo: modernização aplicativos herdados de web do ASP.NET usando contêineres do Windows**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (net-core-contêiner-scenarios.md)
