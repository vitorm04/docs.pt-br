---
title: Fluxo de trabalho de desenvolvimento de loop interno para aplicativos do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: be9c3fe165be32df43073919904b85120c52d595
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50034443"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Fluxo de trabalho de desenvolvimento de loop interno para aplicativos do Docker

Antes de disparar o fluxo de trabalho de loop externo que abrangem o DevOps todo ciclo, tudo começa em cada computador de desenvolvedor, codificando o aplicativo em si, usando seus idiomas preferenciais ou plataformas e testá-lo localmente (Figura 4 a 14). Mas, em todos os casos, você terá um ponto muito importante em comum, não importa qual linguagem, estrutura ou plataformas você escolher. Nesse fluxo de trabalho específico, você sempre estiver desenvolvendo e testando contêineres do Docker, mas localmente.

![](./media/image18.png)

Figura 4 a 14: contexto de desenvolvimento de loop interno

O contêiner ou uma instância de uma imagem de Docker conterá esses componentes:

-   Uma seleção do sistema operacional (por exemplo, uma distribuição Linux ou Windows)

-   Arquivos adicionados pelo desenvolvedor (por exemplo, binários de aplicativo)

-   Configuração (por exemplo, as configurações de ambiente e dependências)

-   Instruções para quais processos para ser executado pelo Docker

Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como o processo (descrito na próxima seção). Leve em consideração que as etapas iniciais para configurar o ambiente não está incluída, pois você precisa fazer isso apenas uma vez.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Criação de um único aplicativo dentro de um contêiner do Docker usando o Visual Studio Code e CLI do Docker

Aplicativos são compostos de seus próprios serviços e bibliotecas adicionais (dependências).

Figura 4-15 mostra as etapas básicas que você normalmente precisará realizar ao compilar um aplicativo do Docker, seguido por descrições detalhadas de cada etapa.

![](./media/image19.png)

Figura 4-15: aplicativos usando a CLI do Docker em contêineres de fluxo de trabalho de alto nível para o ciclo de vida para o Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Etapa 1: Iniciar a codificação no Visual Studio Code e criar a linha de base inicial/serviço de aplicativo

A maneira que você desenvolve seu aplicativo é muito semelhante à forma como você pode fazê-lo sem o Docker. A diferença é que, durante o desenvolvimento, você está implantando e testando o aplicativo ou serviços em execução em contêineres do Docker colocados no seu ambiente local (como uma VM do Linux ou Windows).

**Como configurar seu ambiente local**

Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker e a instalação é simples.

**Obter mais informações** para obter instruções sobre como configurar o Docker para Windows, acesse [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).

Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.

Além disso, será necessário um editor de código, de modo que, na verdade, você pode desenvolver seu aplicativo enquanto estiver usando a CLI do Docker.

A Microsoft fornece o Visual Studio Code, que é um editor de código leve que tem suporte no Mac, Windows e Linux e fornece o IntelliSense com [suporte para várias linguagens](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e mais linguagens modernas), [depurando](https://code.visualstudio.com/Docs/editor/debugging), [integração com o Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte a extensões](https://code.visualstudio.com/docs/extensions/overview). Esse editor é uma excelente opção para os desenvolvedores do Mac e Linux. No Windows, você também pode usar o aplicativo completo do Visual Studio.

**Obter mais informações** para obter instruções sobre como instalar o Visual Studio para Windows, Mac ou Linux, vá para <https://code.visualstudio.com/docs/setup/setup-overview/>.

Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de código, mas se você usar o Visual Studio Code, faz a autor Dockerfile e docker-Compose. yml arquivos em seu espaço de trabalho. Além disso, você pode executar tarefas do Visual Studio Code do IDE que solicitará que os scripts que podem executar operações elaboradas usando a CLI do Docker abaixo.

Visual Studio Code é fornecido por uma extensão, que você precisará instalar. Para fazer isso, pressione Ctrl + Shift + P, digite **ext instalar**, e, em seguida, executar as extensões: comando Instalar extensão para abrir a lista de extensões do Marketplace. Em seguida, digite **docker** para filtrar os resultados e, em seguida, selecione o Dockerfile e Docker Compose arquivo (yml) a extensão de suporte, conforme ilustrado na Figura 4 a 16.

![](./media/image20.png)

Figura 4 a 16: instalar a extensão do Docker no Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Etapa 2: Criar um DockerFile relacionado a uma imagem existente (sem formatação do sistema operacional ou ambientes de desenvolvimento, como Ruby, Node. js e .NET Core)

Você precisará de um DockerFile por uma imagem personalizada a ser criado e por contêiner a serem implantados, portanto, se seu aplicativo é composto por um único serviço personalizado, será necessário um único DockerFile. Mas, se seu aplicativo é composto de vários serviços (como em uma arquitetura de microsserviços), será necessário um Dockerfile por serviço.

O DockerFile normalmente é colocado dentro da pasta raiz do seu aplicativo ou serviço e contém os comandos necessários para que o Docker Saiba como configurar e executar esse aplicativo ou serviço. Você pode criar seu DockerFile e adicioná-lo ao seu projeto, juntamente com seu código (Node. js, .NET Core, etc.), ou, se você for novo no ambiente, examine a seguinte dica.

> [!TIP]
> Você pode usar uma ferramenta de linha de comando chamada [yo docker](https://github.com/Microsoft/generator-docker), que usa o Scaffold de arquivos do seu projeto no idioma que você escolha e adiciona os arquivos de configuração necessários do Docker. Basicamente, para ajudar os desenvolvedores de Introdução, ele cria o DockerFile apropriado, docker-Compose. yml e outros scripts associados para compilar e executar seus contêineres do Docker. Esse gerador yeoman solicitará que você com algumas perguntas, solicitando que o host do contêiner selecionado desenvolvimento idioma e de destino.

![yo docker](./media/image21.png)

Por exemplo, a Figura 4-17 mostra duas capturas de tela dos terminais de, no Windows e no Mac, em ambos os casos, executando yo docker, que irá gerar os código projetos de exemplo (atualmente, o .NET Core, Golang e Node. js como idiomas com suporte) já está configurados para funcionar em parte superior do Docker.

![](./media/image22.PNG)  ![](./media/image23.png)

Figura 4-17: yo docker ferramenta de comando no Windows (esquerda) e em um Mac

Figura 4-18 apresenta um exemplo usando yo docker depois que você tiver um projeto existente do .NET Core em vigor para ser gerado automaticamente.

![](./media/image24.PNG)

Figura 4-18: yo docker com um existentes do .NET Core de projeto em vigor

O DockerFile, você especifica qual imagem base do Docker, você vai usar (como usando "de microsoft/dotnet:1.0.0-core"). Normalmente, você irá criar sua imagem personalizada na parte superior de uma imagem de base que pode ser de qualquer repositório oficial na [registro de Hub do Docker](https://hub.docker.com/) (como um [imagem para o .NET Core](https://hub.docker.com/r/microsoft/dotnet/) ou um [para Node. js](https://hub.docker.com/_/node/)).

***Opção de r: Use uma imagem de Docker oficial existente***

Usando um repositório oficial de uma pilha de idiomas com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).

A seguir está um exemplo de DockerFile para um contêiner do .NET Core:

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Nesse caso, ele está usando a versão 1.0.1 da imagem oficial do docker do ASP.NET Core para Linux denominado microsoft/aspnetcore:1.0.1. Para obter mais detalhes, consulte o [página de imagem do Docker do ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) e o [página de imagem do Docker do .NET Core](https://hub.docker.com/r/microsoft/dotnet/). Você também pode usar outra imagem comparável, como o nó: 4-onbuild para Node. js ou muitas outras imagens pré-configuradas para linguagens de desenvolvimento, estão disponíveis em [Hub do Docker](https://hub.docker.com/explore/).

No DockerFile, você também precisará instruir o Docker a escutar na porta TCP que você usará em tempo de execução (como a porta 80).

Há outras linhas de configuração que podem ser adicionados no DockerFile, dependendo da linguagem/estrutura que você está usando, para que o Docker Saiba como executar o aplicativo. Por exemplo, você precisa que a linha ENTRYPOINT, com \["dotnet", "MyCustomMicroservice.dll"\] para executar um aplicativo .NET Core, embora você possa ter várias variantes dependendo da abordagem para compilar e executar seu serviço. Se você estiver usando o SDK e a CLI do dotnet para compilar e executar o aplicativo .NET, ele seria um pouco diferente. O resultado final é que a linha ENTRYPOINT mais linhas adicionais serão diferentes dependendo da linguagem/plataforma escolhidas para seu aplicativo.

**Obter mais informações** para obter informações sobre a criação de imagens do Docker para aplicativos .NET Core, acesse <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.

Para saber mais sobre como criar suas próprias imagens, acesse [ https://docs.docker.com/engine/\ tutoriais/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Repositórios de imagens de várias plataformas**

Como contêineres do Windows mais usado ultimamente, um único repositório pode conter variantes de plataforma, como uma imagem do Linux e Windows. Isso é um novo recurso do Docker que torna possível usar um único repositório para abranger várias plataformas, como os fornecedores [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repositório, que está disponível no registro do DockerHub. Como o recurso se torna ativo, extraindo essa imagem de um host Windows efetuará pull a variante do Windows, enquanto recebendo o mesmo nome de imagem de um host Linux efetuará o pull da variante do Linux.

***Opção b: criar sua imagem base do zero***

Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker. Esse é um cenário que provavelmente não é melhor para você se você estiver apenas começando com o Docker, mas se você quiser definir as partes específicas de sua própria imagem base, você pode fazê-lo.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Etapa 3: Criar imagens personalizadas do Docker inserindo seu serviço nele

Para cada serviço personalizado que consiste em seu aplicativo, você precisará criar uma imagem relacionada. Se seu aplicativo é composto por um único serviço ou aplicativo web, você precisará apenas uma única imagem.

> [!NOTE]
> Ao levar em consideração o "loop externo DevOps fluxo de trabalho", as imagens serão criadas por um processo automatizado de compilação sempre que você enviar por push seu código-fonte para um repositório Git (integração contínua) para que as imagens serão criadas no ambiente global do seu código-fonte.

Mas, antes de considerarmos indo para aquela rota de loop externo, precisamos garantir que o aplicativo do Docker está funcionando corretamente, de modo que eles não envie por push o código que pode não funcionar corretamente para o sistema de controle do código-fonte (Git, etc.).

Portanto, cada desenvolvedor precisa primeiro fazer todo o processo de loop interno para testar localmente e continuar a desenvolver até que eles querem enviar por push a um recurso completo ou altere para o sistema de controle do código-fonte.

Para criar uma imagem no seu ambiente local e usando o DockerFile, você pode usar o comando docker build, conforme demonstrado na Figura 4-19 (você também pode executar docker-compose up-- compilar para aplicativos compostos por vários contêineres/serviços).

![](./media/image25.png)

Figura 4-19: executar build do docker

Opcionalmente, em vez de executar diretamente o docker build na pasta do projeto, você primeiro pode gerar uma pasta implantável com as bibliotecas .NET necessárias usando a execução do dotnet publicar comando e, em seguida, executar build do docker.

Neste exemplo, isso cria uma imagem do Docker com o nome cesardl/netcore-webapi-microsserviço-docker: first (: first é uma marcação, como uma versão específica). Você pode executar esta etapa para cada imagem personalizada, que você precisará criar seu aplicativo composto do Docker com vários contêineres.

Você pode encontrar imagens existentes no seu repositório local (computador de desenvolvimento) usando o docker imagens comando, conforme ilustrado na Figura 4 a 20.

![](./media/image26.png)

Figura 4 a 20: exibindo imagens existentes usando imagens do docker

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Etapa 4: (Opcional) definir seus serviços no docker-Compose. yml ao compilar um aplicativo composto do Docker com vários serviços

Com o arquivo docker-Compose. yml, você pode definir um conjunto de serviços relacionados para ser implantado como um aplicativo composto com os comandos de implantação, explicados na seção próxima etapa.

Você precisa criar esse arquivo em seu principal ou a pasta raiz da solução; ele deve ter um conteúdo semelhante ao seguinte arquivo docker-Compose. yml:

```yml
version: '2'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

Nesse caso específico, esse arquivo define dois serviços: o serviço web (seu serviço personalizado) e o serviço de redis (um serviço de cache populares). Cada serviço será implantado como um contêiner, portanto, precisamos usar uma imagem do Docker concreta para cada um. Para este serviço da web específica, a imagem será necessário fazer o seguinte:

-   Build do DockerFile no diretório atual

-   Encaminhar a porta 80 no contêiner para a porta 81 no computador host, exposta

-   Montar o diretório do projeto no host para /code dentro do contêiner, possibilitando que você pode modificar o código sem ter que recompilar a imagem

-   Vincular o serviço web para o serviço de redis

O serviço do redis usa o [imagem mais recente do redis público](https://hub.docker.com/_/redis/) extraído do registro de Hub do Docker. [redis](https://redis.io/) é um sistema de cache muito popular para aplicativos do lado do servidor.

### <a name="step-5-build-and-run-your-docker-app"></a>Etapa 5: Compilar e executar seu aplicativo do Docker

Se seu aplicativo tem apenas um único contêiner, basta executá-lo Implantando-o em seu Host do Docker (VM ou servidor físico). No entanto, se seu aplicativo é composto por vários serviços, você precisará *compô-la*também. Vamos ver as diferentes opções.

***Opção de execução de r: um único contêiner ou serviço***

Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Observe que, para essa implantação específica, podemos vai ser redirecionar as solicitações enviadas para a porta 80 para a porta interna 5000. Agora, o aplicativo está escutando na porta 80 no nível do host externa.

***Opção b: compor e executar um aplicativo de vários contêineres***

Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços. Nesses casos, você pode executar o comando docker-compose para cima (Figura 4-21), que usará o arquivo docker-Compose. yml que talvez você tenha criado anteriormente. Executar esse comando implanta um aplicativo composto com todos os seus contêineres relacionados.

![](./media/image27.png)

Figura 4-21: resultados da execução do comando "docker-compose up"

Depois de executar docker-compose, você implantar seu aplicativo e seus contêineres relacionados no Host do Docker, conforme ilustrado na Figura 4-22, na representação de VM.

![](./media/image28.png)

Figura 4-22: VM com contêineres do Docker implantados

Observação docker-compose e execução do docker pode ser suficiente para testar seus contêineres em seu ambiente de desenvolvimento, mas você talvez não usá-los em todos os se você está esperando trabalhar com clusters do Docker e orquestradores como Kubernetes, Mesosphere DC/SO ou Docker Swarm para poder escalar verticalmente. Se você estiver usando um cluster, como [modo Docker Swarm](https://docs.docker.com/engine/swarm/) (disponível no Docker para Windows e Mac desde a versão 1.12), você precisa implantar e testar com comandos adicionais, como o serviço docker criar para serviços únicos ou quando você estiver implantar um aplicativo composto de vários contêineres, usando o docker compose bundle e implantar o docker myBundleFile, implantando o aplicativo composto como uma pilha, conforme explicado no artigo [pacotes de aplicativos distribuídos](https://blog.docker.com/2016/06/docker-app-bundle/) do Docker.

Para [DC/SO](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) você usaria também scripts e comandos de implantação diferentes.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Etapa 6: Testar seu aplicativo do Docker (localmente, em sua VM local do CD)

Esta etapa irá variar dependendo de seu aplicativo está funcionando.

Uma .NET Core da Web muito simples "Hello World" implantado como um único contêiner ou serviço de API, você apenas precisará acessar o serviço, fornecendo a porta TCP especificada no DockerFile.

Se o host local não está ativado, para navegar até seu serviço, localize o endereço IP para a máquina usando este comando:

ip do computador docker *seu nome de contêiner*

No host do Docker, abra um navegador e navegue até o site; Você deve ver seu aplicativo ou serviço em execução, conforme demonstrado na Figura 4 a 23.

![](./media/image29.png)

Figura 4 a 23: Testando seu aplicativo do Docker localmente usando localhost

Observe que ele está usando a porta 80, mas internamente estava sendo redirecionado para a porta 5000, pois é como ele foi implantado com docker run, conforme explicado anteriormente.

Você pode testar isso usando o CURL no terminal. Em uma instalação do Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-24.

![](./media/image30.png)

Figura 4-24: Testando um aplicativo do Docker localmente usando CURL

**Depuração de um contêiner em execução no Docker**

Visual Studio Code dá suporte à depuração Docker se você estiver usando o Node. js e outras plataformas como contêineres do .NET Core.

Você também pode depurar contêineres do .NET Core no Docker ao usar o Visual Studio, conforme descrito na próxima seção.

**Obter mais informações:** para saber mais sobre a depuração de contêineres do Docker do Node. js, acesse <https://blog.docker.com/2016/07/live-debugging-docker/> e [ https://blogs.msdn.microsoft.com/\ usuário\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-Node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).


>[!div class="step-by-step"]
[Anterior](docker-apps-development-environment.md)
[Próximo](visual-studio-tools-for-docker.md)
