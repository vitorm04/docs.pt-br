---
title: Implantando aplicativos Web .NET Core baseados em um único contêiner em hosts do Linux ou do Windows Nano Server
description: Arquitetura de microsserviços do .NET para aplicativos do .NET em contêineres | Implantando aplicativos Web .NET Core baseados em um único contêiner em hosts do Linux ou do Windows Nano Server
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 45be99a86a52ed450b795ca5f91c01ab82c7da47
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43539693"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a>Implantando aplicativos Web .NET Core baseados em um único contêiner em hosts do Linux ou do Windows Nano Server

_Você pode usar contêineres do Docker para a implantação monolítica de aplicativos Web mais simples. Isso melhora os pipelines de integração contínua e de implantação contínua e ajuda a obter êxito na implantação de produção. Não existe mais "funciona no meu computador, por que não funciona na produção?"_

Uma arquitetura baseada em microsserviços tem muitos benefícios, mas esses benefícios são fornecidos ao custo do aumento da complexidade. Em alguns casos, os custos superam os benefícios e um aplicativo de implantação monolítico em execução em um ou mais contêineres é uma opção melhor.

Um aplicativo monolítico não pode ser facilmente decomposto em microsserviços bem separados. Você aprendeu que esses microsserviços devem ser particionados por função: eles devem funcionar independentemente uns dos outros para fornecer um aplicativo mais resiliente. Se você não puder entregar fatias de recurso do aplicativo, separá-las apenas aumentará a complexidade.

Talvez o aplicativo ainda não precise dimensionar recursos de modo independente. Vamos supor que nos estágios iniciais do aplicativo de referência `eShopOnContainers`, o tráfego não justificava a separação de recursos em microsserviços diferentes. O tráfego era tão pequeno que a adição de recursos a um serviço normalmente significava adicionar recursos a todos os serviços. O trabalho adicional para separar o aplicativo em serviços distintos fornecia o mínimo de benefício.

Além disso, no início do desenvolvimento de um aplicativo talvez você não tenha uma ideia clara de onde estão os limites funcionais naturais. Mesmo depois de desenvolve rum produto mínimo viável, a separação natural pode ainda não ter surgido.

Algumas dessas condições podem ser temporárias. Você pode começar criando um aplicativo monolítico e posteriormente separar alguns recursos para serem desenvolvidos e implantados como microsserviços. Outras condições podem ser essenciais para o espaço do problema do aplicativo, o que significa que o aplicativo pode nunca ser dividido em vários microsserviços.

A separação de um aplicativo em vários processos distintos também apresenta sobrecarga. É mais complexo separar recursos em processos diferentes. Os protocolos de comunicação tornam-se mais complexos. Em vez de chamadas de método, você deve usar a comunicação assíncrona entre serviços. Ao passar para uma arquitetura de microsserviços, você precisa adicionar muitos dos blocos de construção implementados na versão de microsserviços do aplicativo `eShopOnContainers`: a manipulação de barramento de eventos, a resiliência e novas tentativas de mensagem, a consistência eventual e muito mais.

Uma versão muito mais simplificada do eShopOnContainers (chamada [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) e incluída no mesmo repositório do GitHub) é executada como um aplicativo MVC monolítico. Conforme descrito, há vantagens oferecidas por essa opção de design. Você pode baixar o código-fonte desse aplicativo do GitHub e executá-lo localmente. Até mesmo esse aplicativo monolítico beneficia-se de ser implantado em um ambiente do contêiner.

Por exemplo, a implantação em contêineres significa que cada instância do aplicativo é executada no mesmo ambiente. Isso inclui o ambiente de desenvolvedor no qual os testes e o desenvolvimento iniciais ocorrem. A equipe de desenvolvimento pode executar o aplicativo em um ambiente em contêineres que corresponda ao ambiente de produção.

Além disso, os aplicativos em contêineres podem ser expandidos com um custo menor. Como você viu anteriormente, o ambiente de contêiner permite um compartilhamento maior de recursos do que os ambientes de VM tradicionais.

Por fim, colocar o aplicativo em contêineres força uma separação entre a lógica de negócios e o servidor de armazenamento. À medida que o aplicativo é escalado horizontalmente, os vários contêineres dependem de uma única mídia de armazenamento físico. Geralmente, esse armazenamento seria um servidor de alta disponibilidade executando um banco de dados do SQL Server.

## <a name="application-tour"></a>Tour do aplicativo

O aplicativo [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) representa uma parte do aplicativo eShopOnContainers em execução como um aplicativo monolítico, ou seja, um aplicativo baseado no ASP.NET Core MVC em execução no .NET Core. Ele fornece principalmente as funcionalidades de pesquisa no catálogo que foram descritas nas seções anteriores.

O aplicativo usa um banco de dados do SQL Server para o armazenamento de catálogo. Em implantações com base em contêiner, este aplicativo monolítico pode acessar o mesmo armazenamento de dados que o aplicativo baseado em microsserviços. O aplicativo é configurado para executar o SQL Server em um contêiner ao lado do aplicativo monolítico. Em um ambiente de produção, o SQL Server seria executado em um computador de alta disponibilidade, fora do host do Docker. Para facilitar, é recomendado executar o SQL Server em seu próprio contêiner em um ambiente de desenvolvimento ou de teste.

O conjunto inicial de recursos apenas habilita a pesquisa no catálogo. As atualizações habilitarão o conjunto completo de recursos do aplicativo em contêiner. Uma arquitetura de aplicativo Web monolítico mais avançada é descrita no livro eletrônico [ASP.NET Web Application architecture practices](https://aka.ms/webappebook) (Práticas de arquitetura do aplicativo Web ASP.NET) e no [aplicativo de exemplo eShopOnWeb](https://aka.ms/WebAppArchitecture) relacionado.

## <a name="docker-support"></a>Suporte ao Docker

O projeto eShopOnWeb é executado no .NET Core. Isso significa que ele pode ser executado em contêineres baseados em Linux ou em Windows. Observe que, para a implantação do Docker, você deseja usar o mesmo tipo de host para o SQL Server. Os contêineres baseados em Linux permitem o uso de um espaço menor e são preferenciais.

O Visual Studio fornece um modelo de projeto que adiciona o suporte ao Docker em uma solução. Clique com o botão direito do mouse no projeto, clique em **Adicionar** e, em seguida, em **Suporte ao Docker**. O modelo adiciona um Dockerfile ao projeto e um novo projeto **docker-compose** que fornece um arquivo *docker-compose.yml* inicial. Esta etapa já foi feita no projeto eShopOnWeb baixado do GitHub. Você verá que a solução contém o projeto **eShopOnWeb** e o projeto **docker-compose** conforme é mostrado na Figura 6-1.

![](./media/image1.png)

**Figura 6-1**. O projeto **docker-compose** em um aplicativo Web de contêiner único

Esses são arquivos docker-compose padrão, consistentes com qualquer projeto do Docker. Você pode usá-los com o Visual Studio ou por meio da linha de comando. Esse aplicativo é executado no .NET Core e usa contêineres do Linux. Portanto, você também pode codificar, compilar e executá-lo em um computador Mac ou Linux.

O arquivo *docker-compose.yml* contém informações de quais imagens devem ser criadas e quais contêineres devem ser iniciados. Os modelos especificam como criar a imagem `eshopweb` e iniciar os contêineres do aplicativo. Você precisa adicionar a dependência do SQL Server incluindo uma imagem para ele (por exemplo, `mssql-server-linux`) e um serviço para a imagem sql.data para que o Docker crie e inicie esse contêiner. Essas configurações são mostradas no exemplo a seguir:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

A diretiva `depends_on` mostra ao Docker que a imagem eShopWeb depende da imagem sql.data. As linhas abaixo de `depends_on` são as instruções para criar uma imagem marcada como `sql.data` usando a imagem `microsoft/mssql-server-linux`.

O projeto **docker-compose** exibe os outros arquivos docker-compose no nó *docker-compose.yml* principal para fornecer uma indicação visual de que esses arquivos estão relacionados. O arquivo *docker-compose-override.yml* contém configurações para os dois serviços, como cadeias de conexão e outras configurações de aplicativo.

O exemplo a seguir mostra o arquivo *docker-compose.vs.debug.yml*, que contém as configurações usadas para depuração no Visual Studio. Nesse arquivo, a imagem eshopweb tem a marca dev anexada. Isso ajuda a separar a depuração das imagens de versão para que você não implante acidentalmente as informações de depuração em um ambiente de produção:

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

O último arquivo adicionado é o *docker-compose.ci.build.yml*. Esse arquivo seria usado na linha de comando para criar o projeto em um servidor de CI. Esse arquivo compose inicia um contêiner do Docker que compilar as imagens necessárias para o aplicativo. O exemplo a seguir mostra o conteúdo do arquivo *docker-compose.ci.build.yml*:

```yml
version: '2'

services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

> [!NOTE]
> Começando com o SDK do .NET Core 2.0, o comando [dotnet restore](../../../core/tools/dotnet-restore.md) é executado automaticamente quando [dotnet publish](../../../core/tools/dotnet-publish.md) é executado.

Observe que a imagem é uma imagem de build do ASP.NET Core. Essa imagem inclui as ferramentas do SDK e de build para compilar seu aplicativo e criar as imagens necessárias. Executar o projeto **docker-compose** usando este arquivo inicia o contêiner de build da imagem, em seguida, compila a imagem do aplicativo nesse contêiner. É possível especificar esse arquivo *docker-compose* como parte da linha de comando para criar o aplicativo em um contêiner do Docker e, em seguida, o iniciar.

No Visual Studio, você pode executar seu aplicativo em contêineres do Docker, selecionando o projeto **docker-compose** como o projeto de inicialização e, em seguida, pressionando Ctrl + F5 (F5 para depurar), como faria com qualquer outro aplicativo. Quando você inicia o projeto **docker-compose**, o Visual Studio executa o **docker-compose** usando o arquivo *docker-compose.yml*, o arquivo *docker-compose.override.yml* e um dos arquivos docker-compose.vs\*. Depois que o aplicativo é iniciado, o Visual Studio inicia o navegador.

Se você iniciar o aplicativo no depurador, o Visual Studio será anexado ao aplicativo em execução no Docker.

## <a name="troubleshooting"></a>Solução de problemas

Esta seção descreve alguns problemas que podem surgir ao executar contêineres localmente e sugere algumas correções.

### <a name="stop-docker-containers"></a>Parar contêineres do Docker

Depois que você inicia o aplicativo em contêineres, os contêineres continuam em execução, mesmo depois de interromper a depuração. Você pode executar o comando `docker ps` da linha de comando para ver quais contêineres estão em execução. O comando `docker stop` interrompe um contêiner em execução, conforme é mostrado na Figura 6-2.

![](./media/image2.png)

**Figura 6-2**. Listando e interrompendo contêineres com os comandos da CLI docker ps e docker stop

Talvez seja necessário interromper os processos em execução ao alternar entre diferentes configurações. Caso contrário, o contêiner que está executando o aplicativo Web usará a porta do aplicativo (5106 neste exemplo).

### <a name="add-docker-to-your-projects"></a>Adicionar o Docker aos seus projetos

O assistente que adiciona o suporte ao Docker se comunica com o processo do Docker em execução. Se o Docker não estiver em execução quando você iniciar o assistente, o assistente não será executado corretamente. O assistente examinará sua opção de contêiner atual para adicionar o suporte ao Docker correto. Para adicionar suporte para contêineres do Windows, execute o assistente enquanto o Docker estiver em execução com os contêineres do Windows configurados. Para adicionar suporte para contêineres do Linux, execute o assistente enquanto o Docker estiver em execução com os contêineres do Linux configurados.

>[!div class="step-by-step"]
[Anterior](../docker-application-development-process/docker-app-development-workflow.md)
[Próximo](../containerize-net-framework-applications/index.md)
