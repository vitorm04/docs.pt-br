---
title: "Introdução ao .NET e ao Docker"
description: "Noções básicas do Docker e do .NET Core"
keywords: .NET, .NET Core, Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.workload:
- dotnetcore
ms.openlocfilehash: dabc7c0c4a0afab8edf7d2bab410bb9635821936
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="introduction-to-net-and-docker"></a>Introdução ao .NET e ao Docker

Este artigo fornece uma introdução e uma base conceitual para trabalhar com o .NET no Docker.

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: empacotar seus aplicativos para implantar e executar em qualquer lugar

[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) é uma plataforma aberta que permite aos desenvolvedores e administradores compilar [imagens](https://docs.docker.com/glossary/?term=image), enviar e executar aplicativos distribuídos em um ambiente isolado de forma flexível chamado de [contêiner](https://www.docker.com/what-container). Essa abordagem permite um gerenciamento eficiente do ciclo de vida do aplicativo entre ambientes de desenvolvimento, garantia de qualidade e produção.
 
A [plataforma do Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [Mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para compilar e empacotar rapidamente aplicativos como [imagens do Docker](https://docs.docker.com/glossary/?term=image) criadas usando arquivos escritos no formato [Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) que, depois, são implantados e executados em um [contêiner de camadas ](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Você pode criar suas próprias [imagens em camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) como dockerfiles, ou usar imagens existentes de um [registro](https://docs.docker.com/glossary/?term=registry), como [Hub do Docker](https://docs.docker.com/glossary/?term=Docker%20Hub).

A [relação entre contêineres, imagens e registros do Docker](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) é um conceito importante ao [arquitetar e compilar aplicativos ou microsserviços em contêineres](../../standard/microservices-architecture/architect-microservice-container-applications/index.md). Essa abordagem reduz bastante o tempo entre o desenvolvimento e a implantação.

### <a name="further-reading-and-watching"></a>Leituras (e vídeos) adicionais

* [Contêineres baseados em Windows: desenvolvimento de aplicativos modernos com controle de nível empresarial.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Visão geral do docker](https://docs.docker.com/engine/docker-overview/)
* [Dockerfile em contêineres do Windows](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Práticas recomendadas para escrever Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Compilar Imagens do Docker para aplicativos .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Obtendo imagens do Docker no .NET

As imagens oficiais do .NET Docker são criadas e otimizadas pela Microsoft. Elas ficam publicamente disponíveis nos repositórios da Microsoft no Hub do Docker. Cada repositório pode conter várias imagens, dependendo das versões do .NET e das versões do sistema operacional. A maioria dos repositórios de imagens fornecem muitas opções de marcação para ajudar você a selecionar uma versão específica do framework e um sistema operacional (distribuição Linux ou versão do Windows).

## <a name="scenario-based-guidance"></a>Diretrizes baseadas em cenário

A intenção da Microsoft para repositórios do .NET é ter repositórios granulares e focados, que representam um cenário ou carga de trabalho específica.

As imagens `microsoft/aspnetcore` são otimizadas para aplicativos do ASP.NET Core no Docker, assim os contêineres podem ser iniciados com mais rapidez.

As imagens do .NET Core (`microsoft/dotnet`) servem para aplicativos de console com base no .NET Core. Por exemplo, processos em lote, Azure WebJobs e outros cenários do console devem usar imagens otimizadas do .NET Core.

O cenário horizontal mais óbvio para o uso de aplicativos .NET e de Docker é para implantação de produção e hospedagem. Acontece que produção é apenas um cenário, e os outros são igualmente úteis. Esses cenários não são específicos ao .NET, mas devem ser aplicados à maioria das plataformas de desenvolvimento.

* **Instalação de baixa fricção** — Você pode experimentar o .NET sem uma instalação local. Basta baixar uma imagem do Docker com o .NET nele.

* **Desenvolver em um contêiner**: você pode desenvolver em um ambiente consistente, tornando os ambientes de desenvolvimento e produção semelhantes (evitando problemas como estado global em computadores de desenvolvedor). As Ferramentas do Visual Studio para Docker permitem até que você inicie um contêiner diretamente do Visual Studio.

* **Testar em um contêiner**: você pode testar em um contêiner, reduzindo falhas devido a ambientes configurados incorretamente ou a outras alterações deixadas para trás do último teste.

* **Compilar um contêiner**: você pode compilar o código em um contêiner, evitando a necessidade de configurar corretamente as máquinas de compilação compartilhadas com vários ambientes, mas, em vez disso, mudar para uma abordagem "BYOC" (traga seu próprio contêiner).

* **Implantação em todos os ambientes**: você pode implantar uma imagem em todos os seus ambientes. Essa abordagem reduz falhas devido a diferenças de configuração, normalmente alterando o comportamento da imagem por meio da configuração externa (por exemplo, variáveis de ambiente injetadas).

[Orientação geral](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) para decidir entre o .NET Core e o .NET Framework para desenvolvimento de contêiner do Docker.

### <a name="common-docker-development-scenarios"></a>Cenários comuns de desenvolvimento do Docker

#### <a name="net-core"></a>.NET Core

**Recursos do .NET Core**

 Escolha os exemplos do .NET Core que se ajustam aos cenários de seu interesse. Todas as instruções de exemplo descrevem como direcionar imagens do Docker para Windows ou do Linux a partir de hosts do Windows, Linux ou macOS.

Os exemplos usam o .NET Core 2.0. Eles usam a [compilação de vários estágios](https://github.com/dotnet/announcements/issues/18) do Docker e [marcas de vários arcos](https://github.com/dotnet/announcements/issues/14), quando apropriado.

* [Imagens do .NET Core no DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Colocar no docker um aplicativo .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* Este exemplo de Docker no .NET Core demonstra como [usar o Docker em seu processo de desenvolvimento do .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). O exemplo funciona com contêineres do Linux e do Windows.

* Este exemplo do Docker no .NET Core demonstra um padrão de prática recomendada para [compilação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) O exemplo funciona com contêineres do Linux e do Windows.

* Este [exemplo do Docker no .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstra um padrão de prática recomendada para compilação de imagens do Docker para [aplicativos .NET Core autossuficientes](../deploying/index.md). Usado para o menor contêiner de produção sem um benefício do [compartilhamento de imagens base entre contêineres](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). No entanto, camadas inferiores do Docker podem ser compartilhadas.

#### <a name="arm32--raspberry-pi"></a>ARM32 / Raspberry Pi

* [Anúncio de compilações ARM32 do tempo de execução do .NET Core](https://github.com/dotnet/announcements/issues/29)

* [Imagens do .NET Core para ARM32 / Raspberry Pi no DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Exemplos do Docker do .NET Core ARM32 / Raspberry Pi no GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Imagens do .NET framework no DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/)

Este repositório contém exemplos que demonstram várias configurações do Docker do .NET Framework. Use essas imagens como a base de suas próprias imagens do Docker.

**.NET Framework 4.7**

A [amostra dotnet-framework:4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstra o uso básico de “olá, mundo” do [.NET Framework 4.7](../../framework/whats-new/index.md#v47). Ele mostra como você pode compilar e implantar o aplicativo dependendo da [imagem do docker para .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**.NET Framework 4.6.2**

O [exemplo dotnet-framework:4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstra o uso de "hello world" básico do [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462). Ele mostra como você pode compilar e implantar o aplicativo dependendo da [imagem do docker para .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**.NET Framework 3.5**

 O [exemplo dotnet-framework:3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstra o uso de "hello world" básico do [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Ele mostra como você pode compilar e implantar um projeto dependendo do .NET Framework 3.5 no Docker.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Este exemplo do Docker no ASP.NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstra um padrão de prática recomendada para compilação de imagens do Docker para aplicativos ASP.NET Core para produção. O exemplo funciona com contêineres do Linux e do Windows.

* [Imagens do ASP.NET Core no DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Imagens do ASP.NET Core no GitHub](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>ASP.NET Framework

* [Imagens do ASP.NET Framework no DockerHub](https://hub.docker.com/r/microsoft/aspnet/)

* [Exemplo de aplicativo Web Forms do ASP.NET no .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Imagens do Windows Communication Framework (WCF) no DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [Imagens do Windows Communication Framework (WCF) no GitHub](https://github.com/microsoft/iis-docker)

* [Exemplos de Docker do Windows Communication Framework (WCF) usando o .NET Full Framework 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Internet Information Server (IIS)

* [Imagens do Internet Information Server (IIS) no DockerHub](https://hub.docker.com/r/microsoft/iis/)

* [Imagens do Internet Information Server (IIS) no GitHub](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Interagir com outras imagens de contêiner de pilha da Microsoft

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Executar o Microsoft SQL Server para imagem de contêiner do Linux 2017 com o Início Rápido do Docker](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server para imagens do Linux no DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Microsoft SQL Server para imagens de contêiner do Windows no DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Imagens do Microsoft SQL Server Express Edition para contêineres do Windows no DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Imagens do Microsoft SQL Server Developer Edition para contêineres do Windows no DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Agente do VSTS (Visual Studio Team Services)

* [Imagens de agente VSTS (Visual Studio Team Services) no DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Imagens de agente VSTS (Visual Studio Team Services) no GitHub](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agente do OMS (Operations Management Suite) para Linux

* [Visão geral do agente do OMS (Operations Management Suite) para Linux](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Imagens do OMS (Operations Management Suite) no DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Imagens do OMS (Operations Management Suite) no GitHub](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>CLI (Interface de linha de comando) do Microsoft Azure

* [Imagens da CLI (Interface de linha de comando) do Microsoft Azure no DockerHub](https://hub.docker.com/r/microsoft/azure-cli/) 

* [Imagens da CLI (Interface de linha de comando) do Microsoft Azure no GitHub](https://github.com/Microsoft/OMS-docker)

> [!NOTE]
> Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Emulador do Microsoft Azure Cosmos DB (apenas Contêineres do Windows)

* [Imagens do Emulador do Microsoft Azure Cosmos DB no DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Usar o Emulador do Azure Cosmos DB para desenvolvimento e teste local](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Exploração do ecossistema de desenvolvimento avançado do Docker

Agora que você aprendeu sobre a plataforma do Docker e imagens diferentes do Docker, a próxima etapa é explorar o ecossistema avançado do Docker. Os links a seguir mostram como as ferramentas da Microsoft complementam o desenvolvimento de contêiner.

* [Usar o .NET e o Docker juntos](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [Projetar e desenvolver aplicativos .NET baseados em microsserviço e em vários contêineres](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [Extensão do Docker do Visual Studio Code](https://code.visualstudio.com/docs/languages/dockerfile)
* [Saiba como usar o Azure Service Fabric](/azure/service-fabric/index)
* [Exemplo de introdução ao Service Fabric](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Benefícios dos contêineres do Windows](/virtualization/windowscontainers/about/index#video-overview)
* [Trabalhar com ferramentas de Docker do Visual Studio](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Depurar com o Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [Prática com o Visual Studio para Mac, contêineres e código sem servidor na nuvem](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Introdução ao Docker e ao Visual Studio para Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Próximas etapas

* [Aprenda noções básicas do Docker com o .NET Core](docker-basics-dotnet-core.md)
* [Compilando imagens do Docker no .NET Core](building-net-docker-images.md)
