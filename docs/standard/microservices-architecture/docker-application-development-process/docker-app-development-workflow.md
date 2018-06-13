---
title: Fluxo de trabalho de desenvolvimento para aplicativos do Docker
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Fluxo de trabalho de desenvolvimento para aplicativos do Docker
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 2eb205e85300f22108b866e8446d6730d89ae6cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579672"
---
# <a name="development-workflow-for-docker-apps"></a>Fluxo de trabalho de desenvolvimento para aplicativos do Docker

O ciclo de vida de desenvolvimento do aplicativo inicia-se no computador de cada desenvolvedor, em que o desenvolvedor codifica o aplicativo usando a linguagem de sua preferência, testando-o localmente. Independentemente da linguagem, da estrutura e da plataforma escolhidas pelo desenvolvedor, com esse fluxo de trabalho, ele estará sempre desenvolvendo e testando contêineres do Docker, fazendo-o, entretanto, localmente.

Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:

-   Uma seleção do sistema operacional (por exemplo, uma distribuição do Linux, o Windows Nano Server ou o Windows Server Core).

-   Arquivos adicionados pelo desenvolvedor (binários do aplicativo, etc.).

-   Informações de configuração (configurações de ambiente e dependências).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Fluxo de trabalho para o desenvolvimento de aplicativos baseados em contêiner do Docker

Esta seção descreve o fluxo de trabalho de desenvolvimento do *loop interno* de aplicativos baseados em contêiner do Docker. O fluxo de trabalho de loop interno não leva em conta o fluxo de trabalho de DevOps mais amplo, mas concentra-se apenas no trabalho de desenvolvimento realizado no computador do desenvolvedor. As etapas iniciais para configurar o ambiente não estão incluídas, pois elas são realizadas apenas uma vez.

Um aplicativo é composto de seus próprios serviços e de bibliotecas adicionais (dependências). A figura 5-1 a seguir ilustra as etapas básicas que são normalmente realizadas para criar um aplicativo do Docker.

![](./media/image1.png)

**Figura 5-1.** Fluxo de trabalho passo a passo para o desenvolvimento de aplicativos do Docker em contêineres

Neste guia, todo esse processo será detalhado e cada etapa principal será explicada com base em um ambiente do Visual Studio.

Ao usar uma abordagem de desenvolvimento de editor/CLI (por exemplo, Visual Studio Code com CLI do Docker no macOS ou no Windows), você precisará conhecer cada etapa e, na maioria das vezes, com mais detalhes do que ao usar o Visual Studio. Para obter mais detalhes sobre como trabalhar em um ambiente de CLI, consulte o livro eletrônico [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/) (Ciclo de vida de aplicativo do Docker em contêineres com ferramentas e plataformas da Microsoft).

Ao usar o Visual Studio 2015 ou Visual Studio 2017, muitas dessas etapas serão controladas para você, melhorando significativamente a produtividade. Isso é especialmente verdadeiro quando você usa o Visual Studio 2017 e tem aplicativos de vários contêineres como destino. Por exemplo, com apenas um clique do mouse, o Visual Studio adiciona o Dockerfile e o arquivo docker-compose.yml aos seus projetos com a configuração correta para o seu aplicativo. Ao executar o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de vários contêineres diretamente no Docker; e até mesmo permite que você depure vários contêineres de uma só vez. Esses recursos vão acelerar sua velocidade de desenvolvimento.

No entanto, apenas o fato de o Visual Studio automatizar essas etapas não significa que você não precisa saber o que está acontecendo nos bastidores com o Docker. Portanto, nas diretrizes a seguir, vamos detalhar cada etapa.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Etapa 1. Iniciar a codificação e a criação do aplicativo inicial ou da linha de base do serviço

O desenvolvimento de um aplicativo do Docker é semelhante à forma como você desenvolve um aplicativo sem Docker. A diferença é que, durante o desenvolvimento para o Docker, você está implantando e testando o aplicativo ou os serviços executando-os dentro de contêineres do Docker em seu ambiente local. O contêiner pode ser do Linux ou do Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Configurar seu ambiente local com o Visual Studio

Para começar, instale o [Docker CE (Community Edition)](https://www.docker.com/community-edition) para Windows, conforme explicado nas instruções a seguir:

[Introdução ao Docker CE para Windows](https://docs.docker.com/docker-for-windows/)

Além disso, você precisará do Visual Studio 2017 instalado. Ele é preferível ao Visual Studio 2015 com o suplemento Ferramentas do Visual Studio para Docker, porque o Visual Studio 2017 tem suporte mais avançado para o Docker, como suporte para depuração de contêineres. O Visual Studio 2017 inclui as ferramentas para o Docker se você selecionou a carga de trabalho **.NET Core e Docker** durante a instalação, conforme mostrado na Figura 5-2.

![](./media/image3.png)

**Figura 5-2**. Selecionando a carga de trabalho **.NET Core e Docker** durante a instalação do Visual Studio 2017

Você pode iniciar a codificação do seu aplicativo no .NET simples (normalmente no .NET Core, se você estiver planejando usar contêineres) mesmo antes de habilitar o Docker em seu aplicativo e antes da implantação e do teste no Docker. No entanto, é recomendável que você comece a trabalhar no Docker assim que possível, porque que esse será o ambiente real e os problemas poderão ser descobertos o mais rápido possível. Isso é recomendável porque o Visual Studio facilita tanto o trabalho com o Docker parecendo, até mesmo, transparente — o melhor exemplo ao depurar aplicativos de vários contêineres do Visual Studio.

### <a name="additional-resources"></a>Recursos adicionais

-   **Introdução ao Docker CE para Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio 2017**
    [*https://www.visualstudio.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Etapa 2. Criar um Dockerfile relacionado a uma imagem base existente do .NET

Você precisa de um Dockerfile para cada imagem personalizada que você deseja criar. Você também precisará de um Dockerfile para cada contêiner a ser implantado automaticamente, por meio do Visual Studio, ou implantado manualmente, usando a CLI do Docker (comandos docker run e docker-compose). Se seu aplicativo contém um único serviço personalizado, é necessário um único Dockerfile. Se seu aplicativo contém vários serviços (como em uma arquitetura de microsserviços), é necessário um Dockerfile para cada serviço.

O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço. Ele contém os comandos que indicam ao Docker como configurar e executar seu aplicativo ou serviço em um contêiner. Você pode criar manualmente um Dockerfile por meio de código e adicioná-lo ao seu projeto junto com as dependências do .NET.

Com o Visual Studio e suas ferramentas para Docker, esta tarefa requer apenas alguns cliques do mouse. Quando você cria um novo projeto no Visual Studio 2017, há uma opção chamada **Habilitar Suporte a Contêiner (Docker)**, conforme mostrado na Figura 5-3.

![](./media/image5.png)

**Figura 5-3**. Habilitando o suporte do Docker ao criar um novo projeto no Visual Studio 2017

Você também pode habilitar o suporte do Docker em um projeto novo ou existente ao clicar com o botão direito do mouse no arquivo de projeto no Visual Studio e selecionar a opção **Adicionar, Suporte a projeto do Docker**, conforme mostrado na Figura 5-4.

![](./media/image6.png)

**Figura 5-4**. Habilitando o suporte do Docker em um projeto existente do Visual Studio 2017

Essa ação, em um projeto (como um aplicativo Web ASP.NET ou um serviço da API Web), adiciona um Dockerfile com a configuração necessária. Ela também adiciona um arquivo docker-compose.yml para toda a solução. Nas seções a seguir, descrevemos as informações que vão em cada um desses arquivos. O Visual Studio realiza esse trabalho para você, mas é útil entender o que vai dentro de um Dockerfile.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Opção a: criação de um projeto usando uma imagem do Docker oficial existente do .NET

Geralmente, você cria uma imagem personalizada para seu contêiner sobre uma imagem base que você pode obter de um repositório oficial, no registro do [Hub do Docker](https://hub.docker.com/). É exatamente isso o que acontece nos bastidores quando você habilita o suporte do Docker no Visual Studio. O Dockerfile usará uma imagem aspnetcore existente.

Anteriormente, explicamos quais imagens do Docker e quais repositórios você poderia usar, dependendo da estrutura e do sistema operacional que você escolheu. Por exemplo, se você quer usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada é microsoft/aspnetcore:2.0. Assim, basta especificar qual imagem base do Docker será usada para o seu contêiner. Isso é feito com a adição de FROM microsoft/aspnetcore:2.0 ao seu Dockerfile. Isso será realizado automaticamente pelo Visual Studio, mas se você precisar atualizar a versão, será esse valor que você atualizará.

O uso de um repositório de imagem oficial do .NET do Hub do Docker com um número de versão garante que os mesmos recursos de linguagem estejam disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).

O exemplo a seguir mostra um Dockerfile de exemplo para um contêiner do ASP.NET Core.

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Nesse caso, o contêiner é baseado na versão 2.0 da imagem do Docker do ASP.NET Core oficial (de várias arquiteturas, para Linux e Windows). Essa é a configuração `FROM microsoft/aspnetcore:2.0`. (Para obter mais detalhes sobre essa imagem base, consulte a página [Imagem do Docker do ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) e a página [Imagem do Docker do .NET Core](https://hub.docker.com/r/microsoft/dotnet/)). No Dockerfile, você também precisará instruir o Docker a escutar na porta TCP que você usará em tempo de execução (nesse caso, a porta 80, conforme definido com a configuração EXPOSE).

Você pode especificar mais configurações no Dockerfile, dependendo da linguagem e da estrutura que você está usando. Por exemplo, a linha ENTRYPOINT, com \["dotnet", "MySingleContainerWebApp.dll"\], informa ao Docker para executar um aplicativo do .NET Core. Se você estiver usando o SDK e a CLI do .NET Core (CLI do dotnet) para compilar e executar o aplicativo do .NET, essa configuração será diferente. O essencial é que a linha ENTRYPOINT e outras configurações serão diferentes dependendo da linguagem e da plataforma que você escolher para seu aplicativo.

### <a name="additional-resources"></a>Recursos adicionais

-   **Compilar Imagens do Docker para Aplicativos .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

-   **Criar sua própria imagem**. Na documentação oficial do Docker.
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Usando repositórios de imagens para várias arquiteturas

Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows. Esse recurso permite que fornecedores, como a Microsoft (criadores de imagem base), criem um único repositório para abranger várias plataformas (ou seja, Linux e Windows). Por exemplo, o repositório [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/), disponível no registro do Hub do Docker, é compatível com Linux e Windows Nano Server usando o mesmo nome de repositório.

Ao especificar uma marcação, você direciona a uma plataforma que é explícita, como nos seguintes casos:

-   **microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Mas (e isso é novo desde meados de 2017) se você especificar o mesmo nome de imagem, e até a mesma marcação, as novas imagens de várias arquiteturas (como a imagem aspnetcore, que é compatível com várias arquiteturas) usarão a versão do Windows ou do Linux, dependendo do sistema operacional host do Docker que você está implantando, conforme mostrado no exemplo a seguir:

-   **microsoft/aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Dessa forma, ao efetuar pull de uma imagem de um host do Windows, será efetuado o pull da variante do Windows e, ao efetuar pull do mesmo nome de imagem de um host do Linux, será efetuado pull da variante do Linux.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Opção B: criação da imagem base do zero

Você pode criar sua própria imagem base do Docker do zero. Esse cenário não é recomendável para um iniciante no Docker, mas se você desejar definir os bits específicos da sua própria imagem base, isso será possível.

### <a name="additional-resources"></a>Recursos adicionais

-   **Imagens do .NET Core para várias arquiteturas**.
https://github.com/dotnet/announcements/issues/14 
-   **Criar uma imagem base**. Documentação oficial do Docker.
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Etapa 3. Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço nelas

Para cada serviço do seu aplicativo, você precisa criar uma imagem relacionada. Se seu aplicativo é composto de um único serviço ou aplicativo Web, você precisa apenas de uma única imagem.

Observe que as imagens do Docker são criadas automaticamente para você no Visual Studio. As etapas a seguir são necessárias apenas para o fluxo de trabalho de editor/CLI e são explicadas com a finalidade de esclarecer o que acontece nos bastidores.

Você, como desenvolvedor, precisa desenvolver e testar localmente até enviar um recurso concluído por push ou mudar para o sistema de controle do código-fonte (por exemplo, para o GitHub). Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host do Docker local (VM do Windows ou Linux) e executar, testar e depurar nesses contêineres locais.

Para criar uma imagem personalizada no seu ambiente local, usando a CLI do Docker e o Dockerfile, você pode usar o comando docker build, como na Figura 5-5.

![](./media/image8.png)

**Figura 5-5**. Criando uma imagem personalizada do Docker

Opcionalmente, em vez de executar diretamente o comando docker build na pasta do projeto, você pode, primeiro, gerar uma pasta implantável com as bibliotecas e binários necessários do .NET, executando dotnet publish e, em seguida, usar o comando docker build.

Isso criará uma imagem do Docker com o nome cesardl/netcore-webapi-microservice-docker:first. Nesse caso, :first é uma marcação que representa uma versão específica. Você poderá repetir esta etapa para cada imagem personalizada que tiver que criar para o seu aplicativo composto do Docker.

Quando um aplicativo é composto de diversos contêineres (ou seja, é um aplicativo de vários contêineres), você também pode usar o comando docker-compose up --build para compilar todas as imagens relacionadas com um único comando, usando os metadados expostos nos arquivos docker-compose.yml relacionados.

Você pode encontrar as imagens existentes no seu repositório local usando o comando docker images, conforme mostrado na Figura 5-6.

![](./media/image9.png)

**Figura 5-6.** Exibição de imagens existentes usando o comando docker images

### <a name="creating-docker-images-with-visual-studio"></a>Criação de imagens do Docker com o Visual Studio

Ao usar o Visual Studio para criar um projeto com suporte do Docker, você não cria, explicitamente, uma imagem. Em vez disso, a imagem é criada para você ao pressionar F5 e executar o aplicativo ou serviço do Docker. Esta etapa é automática no Visual Studio e você não verá ela ocorrer, mas é importante que você saiba o que está acontecendo nos bastidores.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Etapa 4. Definir os serviços no docker-compose.yml ao compilar um aplicativo de vários contêineres do Docker

O arquivo [docker-compose.yml](https://docs.docker.com/compose/compose-file/) permite que você defina um conjunto de serviços relacionados para que sejam implantados como um aplicativo composto com comandos de implantação.

Para usar um arquivo docker-compose.yml, você precisa criar o arquivo na pasta principal ou raiz da sua solução, com conteúdo semelhante ao do exemplo a seguir:

```yml
version: '3'
  
services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment: 
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"

```

Observe que esse arquivo docker-compose.yml é uma versão simplificada e mesclada. Ele contém dados de configuração estática para cada contêiner (como o nome da imagem personalizada), o que é sempre aplicável, além das informações de configuração que dependerão do ambiente de implantação, como a cadeia de conexão. Nas próximas seções, você aprenderá como dividir a configuração do docker-compose.yml em vários arquivos e valores de substituição de docker-compose, dependendo do ambiente e do tipo de execução (depuração ou lançamento).

O arquivo docker-compose.yml de exemplo define cinco serviços: o serviço webmvc (um aplicativo Web), dois microsserviços (catalog.api e ordering.api) e um contêiner de fonte de dados, sql.data, com base no SQL Server para Linux, em execução como um contêiner. Cada serviço é implantado como um contêiner, assim, é necessário uma imagem do Docker para cada serviço.

O arquivo docker-compose.yml não apenas especifica quais contêineres estão sendo usados, mas também como eles são configurados individualmente. Por exemplo, a definição de contêiner do webmvc, no arquivo .yml:

-   Usa uma imagem eshop/web:latest pré-compilada. Entretanto, você também poderia definir a imagem para ser compilada como parte da execução do docker-compose, com uma configuração adicional baseada em uma seção build: no arquivo docker-compose.

-   Inicializa duas variáveis de ambiente (CatalogUrl e OrderingUrl).

-   Encaminha a porta 80, exposta no contêiner, para a porta 80 externa, no computador host.

-   Vincula o aplicativo Web ao serviço de catálogo e pedidos com a configuração depends\_on. Isso faz com que o serviço aguarde até que esses serviços sejam iniciados.

Vamos abordar novamente o arquivo docker-compose.yml em uma seção posterior, ao explicar como implementar microsserviços e aplicativos de vários contêineres.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Trabalhando com o docker-compose.yml no Visual Studio 2017

Quando você adiciona suporte à solução do Docker para um projeto de serviço em uma solução do Visual Studio, conforme mostrado na Figura 5-7, o Visual Studio adiciona um Dockerfile ao seu projeto e ele adiciona uma seção de serviço (projeto) em sua solução, com os arquivos docker-compose.yml. Essa é uma maneira fácil de iniciar a composição da sua solução de vários contêineres. Depois, você pode abrir os arquivos docker-compose.yml e atualizá-los com mais recursos.

![](./media/image6.png)

**Figura 5-7**. Adicionar suporte do Docker no Visual Studio 2017 ao clicar com o botão direito do mouse em um projeto do ASP.NET Core

A adição de suporte do Docker no Visual Studio não somente adiciona o Dockerfile ao seu projeto, mas também adiciona as informações de configuração a diversos arquivos docker-compose.yml globais que são definidos no nível da solução.

Depois de adicionar suporte do Docker à sua solução no Visual Studio, você também verá um novo nó (no arquivo de projeto docker-compose.dcproj) no Gerenciador de Soluções que contém os arquivos docker-compose.yml incluídos, conforme mostrado na Figura 5-8.

![](./media/image11.PNG)

**Figura 5-8**. O nó de árvore **docker-compose** adicionado no Gerenciador de Soluções do Visual Studio 2017

Você pode implantar um aplicativo de vários contêineres com um único arquivo docker-compose.yml, usando o comando docker-compose up. No entanto, o Visual Studio adiciona um grupo desses arquivos, para que você possa substituir os valores de acordo com o ambiente (desenvolvimento versus produção) e o tipo de execução (lançamento versus depuração). Essa funcionalidade será explicada nas seções posteriores.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Etapa 5. Compilar e executar seu aplicativo do Docker

Se seu aplicativo tem apenas um contêiner, você pode executá-lo implantando-o no host do Docker (VM ou servidor físico). No entanto, se seu aplicativo contém vários serviços, você pode implantá-lo como um aplicativo composto, usando um único comando de CLI (docker-compose up), ou com o Visual Studio, que usará esse mesmo comando nos bastidores. Vamos examinar as diferentes opções.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Opção A: executando um único contêiner com a CLI do Docker

Você pode executar um contêiner do Docker usando o comando docker run, como na Figura 5-9:

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Figura 5-9**. Executando um contêiner do Docker usando o comando docker run

Nesse caso, o comando associa a porta interna 5000 do contêiner à porta 80 do computador host. Isso significa que o host está escutando na porta 80 e encaminhando para a porta 5000 no contêiner.

### <a name="option-b-running-a-multi-container-application"></a>Opção B: executando um aplicativo de vários contêineres

Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços, o que significa que você precisará executar um aplicativo de vários contêineres, conforme mostrado na Figura 5-10.

![](./media/image14.png)

**Figura 5-10**. VM com contêineres do Docker implantados

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Executando um aplicativo de vários contêineres com a CLI do Docker

Para executar um aplicativo de vários contêineres com a CLI do Docker, você pode executar o comando docker-compose up. Esse comando usa o arquivo docker-compose.yml, que você tem no nível da solução, para implantar um aplicativo de vários contêineres. A figura 5-11 mostra os resultados da execução do comando no diretório principal do projeto, que contém o arquivo docker-compose.yml.

![](./media/image15.png)

**Figura 5-11**. Resultados de exemplo ao executar o comando docker-compose up

Depois que o comando docker-compose up é executado, o aplicativo e os contêineres relacionados são implantados no host do Docker, conforme ilustrado na representação de VM da Figura 5-10.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Executando e depurando um aplicativo de vários contêineres com o Visual Studio 

A execução de um aplicativo de vários contêineres com o Visual Studio 2017 é muito simples. Você não somente executa o aplicativo de vários contêineres, mas também depura todos os respectivos contêineres diretamente no Visual Studio, por meio da definição de pontos de interrupção regulares.

Conforme mencionado anteriormente, sempre que você adiciona suporte à solução do Docker a um projeto de uma solução, esse projeto é configurado no arquivo global (nível da solução) docker-compose.yml, o que permite que você execute ou depure toda a solução de uma só vez. O Visual Studio iniciará um contêiner para cada projeto que tenha suporte habilitado à solução do Docker e executará todas as etapas internas para você (dotnet publish, docker build, etc.).

O ponto importante aqui é que, conforme mostrado na Figura 5-12, há um comando adicional do **Docker**, no Visual Studio 2017, para a ação da tecla F5. Essa opção permite que você execute ou depure um aplicativo de vários contêineres executando todos os contêineres que estão definidos nos arquivos docker-compose.yml no nível da solução. A capacidade de depurar soluções de vários contêineres significa que você poderá definir vários pontos de interrupção, cada ponto de interrupção em um projeto (contêiner) diferente e que, durante a depuração no Visual Studio, você vai parar nos pontos de interrupção definidos em diferentes projetos e em execução em diferentes contêineres.

![](./media/image16.png)

**Figura 5-12**. Executando aplicativos de vários contêineres no Visual Studio 2017

### <a name="additional-resources"></a>Recursos adicionais

-   **Implantar um contêiner do ASP.NET em um host remoto do Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uma observação sobre teste e implantação com orquestradores

Os comandos docker-compose up e docker run (ou executar e depurar os contêineres no Visual Studio) são adequados para contêineres de teste em seu ambiente de desenvolvimento. Mas você não deve usar essa abordagem se tiver como destino os clusters e orquestradores do Docker, como Docker Swarm, Mesosphere DC/OS ou Kubernetes. Se estiver usando um cluster como [modo Docker Swarm](https://docs.docker.com/engine/swarm/) (disponível no Docker CE para Windows e Mac desde a versão 1.12), você precisará implantar e testar com comandos adicionais, como [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/), para serviços únicos. Se estiver implantando um aplicativo composto por vários contêineres, você usará [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) e [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) para implantar o aplicativo composto como uma *pilha*. Para obter mais informações, consulte a postagem no blog [Introducing Experimental Distributed Application Bundles (Apresentando pacotes de aplicativos experimentais distribuídos)](https://blog.docker.com/2016/06/docker-app-bundle/) na documentação do Docker, no site do Docker.

Para [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) você também teria que usar outros scripts e comandos de implantação.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Etapa 6. Testar seu aplicativo do Docker usando o host local do Docker

Esta etapa varia de acordo com o que seu aplicativo está fazendo. Em um aplicativo Web simples do .NET Core que é implantado como um único contêiner ou serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegando até o site, conforme mostrado na Figura 5-13. (Se a configuração do Dockerfile mapear o contêiner para uma porta no host que seja diferente de 80, inclua a porta do host na URL).

![](./media/image18.png)

**Figura 5-13**. Exemplo de teste do seu aplicativo do Docker localmente usando localhost

Se o localhost não estiver apontando para o IP do host do Docker (por padrão, ao usar o Docker CE, ele deveria fazê-lo), use o endereço IP da placa de rede do seu computador para navegar até o serviço.

Observe que a URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo discutido. No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois é assim que ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.

Você também pode testar o aplicativo usando o comando curl no terminal, conforme mostrado na Figura 5-14. Em uma instalação do Docker no Windows, o IP padrão do Host do Docker é sempre 10.0.75.1, além do endereço IP do seu computador.

![](./media/image19.png)

**Figura 5-14**. Exemplo de teste do seu aplicativo do Docker localmente usando curl

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testando e depurando contêineres com o Visual Studio 2017

Ao executar e depurar contêineres com o Visual Studio 2017, você depura o aplicativo do .NET de maneira muito parecida como você faria ao executar sem contêineres.

### <a name="testing-and-debugging-without-visual-studio"></a>Testando e depurando sem o Visual Studio

Se você estiver desenvolvendo por meio da abordagem de editor/CLI, a depuração de contêineres será mais difícil e será necessário fazer a depuração por meio da geração de rastreamentos.

### <a name="additional-resources"></a>Recursos adicionais

-   **Depuração de aplicativos em um contêiner local do Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Compilar, depurar, implantar aplicativos do ASP.NET Core com o Docker.** Vídeo.
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio

Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que ao usar a abordagem de editor/CLI. A maioria das etapas necessárias pelo Docker, relacionadas ao Dockerfile e aos arquivos docker-compose.yml, são ocultas ou simplificadas pelo Visual Studio, conforme mostrado na Figura 5-15.

![](./media/image20.png)

**Figura 5-15**. Fluxo de trabalho simplificado ao desenvolver com o Visual Studio

Além disso, será necessário executar a etapa 2 (adicionar suporte do Docker aos seus projetos) apenas uma vez. Portanto, o fluxo de trabalho é semelhante às suas tarefas de desenvolvimento regulares, quando utiliza o .NET para qualquer outro desenvolvimento. É necessário saber o que está acontecendo nos bastidores (o processo de build da imagem, quais imagens base você está usando, implantação de contêineres, etc.) e, às vezes, você também precisará editar o Dockerfile ou o arquivo docker-compose.yml para personalizar comportamentos. Mas a maior parte do trabalho é bastante simplificada com o uso do Visual Studio, o que o torna muito mais produtivo.

### <a name="additional-resources"></a>Recursos adicionais

-   **Steve Lasker. Desenvolvimento de Docker no .NET com o Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Colocar um aplicativo .NET Core em um contêiner com as novas Ferramentas do Docker para Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Usando comandos do PowerShell em um DockerFile para configurar contêineres do Windows 

Os [contêineres do Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker. Para usar contêineres do Windows, você executa comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração FROM) e instalando IIS com um comando do PowerShell (a configuração RUN). Da mesma forma, você também pode usar comandos do PowerShell para configurar outros componentes, como ASP.NET 4.x, .NET 4.6 ou qualquer outro software do Windows. Por exemplo, o seguinte comando, em um Dockerfile, configura o ASP.NET 4.5:

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Recursos adicionais

-   **aspnet-docker/Dockerfile.** Comandos do PowerShell de exemplo para executar em Dockerfiles e incluir recursos do Windows.
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Anterior] (index.md) [Próximo] (../net-core-single-containers-linux-windows-server-hosts/index.md)
