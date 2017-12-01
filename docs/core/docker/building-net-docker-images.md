---
title: Criando imagens do Docker do .NET Core
description: "Noções básicas de imagens do Docker e do .NET Core"
keywords: .NET, .NET Core, Docker
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
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a>Criando imagens do Docker para .NET Core Applications

 Neste tutorial, vamos nos concentrar em como usar o .NET Core no Docker. Primeiro, exploraremos diferentes imagens do Docker oferecidos e mantido pela Microsoft e casos de uso. Em seguida, aprendemos como criar e dockerize um aplicativo ASP.NET Core.

No decorrer deste tutorial, você aprenderá:
> [!div class="checklist"]
> * Saiba mais sobre as imagens do Microsoft .NET Core Docker 
> * Obter um ASP.NET Core Dockerize de aplicativo de exemplo
> * Executar o aplicativo de exemplo do ASP.NET localmente
> * Compilar e executar o exemplo com o Docker para contêineres do Linux
> * Compilar e executar o exemplo com contêineres do Docker para Windows

## <a name="docker-image-optimizations"></a>Otimizações de imagem de Docker

Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:

* Imagens usadas para desenvolver aplicativos .NET Core
* Imagens usadas para compilar aplicativos .NET Core
* Imagens usadas para executar aplicativos .NET Core

Por que três imagens?
Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.

* **Desenvolvimento:** a prioridade enfoca itera rapidamente as alterações e a capacidade de depurar as alterações. O tamanho da imagem não é tão importante, em vez disso, você pode fazer alterações no seu código e vê-los rapidamente?

* **Compilação:** essa imagem contém todos os componentes necessários para compilar seu aplicativo, que inclui o compilador e qualquer outra dependência de otimizar os binários.  Você pode usar a imagem de compilação para criar os ativos que você coloca em uma imagem de produção. A imagem de compilação seria usada para a integração contínua, ou em um ambiente de compilação. Essa abordagem permite que um agente de compilação Compilar e criar o aplicativo (com todas as dependências necessárias) em uma instância de imagem de compilação. O agente de build precisa saber apenas como executar essa imagem do Docker.

* **Produção:** rapidez você pode implantar e iniciar sua imagem? Esta imagem é pequena para otimização de desempenho de rede de seu registro de Docker para seus hosts de Docker. O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados. Compilação de código dinâmico não é necessária no modelo do Docker. O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo.

    Por exemplo, o `dotnet publish` saída contém:

    * os binários compilados
    * arquivos. CSS e. js


O motivo para incluir o `dotnet publish` saída do comando em sua imagem de produção é manter o ' tamanho mínimo.

Algumas imagens de .NET Core compartilham camadas entre marcas diferentes para que baixar a última marca é um processo relativamente simples. Se você já tiver uma versão mais antiga em seu computador, essa arquitetura diminui o espaço em disco necessário.

Quando vários aplicativos usam imagens comuns no mesmo computador, a memória é compartilhada entre as imagens comuns. As imagens devem ser os mesmos para ser compartilhado.

## <a name="docker-image-variations"></a>Variações de imagem do Docker

Para atingir os objetivos descritos acima, fornecemos variantes de imagem em [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Esta imagem contém o SDK de núcleo do .NET, que inclui o .NET Core e ferramentas de linha de comando (CLI). Essa imagem é mapeada para o **cenário de desenvolvimento**. Você pode usar essa imagem para o local de desenvolvimento, depuração e teste de unidade. Essa imagem também pode ser usada para cenários **de build**. Usando `microsoft/dotnet:sdk` sempre fornece a versão mais recente.

> [!TIP]
> Se você não tiver certeza sobre as suas necessidades, você deseja usar o `microsoft/dotnet:<version>-sdk` imagem. Como a imagem "verdadeiro", ele foi projetado para ser usado como um throw contêiner ausente (montar seu código-fonte e inicie o contêiner para iniciar seu aplicativo) e como a imagem base para criar imagens de.

* `microsoft/dotnet:<version>-runtime`: Esta imagem contém o .NET Core (tempo de execução e bibliotecas) e é otimizada para executar aplicativos .NET Core em **produção**.

## <a name="alternative-images"></a>Imagens alternativas

Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:

* `microsoft/dotnet:<version>-runtime-deps`: O **deps de tempo de execução** imagem contém o sistema operacional com todas as dependências nativo necessárias ao .NET Core. Esta imagem é para [aplicativos independentes](https://docs.microsoft.com/dotnet/core/deploying/index).

Versões mais recentes de cada variante:

* `microsoft/dotnet`ou `microsoft/dotnet:latest` (alias para a imagem do SDK)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Exemplos para explorar

* [Este exemplo do ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstra um padrão de práticas recomendado para a criação de imagens do Docker para ASP.NET Core aplicativos de produção. O exemplo funciona com contêineres do Linux e Windows.

* .NET Core Docker demonstra um padrão de prática recomendado para [criação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)

## <a name="your-first-aspnet-core-docker-app"></a>Seu primeiro aplicativo ASP.NET Core Docker

Para este tutorial, permite usar um aplicativo de exemplo do ASP.NET Core Docker para o aplicativo que desejamos dockerize. Este aplicativo de exemplo do ASP.NET Core Docker demonstra um padrão de práticas recomendado para a criação de imagens do Docker para ASP.NET Core aplicativos de produção. O exemplo funciona com contêineres do Linux e Windows.

O exemplo Dockerfile cria uma imagem de Docker de aplicativo do ASP.NET Core baseada a imagem base do Docker de tempo de execução do ASP.NET Core.

Ele usa o [vários estágios do Docker build recurso](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) para:

* criar o exemplo em um contêiner com base no **maior** imagem base do ASP.NET Core compilação Docker 
* Copia o resultado da compilação final em uma imagem do Docker com base no **menor** imagem base do tempo de execução do ASP.NET Core Docker

> [!Note]
> A imagem de compilação contém as ferramentas necessárias para criar aplicativos, enquanto a imagem de tempo de execução, não.

### <a name="prerequisites"></a>Pré-requisitos

Para compilar e executar, instale os seguintes itens:

#### <a name="net-core-20-sdk"></a>.NET core SDK 2.0

* Instalar [.NET Core SDK 2.0](https://www.microsoft.com/net/core).

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

#### <a name="installing-git-for-sample-repository"></a>Instalando o Git para o repositório de exemplo

* Instalar [git](https://git-scm.com/download) se você deseja clonar o repositório.

### <a name="getting-the-sample-application"></a>Obtendo o aplicativo de exemplo

A maneira mais fácil de obter o exemplo é por meio da clonagem de [repositório exemplos](https://github.com/dotnet/dotnet-docker-samples) com git, usando as instruções a seguir: 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

Você também pode baixar o repositório (é pequeno) como um zip do repositório de amostras do .NET Core Docker.

### <a name="run-the-aspnet-app-locally"></a>Executar o aplicativo ASP.NET localmente

Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente.

Você pode criar e executar o aplicativo localmente com o SDK do .NET Core 2.0 usando os comandos a seguir (as instruções presumem que a raiz do repositório):

```console
cd aspnetapp
dotnet run
```

Depois que o aplicativo for iniciado, visite **http://localhost:5000/** no navegador da web.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Compilar e executar o exemplo com o Docker para contêineres do Linux

Você pode criar e executar o exemplo no Docker usando os contêineres do Linux usando os comandos a seguir (as instruções presumem que a raiz do repositório):

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] O `docker run` '-p' argumento mapas 5000 em seu computador local para a porta 80 no contêiner da porta (o formato de mapeamento de porta é `host:container`). Para obter mais informações, consulte o [docker executar](https://docs.docker.com/engine/reference/commandline/exec/) referência nos parâmetros de linha de comando.

Depois que o aplicativo for iniciado, visite **http://localhost:5000/** no navegador da web.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Compilar e executar o exemplo com contêineres do Docker para Windows

Você pode criar e executar o exemplo no Docker usando contêineres do Windows usando os comandos a seguir (as instruções presumem que a raiz do repositório):

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Navegue até o **endereço IP de contêiner** (em vez de http://localhost) em seu navegador diretamente ao usar contêineres do Windows. Você pode obter o endereço IP do seu contêiner com as seguintes etapas:

* Abra o prompt de comando do outro.
* Execute `docker ps` para ver os contêineres em execução. O contêiner "aspnetcore_sample" deve existir.
* Execute `docker exec aspnetcore_sample ipconfig`.
* Copie o endereço IP de contêiner e cole no navegador (por exemplo, 172.29.245.43).

> [!Note]
> A execução do docker oferece suporte à identificação contêineres com o nome ou hash. O nome (aspnetcore_sample) é usado no exemplo.

Consulte o seguinte exemplo de como obter o endereço IP de um contêiner do Windows em execução.

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> A execução do docker executa um comando de novo em um contêiner em execução. Para obter mais informações, consulte o [referência do docker exec](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.

Você pode produzir um aplicativo que está pronto para implantar na produção localmente usando o [dotnet publicar](../tools/dotnet-publish.md) comando.

```console
dotnet publish -c release -o published
```

> [!Note]
> O argumento de versão - c cria o aplicativo no modo de liberação (o padrão é o modo de depuração). Para obter mais informações, consulte o [dotnet executar referência](../tools/dotnet-run.md) nos parâmetros de linha de comando.

Você pode executar o aplicativo em **Windows** usando o comando a seguir.

```console
dotnet published\aspnetapp.dll
```

Você pode executar o aplicativo em **Linux** ou **macOS** usando o comando a seguir.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Imagens do docker usadas neste exemplo

As seguintes imagens do Docker são usadas neste exemplo

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

Parabéns! Você tem apenas:
> [!div class="checklist"]
> * Aprendeu sobre as imagens do Microsoft .NET Core Docker
> * Temos um ASP.NET Core Dockerize de aplicativo de exemplo
> * Executar o aplicativo de exemplo do ASP.NET localmente
> * Compilado e executado o exemplo com o Docker para contêineres do Linux
> * Compilado e executado o exemplo com contêineres do Docker para Windows


**Próximas Etapas**

Aqui estão algumas das próximas etapas que você pode executar:

* [Trabalhando com ferramentas de Docker do Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Implantação de imagens do Docker do registro do contêiner do Azure para instâncias de contêiner do Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Depuração com o código do Visual Studio](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Obtendo ponteiros com o Visual Studio para Mac, contêineres e código sem servidor na nuvem](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Introdução ao Docker e o Visual Studio para Mac laboratório](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> Se você não tiver uma assinatura do Azure, [Inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) para uma conta gratuita de 30 dias e get US $200 em créditos do Azure para testar qualquer combinação de serviços do Azure.
