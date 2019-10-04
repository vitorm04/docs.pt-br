---
title: Fluxo de trabalho de desenvolvimento do loop interno para aplicativos do Docker
description: Conheça o fluxo de trabalho de "loop interno" para desenvolvimento de aplicativos do Docker.
ms.date: 02/15/2019
ms.openlocfilehash: c97cd9ba8d740f13c22caa45e344c4961e3b0600
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834488"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a>Fluxo de trabalho de desenvolvimento do loop interno para aplicativos do Docker

Antes de disparar o fluxo de trabalho de loop externo que abrange todo o ciclo de DevOps, tudo começa no computador de cada desenvolvedor, codificando o aplicativo em si, usando suas linguagens ou plataformas preferenciais e testando localmente (Figura 4-21). Mas, em todos os casos, você terá um ponto importante em comum, independentemente da linguagem, da estrutura ou das plataformas escolhidas. Neste fluxo de trabalho específico, você sempre está desenvolvendo e testando contêineres do Docker, mas localmente.

![Diagrama mostrando o conceito de um ambiente de desenvolvimento de loop interno.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

**Figura 4-21**. Contexto de desenvolvimento do loop interno

O contêiner ou instância de uma imagem de Docker terá estes componentes:

- Uma seleção de sistema operacional (por exemplo, uma distribuição do Linux ou Windows)

- Arquivos adicionados pelo desenvolvedor (por exemplo, binários do aplicativo)

- Configuração (por exemplo, configurações de ambiente e dependências)

- Instruções sobre quais processos devem ser executados pelo Docker

Você pode configurar o fluxo de trabalho de desenvolvimento do loop interno que utiliza o Docker como processo (descrito na próxima seção). Observe que as etapas iniciais para configurar o ambiente não estão incluídas, porque você só precisa fazer isso uma vez.

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a>Criando um único aplicativo dentro de um contêiner do Docker usando o Visual Studio Code e a CLI do Docker

Aplicativos são compostos por seus próprios serviços e por bibliotecas adicionais (dependências).

A Figura 4-22 mostra as etapas básicas que normalmente você precisaria executar ao criar um aplicativo do Docker, seguidas por descrições detalhadas de cada etapa.

![Diagrama mostrando as sete etapas necessárias para criar um aplicativo em contêineres.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

**Figura 4-22**. Fluxo de trabalho de alto nível do ciclo de vida de aplicativos em contêineres do Docker usando a CLI do Docker

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a>Etapa 1: Iniciar a codificação no Visual Studio Code e criar a linha de base do aplicativo/serviço inicial

A maneira como você desenvolve seu aplicativo é semelhante à maneira como o faz sem o Docker. A diferença é que, durante o desenvolvimento, você está implantando e testando o aplicativo ou os serviços em execução dentro de contêineres do Docker colocados no ambiente local (como uma VM Linux ou Windows).

**Configurando o ambiente local**

Com as versões mais recentes do Docker para Mac e Windows, é mais fácil do que nunca desenvolver aplicativos do Docker e a configuração é simples.

> [!TIP]
> Para obter instruções sobre como configurar o Docker for Windows, acesse <https://docs.docker.com/docker-for-windows/>.
>
>Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.

Além disso, você precisará de um editor de código para que possa desenvolver o aplicativo enquanto estiver usando a CLI do Docker.

A Microsoft fornece o Visual Studio Code, que é um editor de código leve com suporte no Mac, no Windows e no Linux, além do IntelliSense com [suporte para várias linguagens](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python e a maioria das linguagens modernas), [depuração](https://code.visualstudio.com/Docs/editor/debugging), [integração com Git](https://code.visualstudio.com/Docs/editor/versioncontrol) e [suporte para extensões](https://code.visualstudio.com/docs/extensions/overview). Esse editor é uma excelente opção para desenvolvedores de Mac e Linux. No Windows, também é possível usar o aplicativo do Visual Studio completo.

> [!TIP]
> Para obter instruções sobre como instalar o Visual Studio Code para Windows, Mac ou Linux, acesse <https://code.visualstudio.com/docs/setup/setup-overview/>.
>
> Para obter instruções sobre como configurar o Docker para Mac, acesse <https://docs.docker.com/docker-for-mac/>.

Você pode trabalhar com a CLI do Docker e escrever seu código usando qualquer editor de código, mas usar o Visual Studio Code com a extensão do Docker torna mais fácil criar arquivos `Dockerfile` e `docker-compose.yml` em seu workspace. Você também pode executar tarefas e scripts do IDE do Visual Studio Code para executar comandos do Docker usando a CLI do Docker abaixo.

A extensão do Docker para o VS Code fornece os seguintes recursos:

- Geração automática de arquivos `Dockerfile` e `docker-compose.yml`

- Destaque de sintaxe e dicas ao passar o mouse para arquivos `docker-compose.yml` e `Dockerfile`

- IntelliSense (preenchimentos) para arquivos `Dockerfile` e `docker-compose.yml`

- Linting (erros e avisos) para arquivos `Dockerfile`

- Integração de paleta de comandos (F1) para os comandos do Docker mais comuns

- Integração do Explorer para gerenciar Imagens e Contêineres

- Implantar imagens do DockerHub e dos Registros de Contêiner do Azure no Serviço de Aplicativo do Azure

Para instalar a extensão do Docker, pressione Ctrl + Shift + P, digite `ext install` e, em seguida, execute o comando Instalar Extensão para abrir a lista de extensões do Marketplace. Em seguida, digite **docker** para filtrar os resultados e, então, selecione a extensão Docker Support, conforme ilustrado na Figura 4-23.

![Modo de exibição da extensão do Docker para VS Code.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

**Figura 4-23**. Instalando a extensão do Docker no Visual Studio Code

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a>Etapa 2: Criar um DockerFile relacionado a uma imagem existente (ambientes de desenvolvimento ou SO sem formatação, como Ruby, Node.js e .NET Core)

Você precisará de um `DockerFile` por imagem personalizada a ser criada e por contêiner a ser implantado. Se seu aplicativo for composto por um único serviço personalizado, você precisará de um único `DockerFile`. No entanto, se o aplicativo for composto por vários serviços (por exemplo, em uma arquitetura de microsserviços), você precisará de um `Dockerfile` por serviço.

Normalmente, o `DockerFile` é colocado na pasta raiz do aplicativo ou serviço e contém os comandos necessários para que o Docker saiba como configurar e executar esse aplicativo ou serviço. Você pode criar seu `DockerFile` e adicioná-lo ao projeto junto com o código (Node.js, .NET Core etc.) ou, se você for novo no ambiente, veja a dica a seguir.

> [!TIP]
> Você pode usar a extensão do Docker para orientá-lo ao usar os arquivos `Dockerfile` e `docker-compose.yml` relacionados a seus contêineres do Docker. Eventualmente, você provavelmente gravará esses tipos de arquivos sem essa ferramenta, mas usar a extensão do Docker é um bom ponto de partida que acelerará sua curva de aprendizado.

Na Figura 4-24, você pode ver como um arquivo docker-compose é adicionado usando a extensão do Docker para VS Code.

![Modo de exibição de console da extensão do Docker para VS Code.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

**Figura 4-24**. Arquivos do Docker adicionados usando o **Adicionar arquivos do Docker ao Workspace**

Quando adiciona um DockerFile, você especificar qual imagem de base do Docker usará (como usar `FROM mcr.microsoft.com/dotnet/core/aspnet`). Normalmente, você criará sua imagem personalizada usando uma imagem de base que obteve de qualquer repositório oficial no [Registro do Docker Hub](https://hub.docker.com/) (como uma [imagem para .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) o a imagem [para Node.js](https://hub.docker.com/_/node/)).

***Usar uma imagem do Docker oficial existente***

Usar um repositório oficial de uma pilha de linguagem com um número de versão garante que recursos da mesma linguagem estejam disponíveis em todos os computadores (incluindo desenvolvimento, teste e produção).

A seguir, há um DockerFile de exemplo para um contêiner do .NET Core:

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

Nesse caso, a imagem é baseada na versão 2.2 da imagem oficial do Docker do ASP.NET Core (com várias arquiteturas para Linux e Windows), de acordo com a linha `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`. (Para obter mais informações sobre esse tópico, confira a página [Imagem do Docker do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) e a página [Imagem do Docker do .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/)).

No DockerFile, você também pode instruir o Docker a escutar na porta TCP que usará em tempo de execução (como a porta 80).

Você pode especificar mais definições de configurações no Dockerfile, dependendo da linguagem e da estrutura usadas. Por exemplo, a linha `ENTRYPOINT` com `["dotnet", "MySingleContainerWebApp.dll"]` instrui o Docker a executar um aplicativo do .NET Core. Se você estiver usando o SDK e a CLI do .NET Core (`dotnet CLI`) para criar e executar o aplicativo do .NET, essa configuração será diferente. O essencial aqui é que a linha ENTRYPOINT e outras configurações dependem da linguagem e da plataforma que você escolher para seu aplicativo.

> [!TIP]
> Para obter mais informações sobre a criação de imagens do Docker para aplicativos .NET Core, acesse <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.
>
> Para saber mais sobre como criar suas próprias imagens, acesse <https://docs.docker.com/engine/tutorials/dockerimages/>.

**Usar repositórios de imagens com várias arquiteturas**

Um único nome de imagem em um repositório pode conter variantes de plataforma, como uma imagem do Linux e uma imagem do Windows. Esse recurso permite que fornecedores como a Microsoft (criadores de imagem base) criem um único repositório para abranger várias plataformas (ou seja, Linux e Windows). Por exemplo, o repositório [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/), disponível no registro do Docker Hub, é compatível com Linux e Windows Nano Server usando o mesmo nome de imagem.

Efetuar pull da imagem [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) de um host do Windows efetua pull da variante do Windows, enquanto efetuar pull do mesmo nome de imagem de um host Linux efetua pull da variante do Linux.

***Criar a imagem base do zero***

Você pode criar sua própria imagem base do Docker do zero, conforme explicado neste [artigo](https://docs.docker.com/engine/userguide/eng-image/baseimages/) do Docker. Esse cenário provavelmente não é recomendado para iniciantes no Docker, mas, se você quiser definir os bits específicos de sua própria imagem base, poderá fazer isso.

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a>Etapa 3: Criar suas imagens do Docker personalizadas inserindo seu serviço nelas

Para cada serviço personalizado que compõe seu aplicativo, você precisará criar uma imagem relacionada. Se seu aplicativo for composto por um único serviço ou aplicativo Web, você precisará apenas de uma única imagem.

> [!NOTE]
> Ao levar em consideração o "fluxo de trabalho de DevOps de loop externo", as imagens serão criadas por um processo de build automatizado sempre que você efetuar push de seu código-fonte para um repositório Git (integração contínua), portanto, as imagens serão criadas no ambiente global de seu código-fonte.
>
> Mas, antes de considerarmos seguir essa rota do loop externo, precisamos garantir que o aplicativo do Docker está funcionando corretamente para que não efetue push de um código que não funciona corretamente para o sistema de controle do código-fonte (Git etc.).
>
> Sendo assim, cada desenvolvedor precisa primeiro realizar todo o processo de loop interno para testar localmente e continuar desenvolvendo até que queiram efetuar push de um recurso ou alteração completa para o sistema de controle do código-fonte.

Para criar uma imagem no ambiente local usando o DockerFile, você pode usar o comando docker build, conforme demonstrado na Figura 4-25 (você também pode executar `docker-compose up --build` para aplicativos compostos por vários contêineres/serviços).

![Captura de tela mostrando a saída do console do comando de Build do Docker.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

**Figura 4-25**. Executando docker build

Opcionalmente, em vez de executar `docker build` diretamente da pasta do projeto, você pode primeiro gerar uma pasta implantável com as bibliotecas .NET necessárias usando o comando run `dotnet publish` e, em seguida, executando `docker build`.

Este exemplo cria uma imagem do Docker com o nome `cesardl/netcore-webapi-microservice-docker:first` (`:first` é uma marca, como uma versão específica). Você poderá realizar esta etapa para cada imagem personalizada que precisar criar para o seu aplicativo do Docker composto com vários contêineres.

Você pode encontrar as imagens existentes no repositório local (seu computador de desenvolvimento) usando o comando docker images, conforme mostrado na Figura 4-26.

![Saída do console do comando docker images, mostrando as imagens existentes.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

**Figura 4-26**. Exibindo imagens existentes usando imagens do Docker

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a>Etapa 4: Definir os serviços em docker-compose.yml ao criar um aplicativo composto do Docker com vários serviços

Com o arquivo `docker-compose.yml`, você pode definir um conjunto de serviços relacionados para que sejam implantados como um aplicativo composto usando os comandos de implantação explicados na seção sobre a próxima etapa.

Crie esse arquivo na pasta principal ou raiz da solução; ele deve ter conteúdo semelhante ao mostrado neste arquivo `docker-compose.yml`:

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

Nesse caso específico, o arquivo define dois serviços: o serviço Web (seu serviço personalizado) e o serviço Redis (um serviço de cache popular). Cada serviço será implantado como um contêiner, portanto, precisamos usar uma imagem do Docker concreta para cada um. Para este serviço Web específico, a imagem precisará fazer o seguinte:

- Criar por meio do DockerFile no diretório atual

- Encaminhar a porta 80, exposta no contêiner, para a porta 81, no computador host

- Montar o diretório do projeto no host em /code dentro do contêiner, possibilitando que você modifique o código sem precisar recompilar a imagem

- Vincular o serviço Web ao serviço Redis

O serviço Redis usa a [imagem pública do Redis mais recente](https://hub.docker.com/_/redis/) extraída do registro do Docker Hub. [redis](https://redis.io/) é um sistema de cache popular para aplicativos do lado do servidor.

### <a name="step-5-build-and-run-your-docker-app"></a>Etapa 5: Criar e executar seu aplicativo do Docker

Se seu aplicativo tiver apenas um contêiner, você precisará apenas executá-lo implantando-o no host do Docker (VM ou servidor físico). No entanto, se o aplicativo for composto por vários serviços, você também precisará *compô-lo*. Vejamos as diferentes opções.

***Opção A: Executar um único contêiner ou serviço***

Você pode executar a imagem do Docker usando o comando docker run, conforme mostrado aqui:

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

Para essa implantação específica, redirecionaremos as solicitações enviadas à porta 80 para a porta 5000 interna. Agora, o aplicativo está escutando na porta 80 externa no nível do host.

***Opção B: Compor e executar um aplicativo de vários contêineres***

Na maioria dos cenários empresariais, um aplicativo do Docker será composto por vários serviços. Nesses casos, você pode executar o comando `docker-compose up` (Figura 4-27), que usará o arquivo docker-compose.yml, que talvez tenha criado anteriormente. Executar esse comando implanta um aplicativo composto com todos os contêineres relacionados.

![Saída de console do comando docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

**Figura 4-27**. Resultados da execução do comando "docker-compose up"

Depois de executar `docker-compose up`, implante seu aplicativo e os contêineres relacionados no Host do Docker, conforme ilustrado na Figura 4-28, na representação da VM.

![VM executando aplicativos de vários contêineres.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

**Figura 4-28**. VM com contêineres do Docker implantados

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a>Etapa 6: Testar seu aplicativo do Docker (localmente, na VM de CD local)

Esta etapa varia de acordo com o que seu aplicativo está fazendo.

Em um simples "Olá, Mundo" da API Web do .NET Core implantado como um único contêiner ou serviço, você precisará apenas acessar o serviço fornecendo a porta TCP especificada no DockerFile.

Se o localhost não estiver ativado, para navegar até seu serviço, localize o endereço IP do computador usando este comando:

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

No host do Docker, abra um navegador e navegue até esse site. Você deverá ver seu aplicativo/serviço em execução, conforme demonstrado na Figura 4-29.

![Modo de exibição de navegador da resposta de localhost/API/ valores.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

**Figura 4-29**. Testando seu aplicativo do Docker localmente usando localhost

Observe que ele está usando a porta 80, mas internamente está sendo redirecionado para a porta 5000, pois é como ele foi implantado com `docker run`, conforme explicado anteriormente.

Isso pode ser testado usando o CURL no terminal. Em uma instalação do Docker no Windows, o IP padrão é 10.0.75.1, conforme ilustrado na Figura 4-30.

![Saída do console ao obter o http://10.0.75.1/API/values com cURL](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

**Figura 4-30**. Testando um aplicativo do Docker localmente usando CURL

**Depurando um contêiner em execução no Docker**

O Visual Studio Code dá suporte à depuração do Docker quando você está usando Node.js e outras plataformas, como contêineres do .NET Core.

Você também pode depurar contêineres do .NET Core ou .NET Framework no Docker ao usar o Visual Studio para Windows ou Mac, conforme descrito na próxima seção.

> [!INFORMAÇÕES]
>
> Para saber mais sobre a depuração de contêineres do Docker do Node.js, acesse <https://blog.docker.com/2016/07/live-debugging-docker/> e <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.

>[!div class="step-by-step"]
>[Anterior](docker-apps-development-environment.md)
>[Próximo](visual-studio-tools-for-docker.md)
