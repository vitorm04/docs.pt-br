---
title: Fluxo de trabalho de desenvolvimento do loop interno para aplicativos de Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: cda9aa77ca033dced8b6b30538f19f28a5fa63a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579204"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Fluxo de trabalho de desenvolvimento do loop interno para aplicativos de Docker

Antes de disparar o fluxo de trabalho do loop externo abrangendo o DevOps todo o ciclo, tudo começa em cada computador de um desenvolvedor, codificar o aplicativo em si, usando seu idioma de preferência ou plataformas e testá-lo localmente (Figura 4-14). Mas em todos os casos, você terá um ponto muito importante em comum, não importa quais plataformas, idioma ou estrutura que você escolher. Nesse fluxo de trabalho específico, você sempre estiver desenvolvendo e testando contêineres do Docker, mas localmente.

![](./media/image18.png)

Figura 4-14: contexto de desenvolvimento de loop interno

O contêiner ou uma instância de uma imagem do Docker conterá esses componentes:

-   Uma seleção de sistema operacional (por exemplo, uma distribuição de Linux ou Windows)

-   Arquivos adicionados pelo desenvolvedor (por exemplo, binários de aplicativo)

-   Configuração (por exemplo, configurações de ambiente e dependências)

-   Instruções para o que processa a execução do Docker

Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como o processo (descrito na próxima seção). Leve em consideração as etapas iniciais para configurar o ambiente não é incluído, porque você precisa fazer isso apenas uma vez.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Criação de um único aplicativo em um contêiner do Docker usando o código do Visual Studio e a CLI do Docker

Aplicativos são compostos de seus próprios serviços mais bibliotecas adicionais (dependências).

Figura 4-15 mostra as etapas básicas que você geralmente precisa realizar ao compilar um aplicativo do Docker, seguido por descrições detalhadas de cada etapa.

![](./media/image19.png)

Figura 4-15: aplicativos usando a CLI do Docker em contêineres de fluxo de trabalho de alto nível para o ciclo de vida para Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Etapa 1: Iniciar a codificação no código do Visual Studio e crie a linha de base do aplicativo/serviço inicial

A maneira que você desenvolve seu aplicativo é muito semelhante à forma como você pode fazê-lo sem Docker. A diferença é que, durante o desenvolvimento, você está implantando e testando seu aplicativo ou serviços em execução dentro de contêineres do Docker colocados em seu ambiente local (como uma VM do Linux ou Windows).

**Configurando o ambiente local**

Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker e a instalação é simples.

**Obter mais informações** para obter instruções sobre como configurar o Docker para Windows, acesse [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).

Para obter instruções sobre como configurar o Docker para Mac, vá para <https://docs.docker.com/docker-for-mac/>.

Além disso, você precisará de um editor de código para que, na verdade, você pode desenvolver seu aplicativo enquanto estiver usando a CLI do Docker.

A Microsoft fornece o código do Visual Studio, que é um editor de código leve que é suportado no Linux, Mac e Windows e fornece o IntelliSense com [suporte para vários idiomas](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e mais linguagens modernas), [depuração](https://code.visualstudio.com/Docs/editor/debugging), [integração com o Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte a extensões](https://code.visualstudio.com/docs/extensions/overview). Este editor é ideal para desenvolvedores de Mac e Linux. No Windows, você também pode usar o aplicativo do Visual Studio completo.

**Obter mais informações** para obter instruções sobre como instalar o Visual Studio para Windows, Mac ou Linux, acesse [ http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/ ](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).

Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de códigos, mas se você usar o código do Visual Studio, faz a autor Dockerfile e arquivos de docker compose.yml no espaço de trabalho. Além disso, você pode executar tarefas de código do Visual Studio do IDE que solicitará scripts que podem executar operações elaboradas usando a CLI do Docker abaixo.

Código do Visual Studio é fornecido por uma extensão, o que você precisará instalar. Para fazer isso, pressione Ctrl + Shift + P, digite **ext instalar**, e, em seguida, executar as extensões: comando de extensão de instalação para exibir a lista de extensão do Marketplace. Em seguida, digite **docker** para filtrar os resultados e, em seguida, selecione o Dockerfile e compor Dockerfile (yml) extensão de suporte, conforme ilustrado na Figura 4-16.

![](./media/image20.png)

Figura 4-16: instalar a extensão de Docker no código do Visual Studio

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Etapa 2: Criar um DockerFile relacionado a uma imagem existente (SO simples ou ambientes de desenvolvimento como o núcleo do .NET, Node.js e Ruby)

Você precisará de um DockerFile por uma imagem personalizada a ser criado e por contêiner a ser implantado, portanto, se seu aplicativo é composto de um único serviço personalizado, será necessário um DockerFile único. Mas, se seu aplicativo é composto de vários serviços (como em uma arquitetura microservices), você precisará de um Dockerfile por serviço.

O DockerFile é posicionado dentro da pasta raiz do seu aplicativo ou serviço e contém os comandos necessários para que Docker Saiba como configurar e executar esse aplicativo ou serviço. Você pode criar o DockerFile e adicioná-lo ao seu projeto junto com seu código (Node. js, .NET Core, etc.), ou, se você estiver familiarizado com o ambiente, examine a seguinte dica.

> [!TIP]
> Você pode usar uma ferramenta de linha de comando chamada [de docker](https://github.com/Microsoft/generator-docker), qual scaffolds arquivos do seu projeto no idioma que você escolhe e adiciona os arquivos de configuração necessários do Docker. Basicamente, para ajudar os desenvolvedores de Introdução, ele cria o DockerFile apropriado, docker compose.yml e outros scripts associados para compilar e executar seus contêineres do Docker. Esse gerador yeoman solicitará a algumas perguntas, solicitando que o host do contêiner selecionado desenvolvimento idioma e de destino.

![de docker](./media/image21.png)

Por exemplo, a Figura 4-17 mostra duas capturas de tela dos terminais no Windows e em um Mac, ambos os casos, execução de docker, o que irá gerar os código projetos de exemplo (atualmente .NET Core, Golang e Node. js como idiomas com suporte) já está configurados para funcionar em parte superior do Docker.

![](./media/image22.PNG)  ![](./media/image23.png)

Figura 4-17: de docker ferramenta de comando no Windows (esquerdo) e em um Mac

Figura 4-18 apresenta um exemplo de uso de docker depois de ter um projeto existente do .NET Core em vigor para ser Scaffold.

![](./media/image24.PNG)

Figura 4-18: de docker com um .NET Core existente do projeto no local

Do DockerFile, você deve especificar quais imagem base do Docker, você vai usar (como usando "de microsoft/dotnet:1.0.0-core"). Você geralmente criará sua imagem personalizada na parte superior de uma imagem de base que pode ser de qualquer repositório oficial no [registro do Hub do Docker](https://hub.docker.com/) (como um [imagem para .NET Core](https://hub.docker.com/r/microsoft/dotnet/) ou um [para Node.js](https://hub.docker.com/_/node/)).

***R: a opção Usar uma imagem de Docker oficial existente***

Usar um repositório oficial de uma pilha de idioma com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo o desenvolvimento, teste e produção).

A seguir está um exemplo DockerFile para um contêiner de núcleo do .NET:

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

Nesse caso, ele está usando a versão 1.0.1 da imagem do ASP.NET Core Docker oficial para Linux denominada microsoft/aspnetcore:1.0.1. Para obter detalhes, consulte o [página de imagem do ASP.NET Core Docker](https://hub.docker.com/r/microsoft/aspnetcore/) e [página de imagem do Docker .NET Core](https://hub.docker.com/r/microsoft/dotnet/). Você também pode usar outra imagem comparável como nó: 4-onbuild para Node.js ou muitas outras imagens pré-configuradas para linguagens de desenvolvimento que estão disponíveis em [Hub do Docker](https://hub.docker.com/explore/).

No DockerFile, você também precisa instruem o Docker para escutar na porta TCP que você usará em tempo de execução (como a porta 80).

Há outras linhas de configuração que você pode adicionar o DockerFile dependendo da linguagem/estrutura que você está usando, para que Docker Saiba como executar o aplicativo. Por exemplo, é necessário que a linha do ponto de entrada com \["dotnet", "MyCustomMicroservice.dll"\] para executar um aplicativo .NET Core, embora você possa ter várias variantes dependendo da abordagem para compilar e executar seu serviço. Se você estiver usando o SDK e dotnet CLI para compilar e executar o aplicativo .NET, poderá ser ligeiramente diferente. O resultado final é que a linha do ponto de entrada mais linhas adicionais serão diferentes dependendo da linguagem/plataforma que você escolhe para seu aplicativo.

**Obter mais informações** para obter informações sobre como criar imagens do Docker para aplicativos .NET Core, vá para <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.

Para saber mais sobre como criar suas próprias imagens, vá para [ https://docs.docker.com/engine/\tutoriais/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).

**Repositórios de imagens em várias plataformas**

Conforme os contêineres do Windows se tornam mais frequente, um único repositório pode conter variantes de plataforma, como uma imagem do Linux e Windows. Este é um novo recurso disponível no Docker que torna possível usar um único repositório para abranger várias plataformas, como fornecedores de [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repositório, que está disponível no registro de DockerHub. Como o recurso é ativado, recebendo essa imagem de um host Windows efetuará o pull a variante do Windows, enquanto recebendo o mesmo nome da imagem de um host Linux obterá a variante de Linux.

***Opção b: criar a imagem base do zero***

Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker. Este é um cenário que provavelmente não é melhor para você se você estiver apenas começando com o Docker, mas se você deseja definir os bits específicos de sua própria imagem base, você pode fazê-lo.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Etapa 3: Criar as imagens do Docker personalizadas inserindo seu serviço nele

Para cada serviço personalizado que consiste em seu aplicativo, você precisará criar uma imagem de relacionados. Se seu aplicativo é composto de um único serviço ou aplicativo web, você precisará apenas uma única imagem.

> [!NOTE]
> Ao levar em consideração o "loop externo DevOps fluxo de trabalho", as imagens serão criadas por um processo de compilação automatizado sempre que você enviar seu código-fonte para um repositório Git (integração contínua) para que as imagens serão criadas no ambiente global do seu código-fonte.

Mas, antes de considerarmos indo para essa rota de loop externo, precisamos garantir que o aplicativo do Docker está funcionando corretamente para que eles não enviar por push o código que pode não funcionar corretamente para o sistema de controle do código-fonte (Git, etc.).

Portanto, cada desenvolvedor deve primeiro fazer todo o processo de loop interno para testar localmente e continuar a desenvolver até que deseja enviar por push a um recurso completo ou altere para o sistema de controle de origem.

Para criar uma imagem em seu ambiente local e usando o DockerFile, você pode usar o comando de build do docker, conforme mostrado na Figura 4-19 (você também pode executar compor docker backup – criar aplicativos compostos por vários contêineres/serviços).

![](./media/image25.png)

Figura 4-19: executando o build do docker

Opcionalmente, em vez de executar o docker build da pasta do projeto, você primeiro pode gerar uma pasta de implantação com as bibliotecas .NET necessárias usando a execução dotnet publicar o comando e, em seguida, execute o build do docker.

Neste exemplo, isso cria uma imagem do Docker com o nome cesardl/netcore-webapi-microsserviço-docker: primeiro (: primeiro, é uma marca, como uma versão específica). Você pode adotar essa etapa para cada imagem personalizada, que você precisa criar seu aplicativo Docker composto com vários contêineres.

Você pode encontrar as imagens existentes no seu repositório local (computador de desenvolvimento) usando o docker imagens comando, conforme ilustrado na Figura 4-20.

![](./media/image26.png)

Figura 4-20: exibindo imagens existentes usando imagens do docker

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Etapa 4: (Opcional) definir seus serviços no docker-compose.yml ao compilar um aplicativo de Docker composto com vários serviços

Com o arquivo de docker compose.yml, você pode definir um conjunto de serviços relacionados a ser implantado como um aplicativo composto com os comandos de implantação explicados na seção próxima etapa.

Você precisa criar esse arquivo em seu principal ou a pasta de solução raiz; ele deve ter um conteúdo semelhante ao arquivo de docker compose.yml a seguir:

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

Nesse caso específico, esse arquivo define dois serviços: o serviço da web (o personalizado) e o serviço de redis (um serviço de cache populares). Cada serviço será implantado como um contêiner, portanto, precisamos usar uma imagem de Docker concreta para cada. Para este serviço web específico, a imagem será necessário fazer o seguinte:

-   Compilação do DockerFile no diretório atual

-   Encaminhar a exposto a porta 80 no contêiner para a porta 81 no computador host

-   Montar o diretório do projeto no host para /code dentro do contêiner, tornando possível para modificar o código sem precisar recriar a imagem

-   Vincular o serviço web para o serviço de redis

O serviço de redis usa o [imagem pública redis mais recente](https://hub.docker.com/_/redis/) extraída do registro do Hub do Docker. [redis](https://redis.io/) é um sistema de cache muito popular para aplicativos do lado do servidor.

### <a name="step-5-build-and-run-your-docker-app"></a>Etapa 5: Criar e executar seu aplicativo de Docker

Se seu aplicativo tiver apenas um único contêiner, basta executá-lo, implantando-a para o Host do Docker (VM ou servidor físico). No entanto, se seu aplicativo é composto de vários serviços, você precisa *compô-la*também. Vamos ver as diferentes opções.

***Opção de execução de r: um único contêiner ou serviço***

Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

Observe que para essa implantação específica, vai redirecionar as solicitações enviadas para a porta 80 para a porta interna 5000. Agora, o aplicativo está escutando na porta 80 no nível do host externa.

***Opção b: compor e executar um aplicativo de contêiner de vários***

Na maioria dos cenários de empresa, um aplicativo de Docker será ser composto de vários serviços. Nesses casos, você pode executar o comando docker-compor para cima (Figura 4-21), que usará o arquivo de docker compose.yml que talvez você tenha criado anteriormente. A execução desse comando implanta um aplicativo composto com todos os seus contêineres relacionados.

![](./media/image27.png)

Figura 4-21: resultados da execução do comando "docker-compor a"

Após a execução do docker-compor backup, você implantar seu aplicativo e seus contêineres relacionados em seu Host do Docker, conforme ilustrado na Figura 4-22, a representação de VM.

![](./media/image28.png)

Figura 4-22: VM com contêineres do Docker implantado

Observação compor docker backup e docker executar pode ser suficiente para os contêineres de teste em seu ambiente de desenvolvimento, mas você talvez não usá-los em todos os se você está esperando trabalhar com clusters de Docker e orchestrators como Docker Swarm, Mesosphere DC/sistema operacional ou Kubernetes para poder dimensionar. Se você estiver usando um cluster como [Docker Swarm modo](https://docs.docker.com/engine/swarm/) (disponível no Docker para Windows e Mac desde a versão 1.12), você precisa implantar e testar com comandos adicionais, como criar serviço do docker para serviços únicos ou quando estiver Implantando um aplicativo composto por vários contêineres, usando o docker compõem o pacote e implantar o docker myBundleFile, ao implantar o aplicativo composto como uma pilha, conforme explicado no artigo [pacotes de aplicativos distribuídos](https://blog.docker.com/2016/06/docker-app-bundle/) do Docker.

Para [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) e [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) você usaria comandos de implantação diferentes e scripts, também.

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Etapa 6: Testar seu aplicativo de Docker (localmente, em sua VM local do CD)

Esta etapa irá variar dependendo de seu aplicativo está funcionando.

Uma muito simple .NET Core API da Web "Olá, mundo" implantado como um único contêiner ou um serviço, você apenas precisa acessar o serviço, fornecendo a porta TCP especificada no DockerFile.

Se o host local não está ativado, para navegar até o seu serviço, localize o endereço IP para a máquina usando este comando:

ip de máquinas de docker *seu nome de contêiner*

No host do Docker, abra um navegador e navegue para o site; Você deve ver o aplicativo/serviço em execução, conforme mostrado na Figura 4-23.

![](./media/image29.png)

Figura 4-23: testar seu aplicativo de Docker localmente usando localhost

Observe que ele está usando a porta 80, mas internamente ele estava sendo redirecionado para porta 5000, pois é como ele foi implantado com docker run, conforme explicado anteriormente.

Você pode testar isso, usando a ROTAÇÃO de terminal. Em uma instalação de Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-24.

![](./media/image30.png)

Figura 4-24: Testando um aplicativo de Docker localmente usando ONDULAÇÃO

**Depuração de um contêiner em execução no Docker**

Código do Visual Studio oferece suporte à depuração Docker se você estiver usando o Node. js e outras plataformas como contêineres de núcleo do .NET.

Você também pode depurar recipientes de núcleo do .NET do Docker ao usar o Visual Studio, conforme descrito na próxima seção.

**Obter mais informações:** para saber mais sobre a depuração de contêineres do Docker Node. js, vá para <https://blog.docker.com/2016/07/live-debugging-docker/> e [ https://blogs.msdn.microsoft.com/\ usuário\_ed/2016/02/27 / Visual-Studio-Code-New-Features-13-big-Debugging-Updates-Rich-Object-hover-Conditional-Breakpoints-Node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).


>[!div class="step-by-step"]
[Anterior] (docker-aplicativos-desenvolvimento-environment.md) [Avançar] (visual-studio-ferramentas-para-docker.md)
