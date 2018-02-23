---
title: Imagens oficiais do .NET Docker
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Imagens oficiais do .NET Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42872caa1a9306187daeefd35feb9bec3fae60af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="official-net-docker-images"></a>Imagens oficiais do .NET Docker

As imagens oficiais do .NET Docker são imagens do Docker criadas e otimizadas pela Microsoft. Elas ficam publicamente disponíveis nos repositórios da Microsoft no [Hub do Docker](https://hub.docker.com/u/microsoft/). Cada repositório pode conter várias imagens, dependendo de versões do .NET e, dependendo do sistema operacional e das versões (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).

A visão da Microsoft para repositórios do .NET é ter repositórios granulares e focados, em que um repositório representa um cenário ou carga de trabalho específico. Por exemplo, as imagens do [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) devem ser usadas ao usar o ASP.NET Core no Docker, porque essas imagens do ASP.NET Core fornecem otimizações adicionais para que os contêineres possam iniciar mais rapidamente.

Por outro lado, as imagens do .NET Core (microsoft/dotnet) são destinadas para aplicativos de console com base no .NET Core. Por exemplo, processos em lote, Azure WebJobs e outros cenários do console devem usar o .NET Core. Essas imagens não incluem a pilha do ASP.NET Core, resultando em uma imagem de contêiner menor.

A maioria dos repositórios de imagens fornecem marcação extensiva para ajudar a selecionar não apenas uma versão de estrutura específica, mas também escolher um sistema operacional (distribuição Linux ou versão do Windows).

Para obter mais informações sobre imagens oficiais do .NET Docker fornecidas pela Microsoft, consulte [resumo de imagens do .NET Docker](https://aka.ms/dotnetdockerimages).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Otimizações de imagem do .NET Core e do Docker para desenvolvimento versus produção

Ao criar imagens do Docker para desenvolvedores, a Microsoft se concentrava nos seguintes cenários principais:

-   Imagens usadas para *desenvolver* e criar aplicativos .NET Core.

-   Imagens usadas para *executar* aplicativos .NET Core.

Por que várias imagens? Ao desenvolver, criar e executar aplicativos em contêineres, você geralmente tem prioridades diferentes. Fornecendo diferentes imagens para essas tarefas separadas, a Microsoft ajuda a otimizar os processos separados de desenvolver, criar e implantar aplicativos.

### <a name="during-development-and-build"></a>Durante o desenvolvimento e o build

Durante o desenvolvimento, o que é importante é a velocidade em que é possível iterar alterações e a capacidade de depurá-las. O tamanho da imagem não é tão importante quanto a capacidade de fazer alterações em seu código e ver as alterações rapidamente. Algumas ferramentas e "contêineres de agente de build" usam a imagem de desenvolvimento do ASP.NET Core (microsoft/aspnetcore-build) durante o processo de build e de desenvolvimento. Ao compilar dentro de um contêiner do Docker, os aspectos importantes são os elementos necessários a fim de compilar seu aplicativo. Isso inclui o compilador e quaisquer outras dependências do .NET, além de dependências de desenvolvimento da Web como o npm, Gulp e Bower.

Por que este tipo de imagem de build é importante? Você não implanta essa imagem em produção. Em vez disso, é uma imagem usada para criar o conteúdo inserido em uma imagem de produção. Essa imagem seria usada em seu ambiente de CI (integração contínua) ou ambiente de build. Por exemplo, em vez de instalar manualmente todas as suas dependências de aplicativo diretamente em um host de agente de build (uma VM, por exemplo), o agente de build criaria uma instância de uma imagem de build do .NET Core com todas as dependências necessárias para criar o aplicativo. O agente de build precisa saber apenas como executar essa imagem do Docker. Isso simplifica seu ambiente de CI e o torna muito mais previsível.

### <a name="in-production"></a>Em produção

O que é importante na produção é a rapidez com que é possível implantar e iniciar seus contêineres com base em uma imagem do .NET Core de produção. Portanto, a imagem somente em tempo de execução baseada em [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) é pequena, então ela pode percorrer rapidamente a rede do seu Registro do Docker para seus hosts do Docker. O conteúdo está pronto para ser executado, habilitando o tempo mais rápido possível da inicialização do contêiner ao processamento de resultados. No modelo do Docker, não há necessidade de compilação de código C\#, como há quando você executa dotnet build ou dotnet publish ao usar o contêiner de build.

Nesta imagem otimizada você colocar somente os binários e outro conteúdo necessário para executar o aplicativo. Por exemplo, o conteúdo criado pelo dotnet publish contém apenas os binários do .NET compilados, imagens e arquivos .js e .css. Com o passar do tempo, você verá imagens que contêm pacotes pré-compilados com JIT.

Embora haja várias versões das imagens do .NET Core e do ASP.NET Core, todas elas compartilham uma ou mais camadas, incluindo a camada base. Portanto, a quantidade de espaço em disco necessário para armazenar uma imagem é pequena; ela é composta apenas pelo delta entre sua imagem personalizada e sua imagem de base. O resultado é que é rápido extrair a imagem do Registro.

Quando você explorar os repositórios de imagem do .NET no Hub do Docker, encontrará várias versões de imagem confidenciais ou marcadas. Essas marcas ajudam a decidir qual usar, dependendo da versão de que você precisa, como as que estão na tabela a seguir:

-   microsoft/**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   microsoft/**aspnetcore-build:2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Anterior] (net-container-os-targets.md) [Próximo] (../architect-microservice-container-applications/index.md)
