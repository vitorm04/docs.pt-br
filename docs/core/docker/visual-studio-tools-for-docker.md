---
title: Ferramentas do Visual Studio para Docker | Microsoft Docs
description: Usando as Ferramentas do Visual Studio para Docker
keywords: .NET, .NET Core, Docker, ASP.NET Core, Visual Studio
author: spboyer
ms.author: shboyer
ms.date: 04/27/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 1f3b9a68-4dea-4b60-8cb3-f46164eedbbf
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: dd1a0dc226d6ac9af5a474da54ac14094855fe31
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---

<a id="visual-studio-tools-for-docker" class="xliff"></a>

# Ferramentas do Visual Studio para Docker

O [Microsoft Visual Studio 2017](https://www.visualstudio.com/) com [Docker para Windows](https://docs.docker.com/docker-for-windows/install/) dá suporte ao build, depuração e execução de aplicativos Web e de console do .NET Framework e .NET Core usando contêineres do Windows e do Linux.

<a id="prerequisites" class="xliff"></a>

## Pré-requisitos

- [Microsoft Visual Studio 2017](https://www.visualstudio.com/)
- [Docker para Windows](https://docs.docker.com/docker-for-windows/install/)

<a id="installation-and-setup" class="xliff"></a>

## Instalação e configuração

Instale o [Microsoft Visual Studio 2017](https://www.visualstudio.com/) com a carga de trabalho do .NET Core. Examine as informações em [Docker for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker para Windows: o que saber antes de instalar) e instale o [Docker para Windows](https://docs.docker.com/docker-for-windows/install/).

É uma configuração necessária para instalação de **[Unidades Compartilhadas](https://docs.docker.com/docker-for-windows/#shared-drives)** no Docker para Windows. A configuração é necessária para o mapeamento do volume e suporte à depuração.

Clique com botão direito do mouse no ícone do Docker na Bandeja do Sistema e selecione as Unidades Compartilhadas.

![Unidades Compartilhadas](./media/visual-studio-tools-for-docker/settings-shared-drives-win.png)

<a id="create-an-aspnet-web-application-and-add-docker-support" class="xliff"></a>

## Criar um Aplicativo Web ASP.NET e adicionar suporte ao Docker

Usando o Visual Studio, crie um novo Aplicativo Web ASP.NET Core. Quando o aplicativo é carregado, selecione **Adicionar Suporte ao Docker** no **Menu Projeto** ou clique com botão direito do mouse no projeto no Gerenciador de Soluções e selecione **Adicionar** > **Suporte ao Docker**.

Menu Projeto

![Projeto Adicionar Suporte ao Docker](./media/visual-studio-tools-for-docker/project-add-docker-support.png)

Projeto Menu de Contexto

![Clique com o botão direito do mouse em Adicionar Suporte ao Docker](./media/visual-studio-tools-for-docker/right-click-add-docker-support.png)

Os seguintes arquivos são adicionados ao projeto.

- **Dockerfile**: o arquivo do Docker para aplicativos do ASP.NET Core se baseia na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore). Essa imagem inclui os pacotes NuGet do ASP.NET Core, que foram pré-compilados com JIT para melhorar o desempenho de inicialização. Ao criar Aplicativos de Console do .NET Core, o Dockerfile FROM fará referência à imagem [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet) mais recente.   
- **docker-compose.yml**: arquivo base do Docker Compose usado para definir o conjunto de imagens que serão compiladas e executadas com o build/execução do docker-compose.   
- **docker-compose.dev.debug.yml**: arquivo docker-compose adicional com alterações iterativas quando a configuração está definida para depuração. O Visual Studio chamará -f docker-compose.yml -f docker-compose.dev.debug.yml para mesclá-los. Esse arquivo de composição é usado pelas ferramentas de desenvolvimento do Visual Studio.   
- **docker-compose.dev.release.yml**: arquivo adicional do Docker Compose para depurar sua definição de versão. Ele montará o volume do depurador, portanto ele não altera o conteúdo da imagem de produção.  

O arquivo docker-compose.yml contém o nome da imagem que é criada quando o projeto é executado. 

```
version '2'

services:
  hellodockertools:
    image:  user/hellodockertools${TAG}
    build:
      context: .
      dockerfile: Dockerfile
    ports:
      - "80"
``` 

Neste exemplo, `image: user/hellodockertools${TAG}` gera a imagem `user/hellodockertools:dev` quando o aplicativo é executado no modo de **Depuração** e `user/hellodockertools:latest` no modo de **Lançamento**, respectivamente. 

Você deve alterar o `user` para seu nome de usuário do Hub do Docker se planejar enviar a imagem por push para o Registro. Por exemplo, `spboyer/hellodockertools`, ou altere a URL do seu Registro privado `privateregistry.domain.com/` dependendo da configuração.

<a id="debugging" class="xliff"></a>

### Depuração

Selecione **Docker** no menu suspenso de depuração na barra de ferramentas e use F5 para iniciar a depuração do aplicativo. 

- A imagem do microsoft/aspnetcore é adquirida (se ainda não estiver em seu cache)
- ASPNETCORE_ENVIRONMENT é definido como Desenvolvimento dentro do contêiner
- A PORTA 80 é EXPOSTA e mapeada para uma porta atribuída dinamicamente para o localhost. A porta é determinada pelo host do docker e pode ser consultada com o docker ps. 
- Seu aplicativo é copiado para o contêiner
- O navegador padrão é iniciado com o depurador anexado ao contêiner, usando a porta atribuída dinamicamente. 

A imagem resultante do Docker criada é a imagem `dev` do seu aplicativo com as imagens `microsoft/aspnetcore` como a imagem base.
Observação: a imagem de desenvolvimento está vazia, o conteúdo do aplicativo, como configurações de Depuração, usam montagem de volume para fornecer uma experiência iterativa. Para enviar uma imagem por push, use a configuração de Lançamento.

```console
REPOSITORY                  TAG         IMAGE ID            CREATED         SIZE
spboyer/hellodockertools    dev         0b6e2e44b3df        4 minutes ago   268.9 MB
microsoft/aspnetcore        1.0.1       189ad4312ce7        5 days ago      268.9 MB
```

O aplicativo é executado usando o contêiner que pode ser visto executando o comando `docker ps`.

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   4 minutes ago       Up 4 minutes        0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

<a id="edit-and-continue" class="xliff"></a>

### Editar e continuar

Alterações em arquivos estáticos e/ou arquivos de modelo do razor (.cshtml) são atualizadas automaticamente sem a necessidade de uma etapa de compilação. Faça a alteração, salve e toque em Atualizar no navegador para exibir a atualização.  

Modificações em arquivos de código exigem a compilação e a reinicialização do Kestrel dentro do contêiner. Depois de fazer a alteração, use CTRL + F5 para executar o processo e iniciar o aplicativo dentro do contêiner. O contêiner Docker não é recriado ou interrompido; usando `docker ps` na linha de comando, você pode ver que o contêiner original ainda está em execução a partir de 10 minutos atrás. 

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   10 minutes ago      Up 10 minutes       0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

<a id="publishing-docker-images" class="xliff"></a>

### Publicando imagens do Docker

Depois de ter concluído o ciclo de desenvolvimento e depuração do seu aplicativo, o Ferramentas do Visual Studio para Docker ajudará você a criar a imagem de produção do seu aplicativo. Altere o menu suspenso de depuração para **Lançamento** e compile o aplicativo. A ferramenta produzirá a imagem com o marcador `:latest` que você pode enviar por push para seu Registro privado ou Hub do Docker. 

Usando o `docker images`, você pode ver a lista de imagens.

```console
REPOSITORY                 TAG                 IMAGE ID            CREATED             SIZE
spboyer/hellodockertools   latest              8184ae38ba91        5 seconds ago       278.4 MB
spboyer/hellodockertools   dev                 0b6e2e44b3df        About an hour ago   268.9 MB
microsoft/aspnetcore       1.0.1               189ad4312ce7        5 days ago          268.9 MB
```

Pode haver uma expectativa para a imagem de produção ou de lançamento serem menores em comparação à imagem de **desenvolvimento**, no entanto, com o uso do mapeamento de volume, o depurador e o aplicativo realmente foram executados em seu computador local e não dentro do contêiner. A imagem **mais recente** empacotou todo o código de aplicativo necessário para executar o aplicativo em um computador host, portanto, o delta é do tamanho do código do aplicativo.

