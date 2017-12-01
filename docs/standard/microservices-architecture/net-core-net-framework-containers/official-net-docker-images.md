---
title: Imagens do Docker .NET oficiais
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Imagens do Docker .NET oficiais"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 6f14bd0cf55a552f3881d755ebe7389f000975d8
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="official-net-docker-images"></a>Imagens do Docker .NET oficiais

As imagens do Docker oficial do .NET são imagens do Docker criados e otimizados pela Microsoft. Estiverem publicamente disponíveis nos repositórios no Microsoft [Hub do Docker](https://hub.docker.com/u/microsoft/). Cada repositório pode conter várias imagens, dependendo de versões do .NET e, dependendo do sistema operacional e as versões (Linux Debian Alpine do Linux, Windows Nano Server, Windows Server Core, etc.).

A visão da Microsoft para repositórios de .NET é ter granulares e determinados repositórios, onde um repositório representa um cenário específico ou a carga de trabalho. Por exemplo, o [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) imagens devem ser usadas quando usando o ASP.NET Core no Docker, porque essas imagens ASP.NET Core fornecem otimizações adicionais caso contêineres pode iniciar mais rapidamente.

Por outro lado, as imagens do núcleo do .NET (microsoft/dotnet) são destinadas ao aplicativos de console com base em .NET Core. Por exemplo, os processos em lote do Azure WebJobs e outros cenários do console devem usar .NET Core. Essas imagens não incluem a pilha do ASP.NET Core, resultando em uma imagem de contêiner menor.

A maioria dos repositórios de imagem fornecem amplo marcação para ajudá-lo a selecionar não apenas uma versão específica do framework, mas também para escolher um sistema operacional (distribuição Linux ou versão do Windows).

Para obter mais informações sobre as imagens do Docker .NET oficiais fornecida pela Microsoft, consulte o [resumo de imagens do Docker .NET](https://aka.ms/dotnetdockerimages).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>.NET core e o Docker otimizações de imagem para o desenvolvimento e produção

Ao criar imagens do Docker para desenvolvedores, a Microsoft se concentra em cenários principais a seguir:

-   Imagens usadas para *desenvolver* e criar aplicativos .NET Core.

-   Imagens usadas para *executar* aplicativos .NET Core.

Por que várias imagens? Ao desenvolver, compilar e executar aplicativos em contêineres, você geralmente têm prioridades diferentes. Ao fornecer imagens diferentes para essas tarefas separadas, a Microsoft ajuda a otimizar os processos separados de desenvolvimento, criação e implantação de aplicativos.

### <a name="during-development-and-build"></a>Durante a criação e desenvolvimento

Durante o desenvolvimento, o que é importante é a velocidade é possível iterar alterações e a capacidade de depurar as alterações. O tamanho da imagem não é tão importante quanto a capacidade de fazer alterações no seu código e ver as alterações rapidamente. Algumas ferramentas e "contêineres de agente de compilação", use o desenvolvimento de imagem do ASP.NET Core (aspnetcore/microsoft-compilação) durante o desenvolvimento e processo de compilação. Ao criar um contêiner do Docker, os aspectos importantes são os elementos que são necessários para compilar seu aplicativo. Isso inclui o compilador e quaisquer outras dependências do .NET, além de dependências de desenvolvimento da web como o npm, Gulp e Bower.

Por esse tipo de imagem de compilação é importante? Você não implantar essa imagem em produção. Em vez disso, é uma imagem que você pode usar para construir o conteúdo que você coloca em uma imagem de produção. Essa imagem será usada em seu ambiente de CI (integração contínua) ou o ambiente de compilação. Por exemplo, em vez de instalar manualmente todas as suas dependências de aplicativo diretamente em um agente de compilação de host (uma VM, por exemplo), o agente de compilação seria criar uma instância de uma imagem de compilação do .NET Core com todas as dependências necessárias para criar o aplicativo. O agente de build precisa saber apenas como executar essa imagem do Docker. Isso simplifica o seu ambiente de CI e torna muito mais previsível.

### <a name="in-production"></a>Em produção

O que é importante na produção é rapidez você pode implantar e iniciar os contêineres com base em uma imagem de .NET Core de produção. Portanto, a imagem somente em tempo de execução com base em [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) é pequeno para que ele pode percorrer rapidamente a rede de seu registro de Docker para seus hosts de Docker. O conteúdo está pronto para ser executado, permitindo que o tempo mais rápido de iniciar o contêiner com o processamento de resultados. No modelo do Docker, não é necessário para a compilação do C\# de código, como há quando você executa dotnet compilação ou dotnet publicar quando usando o contêiner de compilação.

Nesta imagem otimizada você colocar somente os binários e outro conteúdo necessário para executar o aplicativo. Por exemplo, publicar o conteúdo criado por dotnet contém apenas os binários .NET compilados, imagens,. js e arquivos. CSS. Ao longo do tempo, você verá imagens que contêm pacotes pré-compilados JIT.

Embora haja várias versões das imagens .NET Core e ASP.NET Core, todos eles compartilham uma ou mais camadas, incluindo a camada base. Portanto, a quantidade de espaço em disco necessário para armazenar uma imagem é pequena. Ele consiste apenas no delta entre sua imagem personalizada e sua imagem de base. O resultado é que é rápido extrair a imagem do registro.

Ao explorar os repositórios de imagem do .NET no Hub do Docker, você encontrará várias versões de imagem classificados ou marcado com marcas. Essas marcas ajudam a decidir qual delas usar, dependendo da versão que você precisa, como aqueles na tabela a seguir:

-   Microsoft /**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   Microsoft /**aspnetcore-compilação: 2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Anterior] (net-contêiner-os-targets.md) [Avançar] (... /Architect-microservice-container-Applications/Index.MD)
