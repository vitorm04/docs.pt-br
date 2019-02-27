---
title: Fluxo de trabalho de desenvolvimento de loop interno para aplicativos do Docker
description: Aprenda o fluxo de trabalho de "loop interno" para o desenvolvimento de aplicativos do Docker.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1134ff439235609db840c85a1e67bc9fe4ccec84
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835675"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Fluxo de trabalho de desenvolvimento de loop interno para aplicativos do Docker

Antes de disparar o fluxo de trabalho de loop externo que abrangem o DevOps todo ciclo, tudo começa em cada computador de desenvolvedor, codificando o aplicativo em si, usando seus idiomas preferenciais ou plataformas e testá-lo localmente (Figura 4-21). Mas, em todos os casos, você terá um ponto importante em comum, não importa qual linguagem, estrutura ou plataformas você escolher. Nesse fluxo de trabalho específico, você sempre estiver desenvolvendo e testando contêineres do Docker, mas localmente.

![Etapa 1 - código/execução/depuração](./media/image18.png)

**Figura 4-21**. Contexto de desenvolvimento de loop interno

O contêiner ou uma instância de uma imagem de Docker conterá esses componentes:

-   Uma seleção do sistema operacional (por exemplo, uma distribuição Linux ou Windows)

- Arquivos adicionados pelo desenvolvedor (por exemplo, binários de aplicativo)

-   Configuração (por exemplo, as configurações de ambiente e dependências)

- Instruções para quais processos para ser executado pelo Docker

Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como o processo (descrito na próxima seção). Considere as etapas iniciais para configurar o ambiente não são incluídas, porque você só precisa fazê-lo uma vez.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Criação de um único aplicativo dentro de um contêiner do Docker usando o Visual Studio Code e CLI do Docker

Aplicativos são compostos de seus próprios serviços e bibliotecas adicionais (dependências).

Figura 4-22 mostra as etapas básicas que você normalmente precisará realizar ao compilar um aplicativo do Docker, seguido por descrições detalhadas de cada etapa.

![Visão geral do fluxo de trabalho: Etapa 1: código, etapa 2 - escrever Dockerfiles, etapa 3 - criar imagens definidas com Dockerfiles, etapa 4 – definir serviços com o arquivo docker-Compose, etapa 5: executar contêineres ou aplicativos compostos, etapa 6 - teste de aplicativos, etapa 7 – enviar por Push para iniciar o loop externo (pipelines de CI/CD) ou continuar de veloping.](./media/image19.png)

**Figura 4-22**. Fluxo de trabalho de alto nível para o ciclo de vida de aplicativos do Docker em contêineres usando a CLI do Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Etapa 1: Iniciar a codificação no Visual Studio Code e crie sua linha de base inicial/serviço de aplicativo

A maneira de desenvolver seu aplicativo é semelhante à forma como você pode fazê-lo sem o Docker. A diferença é que, durante o desenvolvimento, você está implantando e testando o aplicativo ou serviços em execução em contêineres do Docker colocados no seu ambiente local (como uma VM do Linux ou Windows).

**Como configurar seu ambiente local**

Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca para desenvolver aplicativos do Docker e a instalação é simples.

> [! INFORMAÇÕES]
>
> Para obter instruções sobre como configurar o Docker para Windows, acesse <https://docs.docker.com/docker-for-windows/>.
>
>Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.

Além disso, será necessário um editor de código, de modo que, na verdade, você pode desenvolver seu aplicativo enquanto estiver usando a CLI do Docker.

A Microsoft fornece o Visual Studio Code, que é um editor de código leve que tem suporte no Mac, Windows e Linux e fornece o IntelliSense com [suporte para várias linguagens](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e mais linguagens modernas), [depurando](https://code.visualstudio.com/Docs/editor/debugging), [integração com o Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte a extensões](https://code.visualstudio.com/docs/extensions/overview). Esse editor é uma excelente opção para os desenvolvedores do Mac e Linux. No Windows, você também pode usar o aplicativo completo do Visual Studio.

> [! INFORMAÇÕES]
>
> Para obter instruções sobre como instalar o Visual Studio código para Windows, Mac ou Linux, vá para <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.

Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de código, mas usando o Visual Studio Code com a extensão Docker torna mais fácil para o autor `Dockerfile` e `docker-compose.yml` arquivos em seu espaço de trabalho. Você também pode executar tarefas e scripts do IDE do Visual Studio código para executar comandos do Docker usando a CLI do Docker abaixo.

A extensão do Docker para VS Code fornece os seguintes recursos:

- Automática `Dockerfile` e `docker-compose.yml` geração de arquivo

- Dicas de sintaxe realce e passe o mouse para `docker-compose.yml` e `Dockerfile` arquivos

- IntelliSense (preenchimentos) para `Dockerfile` e `docker-compose.yml` arquivos

- Linting (erros e avisos) para `Dockerfile` arquivos

- Integração de paleta (F1) para os comandos mais comuns do Docker de comando

- Integração com o Gerenciador para gerenciar imagens e contêineres

- Implantar imagens do DockerHub e registros de contêiner do Azure para o serviço de aplicativo do Azure

Para instalar a extensão do Docker, pressione Ctrl + Shift + P, digite `ext install`, e, em seguida, execute o comando de extensão de instalação para abrir a lista de extensões do Marketplace. Em seguida, digite **docker** para filtrar os resultados e, em seguida, selecione a extensão de suporte do Docker, conforme ilustrado na Figura 4 a 23.

![Modo de exibição da extensão do Docker para VS Code.](./media/image20.png)

**Figura 4-23**. Instalando a extensão do Docker no Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Etapa 2: Criar um DockerFile relacionado a uma imagem existente (sem formatação do sistema operacional ou ambientes de desenvolvimento, como Ruby, Node. js e .NET Core)

Você precisará de um `DockerFile` por uma imagem personalizada a ser criado e por contêiner a ser implantado. Se seu aplicativo é composto por um único serviço personalizado, será necessário um único `DockerFile`. Mas se seu aplicativo é composto de vários serviços (como em uma arquitetura de microsserviços), você precisará de uma `Dockerfile` por serviço.

O `DockerFile` normalmente é colocado na pasta raiz do seu aplicativo ou serviço e contém os comandos necessários para que o Docker Saiba como configurar e executar esse aplicativo ou serviço. Você pode criar seu `DockerFile` e adicioná-lo ao seu projeto, juntamente com seu código (Node. js, .NET Core, etc.), ou, se você for novo no ambiente, examine a seguinte dica.

> [!TIP]
>
> Você pode usar a extensão do Docker para orientá-lo ao usar o `Dockerfile` e `docker-compose.yml` arquivos relacionados ao seus contêineres do Docker. Por fim, provavelmente você vai escrever esses tipos de arquivos sem essa ferramenta, mas usando a extensão do Docker é um bom ponto de partida que acelerará sua curva de aprendizado.

Na Figura 4-24, você pode ver como o docker-compose arquivo for adicionado usando a extensão do Docker para VS Code.

![Exibição do console da extensão do Docker para VS Code.](./media/image24.png)

**Figura 4-24**. Arquivos do docker adicionados usando o **arquivos Docker adicionar ao comando de espaço de trabalho**

Quando você adiciona um DockerFile, você especificar qual imagem base do Docker, você vai usar (como o uso de `FROM microsoft/aspnetcore`). Geralmente, você cria sua imagem personalizada na parte superior de uma imagem de base que você obteve de qualquer repositório oficial, nos [registro de Hub do Docker](https://hub.docker.com/) (como um [imagem para o .NET Core](https://hub.docker.com/r/microsoft/dotnet/) o um ou mais [para Node. js](https://hub.docker.com/_/node/)).

***Usar uma imagem de Docker oficial existente***

Usando um repositório oficial de uma pilha de idiomas com um número de versão garante que os mesmos recursos de idioma estão disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).

Este é um DockerFile de exemplo para um contêiner do .NET Core:

```Dockerfile
# Base Docker image to use  
FROM microsoft/dotnet:2.1-aspnetcore-runtime
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Nesse caso, a imagem se baseia na versão 2.1 da imagem de docker do ASP.NET Core oficial (de várias arquiteturas para Linux e Windows), de acordo com a linha `FROM microsoft/dotnet:2.1-aspnetcore-runtime`. (Para obter mais informações sobre esse tópico, consulte o [imagem do Docker do ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) página e o [imagem do Docker do .NET Core](https://hub.docker.com/r/microsoft/dotnet/) página).

No DockerFile, você também pode instruir o Docker a escutar na porta TCP que você usará em tempo de execução (como a porta 80).

Você pode especificar mais definições de configurações no Dockerfile, dependendo da linguagem e da estrutura usadas. Por exemplo, o `ENTRYPOINT` de linha com `["dotnet", "MySingleContainerWebApp.dll"]` diz ao Docker para executar um aplicativo .NET Core. Se você estiver usando o SDK e a CLI do .NET Core (`dotnet CLI`) para compilar e executar o aplicativo .NET, essa configuração será diferente. O ponto principal aqui é que a linha ENTRYPOINT e outras configurações dependem do idioma e plataforma que escolher para seu aplicativo.

> [! INFORMAÇÕES]
>
> Para obter mais informações sobre a criação de imagens do Docker para aplicativos .NET Core, acesse <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Para saber mais sobre como criar suas próprias imagens, acesse <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Usar repositórios de imagem para várias arquiteturas**

Um nome de imagem única em um repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows. Esse recurso permite que os fornecedores, como a Microsoft (criadores de imagem base) criar um único repositório para abranger várias plataformas (ou seja, Linux e Windows). Por exemplo, o [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repositório disponível no registro do Hub do Docker fornece suporte para Linux e Windows Nano Server usando o mesmo nome de imagem.

Extraindo o [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) pulls de imagem de um host do Windows a variante do Windows, ao passo que recebendo o mesmo nome de imagem de um host Linux efetua pull da variante do Linux.

***Criar sua imagem de base a partir do zero***

Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker. Esse cenário provavelmente não é o melhor para você, se você estiver apenas começando com o Docker, mas se você quiser definir as partes específicas de sua própria imagem base, você pode fazê-lo.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Etapa 3: Criar imagens personalizadas do Docker inserindo seu serviço nele

Para cada serviço personalizado que consiste em seu aplicativo, você precisará criar uma imagem relacionada. Se seu aplicativo é composto por um único serviço ou aplicativo web, você precisará apenas uma única imagem.

> [!NOTE]
>
> Ao levar em consideração o "loop externo DevOps fluxo de trabalho", as imagens serão criadas por um processo de build automatizado sempre que você enviar por push seu código-fonte para um repositório Git (integração contínua), portanto, as imagens serão criadas no ambiente global do seu código-fonte.
>
> Mas antes de considerarmos indo para aquela rota de loop externo, é necessário garantir que o aplicativo do Docker está funcionando corretamente, de modo que eles não envie por push o código que pode não funcionar corretamente para o sistema de controle do código-fonte (Git, etc.).
>
> Portanto, cada desenvolvedor precisa primeiro fazer todo o processo de loop interno para testar localmente e continuar a desenvolver até que eles querem enviar por push a um recurso completo ou altere para o sistema de controle do código-fonte.

Para criar uma imagem no seu ambiente local e usando o DockerFile, você pode usar o comando docker build, conforme demonstrado na Figura 4-25 (você também pode executar `docker-compose up --build` para aplicativos compostos por vários contêineres/serviços).

![Saída do console de build do docker-Compose, que mostra as imagens de progresso de download.](./media/image25.png)

**Figura 4-25**. Compilação do docker em execução

Opcionalmente, em vez de diretamente em execução `docker build` da pasta do projeto, você pode gerar primeiro uma pasta implantável com as bibliotecas .NET necessárias por meio da execução `dotnet publish` de comando e, em seguida, executar `docker build`.

Este exemplo cria uma imagem do Docker com o nome `cesardl/netcore-webapi-microservice-docker:first` (`:first` é uma marca, como uma versão específica). Você pode executar esta etapa para cada imagem personalizada, que você precisará criar seu aplicativo composto do Docker com vários contêineres.

Você pode encontrar imagens existentes no seu repositório local (computador de desenvolvimento) usando o docker imagens comando, conforme ilustrado na Figura 4-26.

![Console de saída do comando docker images, que mostra imagens existentes.](./media/image26.png)

**Figura 4-26**. Visualização das imagens existentes usando imagens do docker

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Etapa 4: Definir os serviços no docker-Compose. yml ao compilar um aplicativo composto do Docker com vários serviços

Com o `docker-compose.yml` arquivo, você pode definir um conjunto de serviços relacionados para ser implantado como um aplicativo composto com os comandos de implantação, explicados na seção próxima etapa.

Crie esse arquivo em seu principal ou a pasta raiz da solução; ele deve ter conteúdo semelhante ao mostrado neste `docker-compose.yml` arquivo:

```yml
version: '3.4'
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

- Build do DockerFile no diretório atual

- Encaminhar a porta 80 no contêiner para a porta 81 no computador host, exposta

- Montar o diretório do projeto no host para /code dentro do contêiner, possibilitando que você pode modificar o código sem ter que recompilar a imagem

- Vincular o serviço web para o serviço de redis

O serviço do redis usa o [imagem mais recente do redis público](https://hub.docker.com/_/redis/) extraído do registro de Hub do Docker. [redis](https://redis.io/) é um sistema de cache populares para aplicativos do lado do servidor.

### <a name="step-5-build-and-run-your-docker-app"></a>Etapa 5: Compilar e executar seu aplicativo do Docker

Se seu aplicativo tem apenas um único contêiner, basta executá-lo Implantando-o em seu Host do Docker (VM ou servidor físico). No entanto, se seu aplicativo é composto por vários serviços, você precisará *compô-la*também. Vamos ver as diferentes opções.

***Opção a: Executar um único contêiner ou serviço***

Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Para essa implantação específica, podemos irá redirecionar as solicitações enviadas para a porta 80 para a porta interna 5000. Agora o aplicativo está escutando na porta 80 no nível do host externa.

***Opção b: Compor e executar um aplicativo de vários contêineres***

Na maioria dos cenários empresariais, um aplicativo do Docker será ser composto de vários serviços. Nesses casos, você pode executar o `docker-compose up` comando (Figura 4-27), que usará o arquivo docker-Compose. yml que talvez você tenha criado anteriormente. Executar esse comando implanta um aplicativo composto com todos os seus contêineres relacionados.

![Saída a partir do console de-comando docker compose up.](./media/image27.png)

**Figura 4-27**. Resultados da execução do comando "docker-compose up"

Depois de executar `docker-compose up`, implantar seu aplicativo e seus contêineres relacionados no Host do Docker, conforme ilustrado na Figura 4-28, na representação de VM.

![VM executando aplicativos de vários contêineres.](./media/image28.png)

**Figura 4-28**. VM com contêineres do Docker implantados

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Etapa 6: Testar seu aplicativo do Docker (localmente, em sua VM local do CD)

Esta etapa irá variar dependendo de seu aplicativo está funcionando.

Uma simple API do .NET Core Web "Hello World" implantado como um único contêiner ou serviço, você apenas precisará acessar o serviço, fornecendo a porta TCP especificada no DockerFile.

Se o host local não está ativado, para navegar até seu serviço, localize o endereço IP para a máquina usando este comando:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

No host do Docker, abra um navegador e navegue até o site; Você deve ver seu aplicativo ou serviço em execução, conforme demonstrado na Figura 4-29.

![Modo de exibição de navegador da resposta do localhost/API/values.](./media/image29.png)

**Figura 4-29**. Teste seu aplicativo do Docker localmente usando localhost

Observe que ele está usando a porta 80, mas internamente está sendo redirecionado para a porta 5000, pois é como ele foi implantado com `docker run`, conforme explicado anteriormente.

Você pode testar isso usando o CURL no terminal. Em uma instalação do Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-30.

![Saída de Introdução do console a http://10.0.75.1/API/values com curl](./media/image30.png)

**Figura 4-30**. Testando um aplicativo do Docker localmente usando CURL

**Depuração de um contêiner em execução no Docker**

Visual Studio Code dá suporte à depuração Docker se você estiver usando o Node. js e outras plataformas como contêineres do .NET Core.

Você também pode depurar contêineres do .NET Core ou .NET Framework no Docker ao usar o Visual Studio para Windows ou Mac, conforme descrito na próxima seção.

> [! INFORMAÇÕES]
>
> Para saber mais sobre a depuração de contêineres do Docker do Node. js, acesse <https://blog.docker.com/2016/07/live-debugging-docker/> e <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Anterior](docker-apps-development-environment.md)
>[Próximo](visual-studio-tools-for-docker.md)
