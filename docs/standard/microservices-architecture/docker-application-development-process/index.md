---
title: Processo de desenvolvimento de aplicativos baseados no Docker
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Processo de desenvolvimento de aplicativos baseados no Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: f4c241f463ff1270037c7d66ba39409ca5d9e728
ms.contentlocale: pt-br
ms.lasthandoff: 09/05/2017

---
# <a name="development-process-for-docker-based-applications"></a>Processo de desenvolvimento de aplicativos baseados no Docker

*Desenvolva aplicativos .NET em contêineres da maneira que você gosta, seja usando o IDE com o Visual Studio e com as ferramentas do Visual Studio para Docker ou usando a CLI ou o Editor com a CLI do Docker e o Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Ambiente de desenvolvimento para aplicativos do Docker

### <a name="development-tool-choices-ide-or-editor"></a>Opções de ferramenta de desenvolvimento: IDE ou editor

Seja qual for a sua preferência, um IDE avançado e completo ou um editor leve e ágil, a Microsoft oferece as ferramentas que você pode usar para desenvolver aplicativos do Docker.

**Visual Studio com ferramentas para Docker**. Se estiver usando o Visual Studio 2015, você poderá instalar o suplemento [Ferramentas do Visual Studio para Docker](https://marketplace.visualstudio.com/items?itemName=MicrosoftCloudExplorer.VisualStudioToolsforDocker-Preview). Se você estiver usando o Visual Studio 2017, as ferramentas para Docker já estarão presentes. Em ambos os casos, as ferramentas para Docker permitem desenvolver, executar e validar seus aplicativos diretamente no ambiente do Docker de destino. Você pode pressionar F5 para executar e depurar seu aplicativo (contêiner único ou vários contêineres) diretamente em um host do Docker ou pressionar CTRL + F5 para editar e atualizar o aplicativo sem precisar recompilar o contêiner. Essa é a opção mais simples e mais eficiente para desenvolvedores do Windows direcionados aos contêineres do Docker para Windows ou do Linux.

**Visual Studio Code e a CLI do Docker**. Se preferir um editor leve e multiplataforma que dê suporte a qualquer linguagem de desenvolvimento, você poderá usar o VC Code (Microsoft Visual Studio Code) e a CLI do Docker. Essa é uma abordagem de desenvolvimento multiplataforma para Mac, Linux e Windows.

Esses produtos fornecem uma experiência simples mas robusta que simplifica o fluxo de trabalho do desenvolvedor. Ao instalar as ferramentas do [Docker CE (Community Edition)](https://www.docker.com/community-edition), você pode usar uma única CLI do Docker para criar aplicativos para Windows e Linux. Além disso, o Visual Studio Code dá suporte às extensões do Docker, como IntelliSense para Dockerfiles e tarefas de atalho, para executar os comandos do Docker usando o editor.

### <a name="additional-resources"></a>Recursos adicionais

-   **Visual Studio Tools for Docker** (Ferramentas do Visual Studio para Docker) 
    [*https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4*](https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4)

-   **Visual Studio Code**. Site oficial.
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   **Docker Community Edition (CE) for Mac and Windows** [Docker CE (Community Edition) para Mac e Windows] 
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Linguagens e estruturas do .NET para contêineres do Docker

Conforme mencionado nas seções anteriores deste guia, você pode usar o projeto do NET Framework, do .NET Core ou do Mono de software livre ao desenvolver aplicativos .NET em contêineres do Docker. Você poderá desenvolver em C\#, em F\# ou em Visual Basic ao direcionar a contêineres do Linux ou do Windows, dependendo de qual .NET Framework estiver em uso. Para saber mais detalhes sobre as linguagens do .NET detalhes, consulte a postagem no blog [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/) (A estratégia de linguagem do .NET).


>[!div class="step-by-step"]
[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)

