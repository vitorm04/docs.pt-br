---
title: "Introdução ao .NET e o Docker"
description: "Noções básicas sobre Docker e o núcleo do .NET"
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
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a>Introdução ao .NET e o Docker

 Este artigo fornece uma introdução e um plano de fundo conceitual para trabalhar com o .NET no Docker. 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a>Docker: Empacotar seus aplicativos para implantar e executar em qualquer lugar

[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) é uma plataforma aberta que permite aos desenvolvedores e administradores de compilação [imagens](https://docs.docker.com/glossary/?term=image), enviar e executar aplicativos distribuídos em um ambiente isolado de forma flexível chamado um [contêiner](https://www.docker.com/what-container). Essa abordagem permite o gerenciamento de ciclo de vida do aplicativo eficiente entre ambientes de produção, controle de qualidade e desenvolvimento.
 
O [plataforma de Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos como rapidamente [imagens do Docker](https://docs.docker.com/glossary/?term=image) criado usando arquivos escritos no [Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) formato, em seguida, implantado e executado em um [em camadas contêiner](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

Você pode criar seus próprios [em camadas imagens](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) como dockerfiles ou usar existentes de um [registro](https://docs.docker.com/glossary/?term=registry), como [Hub do Docker](https://docs.docker.com/glossary/?term=Docker%20Hub).

O [relação entre contêineres do Docker, imagens e registros](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) é um conceito importante quando [arquitetura e criando em contêineres aplicativos ou microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/). Essa abordagem bastante reduz o tempo entre o desenvolvimento e implantação.

### <a name="further-reading-and-watching"></a>Leitura adicional (e observando)

* [Contêineres baseados em Windows: desenvolvimento de aplicativos modernos com controle de nível empresarial.](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [Visão geral do docker](https://docs.docker.com/engine/docker-overview/)
* [Dockerfile em contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Práticas recomendadas para escrever Dockerfiles](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [Criando imagens do Docker para aplicativos .NET Core](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a>Obtendo imagens do Docker .NET

As imagens do Docker oficial do .NET são criadas e otimizadas pela Microsoft. Eles estão publicamente disponíveis nos repositórios Microsoft no Hub do Docker. Cada repositório pode conter várias imagens, dependendo de versões do .NET e em versões do sistema operacional. A maioria dos repositórios de imagem fornecem amplo de marcação para ajudá-lo a selecionar uma versão do framework específico e um sistema operacional (distribuição Linux ou versão do Windows).

## <a name="scenario-based-guidance"></a>Orientação baseados em cenários

A intenção da Microsoft para repositórios de .NET é ter granulares e determinados repositórios, que representam um cenário específico ou a carga de trabalho.

O `microsoft/aspnetcore` imagens são otimizadas para aplicativos do ASP.NET Core no Docker, para contêineres podem ser iniciada mais rápido.

As imagens do núcleo do .NET (`microsoft/dotnet`) são destinados a aplicativos de console com base em .NET Core. Por exemplo, processos em lote do Azure WebJobs e outros cenários do console devem usar as imagens otimizadas do núcleo do .NET.

É o cenário mais óbvio horizontal para o uso de aplicativos .NET e de Docker para implantação de produção e hospedagem. Acontece que produção é apenas um cenário e os outros são igualmente úteis. Esses cenários não são específicos para .NET, mas devem ser aplicada a maioria das plataformas de desenvolvimento.

* **Instalar o baixa fricção** — você pode experimentar o .NET sem uma instalação local. Basta Baixe uma imagem do Docker com o .NET nele.

* **Desenvolver em um contêiner** — você pode desenvolver em um ambiente consistente, tornando os ambientes de desenvolvimento e produção semelhantes (evitando problemas como estado global em computadores de desenvolvedor). Ferramentas do Visual Studio para Docker mesmo permitem que você iniciar um contêiner diretamente do Visual Studio.

* **Em um contêiner de teste** — você pode testar em um contêiner, reduzindo falhas devido a ambientes configurados incorretamente ou outras alterações deixados para trás do último teste.

* **Criar um contêiner** — você pode compilar o código em um contêiner, evitando a necessidade de configurar corretamente as máquinas de compilação compartilhada para vários ambientes, mas em vez disso, mover para "BYOC" (traga seu próprio contêiner) abordagem.

* **Implantação em todos os ambientes** — você pode implantar uma imagem em todos os seus ambientes. Essa abordagem reduz falhas devido a diferenças de configuração, normalmente alterando o comportamento da imagem através da configuração externa (por exemplo, variáveis de ambiente injetado).

[Diretrizes gerais](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) para decidir entre o .NET Core e do .NET Framework para o desenvolvimento de contêiner do Docker.

### <a name="common-docker-development-scenarios"></a>Cenários comuns de desenvolvimento de Docker

#### <a name="net-core"></a>.NET Core

**Recursos principais do .NET**

 Escolha os exemplos de núcleo do .NET que se adaptam os cenários de interesse. Todas as instruções de exemplo descrevem como imagens do Windows ou Linux Docker do Windows, Linux ou macOS hosts de destino.

Os exemplos usam o núcleo do .NET 2.0. Eles usam Docker [compilação de vários estágio](https://github.com/dotnet/announcements/issues/18) e [arch várias marcas](https://github.com/dotnet/announcements/issues/14) quando apropriado.

* [Imagens de núcleo do .NET em DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [Dockerize um aplicativo .NET Core](https://docs.docker.com/engine/examples/dotnetcore/)

* .NET Core Docker demonstra como [usar Docker no processo de desenvolvimento .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev). O exemplo funciona com contêineres do Linux e Windows.

* .NET Core Docker demonstra um padrão de prática recomendado para [criação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod) O exemplo funciona com contêineres do Linux e Windows.

* Isso [exemplo .NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstra um padrão de práticas recomendado para a criação de imagens do Docker para [aplicativos independentes do .NET Core](https://docs.microsoft.com/dotnet/core/deploying/). Usado para o contêiner de produção menor sem um benefício de [compartilhamento base imagens entre contêineres](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/). No entanto, camadas inferiores do Docker podem ser compartilhadas.

#### <a name="arm32--raspberry-pi"></a>ARM32 / framboesa Pi

* [ARM32 de tempo de execução do .NET core compilações de lançamento](https://github.com/dotnet/announcements/issues/29)

* [ARM32 / framboesa Pi .NET Core imagens em DockerHub](https://hub.docker.com/r/microsoft/dotnet/)

* [ARM32 / Pi framboesa .NET Core Docker amostras no GitHub](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a>.NET Framework

* [Imagens do .NET framework em DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/) este repositório contém exemplos que demonstram várias configurações de Docker do .NET Framework. Você pode usar essas imagens como a base de suas próprias imagens do Docker.

**4.7 do .NET framework**

[O [dotnet-exemplo de estrutura: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstra o uso de "hello world" básico do [4.7 do .NET Framework](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47). Ele mostra como você pode criar e implantar o aplicativo depender de [imagem do .NET Framework 4.7 docker](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).

**.NET framework 4.6.2**

O [dotnet-exemplo de estrutura: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstra o uso de "hello world" básico do [do .NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462). Ele mostra como você pode criar e implantar o aplicativo depender de [imagem do .NET Framework 4.6.2 docker](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).

**.NET framework 3.5**

 O [dotnet-exemplo de estrutura: 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstra o uso de "hello world" básico de [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5). Ele mostra como você pode criar e implantar um projeto dependem do .NET Framework 3.5 no Docker.

#### <a name="aspnet-core"></a>ASP.NET Core

* [Este exemplo do ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstra um padrão de práticas recomendado para a criação de imagens do Docker para ASP.NET Core aplicativos de produção. O exemplo funciona com contêineres do Linux e Windows.

* [Imagens do ASP.NET Core em DockerHub](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [Imagens do ASP.NET Core no GitHub](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a>Estrutura do ASP.NET 

* [Imagens de estrutura do ASP.NET em DockerHub](https://hub.docker.com/r/microsoft/aspnet/)

* [Aplicativo de Web Forms do ASP.NET no exemplo do .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a>Windows Communication Framework (WCF)

* [Imagens do Windows Communication Framework (WCF) em DockerHub](https://hub.docker.com/r/microsoft/wcf/)

* [Imagens do Windows Communication Framework (WCF) no GitHub](https://github.com/microsoft/iis-docker)

* [Exemplos de Docker do Windows Communication Framework (WCF) usando o .NET Framework completo 4.6.2](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a>Servidor de informações da Internet (IIS)

* [Imagens de servidor de informações da Internet (IIS) no DockerHub](https://hub.docker.com/r/microsoft/iis/)

* [Imagens de servidor de informações da Internet (IIS) no GitHub](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a>Interagir com outras imagens de contêiner de pilha do Microsoft

#### <a name="microsoft-sql-server"></a>Microsoft SQL Server

* [Execute o Microsoft SQL Server para Linux 2017 imagem de contêiner com Docker Quickstart](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [Microsoft SQL Server para Linux imagens em DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Imagens do Microsoft SQL Server para os contêineres do Windows em DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [Imagens do Microsoft SQL Server Express Edition para contêineres do Windows no DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [Imagens do Microsoft SQL Server Developer Edition para contêineres do Windows no DockerHub](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a>Agente do Visual Studio Team Services (VSTS)

* [Imagens de agente do Visual Studio Team Services (VSTS) em DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/)

* [Imagens de agente do Visual Studio Team Services (VSTS) no GitHub](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a>Agente do Operations Management Suite (OMS) Linux

* [Visão geral de agente do Operations Management Suite (OMS) Linux](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [Imagens do Operations Management Suite (OMS) em DockerHub](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [Imagens do Operations Management Suite (OMS) no GitHub](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a>Interface de linha de comando (CLI) do Microsoft Azure

* [Imagens do Microsoft Azure Interface de linha de comando (CLI) em DockerHub](Docker image for Microsoft Azure Command Line Interface) 

* [Imagens do Microsoft Azure Interface de linha de comando (CLI) no GitHub](https://github.com/Microsoft/OMS-docker)

> [!Note]
> Se você não tiver uma assinatura do Azure, [Inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) para uma conta gratuita de 30 dias e get US $200 em créditos do Azure para testar qualquer combinação de serviços do Azure.
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a>Emulador do Cosmos banco de dados do Microsoft Azure (apenas os contêineres do Windows)

* [Imagens do emulador de banco de dados do Microsoft Azure Cosmos em DockerHub](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [Usar o emulador do Azure Cosmos banco de dados para teste e desenvolvimento local](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a>Explorando o ecossistema de desenvolvimento avançado do Docker

Agora que você aprendeu sobre a plataforma de Docker e imagens do Docker diferentes, a próxima etapa é explorar o ecossistema do Docker avançado. Os links a seguir mostram como as ferramentas do Microsoft complementam o desenvolvimento de contêiner.

* [Usando o .NET e Docker juntos](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [Criar e desenvolver aplicativos .NET vários contêiner e com base em Microsserviço](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [Extensão do Visual Studio código Docker](https://code.visualstudio.com/docs/languages/dockerfile) 
* [Saiba como usar o Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/) 
* [Exemplo de Introdução ao guia do Service Fabric](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [Benefícios de contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [Trabalhando com ferramentas de Docker do Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Implantação de imagens do Docker do registro do contêiner do Azure para instâncias de contêiner do Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Depuração com o código do Visual Studio](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Obtendo ponteiros com o Visual Studio para Mac, contêineres e código sem servidor na nuvem](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Introdução ao Docker e o Visual Studio para Mac laboratório](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a>Próximas etapas

* [Aprenda noções básicas do Docker com o núcleo do .NET](../docker/docker-basics-dotnet-core.md)
* [Criação de imagens do Docker .NET Core](../docker/building-net-docker-images)