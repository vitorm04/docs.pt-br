---
title: Visão geral de imagens do Docker – .NET Core
description: Saiba como usar as imagens publicadas do Docker do .NET Core no Registro do Docker. Você também aprenderá a efetuar pull de imagens e compilar suas próprias imagens.
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 34ff6ce7d990412fa0ac4896d1e2e39b307681f0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145826"
---
# <a name="learn-about-docker-images-for-net-core"></a>Saiba mais sobre imagens do Docker para .NET Core

Neste tutorial, nós nos concentramos em como usar o .NET Core no Docker. Primeiro, exploramos diferentes imagens do Docker oferecidas e mantidas pela Microsoft, bem como casos de uso. Em seguida, aprendemos a criar e colocar um aplicativo ASP.NET Core no Docker.

Durante este tutorial, você aprenderá:
> [!div class="checklist"]
> * Saiba mais sobre as imagens do Docker no Microsoft .NET Core 
> * Obter um aplicativo ASP.NET Core de exemplo para colocá-lo no Docker
> * Executar o aplicativo ASP.NET de exemplo localmente
> * Compilar e executar a amostra com o Docker para contêineres do Linux
> * Compilar e executar a amostra com o Docker para contêineres do Windows

## <a name="docker-image-optimizations"></a>Otimizações de imagem de Docker

Ao criar imagens do Docker para desenvolvedores, nos concentramos em três cenários principais:

* Imagens usadas para desenvolver aplicativos .NET Core
* Imagens usadas para compilar aplicativos .NET Core
* Imagens usadas para executar aplicativos .NET Core

Por que três imagens?
Ao desenvolver, compilar e executar aplicativos em contêineres, temos prioridades diferentes.

* **Desenvolvimento:** a prioridade enfoca em iterar alterações rapidamente e na capacidade de depurar as alterações. O tamanho da imagem não é tão importante. Em vez disso, você pode fazer alterações no código e observá-las rapidamente?

* **Build:** essa imagem contém tudo o que é necessário para compilar o aplicativo, que inclui o compilador e outras dependências para otimizar os binários.  Use a imagem de build para criar os ativos colocados em uma imagem de produção. A imagem de build será usada para a integração contínua ou em um ambiente de build. Essa abordagem permite que um agente de build compile o aplicativo (com todas as dependências necessárias) em uma instância de imagem de build. O agente de build precisa saber apenas como executar essa imagem do Docker.

* **Produção:** em quanto tempo você pode implantar e iniciar a imagem? Essa imagem é pequena e, portanto, o desempenho de rede do Registro do Docker para os hosts do Docker é otimizado. O conteúdo está pronto para ser executado e habilitar o tempo mais rápido possível da execução do Docker até o processamento de resultados. A compilação de código dinâmico não é necessária no modelo do Docker. O conteúdo colocado nesta imagem ficaria limitado aos binários e conteúdos necessários para executar o aplicativo.

    Por exemplo, a saída `dotnet publish` contém:

    * os binários compilados
    * arquivos .js e .css


O motivo para incluir a saída do comando `dotnet publish` na imagem de produção é manter o tamanho mínimo.

Algumas imagens do .NET Core compartilham camadas entre marcas diferentes e, portanto, baixar a última marca é um processo relativamente leve. Se você já tiver uma versão mais antiga no computador, essa arquitetura diminuirá o espaço em disco necessário.

Quando vários aplicativos usam imagens comuns no mesmo computador, a memória é compartilhada entre as imagens comuns. As imagens devem ser as mesmas para serem compartilhadas.

## <a name="docker-image-variations"></a>Variações de imagem do Docker

Para atingir as metas descritas acima, fornecemos variantes de imagem em [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).

* `microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Essa imagem contém o SDK do .NET Core, que inclui o .NET Core e a CLI (Ferramentas de Linha de Comando). Essa imagem é mapeada para o **cenário de desenvolvimento**. Use essa imagem para o desenvolvimento, depuração e teste de unidade local. Essa imagem também pode ser usada para cenários **de build**. O uso de `microsoft/dotnet:sdk` sempre fornece a última versão.

> [!TIP]
> Caso não tenha certeza sobre suas necessidades, é recomendável usar a imagem `microsoft/dotnet:<version>-sdk`. Como a imagem “de fato”, ela foi projetada para ser usada como um contêiner de descarte (montar o código-fonte e iniciar o contêiner para iniciar o aplicativo) e como a imagem base para criar outras imagens.

* `microsoft/dotnet:<version>-runtime`: essa imagem contém o .NET Core (tempo de execução e bibliotecas) e é otimizada para executar aplicativos .NET Core em **produção**.

## <a name="alternative-images"></a>Imagens alternativas

Além dos cenários otimizados de desenvolvimento, build e produção, fornecemos imagens adicionais:

* `microsoft/dotnet:<version>-runtime-deps`: a imagem **runtime-deps** contém o sistema operacional com todas as dependências nativas exigidas pelo .NET Core. Essa imagem destina-se a [aplicativos autossuficientes](../deploying/index.md).

Versões mais recentes de cada variante:

* `microsoft/dotnet` ou `microsoft/dotnet:latest` (alias para a imagem do SDK)
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a>Amostras para explorar

* [Este exemplo do Docker no ASP.NET Core](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstra um padrão de prática recomendada para compilação de imagens do Docker para aplicativos ASP.NET Core para produção. O exemplo funciona com contêineres do Linux e do Windows.

* Este exemplo do Docker no .NET Core demonstra um padrão de prática recomendada para [compilação de imagens do Docker para aplicativos .NET Core para produção.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)

## <a name="forward-the-request-scheme-and-original-ip-address"></a>Encaminhar o esquema da solicitação e o endereço IP original

Servidores proxy, balanceadores de carga e outros dispositivos de rede geralmente ocultam informações sobre a solicitação antes de elas alcançarem o aplicativo em contêiner:

* Quando solicitações HTTPS são passadas por proxy por HTTP, o esquema original (HTTPS) é perdido e deve ser encaminhado em um cabeçalho.
* Como um aplicativo recebe uma solicitação do proxy, e não de sua origem verdadeira na Internet ou rede corporativa, o endereço IP do cliente original também deve ser encaminhado em um cabeçalho.

Essas informações podem ser importantes no processamento de solicitações, por exemplo, em redirecionamentos, autenticação, geração de link, avaliação de política e localização geográfica do cliente.

Para encaminhar o esquema e o endereço IP original para um aplicativo ASP.NET Core em contêiner, use o Middleware de Cabeçalhos Encaminhados. Para obter mais informações, veja [Configurar o ASP.NET Core para trabalhar com servidores proxy e balanceadores de carga](/aspnet/core/host-and-deploy/proxy-load-balancer).

## <a name="your-first-aspnet-core-docker-app"></a>Seu primeiro aplicativo ASP.NET Core do Docker

Para este tutorial, vamos usar um aplicativo de exemplo ASP.NET Core Docker para o aplicativo que desejamos colocar no Docker. Este aplicativo de exemplo ASP.NET Core Docker demonstra um padrão de melhor prática de compilação de imagens do Docker para aplicativos ASP.NET Core para produção. O exemplo funciona com contêineres do Linux e do Windows.

O Dockerfile de exemplo cria uma imagem do Docker do aplicativo ASP.NET Core baseada na imagem base do Docker do Tempo de Execução do ASP.NET Core.

Ele usa o [recurso de build de vários estágios do Docker](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) para:

* compilar a amostra em um contêiner baseado na imagem base **maior** do Docker do Build do ASP.NET Core 
* copiar o resultado do build final para uma imagem do Docker baseada na imagem base **menor** do Docker do Tempo de Execução do ASP.NET Core

> [!NOTE]
> A imagem de build contém as ferramentas necessárias para compilar aplicativos, ao contrário da imagem de tempo de execução.

### <a name="prerequisites"></a>Pré-requisitos

Para compilar e executar, instale os seguintes itens:

#### <a name="net-core-21-sdk"></a>SDK do .NET Core 2.1

* Instale o [SDK do .NET Core 2.1](https://www.microsoft.com/net/core).

* Instale seu editor de código favorito, caso ainda não tenha um.

> [!TIP]
> Precisa instalar um editor de código? Experimente o [Visual Studio](https://visualstudio.com/downloads)!

#### <a name="installing-docker-client"></a>Instalando o Cliente do Docker

Instale o [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) ou posterior do cliente do Docker.

O cliente do Docker pode ser instalado em:

* Distribuições Linux

   * [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [Debian](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [Fedora](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [macOS](https://docs.docker.com/docker-for-mac/install/)

* [Windows](https://docs.docker.com/docker-for-windows/install/).

#### <a name="installing-git-for-sample-repository"></a>Instalando o Git para o repositório de exemplo

* Instale o [git](https://git-scm.com/download) caso deseje clonar o repositório.

### <a name="getting-the-sample-application"></a>Obtendo o aplicativo de exemplo

A maneira mais fácil de obter a amostra é por meio da clonagem do [repositório do Docker do .NET Core](https://github.com/dotnet/dotnet-docker) com o git, usando as seguintes instruções: 

```console
git clone https://github.com/dotnet/dotnet-docker
```

Você também pode baixar o repositório (que é pequeno) como um zip no repositório do Docker do .NET Core.

### <a name="run-the-aspnet-app-locally"></a>Executar o aplicativo ASP.NET localmente

Para um ponto de referência, antes de colocarmos o aplicativo em contêineres, primeiro devemos executá-lo localmente.

Compile e execute o aplicativo localmente com o SDK do .NET Core 2.1 usando os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

Depois que o aplicativo for iniciado, acesse **http://localhost:5000** no navegador da Web.

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a>Compilar e executar a amostra com o Docker para contêineres do Linux

Compile e execute a amostra no Docker usando contêineres do Linux com os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> O argumento `docker run` '-p' mapeia a porta 5000 no computador local para a porta 80 no contêiner (o formato de mapeamento da porta é `host:container`). Para obter mais informações, consulte a referência [docker run](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.

Depois que o aplicativo for iniciado, acesse **http://localhost:5000** no navegador da Web.

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a>Compilar e executar a amostra com o Docker para contêineres do Windows

Compile e execute a amostra no Docker usando contêineres do Windows com os seguintes comandos (as instruções pressupõem o uso da raiz do repositório):

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> Navegue para o **endereço IP do contêiner** (em vez de `http://localhost`) diretamente no navegador ao usar contêineres do Windows. Obtenha o endereço IP do contêiner com as seguintes etapas:

* Abra outro prompt de comando.
* Execute `docker ps` para ver os contêineres em execução. O contêiner “aspnetcore_sample” deve estar presente.
* Execute `docker exec aspnetcore_sample ipconfig`.
* Copie o endereço IP do contêiner e cole-o no navegador (por exemplo, 172.29.245.43).

> [!NOTE]
> O docker exec dá suporte à identificação de contêineres com o nome ou hash. O nome (aspnetcore_sample) é usado em nosso exemplo.

Consulte o exemplo a seguir de como obter o endereço IP de um contêiner do Windows em execução.

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

> [!NOTE]
> O docker exec executa um novo comando em um contêiner em execução. Para obter mais informações, consulte a [referência de docker exec](https://docs.docker.com/engine/reference/commandline/exec/) nos parâmetros de linha de comando.

Produza um aplicativo que está pronto para ser implantado em produção localmente usando o comando [dotnet publish](../tools/dotnet-publish.md).

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> O argumento de versão -c compila o aplicativo no modo de versão (o padrão é o modo de depuração). Para obter mais informações, consulte a referência [dotnet run](../tools/dotnet-run.md) nos parâmetros de linha de comando.

Execute o aplicativo no **Windows** usando o comando a seguir.

```console
dotnet published\aspnetapp.dll
```

Execute o aplicativo no **Linux** ou **macOS** usando o comando a seguir.

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a>Imagens do Docker usadas nesta amostra

As imagens a seguir do Docker são usadas no dockerfile desta amostra.

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

Parabéns! Você acabou de:
> [!div class="checklist"]
> * Aprender sobre as imagens do Docker no Microsoft .NET Core
> * Obter um aplicativo ASP.NET Core de exemplo para colocá-lo no Docker
> * Executar o aplicativo ASP.NET de exemplo localmente
> * Compilar e executar a amostra com o Docker para contêineres do Linux
> * Compilar e executar a amostra com o Docker para contêineres do Windows

**Próximas Etapas**

Estas são algumas das próximas etapas que podem ser realizadas:

* [Trabalhar com ferramentas de Docker do Visual Studio](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [Implantar imagens do Docker do Registro de Contêiner do Azure para Instâncias de Contêiner do Azure](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [Depurar com o Visual Studio Code](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [Prática com o Visual Studio para Mac, contêineres e código sem servidor na nuvem](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [Introdução ao Docker e ao Visual Studio para Mac Lab](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> Se você não tiver uma assinatura do Azure, [inscreva-se hoje](https://azure.microsoft.com/free/?b=16.48) em uma conta gratuita de 30 dias e receba $200 em Créditos do Azure para experimentar qualquer combinação de serviços do Azure.
