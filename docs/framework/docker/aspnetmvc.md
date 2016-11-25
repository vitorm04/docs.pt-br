---
title: "Migrando aplicativos ASP.NET MVC para contêineres do Windows"
description: "Saiba como selecionar um aplicativo ASP.NET MVC existente e executá-lo em um contêiner do Docker do Windows"
keywords: "Contêineres do Windows, Docker, ASP.NET MVC"
author: BillWagner
manager: wpickett
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework-4.6
ms.technology: dotnet-mvc
ms.devlang: dotnet
ms.assetid: c9f1d52c-b4bd-4b5d-b7f9-8f9ceaf778c4
translationtype: Human Translation
ms.sourcegitcommit: 15c55a87beb64f265a164db918c7721c7690fadf
ms.openlocfilehash: 3e8a8a953cbb3dde6ddf386f8c3b3a1fd4c549f1

---

# <a name="migrating-aspnet-mvc-applications-to-windows-containers"></a>Migrando aplicativos ASP.NET MVC para contêineres do Windows

A execução de um aplicativo baseado em .NET Framework existente em um contêiner do Windows requer a criação da imagem do Docker que contém seu aplicativo e a inicialização de um ou mais contêineres para executar essa imagem. Este tópico explica as tarefas que você deve executar para selecionar um [aplicativo ASP.NET MVC](http://www.asp.net/mvc) existente e implantá-lo em um contêiner do Windows.

Você começará com um aplicativo ASP.NET MVC existente. Em seguida, criará os ativos publicados usando o Visual Studio. Você usará o Docker para criar a imagem que contém seu aplicativo e executa esse aplicativo quando ele é iniciado. Quando tiver terminado, você poderá conectar um navegador ao site em execução em um contêiner do Windows e verificar se o aplicativo está em execução.

Este artigo pressupõe uma compreensão básica do Docker. Você pode aprender mais sobre a arquitetura do Docker lendo a [Docker Overview](https://docs.docker.com/engine/understanding-docker/) (Visão geral do Docker) no site do Docker, caso esses conceitos sejam novos.

O aplicativo que você executará em um contêiner é um site simples que responde a perguntas aleatoriamente. Esse aplicativo é um aplicativo MVC básico sem nenhum suporte ou armazenamento de banco de dados, permitindo que você se concentre em mover a camada da Web para um contêiner. Os tópicos futuros mostrarão como mover e gerenciar o armazenamento persistente em aplicativos em contêineres.

Mover seu aplicativo envolve estas etapas:

1. [Criar uma tarefa de publicação para compilar os ativos para uma imagem.](#publish-script)
2. [Criar uma imagem do Docker que executará o aplicativo.](#build-the-image)
3. [Iniciar um contêiner do Docker que execute sua imagem.](#start-a-container)
4. [Verificar o aplicativo usando o navegador.](#verify-in-the-browser)

O aplicativo concluído está localizado no [repositório dotnet/core-docs no GitHub](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator).

## <a name="prerequisites"></a>Pré-requisitos

No mínimo, seu computador de desenvolvimento deve estar executando a [Atualização de Aniversário do Windows 10](https://www.microsoft.com/en-us/software-download/windows10/) ou o [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server). 

Antes de começar, você precisa instalar o [Docker para Windows](https://docs.docker.com/docker-for-windows/), versão 1.12 Beta 26 ou mais recente. No momento, o suporte do contêiner do Windows está disponível apenas no canal Beta.

> [!IMPORTANT]
> Se você estiver usando o Windows Server 2016, precisará seguir as instruções para [Implantação do Host do Contêiner – Windows Server](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/deployment/deployment) antes de executar os contêineres do Docker.

Após instalar e iniciar o Docker, você precisará clicar com o botão direito do mouse no ícone de bandeja e selecionar **Switch to Windows containers** (Alternar para contêineres do Windows) para executar imagens do Docker baseadas no Windows. Este comando demora alguns segundos para ser executado:

![Contêiner do Windows][windows-container]

## <a name="publish-script"></a>Script de publicação

A primeira etapa é reunir todos os ativos que você precisará carregar em uma imagem do Docker em um único lugar. Felizmente, você pode usar o comando **Publicar** do Visual Studio para criar um perfil de publicação para seu aplicativo. Esse perfil colocará todos os ativos em uma árvore de diretório que você copiará para sua imagem de destino posteriormente neste tutorial.

**Etapas de publicação**

1. Clique com o botão direito do mouse no projeto Web no Visual Studio e selecione **Publicar**.
2. Clique no **botão Perfil personalizado e selecione **Sistema de Arquivo** como o método.
3. Selecione o diretório. Por convenção, o exemplo baixado usa `bin/PublishOutput`.

![Conexão da publicação][publish-connection]

Em seguida, abra a seção **Opções de Publicação de Arquivo** da guia **Configurações**. Selecione **Pré-compilar durante a publicação**. Essa otimização significa que você compila as exibições no contêiner do Docker, está copiando as exibições pré-compiladas.

![Configurações de publicação][publish-settings]

Clique em **Publicar** e o Visual Studio copiará todos os ativos necessários para a pasta de destino. 

## <a name="build-the-image"></a>Criar a imagem

Você define a imagem do Docker em um Dockerfile que contém instruções para a imagem base, todos os componentes adicionais, o aplicativo que você deseja executar e outra imagem de configuração.  O Dockerfile é a entrada para o comando `docker build`, que cria a imagem.

Você criará uma imagem com base na imagem do `microsft/aspnet` localizada no [Hub do Docker](https://hub.docker.com/r/microsoft/aspnet/).
A imagem base, `microsoft/aspnet`, é uma imagem do Windows Server. Além do Windows Server Core, ele tem o IIS e o ASP.NET 4.6.2 instalados e habilitados. Quando você executar essa imagem em um contêiner, ela iniciará automaticamente o IIS e quaisquer sites instalados estarão ativos.

O Dockerfile que cria a imagem tem esta aparência:

```
# The `FROM` instruction specifies the base image. You are
# extending the `microsoft/aspnet` image.

FROM microsoft/aspnet

# Next, this Dockerfile creates a directory for your application
RUN mkdir C:\randomanswers

# configure the new site in IIS.
RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "ASPNET" -PhysicalPath C:\randomanswers -BindingInformation "*:8000:"

# This instruction tells the container to listen on port 8000. 
EXPOSE 8000

# The final instruction copies the site you published earlier into the container.
ADD containerImage/ /randomanswers
```

Não há nenhum comando `ENTRYPOINT` neste Dockerfile. Você não precisa de um.
A imagem base garante que o IIS é iniciado quando o contêiner é iniciado. 

Em seguida, você precisará executar um comando de build do Docker para criar a imagem que executará o aplicativo ASP.NET. Para fazer isso, abra uma janela do PowerShell e digite o seguinte comando no diretório da solução:

```
docker build -t mvcrandomanswers .
```

Esse comando criará a nova imagem seguindo as instruções em seu Dockerfile. Isso pode incluir efetuar o pull da imagem base do [Hub do Docker](http://hub.docker.com), em seguida, ele adicionará seu aplicativo àquela imagem.

Depois que o comando for concluído, você poderá executar o comando `docker images` para ver informações sobre a nova imagem:

```
REPOSITORY                    TAG                 IMAGE ID            CREATED             SIZE
mvcrandomanswers              latest              86838648aab6        2 minutes ago       8.104 GB
```

A ID da IMAGEM será diferente em seu computador. Agora, vamos executar o aplicativo.

## <a name="start-a-container"></a>Iniciar um contêiner

Você inicia um contêiner executando o seguinte comando `docker run`:

```
docker run -d -p 8000:8000 --name randomanswers mvcrandomanswers
```

O argumento `-d` diz ao Docker para iniciar a imagem no modo desconectado. Isso significa que a imagem do Docker é executada desconectada do shell atual.

O argumento `-p 8000:8000` diz ao Docker como mapear as portas de entrada. Neste exemplo, estamos usando a porta 8000 no host e o contêiner.

O `--name randomanswers` fornece um nome para o contêiner em execução. Você pode usar esse nome em vez da ID do contêiner na maioria dos comandos.

O `mvcrandomanswers` é o nome da imagem a ser iniciada.

## <a name="verify-in-the-browser"></a>Verificar no navegador

> [!NOTE]
> Com a versão atual, você não pode usar `http://localhost` para navegar até seu site. Isso ocorre devido a um comportamento conhecido no WinNAT e ele será resolvido no futuro. Até que isso seja resolvido, você precisará usar o endereço IP do contêiner.

Após o contêiner ser iniciado, você precisará localizar seu endereço IP para que possa se conectar ao seu contêiner em execução de um navegador:

```
docker inspect -f "{{ .NetworkSettings.Networks.nat.IPAddress }}" randomanswers
172.31.194.61
```

Você pode se conectar ao contêiner em execução usando o endereço IPv4 e a porta configurada (8000), `http://172.31.194.61:8000` no exemplo mostrado. Digite a URL no navegador e você deverá ver o site em execução.

> [!NOTE]
> Alguns softwares de proxy ou VPN podem impedir que você navegue para seu site.
> Você pode desabilitá-los temporariamente para se certificar de que seu contêiner está funcionando.

O diretório de exemplo no GitHub contém um [script do PowerShell](https://github.com/dotnet/docs/tree/master/samples/framework/docker/MVCRandomAnswerGenerator/run.ps1) que executa esses comandos para você. Abra uma janela do PowerShell, altere o diretório para o diretório da solução e digite:

```
./run.ps1
```

Ele cria a imagem, exibe a lista de imagens no seu computador, inicia um contêiner e exibe o endereço IP do contêiner. 

Quando terminar e desejar parar o contêiner, emitia um comando `docker
stop`:

```
docker stop randomanswers
```

Para remover o contêiner, emita um comando `docker rm`:

```
docker rm randomanswers
```

## <a name="summary"></a>Resumo

Neste tópico, você viu as etapas para mover e executar um aplicativo ASP.NET MVC existente em um contêiner do Windows Server. Executar um aplicativo existente não requer alterações ao seu aplicativo. Você precisa executar as tarefas para publicar seu aplicativo, criar uma imagem do Docker e iniciar a imagem em um novo contêiner. Utilizar os contêineres do Windows Server é o caminho mais fácil para migrar seus aplicativos existentes para esse ambiente.

[windows-container]: media/aspnetmvc/SwitchContainer.png "Alternar para o contêiner do Windows"
[publish-connection]: media/aspnetmvc/PublishConnection.png "Publicar no sistema de arquivos"
[publish-settings]: media/aspnetmvc/PublishSettings.png "Configurações de publicação"



<!--HONumber=Nov16_HO3-->


