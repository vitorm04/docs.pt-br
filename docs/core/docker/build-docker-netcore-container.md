---
title: 'Tutorial: Colocar em contêiner um aplicativo com o Docker'
description: Neste tutorial, você aprenderá a colocar um aplicativo .NET Core em contêiner com o Docker.
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 8255a901c706e55e143cdf23dda0eb9bc79d245d
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58844956"
---
# <a name="tutorial-containerize-a-net-core-app"></a>Tutorial: Colocar em contêiner um aplicativo .NET Core

Este tutorial ensina como criar uma imagem do Docker que contenha seu aplicativo .NET Core. A imagem pode ser usada para criar contêineres para seu ambiente de desenvolvimento local, nuvem privada ou nuvem pública.

Neste tutorial, você aprenderá a:

> [!div class="checklist"]
> * Criar um Dockerfile
> * Efetuar pull de uma imagem base do Docker no Microsoft .NET Core
> * Personalizar e implantar seu aplicativo para a imagem
> * Criar e executar um contêiner
> * Implantar no Azure

Este tutorial ensina as tarefas de build e implantação de contêiner do Docker para um aplicativo .NET Core. A [plataforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) usa o [Mecanismo do Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) para criar e empacotar aplicativos com agilidade [imagens do Docker](https://docs.docker.com/glossary/?term=image). Essas imagens são gravadas no formato [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) para serem implantadas e executadas em um [contêiner em camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).



## <a name="net-core-easiest-way-to-get-started"></a>.NET Core: A maneira mais fácil para começar

Antes de criar a imagem do Docker, é necessário ter um aplicativo para colocá-lo em contêiner. Crie-o no Linux, MacOS ou Windows. A maneira mais rápida e fácil de fazer isso é usando o .NET Core.

Se não estiver familiarizado com o conjunto de ferramentas da CLI do .NET Core, leia a [Visão geral do SDK do .NET Core](../tools/index.md).

Criar contêineres do Windows e Linux com [marcas baseadas em vários arcos](https://github.com/dotnet/announcements/issues/14).

## <a name="your-first-net-core-docker-app"></a>Seu primeiro aplicativo .NET Core do Docker

### <a name="prerequisites"></a>Pré-requisitos

Para concluir este tutorial:

#### <a name="net-core-sdk"></a>SDK do .NET Core

* Instale o [SDK do .NET Core 2.1](https://www.microsoft.com/net/download) ou posterior.

Consulte [Versões de sistema operacional compatíveis com .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) para obter a lista completa de sistemas operacionais compatíveis com .NET Core 2.1, versões de sistema operacional não compatíveis e links para a política de ciclo de vida.

* Instale seu editor de código favorito, caso ainda não tenha um.

> [!TIP]
> Precisa instalar um editor de código? Experimente o [Visual Studio Code](https://code.visualstudio.com/download)!

#### <a name="installing-docker-client"></a>Instalando o Cliente do Docker

Instale o [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) ou cliente do Docker posterior.

O cliente do Docker pode ser instalado em:

* Distribuições Linux

   * [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [macOS](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/).

### <a name="create-a-net-core-21-console-app-for-dockerization"></a>Criar um aplicativo de console .NET Core 2.1 para colocá-lo no Docker

Abra um prompt de comando e crie uma pasta chamada *Hello*. Navegue para a pasta criada e digite os seguintes comandos:

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
   * A marca `TargetFramework` especifica qual implementação do .NET estamos direcionando. Em um cenário avançado, você pode especificar várias estruturas de destino e compilar para as estruturas especificadas em uma única operação. Neste tutorial, compilamos para o .NET Core 2.1.

   `Program.cs`:

   O programa é iniciado por `using System`. Essa declaração significa “colocar tudo no namespace `System` no escopo para este arquivo”. O namespace `System` inclui construções básicas, como `string` ou tipos numéricos.

   Em seguida, definimos um namespace chamado `Hello`. Altere o namespace para o nome desejado. Uma classe chamada `Program` é definida dentro desse namespace, com um método `Main` que usa uma matriz de cadeias de caracteres como argumento. Essa matriz contém a lista de argumentos passados quando o programa compilado é chamado. Em nosso exemplo, o programa grava apenas “Olá, Mundo!” no console.

   **dotnet new** executa o comando [`dotnet restore`](../tools/dotnet-restore.md). **Dotnet restore** restaura a árvore de dependências com uma chamada ao [NuGet](https://www.nuget.org/) (gerenciador de pacotes do .NET).
   O NuGet executa as seguintes tarefas:
   * analisa o arquivo *Hello.csproj*.
   * baixa as dependências de arquivo (ou as captura do cache do computador).
   * grava o arquivo *obj/project.assets.json*.

   O arquivo *project.assets.json* é um conjunto completo do gráfico de dependências do NuGet, das resoluções de associação e de outros metadados do aplicativo. Esse arquivo obrigatório é usado por outras ferramentas, como [`dotnet build`](../tools/dotnet-build.md) e [`dotnet run`](../tools/dotnet-run.md), para processar o código-fonte corretamente.

2. `$ dotnet run`

   [`dotnet run`](../tools/dotnet-run.md) chama [`dotnet build`](../tools/dotnet-build.md) para confirmar um build bem-sucedido e, em seguida, chama `dotnet <assembly.dll>` para executar o aplicativo.

    ```console
    $ dotnet run

    Hello World!
    ```

    Para cenários avançados, consulte [Implantação de aplicativos .NET Core](../deploying/index.md) para obter detalhes.

## <a name="dockerize-the-net-core-application"></a>Colocar o aplicativo .NET Core no Docker

O aplicativo de console Hello .NET Core é executado localmente com êxito. Agora vamos dar mais um passo e compilar e executar o aplicativo no Docker.

### <a name="your-first-dockerfile"></a>Seu primeiro Dockerfile

Abra o editor de texto e vamos começar! Ainda estamos trabalhando no diretório Hello no qual criamos o aplicativo.

Adicione as instruções do Docker a seguir para [Contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) ou do Linux a um novo arquivo. Quando terminar, salve-o na raiz do diretório Hello como um **Dockerfile**, sem extensão (talvez seja necessário definir o tipo de arquivo como `All types (*.*)` ou algo semelhante).

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

O Dockerfile contém instruções de build do Docker que são executadas sequencialmente.

A primeira instrução deve ser [**FROM**](https://docs.docker.com/engine/reference/builder/#from). Essa instrução inicializa um novo estágio de build e define a imagem Base para as instruções restantes. As marcas de vários arcos efetuam pull de contêineres do Windows ou Linux, dependendo do [modo de contêiner](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers) do Docker para Windows. A Imagem Base de nossa amostra é a imagem 2.1-sdk do repositório microsoft/dotnet.

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

A instrução [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) define o diretório de trabalho para as instruções restantes RUN, CMD, ENTRYPOINT, COPY e ADD do Dockerfile. Se o diretório não existir, ele será criado. Nesse caso, WORKDIR é definido como o diretório do aplicativo.

```Dockerfile
WORKDIR /app
```

A instrução [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) copia novos arquivos ou diretórios do caminho de origem e adiciona-os ao sistema de arquivos do contêiner de destino. Com essa instrução, estamos copiando o arquivo de projeto C# para o contêiner.

```Dockerfile
COPY *.csproj ./
```

A instrução [**RUN**](https://docs.docker.com/engine/reference/builder/#run) executa os comandos em uma nova camada na parte superior da imagem atual e confirma os resultados. A imagem confirmada resultante é usada para a próxima etapa do Dockerfile. Estamos executando **dotnet restore** para obter as dependências necessárias do arquivo de projeto C#.

```Dockerfile
RUN dotnet restore
```

Essa instrução **COPY** copia o restante dos arquivos em nosso contêiner para novas [camadas](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).

```Dockerfile
COPY . ./
```

Estamos publicando o aplicativo com essa instrução **RUN**. O comando [**dotnet publish**](../tools/dotnet-publish.md) compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto resultantes de arquivos em um diretório. Nosso aplicativo é publicado com uma configuração **Versão** e uma saída para o diretório padrão.

```Dockerfile
RUN dotnet publish -c Release -o out
```

A instrução [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) permite que o contêiner seja executado como um executável.

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

Agora você tem um Dockerfile que:

* copia o aplicativo para a imagem
* as dependências do aplicativo para a imagem
* compila o aplicativo para ser executado como um executável

### <a name="build-and-run-the-hello-net-core-app"></a>Compilar e executar o aplicativo Hello .NET Core

#### <a name="essential-docker-commands"></a>Comandos essenciais do Docker

Esses comandos do Docker são essenciais:

* [docker build](https://docs.docker.com/engine/reference/commandline/build/)
* [docker run](https://docs.docker.com/engine/reference/commandline/run/)
* [docker ps](https://docs.docker.com/engine/reference/commandline/ps/)
* [docker stop](https://docs.docker.com/engine/reference/commandline/stop/)
* [docker rm](https://docs.docker.com/engine/reference/commandline/rm/)
* [docker rmi](https://docs.docker.com/engine/reference/commandline/rmi/)
* [docker image](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a>Compilar e executar

Você gravou o Dockerfile; agora o Docker compila o aplicativo e, em seguida, executa o contêiner.

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

A saída do comando `docker build` deverá ser semelhante à seguinte saída de console:

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
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
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

Como você pode ver na saída, o Mecanismo do Docker usou o Dockerfile para compilar nosso contêiner.

A saída do comando `docker run` deverá ser semelhante à seguinte saída de console:

```console
Hello World!
```

Parabéns! Você acabou de:
> [!div class="checklist"]
> * criar um aplicativo .NET Core local
> * criar um Dockerfile para criar seu primeiro contêiner
> * criar e executar seu aplicativo no Docker

## <a name="next-steps"></a>Próximas etapas

Estas são algumas das próximas etapas que podem ser realizadas:

* [Vídeo de introdução às imagens do Docker do .NET](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [Visual Studio, Docker e Instâncias de Contêiner do Azure melhor juntos!](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [Guias de início rápido do Docker para Azure](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [Implantar seu aplicativo no Docker para Azure](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.

## <a name="docker-images-used-in-this-sample"></a>Imagens do Docker usadas nesta amostra

As seguintes imagens do Docker são usadas nesta amostra

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a>Recursos relacionados

* [Amostras do Docker do .NET Core](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [Dockerfile em contêineres do Windows](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [Amostras do Docker do .NET Framework](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [ASP.NET Core no DockerHub](https://hub.docker.com/r/microsoft/aspnetcore/)
* [Colocar um aplicativo .NET Core no Docker – Tutorial do Docker](https://docs.docker.com/engine/examples/dotnetcore/)
* [Trabalhar com ferramentas de Docker do Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)