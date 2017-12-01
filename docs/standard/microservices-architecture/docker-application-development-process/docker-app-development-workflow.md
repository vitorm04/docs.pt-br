---
title: Fluxo de trabalho de desenvolvimento para aplicativos de Docker
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Fluxo de trabalho de desenvolvimento para aplicativos de Docker"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5a53aee4261a5a0bfc25b3520c50cf505b84f287
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="development-workflow-for-docker-apps"></a>Fluxo de trabalho de desenvolvimento para aplicativos de Docker

O ciclo de vida de desenvolvimento de aplicativo é iniciado no computador de cada desenvolvedor, onde o desenvolvedor códigos de aplicativo usando o seu idioma preferencial e testa-o localmente. Não importa qual idioma, framework e plataforma escolhe o desenvolvedor, com esse fluxo de trabalho, o desenvolvedor é sempre desenvolver e testar contêineres do Docker, mas fazê-lo localmente.

Cada contêiner (uma instância de uma imagem do Docker) inclui os seguintes componentes:

-   Uma seleção de sistema operacional (por exemplo, uma distribuição de Linux, Windows Nano Server ou Windows Server Core).

-   Arquivos adicionados pelo desenvolvedor do (binários do aplicativo, etc.).

-   Informações de configuração (configurações de ambiente e dependências).

## <a name="workflow-for-developing-docker-container-based-applications"></a>Fluxo de trabalho para o desenvolvimento de aplicativos baseados no contêiner do Docker

Esta seção descreve o *loop interno* fluxo de trabalho de desenvolvimento para aplicativos baseados no contêiner do Docker. O fluxo de trabalho do loop interno significa que ele é não levando em conta o fluxo de trabalho DevOps mais amplo e apenas se concentra em suas tarefas de desenvolvimento no computador do desenvolvedor. As etapas iniciais para configurar o ambiente não são incluídas, como aquelas terminar apenas uma vez.

Um aplicativo é composto de seus próprios serviços mais bibliotecas adicionais (dependências). A seguir estão as etapas básicas normalmente ao criar um aplicativo do Docker, conforme ilustrado na Figura 5-1.

![](./media/image1.png)

**Figura 5-1.** Fluxo de trabalho passo a passo para desenvolvimento de aplicativos em contêineres de Docker

Neste guia, esse processo todo é detalhado e cada etapa principal é explicada concentrando-se em um ambiente do Visual Studio.

Quando você estiver usando uma abordagem de desenvolvimento do editor/CLI (por exemplo, código do Visual Studio mais CLI do Docker em macOS ou Windows), você precisa saber a cada etapa, geralmente em mais detalhes do que se você estiver usando o Visual Studio. Para obter mais detalhes sobre como trabalhar em um ambiente de CLI, consulte o livro eletrônico [ciclo de vida do aplicativo de Docker em contêineres com ferramentas e Microsoft Platforms](http://aka.ms/dockerlifecycleebook/).

Quando você estiver usando o Visual Studio 2015 ou Visual Studio de 2017, muitas dessas etapas serão manipuladas para você, o que melhora significativamente a produtividade. Isso é especialmente verdadeiro quando você estiver usando o Visual Studio de 2017 e contêiner vários aplicativos de destino. Por exemplo, com apenas um clique do mouse, o Visual Studio adiciona o arquivo Dockerfile e docker compose.yml seus projetos com a configuração do seu aplicativo. Quando você executa o aplicativo no Visual Studio, ele cria a imagem do Docker e executa o aplicativo de multi-container diretamente no Docker; até mesmo permite depurar vários contêineres de uma vez. Esses recursos melhora a velocidade de desenvolvimento.

No entanto, apenas porque o Visual Studio torna essas etapas automática não significa que você não precisa saber o que está acontecendo em sob com o Docker. Portanto, na orientação a seguir, estamos detalhes de cada etapa.

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a>Etapa 1. Iniciar a codificação e criar o aplicativo inicial ou a linha de base de serviço

Desenvolvendo um aplicativo de Docker é semelhante à forma como desenvolver um aplicativo sem Docker. A diferença é que durante o desenvolvimento de Docker, você implantar e testar o aplicativo ou os serviços em execução dentro de contêineres do Docker em seu ambiente local. O contêiner pode ser um contêiner do Linux ou um contêiner do Windows.

### <a name="set-up-your-local-environment-with-visual-studio"></a>Configurar seu ambiente local com o Visual Studio

Para começar, verifique se você tem [Docker Community Edition (CE)](https://www.docker.com/community-edition) para o Windows instalado, conforme explicado nas instruções a seguir:

[Introdução ao Docker CE para Windows](https://docs.docker.com/docker-for-windows/)

Além disso, você precisará Visual Studio de 2017 instalado. Isso é preferível Visual Studio 2015 com o Visual Studio Tools para Docker suplemento, porque o Visual Studio de 2017 tem mais suporte avançado para Docker, como suporte para depuração de contêineres. 2017 do Visual Studio inclui as ferramentas do Docker, se você tiver selecionado o **.NET Core e o Docker** cargas de trabalho durante a instalação, conforme mostrado na Figura 5-2.

![](./media/image3.png)

**Figura 5-2**. Selecionando o **.NET Core e o Docker** cargas de trabalho durante a instalação do Visual Studio de 2017

Você pode iniciar a codificação do seu aplicativo no .NET simples (normalmente no núcleo do .NET se você estiver planejando usar contêineres) mesmo antes de habilitar Docker em seu aplicativo e implantação e teste no Docker. No entanto, é recomendável que você começa a trabalhar no Docker assim que possível, porque que será o ambiente real e os problemas podem ser descobertos assim que possível. Isso é recomendável porque o Visual Studio facilita a trabalhar com o Docker que quase parece transparente — o melhor exemplo durante a depuração de contêiner de vários aplicativos do Visual Studio.

### <a name="additional-resources"></a>Recursos adicionais

-   **Introdução ao Docker CE para Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

-   **Visual Studio de 2017**
    [*https://www.visualstudio.com/vs/visual-studio-2017/*](https://www.visualstudio.com/vs/visual-studio-2017/)

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a>Etapa 2. Crie um Dockerfile relacionado a uma imagem de base existente do .NET

Você precisa de um Dockerfile para cada imagem personalizada que você deseja criar; Você também precisa de um Dockerfile para cada contêiner a ser implantado, se você implantar automaticamente do Visual Studio ou manualmente usando a CLI do Docker (execução de docker e o docker-compor comandos). Se seu aplicativo contém um único serviço personalizado, é necessário um Dockerfile único. Se seu aplicativo contém vários serviços (como em uma arquitetura microservices), será necessário um Dockerfile para cada serviço.

O Dockerfile é colocado na pasta raiz do seu aplicativo ou serviço. Ele contém os comandos que indicam como configurar e executar seu aplicativo ou serviço em um contêiner de Docker. Manualmente, você pode criar um Dockerfile no código e adicioná-lo ao seu projeto junto com suas dependências do .NET.

Com o Visual Studio e suas ferramentas para Docker, esta tarefa requer apenas alguns cliques do mouse. Quando você cria um novo projeto no Visual Studio de 2017, há uma opção chamada **suporte habilitar contêiner (Docker)**, conforme mostrado na Figura 5-3.

![](./media/image5.png)

**Figura 5-3**. Habilitar o suporte do Docker ao criar um novo projeto no Visual Studio de 2017

Você também pode habilitar o suporte de Docker em um projeto novo ou existente clicando duas vezes o arquivo de projeto no Visual Studio e selecionando a opção **Docker Adicionar projeto suporte**, conforme mostrado na Figura 5-4.

![](./media/image6.png)

**Figura 5-4**. Habilitar o suporte de Docker em um projeto existente do Visual Studio de 2017

Essa ação em um projeto (como um aplicativo Web ASP.NET ou um serviço de API da Web) adiciona um Dockerfile para o projeto com a configuração necessária. Ele também adiciona um arquivo de docker compose.yml de toda a solução. As seções a seguir, descrevemos as informações que vão para cada um desses arquivos. O Visual Studio pode executar esse trabalho para você, mas é útil entender o que acontece em um Dockerfile.

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a>Opção a: Criando um projeto usando uma imagem do Docker .NET oficial existente

Você normalmente cria uma imagem personalizada para seu contêiner na parte superior de uma imagem de base que você pode obter de um repositório oficial no [Hub do Docker](https://hub.docker.com/) registro. É exatamente o que acontece nos bastidores, quando você habilitar o suporte de Docker no Visual Studio. O Dockerfile usará uma imagem aspnetcore existente.

Anteriormente, explicamos quais imagens do Docker e repositórios, você pode usar, dependendo da estrutura e o sistema operacional que você escolheu. Por exemplo, se você quiser usar o ASP.NET Core (Linux ou Windows), a imagem a ser usada é microsoft / aspnetcore:2.0. Por isso, basta especificar qual imagem base do Docker será usado para o contêiner. Você pode fazer isso com a adição da microsoft / aspnetcore:2.0 para o Dockerfile. Isso será executado automaticamente pelo Visual Studio, mas se você atualizar a versão, atualize esse valor.

Usar um repositório de imagem de .NET oficial do Hub do Docker com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo o desenvolvimento, teste e produção).

O exemplo a seguir mostra um exemplo de Dockerfile para um contêiner do ASP.NET Core.

```
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

Nesse caso, o contêiner se baseia na versão 2.0 da imagem do ASP.NET Core Docker oficial (Multi-arch para Linux e Windows). Essa é a configuração `FROM microsoft/aspnetcore:2.0`. (Para obter mais detalhes sobre essa imagem base, consulte o [imagem do ASP.NET Core Docker](https://hub.docker.com/r/microsoft/aspnetcore/) página e o [.NET Core Docker imagem](https://hub.docker.com/r/microsoft/dotnet/) página.) No Dockerfile, você também precisa instruem o Docker para escutar na porta TCP que você usará em tempo de execução (nesse caso, a porta 80, conforme configurado com a configuração de EXPOR).

Você pode especificar configurações adicionais no Dockerfile, dependendo do idioma e do framework que você está usando. Por exemplo, a linha do ponto de entrada com \["dotnet", "MySingleContainerWebApp.dll"\] informa Docker para executar um aplicativo .NET Core. Se você estiver usando o SDK e .NET Core CLI (dotnet CLI) para compilar e executar o aplicativo do .NET, essa configuração deve ser diferente. O resultado final é que a linha do ponto de entrada e outras configurações serão diferentes dependendo do idioma e plataforma que você escolhe para seu aplicativo.

### <a name="additional-resources"></a>Recursos adicionais

-   **Criação de imagens do Docker para aplicativos do .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images)

-   **Criar sua própria imagem**. Na documentação oficial do Docker.
    [*https://docs.docker.com/Engine/Tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a>Usando repositórios de arch várias imagens

Um único repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows. Esse recurso permite que fornecedores como a Microsoft (criadores de imagem de base) criar um único repositório para abranger várias plataformas (ou seja, Linux e Windows). Por exemplo, o [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repositório disponível no registro do Hub do Docker fornece suporte para Linux e Windows Nano Server usando o mesmo nome de repositório.

Se você especificar uma marca, direcionar uma plataforma que é explícita como nos seguintes casos:

-   **Microsoft/aspnetcore:2.0.0-jessie**

        .NET Core 2.0 runtime-only on Linux 

-   **Microsoft/aspnetcore:2.0.0-nanoserver**

        .NET Core 2.0 runtime-only on Windows Nano Server

Mas e isso é novo desde meados de 2017, se você especificar o mesmo nome de imagem, mesmo com a mesma marca, as novas imagens de várias arch (como a imagem de aspnetcore que dá suporte a vários arch) usará a versão do Windows ou do Linux dependendo do host do Docker sistema operacional você está implantando , conforme mostrado no exemplo a seguir:

-   **Microsoft / aspnetcore:2.0**

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

Dessa forma, quando você efetuar o pull de uma imagem de um host do Windows, ele obterá a variante do Windows e extrair o mesmo nome da imagem de um host Linux obterá a variante de Linux.

### <a name="option-b-creating-your-base-image-from-scratch"></a>Opção b: Criando a imagem base do zero

Você pode criar sua própria imagem base do Docker do zero. Esse cenário não é recomendado para alguém que está iniciando com o Docker, mas se você deseja definir os bits específicos de sua própria imagem base, você pode fazer isso.

### <a name="additional-resources"></a>Recursos adicionais

-   **Arch várias imagens de .NET Core**.
https://GitHub.com/dotnet/Announcements/issues/14 
-   **Criar uma imagem de base**. Documentação oficial do Docker.
    [*https://docs.docker.com/Engine/UserGuide/eng-Image/BaseImages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a>Etapa 3. Criar imagens personalizadas do Docker e inserir seu aplicativo ou serviço neles

Para cada serviço em seu aplicativo, você precisa criar uma imagem de relacionados. Se seu aplicativo é composto de um único serviço ou aplicativo web, você precisa apenas uma única imagem.

Observe que as imagens do Docker são criadas automaticamente para você no Visual Studio. As etapas a seguir apenas são necessários para o fluxo de trabalho do editor/CLI e explicadas para fins de esclarecimento sobre o que acontece abaixo.

Você, como desenvolvedor, precisa para desenvolver e testar localmente até que você enviar por push uma concluído recurso ou altere para o sistema de controle de origem (por exemplo, para GitHub). Isso significa que você precisa criar as imagens do Docker e implantar contêineres em um host Docker local (Windows ou Linux VM) e executar, testar e depurar em relação a esses contêineres locais.

Para criar uma imagem personalizada no seu ambiente local usando a CLI do Docker e o Dockerfile, você pode usar o comando de build do docker, como na Figura 5-5.

![](./media/image8.png)

**Figura 5-5**. Criar uma imagem personalizada do Docker

Opcionalmente, em vez de executar diretamente o build do docker da pasta do projeto, primeiro você pode gerar uma pasta de implantação com as bibliotecas necessárias do .NET e binários executando dotnet publicarem e, em seguida, usam o comando de build do docker.

Isso criará uma imagem do Docker com o nome cesardl/netcore-webapi-microsserviço-docker: primeiro. Nesse caso,: primeiro é uma marca que representa uma versão específica. Você pode repetir esta etapa para cada imagem personalizada, que você precisa criar seu aplicativo composto do Docker.

Quando um aplicativo é feito de vários contêineres (isto é, é um aplicativo de contêiner vários), você também pode usar a compor docker backup – de comando de compilação para compilar todas as imagens relacionadas com um único comando usando os metadados expostos no relacionado arquivos de docker compose.yml.

Você pode encontrar as imagens existentes no seu repositório local usando o docker imagens comando, conforme mostrado na Figura 5-6.

![](./media/image9.png)

**Figura 5-6.** Exibindo imagens existentes usando o comando de imagens do docker

### <a name="creating-docker-images-with-visual-studio"></a>Criação de imagens do Docker com o Visual Studio

Quando você estiver usando o Visual Studio para criar um projeto com suporte do Docker, você não criar explicitamente uma imagem. Em vez disso, a imagem é criada para você quando você pressiona F5 e executar o aplicativo dockerized ou serviço. Esta etapa é automática no Visual Studio e você não verá ele ocorrer, mas é importante que você sabe o que está acontecendo em sob.

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a>Etapa 4. Definir os serviços no docker compose.yml ao compilar um aplicativo de multi-contêiner de Docker

O [docker compose.yml](https://docs.docker.com/compose/compose-file/) arquivo permite que você defina um conjunto de serviços relacionados a ser implantado como um aplicativo composto com comandos de implantação.

Para usar um arquivo de docker compose.yml, você precisa criar o arquivo em seu principal ou a pasta de solução raiz, com conteúdo semelhante ao exemplo a seguir:

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

Observe que esse arquivo compose.yml docker é uma versão simplificada e mesclada. Ele contém dados de configuração estática para cada contêiner (como o nome da imagem personalizada), que se aplica sempre, além de informações de configuração que podem depender do ambiente de implantação, como a cadeia de caracteres de conexão. Nas próximas seções, você aprenderá como você pode dividir a configuração do docker compose.yml em vários compor docker arquivos e valores de substituição, dependendo do tipo de ambiente e a execução (debug ou release).

O exemplo de arquivo de docker compose.yml define cinco serviços: o serviço de webmvc (um aplicativo web), dois microservices (catalog.api e ordering.api) e contêiner de fonte dados, sql.data, com base no SQL Server para Linux em execução como um contêiner. Cada serviço é implantado como um contêiner para que uma imagem do Docker é necessária para cada um.

O arquivo de docker compose.yml especifica não apenas quais contêineres estão sendo usados, mas como eles são configurados individualmente. Por exemplo, webmvc contêiner definição no arquivo .yml:

-   Usa um eshop pré-criado / imagem da web: mais recente. No entanto, você também pode definir a imagem a ser criado como parte da compor docker execução com uma configuração adicional com base em uma compilação: seção no arquivo docker-compose.

-   Inicializa as duas variáveis de ambiente (URL do catálogo e OrderingUrl).

-   Encaminha a exposto a porta 80 no contêiner para a porta 80 externa no computador host.

-   Vincula o aplicativo web para o catálogo e a ordenação de serviço com o depende\_na configuração. Isso faz com que o serviço aguardar até que esses serviços são iniciados.

Vamos revisitar o arquivo de docker compose.yml em uma seção posterior quando abordaremos como implementar microservices e contêiner vários aplicativos.

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a>Trabalhando com o docker-compose.yml no Visual Studio de 2017

Quando você adiciona suporte de solução de Docker para um projeto de serviço em uma solução do Visual Studio, conforme mostrado na Figura 5-7, o Visual Studio adiciona um Dockerfile ao seu projeto, e ele adiciona uma seção de serviço (projeto) em sua solução com os arquivos de docker compose.yml. É uma maneira fácil de iniciar a composição de sua solução de vários contêineres. Em seguida, você pode abrir os arquivos de docker compose.yml e atualizá-los com recursos adicionais.

![](./media/image6.png)

**Figura 5-7**. Adicionando suporte de Docker no Visual Studio de 2017 clicando em um projeto do ASP.NET Core

Adicionando suporte de Docker no Visual Studio não apenas adiciona o Dockerfile ao seu projeto, mas adiciona as informações de configuração em vários arquivos de docker-compose.yml globais que são definidos no nível da solução.

Depois de adicionar suporte de Docker para sua solução no Visual Studio, você também verá um novo nó (no arquivo de projeto docker compose.dcproj) no Gerenciador de soluções que contém os arquivos de inclusão docker-compose.yml, conforme mostrado na Figura 5-8.

![](./media/image11.PNG)

**Figura 5-8**. O **compor docker** adicionado no Gerenciador de soluções do Visual Studio 2017 do nó de árvore

Você pode implantar um aplicativo de contêiner vários com um arquivo único docker-compose.yml usando o docker-compor o comando. No entanto, o Visual Studio adiciona um grupo de-los para que você pode substituir valores dependendo do ambiente (desenvolvimento e produção) e a execução de tipo (versão versus depuração). Esse recurso será explicado nas seções posteriores.

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a>Etapa 5. Compilar e executar seu aplicativo de Docker

Se seu aplicativo tiver apenas um único contêiner, você pode executá-lo, implantando-a para o host do Docker (VM ou servidor físico). No entanto, se seu aplicativo contém vários serviços, você pode implantá-lo como um aplicativo composto, usando um único comando CLI (docker-compor backup), ou com o Visual Studio, que usará esse comando nos bastidores. Vamos examinar as diferentes opções.

### <a name="option-a-running-a-single-container-with-docker-cli"></a>Opção a: executando um único contêiner com Docker CLI

Você pode executar um contêiner do Docker usando o comando docker run, como na Figura 5-9:

```
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

**Figura 5-9**. Executando um contêiner do Docker usando o comando docker run

Nesse caso, o comando associa a porta interna 5000 do contêiner para a porta 80 da máquina de host. Isso significa que o host está escutando na porta 80 e encaminhamento de porta 5000 no contêiner.

### <a name="option-b-running-a-multi-container-application"></a>Opção b: executando um aplicativo de contêiner de vários

Na maioria dos cenários de empresa, um aplicativo de Docker será ser composto de vários serviços, que significa que você precisa executar um aplicativo de multi-container, conforme mostrado na Figura 5-10.

![](./media/image14.png)

**Figura 5-10**. VM com contêineres do Docker implantado

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a>Executando um aplicativo de contêiner vários da CLI do Docker

Para executar um aplicativo de contêiner vários da CLI do Docker, você pode executar o docker-compor o comando. Este arquivo de usa docker-compose.yml de comando que você tem no nível da solução para implantar um aplicativo de contêiner de vários. Figura 5-11 mostra os resultados ao executar o comando do diretório de projeto principal, que contém o arquivo compose.yml docker.

![](./media/image15.png)

**Figura 5-11**. Exemplo de resultados ao executar o docker-compor o comando

Após o docker-compor é executado, o comando, o aplicativo e seus contêineres relacionados são implantados em seu host do Docker, conforme ilustrado na Figura 5-10 de representação de VM.

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a>Executando e depurando um aplicativo de multi-contêiner com o Visual Studio 

Executando um aplicativo de multi-contêiner usando o Visual Studio de 2017 não é possível obter mais simples. Você não pode executar o aplicativo de multi-contêiner só, mas é possível depurar todos os seus contêineres diretamente do Visual Studio, definindo pontos de interrupção regulares.

Conforme mencionado anteriormente, cada vez que você adicionar suporte de solução de Docker para um projeto em uma solução, projeto está configurado no arquivo global (nível de solução) docker-compose.yml, que permite que você executar ou depurar a solução completa de uma vez. Visual Studio iniciar um contêiner para cada projeto que tem suporte a soluções Docker habilitado e executar todas as etapas internas para você (dotnet publicar, build do docker, etc.).

O ponto importante aqui é que, conforme mostrado na Figura 5-12, no Visual Studio de 2017 há adicional **Docker** comando para a ação de chave F5. Essa opção permite a você executar ou depurar um aplicativo de contêiner vários executando todos os contêineres que são definidos nos arquivos de docker compose.yml no nível da solução. A capacidade de depurar o contêiner de várias soluções significa que você pode definir vários pontos de interrupção, cada ponto de interrupção em um projeto diferente (contêiner) e durante a depuração do Visual Studio, você irá parar em pontos de interrupção definidos em diferentes projetos e em execução em contêineres diferentes.

![](./media/image16.png)

**Figura 5-12**. Executando aplicativos de multi-contêiner no Visual Studio de 2017

### <a name="additional-resources"></a>Recursos adicionais

-   **Implantar um contêiner do ASP.NET em um host remoto do Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a>Uma observação sobre como testar e implantar com orchestrators

O docker-compor o e execute os comandos (ou executando e depurando os contêineres no Visual Studio) são adequadas para contêineres de teste em seu ambiente de desenvolvimento. Mas você não deve usar essa abordagem se tiver como alvo clusters do Docker e orchestrators como Docker Swarm, Mesosphere DC/sistema operacional ou Kubernetes. Se você estiver usando um cluster como [Docker Swarm modo](https://docs.docker.com/engine/swarm/) (disponível no Docker CE para Windows e Mac desde a versão 1.12), você precisa implantar e testar com comandos adicionais como [criar serviço do docker](https://docs.docker.com/engine/reference/commandline/service_create/) para Serviços de único. Se você estiver implantando um aplicativo composto por vários contêineres, você usa [docker compor pacote](https://docs.docker.com/compose/reference/bundle/) e [docker implantar myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) para implantar o aplicativo composto como um *pilha*. Para obter mais informações, consulte o postagem de blog [apresentando Experimental distribuídas pacotes de aplicativos](https://blog.docker.com/2016/06/docker-app-bundle/) na documentação do Docker. no site do Docker.

Para [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) você usaria também scripts e comandos de implantação diferentes.

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a>Etapa 6. Testar seu aplicativo de Docker usando o host local do Docker

Esta etapa irá variar dependendo de seu aplicativo está fazendo. Em um aplicativo .NET Core Web simple que é implantado como um único contêiner ou um serviço, você pode acessar o serviço abrindo um navegador no host do Docker e navegar para o site, conforme mostrado na Figura 5-13. (Se a configuração no Dockerfile mapeia o contêiner para uma porta no host que é diferente de 80, incluir a postagem de host na URL).

![](./media/image18.png)

**Figura 5-13**. Exemplo de testar seu aplicativo de Docker localmente usando localhost

Se o host local não está apontando para o Docker IP de host (por padrão, ao usar o CE Docker, deveria), para navegar para o serviço, use o endereço IP da placa de rede do seu computador.

Observe que essa URL no navegador usa a porta 80 para o exemplo de contêiner específico que está sendo discutido. No entanto, internamente as solicitações estão sendo redirecionadas para a porta 5000, pois esse era como ele foi implantado com o comando docker run, conforme explicado em uma etapa anterior.

Você também pode testar o aplicativo usando a rotação de terminal, conforme mostrado na Figura 5-14. Em uma instalação de Docker no Windows, o padrão de IP do Host do Docker é sempre 10.0.75.1 conjunto de endereço IP real do seu computador.

![](./media/image19.png)

**Figura 5-14**. Exemplo de testar seu aplicativo de Docker localmente usando ondulação

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a>Testando e depurando contêineres com o Visual Studio de 2017

Quando executando e depurando contêineres com 2017 do Visual Studio, você pode depurar o aplicativo do .NET em quase da mesma forma como você faria durante a execução sem contêineres.

### <a name="testing-and-debugging-without-visual-studio"></a>Testar e depurar sem o Visual Studio

Se você estiver desenvolvendo usando a abordagem de editor/CLI, contêineres de depuração é mais difícil e você deve gerar rastreamentos de depuração.

### <a name="additional-resources"></a>Recursos adicionais

-   **Depuração de aplicativos em um contêiner de Docker local**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

-   **Steve Lasker. Compilar, depurar, implantar aplicativos do ASP.NET Core com o Docker.** Vídeo.
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a>Fluxo de trabalho simplificado ao desenvolver contêineres com o Visual Studio

Efetivamente, o fluxo de trabalho ao usar o Visual Studio é muito mais simples do que se você usar a abordagem de editor/CLI. A maioria das etapas necessárias pelo Docker relacionada ao Dockerfile e arquivos de docker compose.yml ocultos ou simplificados pelo Visual Studio, conforme mostrado na Figura 5-15.

![](./media/image20.png)

**Figura 5-15**. Fluxo de trabalho simplificado ao desenvolver com o Visual Studio

Além disso, você precisa executar a etapa 2 (Adicionar suporte de Docker para seus projetos) apenas uma vez. Portanto, o fluxo de trabalho é semelhante a suas tarefas de desenvolvimento comuns ao usar o .NET para qualquer outro desenvolvimento. Você precisa saber o que está acontecendo nos bastidores (o processo de criação de imagem, quais imagens de base que você está usando, implantação de contêineres, etc.) e, às vezes, que você também precisará editar o arquivo Dockerfile ou compose.yml docker para personalizar os comportamentos. Mas a maioria do trabalho seja bastante simplificado usando o Visual Studio, o que o torna muito mais produtivo.

### <a name="additional-resources"></a>Recursos adicionais

-   **Steve Lasker. Desenvolvimento de docker .NET com o Visual Studio de 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

-   **Jeffrey T. Fritz. Coloque um aplicativo de núcleo do .NET em um contêiner com as novas ferramentas do Docker para Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a>Usando comandos do PowerShell em um Dockerfile para configurar a contêineres do Windows 

[Contêineres do Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) permitem converter seus aplicativos existentes do Windows em imagens do Docker e implantá-los com as mesmas ferramentas que o resto do ecossistema do Docker. Para usar contêineres do Windows, execute comandos do PowerShell no Dockerfile, conforme mostrado no exemplo a seguir:

```
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

Nesse caso, estamos usando uma imagem base do Windows Server Core (a configuração de) e instalar o IIS com um comando do PowerShell (a configuração de execução). De maneira semelhante, você também pode usar comandos do PowerShell para configurar componentes adicionais como o ASP.NET 4. x, .NET 4.6 ou qualquer outro software do Windows. Por exemplo, o seguinte comando em um Dockerfile configura o ASP.NET 4.5:

```
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a>Recursos adicionais

-   **docker-ASPNET/Dockerfile.** Comandos do Powershell de exemplo para executar a partir de dockerfiles para incluir recursos do Windows.
    [*https://GitHub.com/Microsoft/ASPNET-docker/blob/Master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (... / net-core-single-containers-linux-windows-server-hosts/index.md)
