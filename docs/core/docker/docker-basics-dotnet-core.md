---
title: "Aprenda noções básicas do Docker com o núcleo do .NET"
description: "Um Docker e um Tutorial básico do .NET Core"
keywords: ".NET, o núcleo do .NET, o Docker, o Tutorial"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 5935f67d7e4ca9c9e8768373e2bcaa9febccfdc5
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="learn-docker-basics-with-net-core"></a>Aprenda noções básicas do Docker com o núcleo do .NET

Este tutorial ensina Docker contêiner compilar e implantar tarefas para um aplicativo .NET Core. No decorrer deste tutorial, você aprenderá:

> [!div class="checklist"]
> * Como criar um Dockerfile
> * Como criar um aplicativo .NET Core.
> * Como implantar seu aplicativo em um contêiner do Docker.

O [plataforma de Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos como rapidamente [imagens do Docker](https://docs.docker.com/glossary/?term=image). Essas imagens são escritas no [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) formato a ser implantado e executado um [em camadas contêiner](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).

## <a name="net-core-easiest-way-to-get-started"></a>.NET core: A maneira mais fácil para começar

Antes de criar a imagem do Docker, é necessário um aplicativo coloca. Você pode criá-lo no Linux, MacOS ou Windows. A maneira mais rápida e fácil de fazer isso é usar o .NET Core.

Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).

Você pode criar contêineres do Windows e Linux com [multi-arch com base em marcas](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Seu primeiro aplicativo .NET Core Docker

### <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial:

#### <a name="net-core-20-sdk"></a>.NET core SDK 2.0

* Instalar [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

Consulte [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) (Versões de sistema operacional com suporte pelo .NET Core 2.x) para obter a lista completa de sistemas operacionais com suporte pelo .NET Core 2.x., versões de sistema operacional fora de suporte e links para a política de ciclo de vida.

* Instale o editor de código favorito, se ainda não tiver uma.

> [!TIP]
> É necessário instalar um editor de código? Tente [Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalar o cliente do Docker

Instalar [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.

O cliente do Docker pode ser instalado em:

* Distribuições do Linux

   * [CentOS](https://www.docker.com/docker-centos-distribution)

   * [Debian](https://www.docker.com/docker-debian)

   * [Fedora](https://www.docker.com/docker-fedora)

   * [Ubuntu](https://www.docker.com/docker-ubuntu)

* [macOS](https://docs.docker.com/docker-for-mac/)

* [Windows](https://docs.docker.com/docker-for-windows/).

### <a name="create-a-net-core-20-console-app-for-dockerization"></a>Criar um aplicativo de console .NET Core 2.0 para Dockerization

Abra um prompt de comando e crie uma pasta chamada *Hello*. Navegue até a pasta que você criou e digite os seguintes comandos:

```console
dotnet new console
dotnet run
```

Vejamos um breve passo a passo:

1. `$ dotnet new console`

   [`dotnet new`](../tools/dotnet-new.md) cria um arquivo de projeto `Hello.csproj` atualizado com as dependências necessárias para criar um aplicativo de console.  Ele também cria um `Program.cs`, um arquivo básico que contém o ponto de entrada para o aplicativo.
   
   `Hello.csproj`:

   O arquivo de projeto especifica tudo o que é necessário para restaurar as dependências e compilar o programa.

   * A marca `OutputType` especifica que estamos copilando um executável, em outras palavras, um aplicativo de console.
   * A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando. Em um cenário avançado, você pode especificar várias estruturas de destino e criar estruturas especificado em uma única operação. Neste tutorial, vamos criar para .NET Core 2.0.

   `Program.cs`:

   O programa será iniciado por `using System`. Essa declaração significa, "colocar tudo no `System` namespace no escopo para esse arquivo." O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.

   Em seguida, definimos um namespace chamado `Hello`. Você pode alterar o namespace em que quiser. Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento. Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado. Em nosso exemplo, o programa só grava "Hello World!" no console.

2. `$ dotnet restore`

   No núcleo do .NET 2. x, **dotnet novo** executa o [ `dotnet restore` ](../tools/dotnet-restore.md) comando. **Restauração dotnet** restaura a árvore de dependências com um [NuGet](https://www.nuget.org/)chamada (Gerenciador de pacotes do .NET).
   O NuGet executa as seguintes tarefas:
   * analisa o *Hello.csproj* arquivo 
   * baixa o arquivo dependências (ou captura do seu cache de máquina)
   * grava o *obj/project.assets.json* arquivo

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   O *project.assets.json* arquivo é um conjunto completo de como o gráfico de dependências do NuGet, resoluções de associação e outros metadados do aplicativo. Isso necessário arquivo é usado por outras ferramentas, como [ `dotnet build` ](../tools/dotnet-build.md) e [ `dotnet run` ](../tools/dotnet-run.md), processar corretamente o código-fonte.
   
3. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md)chamadas [ `dotnet build` ](../tools/dotnet-build.md) para confirmar uma compilação bem-sucedida e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo.
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    Para cenários avançados, consulte [implantação de aplicativos .NET Core](../deploying/index.md) para obter detalhes.

## <a name="dockerize-the-net-core-application"></a>Dockerize o aplicativo .NET Core

O aplicativo de console Hello .NET Core com êxito é executado localmente. Agora vamos dar um passo adicional e compilar e executar o aplicativo no Docker.

### <a name="your-first-dockerfile"></a>Sua primeira Dockerfile

Abra o editor de texto e vamos começar! Ainda estamos trabalhando do diretório Olá que criamos o aplicativo no.

Adicione as seguintes instruções de Docker para o Linux ou [contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) para um novo arquivo. Quando terminar, salve-o na raiz do seu diretório Hello como **Dockerfile**, sem extensão (talvez seja necessário definir o tipo de arquivo `All types (*.*)` ou algo semelhante).

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

O Dockerfile contém instruções de build do Docker que são executados sequencialmente.

A primeira instrução deve ser [ **FROM**](https://docs.docker.com/engine/reference/builder/#from). Essa instrução inicia uma nova fase de compilação e define a imagem de Base para as instruções restantes. As marcas várias arch pull contêineres do Windows ou Linux dependendo do Docker para Windows [modo contêiner](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers). A imagem Base para nossa amostra é a imagem do sdk 2.0 do repositório microsoft/dotnet,

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

O [ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrução define o diretório de trabalho para qualquer restantes executar CMD, ENTRYPOINT, cópia e adicionar Dockerfile instruções. Se a pasta não existir, ele será criado. Nesse caso, WORKDIR é definido para o diretório de aplicativo.

```Dockerfile
WORKDIR /app
```

O [ **cópia** ](https://docs.docker.com/engine/reference/builder/#copy) instrução copia novos arquivos ou diretórios do caminho de origem e adiciona-os no sistema de arquivos do contêiner de destino. Com essa instrução, podemos está copiando o arquivo de projeto c# para o contêiner.

```Dockerfile
COPY *.csproj ./
```

O [ **executar** ](https://docs.docker.com/engine/reference/builder/#run) instrução executa os comandos em uma nova camada na parte superior da imagem atual e confirme os resultados. A imagem confirmada resultante é usada para a próxima etapa no Dockerfile. Estamos executando **restauração dotnet** para obter as dependências necessárias de arquivo de projeto c#. 

```Dockerfile
RUN dotnet restore
```

Isso **cópia** instrução copia o restante dos arquivos em nosso contêiner em novos [camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Estamos publicando o aplicativo com essa **executar** instrução. O [ **dotnet publicar** ](../tools/dotnet-publish.md) comando compila o aplicativo lê por meio de suas dependências especificadas no arquivo de projeto e publica o conjunto resultante de arquivos para um diretório. Nosso aplicativo é publicado com uma **versão** configuração e saída para o diretório padrão.

```Dockerfile
RUN dotnet publish -c Release -o out
```

O [ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrução permite que o contêiner ser executado como um executável.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Agora você tem um Dockerfile que:

* Copia a imagem do seu aplicativo
* dependências do aplicativo para a imagem
* cria o aplicativo para ser executado como um executável

### <a name="build-and-run-the-hello-net-core-20-app"></a>Compilar e executar o aplicativo Hello .NET Core 2.0

#### <a name="essential-docker-commands"></a>Comandos essenciais

Esses comandos do Docker são essenciais:

* [build do docker](https://docs.docker.com/engine/reference/commandline/build/)
* [execução de docker](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [parada de docker](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [imagem do docker](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Compilar e executar

Você gravou o dockerfile; Agora Docker compila seu aplicativo e, em seguida, executa o contêiner.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

A saída de `docker build` comando deve ser semelhante à seguinte saída de console:

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

Como você pode ver na saída, o mecanismo do Docker usado Dockerfile para compilar nosso contêiner.

A saída de `docker run` comando deve ser semelhante à seguinte saída de console:

```console
Hello World!
```

Parabéns! Você tem apenas:
> [!div class="checklist"]
> * Criou um aplicativo .NET Core local
> * Criado um Dockerfile para criar o primeiro contêiner
> * Criado e executou seu aplicativo Dockerized



## <a name="next-steps"></a>Próximas etapas

Aqui estão algumas das próximas etapas que você pode executar:

* [Introdução ao .NET Docker imagens vídeo](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, o Docker e as instâncias de contêiner do Azure melhor juntos!](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [Docker para guias de início rápido do Azure](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Implantar seu aplicativo no Docker do Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> Se você não tiver uma assinatura do Azure, [Inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) para uma conta gratuita de 30 dias e get US $200 em créditos do Azure para testar qualquer combinação de serviços do Azure.

## <a name="docker-images-used-in-this-sample"></a>Imagens do docker usadas neste exemplo

As seguintes imagens do Docker são usadas neste exemplo

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Recursos relacionados

* [Amostras do .NET core Docker](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [Dockerfile em contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Amostras do .NET framework Docker](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core em DockerHub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Dockerize um aplicativo .NET Core - Tutorial de Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Trabalhando com ferramentas de Docker do Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Implantação de imagens do Docker do registro do contêiner do Azure para instâncias de contêiner do Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)