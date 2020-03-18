---
title: Imagens oficiais do .NET Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Imagens oficiais do .NET Docker
ms.date: 01/30/2020
ms.openlocfilehash: 50a50587b35f811859841c4e049f40cb99479372
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501875"
---
# <a name="official-net-docker-images"></a>Imagens oficiais do .NET Docker

As imagens oficiais do .NET Docker são imagens do Docker criadas e otimizadas pela Microsoft. Eles estão disponíveis publicamente nos repositórios da Microsoft no [Docker Hub](https://hub.docker.com/u/microsoft/). Cada repositório pode conter várias imagens, dependendo de versões do .NET e, dependendo do sistema operacional e das versões (Linux Debian, Linux Alpine, Windows Nano Server, Windows Server Core, etc.).

Desde o .NET Core 2.1, todas as imagens do .NET Core, incluindo ASP.NET Core, <https://hub.docker.com/_/microsoft-dotnet-core/>estão disponíveis no Docker Hub no repositório de imagens .NET Core: .

Desde maio de 2018, as imagens da Microsoft estão sendo [sindicalizadas no Microsoft Container Registry](https://azure.microsoft.com/blog/microsoft-syndicates-container-catalog/). O catálogo oficial ainda está disponível apenas no Docker Hub, e lá você encontrará o endereço atualizado para puxar a imagem.

A maioria dos repositórios de imagem fornece uma marcação extensiva para ajudá-lo a selecionar não apenas uma versão específica da estrutura, mas também para escolher um SISTEMA OPERACIONAL (distribuição Linux ou versão do Windows).

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>Otimizações de imagem do .NET Core e do Docker para desenvolvimento versus produção

Ao criar imagens do Docker para desenvolvedores, a Microsoft se concentrava nos seguintes cenários principais:

- Imagens usadas para *desenvolver* e criar aplicativos .NET Core.

- Imagens usadas para *executar* aplicativos .NET Core.

Por que várias imagens? Ao desenvolver, criar e executar aplicativos em contêineres, você geralmente tem prioridades diferentes. Fornecendo diferentes imagens para essas tarefas separadas, a Microsoft ajuda a otimizar os processos separados de desenvolver, criar e implantar aplicativos.

### <a name="during-development-and-build"></a>Durante o desenvolvimento e o build

Durante o desenvolvimento, o que é importante é a velocidade em que é possível iterar alterações e a capacidade de depurá-las. O tamanho da imagem não é tão importante quanto a capacidade de fazer alterações no seu código e ver as alterações rapidamente. Algumas ferramentas e "recipientes de agente de construção", usam o desenvolvimento da imagem .NET Core *(mcr.microsoft.com/dotnet/core/sdk:3.1)* durante o processo de desenvolvimento e construção. Ao construir dentro de um contêiner Docker, os aspectos importantes são os elementos necessários para compilar seu aplicativo. Isso inclui o compilador e quaisquer outras dependências do .NET.

Por que este tipo de imagem de build é importante? Você não implanta esta imagem na produção. Em vez disso, é uma imagem que você usa para construir o conteúdo que você coloca em uma imagem de produção. Essa imagem seria usada em seu ambiente de integração contínua (CI) ou ambiente de construção ao usar compilações multiestágio sumidas do Docker.

### <a name="in-production"></a>Em produção

O que é importante na produção é a rapidez com que é possível implantar e iniciar seus contêineres com base em uma imagem do .NET Core de produção. Portanto, a imagem somente em tempo de execução com base em *mcr.microsoft.com/dotnet/core/aspnet:3.1* é pequena para que ela possa viajar rapidamente pela rede do seu registro Docker para seus hosts Docker. O conteúdo está pronto para ser executado, habilitando o tempo mais rápido possível da inicialização do contêiner ao processamento de resultados. No modelo do Docker, não há necessidade de compilação de código C\#, como há quando você executa dotnet build ou dotnet publish ao usar o contêiner de build.

Nesta imagem otimizada, você coloca apenas os binários e outros conteúdos necessários para executar o aplicativo. Por exemplo, o conteúdo `dotnet publish` criado por contém apenas os binários.NET compilados, imagens, .js e .css. Ao longo do tempo, você verá imagens que contêm pacotes pré-compilados (compilação de IL para nativa que ocorre em runtime).

Embora haja várias versões das imagens do .NET Core e do ASP.NET Core, todas elas compartilham uma ou mais camadas, incluindo a camada base. Portanto, a quantidade de espaço em disco necessário para armazenar uma imagem é pequena, ela é composta apenas pelo delta entre sua imagem personalizada e sua imagem de base. O resultado é que é rápido extrair a imagem do Registro.

Quando você explorar os repositórios de imagem do .NET no Hub do Docker, encontrará várias versões de imagem confidenciais ou marcadas. Essas marcas ajudam a decidir qual usar, dependendo da versão de que você precisa, como as que estão na tabela a seguir:

| Imagem | Comentários |
|-------|----------|
| mcr.microsoft.com/dotnet/core/aspnet:**3,1** | ASP.NET Core, somente com runtime e otimizações de ASP.NET Core, no Linux e no Windows (várias arquiteturas) |
| mcr.microsoft.com/dotnet/core/sdk:**3.1** | .NET Core, com SDKs incluídos, no Linux e no Windows (várias arquiteturas) |

> [!div class="step-by-step"]
> [Próximo](net-container-os-targets.md)
> [anterior](../architect-microservice-container-applications/index.md)
