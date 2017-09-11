---
title: Ferramentas do Visual Studio para Docker
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
ms.translationtype: HT
ms.sourcegitcommit: 9bb17207ba72bb22f5d6db55e9d1bd77e3013445
ms.openlocfilehash: 113d470a55fd92704de0e6def392a6e0a1a3a118
ms.contentlocale: pt-br
ms.lasthandoff: 08/25/2017

---

# <a name="visual-studio-tools-for-docker"></a><span data-ttu-id="53984-104">Ferramentas do Visual Studio para Docker</span><span class="sxs-lookup"><span data-stu-id="53984-104">Visual Studio Tools for Docker</span></span>

<span data-ttu-id="53984-105">O [Microsoft Visual Studio 2017](https://www.visualstudio.com/) com [Docker para Windows](https://docs.docker.com/docker-for-windows/install/) dá suporte ao build, depuração e execução de aplicativos Web e de console do .NET Framework e .NET Core usando contêineres do Windows e do Linux.</span><span class="sxs-lookup"><span data-stu-id="53984-105">[Microsoft Visual Studio 2017](https://www.visualstudio.com/) with [Docker for Windows](https://docs.docker.com/docker-for-windows/install/) supports building, debugging, and running .NET Framework and .NET Core web and console applications using Windows and Linux containers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53984-106">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="53984-106">Prerequisites</span></span>

- <span data-ttu-id="53984-107">[Microsoft Visual Studio 2017](https://www.visualstudio.com/) com carga de trabalho do .NET Core</span><span class="sxs-lookup"><span data-stu-id="53984-107">[Microsoft Visual Studio 2017](https://www.visualstudio.com/) with .NET Core workload</span></span>
- [<span data-ttu-id="53984-108">Docker para Windows</span><span class="sxs-lookup"><span data-stu-id="53984-108">Docker for Windows</span></span>](https://docs.docker.com/docker-for-windows/install/)

## <a name="installation-and-setup"></a><span data-ttu-id="53984-109">Instalação e configuração</span><span class="sxs-lookup"><span data-stu-id="53984-109">Installation and setup</span></span>

<span data-ttu-id="53984-110">Instale o [Microsoft Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio) com a carga de trabalho do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="53984-110">Install [Microsoft Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/install/install-visual-studio) with the .NET Core workload.</span></span>

<span data-ttu-id="53984-111">Para a instalação do Docker, examine as informações em [Docker for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) (Docker para Windows: o que saber antes de instalar) e instale o [Docker para Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="53984-111">For Docker installation, review the information at [Docker for Windows: What to know before you install](https://docs.docker.com/docker-for-windows/install/#what-to-know-before-you-install) and install [Docker For Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

<span data-ttu-id="53984-112">É uma configuração necessária para instalação de **[Unidades Compartilhadas](https://docs.docker.com/docker-for-windows/#shared-drives)** no Docker para Windows.</span><span class="sxs-lookup"><span data-stu-id="53984-112">A required configuration is to setup **[Shared Drives](https://docs.docker.com/docker-for-windows/#shared-drives)** in Docker for Windows.</span></span> <span data-ttu-id="53984-113">A configuração é necessária para o mapeamento do volume e suporte à depuração.</span><span class="sxs-lookup"><span data-stu-id="53984-113">The setting is required for the volume mapping and debugging support.</span></span>

<span data-ttu-id="53984-114">Clique com o botão direito do mouse no ícone do Docker na Bandeja do Sistema, clique em **Configurações** e selecione **Unidades Compartilhadas**.</span><span class="sxs-lookup"><span data-stu-id="53984-114">Right click the Docker icon in the System Tray, click **Settings** and select **Shared Drives**.</span></span> <span data-ttu-id="53984-115">Selecione a unidade em que o Docker armazenará seus arquivos e faça as alterações.</span><span class="sxs-lookup"><span data-stu-id="53984-115">Select the drive where Docker will store your files and apply changes.</span></span>

![Unidades Compartilhadas](./media/visual-studio-tools-for-docker/settings-shared-drives-win.png)

## <a name="create-an-aspnet-web-application-and-add-docker-support"></a><span data-ttu-id="53984-117">Criar um Aplicativo Web ASP.NET e adicionar suporte ao Docker</span><span class="sxs-lookup"><span data-stu-id="53984-117">Create an ASP.NET Web Application and add Docker Support</span></span>

<span data-ttu-id="53984-118">Usando o Visual Studio, crie um novo Aplicativo Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="53984-118">Using Visual Studio, create a new ASP.NET Core Web Application.</span></span> <span data-ttu-id="53984-119">Quando o aplicativo é carregado, selecione **Adicionar Suporte ao Docker** no **Menu Projeto** ou clique com botão direito do mouse no projeto no Gerenciador de Soluções e selecione **Adicionar** > **Suporte ao Docker**.</span><span class="sxs-lookup"><span data-stu-id="53984-119">When the application is loaded, either select **Add Docker Support** from the **Project Menu** or right click the project from the Solution Explorer and select **Add** > **Docker Support**.</span></span>

<span data-ttu-id="53984-120">Menu Projeto</span><span class="sxs-lookup"><span data-stu-id="53984-120">Project Menu</span></span>

![Projeto Adicionar Suporte ao Docker](./media/visual-studio-tools-for-docker/project-add-docker-support.png)

<span data-ttu-id="53984-122">Projeto Menu de Contexto</span><span class="sxs-lookup"><span data-stu-id="53984-122">Project Context Menu</span></span>

![Clique com o botão direito do mouse em Adicionar Suporte ao Docker](./media/visual-studio-tools-for-docker/right-click-add-docker-support.png)

<span data-ttu-id="53984-124">Quando você adiciona suporte do Docker ao seu projeto, é possível escolher entre contêineres do Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="53984-124">When you add Docker support to your project, you can choose either Windows or Linux containers.</span></span> <span data-ttu-id="53984-125">(O host do Docker deve estar executando o mesmo tipo de contêiner.</span><span class="sxs-lookup"><span data-stu-id="53984-125">(The Docker host must be running the same container type.</span></span> <span data-ttu-id="53984-126">Se for necessário, altere o tipo de contêiner na instância do Docker em execução, clique com o botão direito do mouse no ícone do **Docker** na Bandeja do Sistema e escolha **Alterar para contêineres do Windows** ou **Alterar para contêineres do Linux**.)</span><span class="sxs-lookup"><span data-stu-id="53984-126">If you need change the container type in the running Docker instance, right click the **Docker** icon in the System Tray, and choose **Switch to Windows containers** or **Switch to Linux containers**.)</span></span> 

<span data-ttu-id="53984-127">Os seguintes arquivos são adicionados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="53984-127">The following files are added to the project.</span></span>

- <span data-ttu-id="53984-128">**Dockerfile**: o arquivo do Docker para aplicativos do ASP.NET Core se baseia na imagem [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore).</span><span class="sxs-lookup"><span data-stu-id="53984-128">**Dockerfile**: the Docker file for ASP.NET Core applications is based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore) image.</span></span> <span data-ttu-id="53984-129">Essa imagem inclui os pacotes NuGet do ASP.NET Core, que foram pré-compilados com JIT para melhorar o desempenho de inicialização.</span><span class="sxs-lookup"><span data-stu-id="53984-129">This image includes the ASP.NET Core NuGet packages, which have been pre-jitted improving startup performance.</span></span> <span data-ttu-id="53984-130">Ao criar Aplicativos de Console do .NET Core, o Dockerfile FROM fará referência à imagem [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet) mais recente.</span><span class="sxs-lookup"><span data-stu-id="53984-130">When building .NET Core Console Applications, the Dockerfile FROM will reference the most recent [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet) image.</span></span>   
- <span data-ttu-id="53984-131">**docker-compose.yml**: arquivo base do Docker Compose usado para definir o conjunto de imagens que serão compiladas e executadas com o build/execução do docker-compose.</span><span class="sxs-lookup"><span data-stu-id="53984-131">**docker-compose.yml**: base Docker Compose file used to define the collection of images to be built and run with docker-compose build/run.</span></span>   
- <span data-ttu-id="53984-132">**docker-compose.dev.debug.yml**: arquivo docker-compose adicional com alterações iterativas quando a configuração está definida para depuração.</span><span class="sxs-lookup"><span data-stu-id="53984-132">**docker-compose.dev.debug.yml**: additional docker-compose file with for iterative changes when your configuration is set to debug.</span></span> <span data-ttu-id="53984-133">O Visual Studio chamará -f docker-compose.yml -f docker-compose.dev.debug.yml para mesclá-los.</span><span class="sxs-lookup"><span data-stu-id="53984-133">Visual Studio will call -f docker-compose.yml -f docker-compose.dev.debug.yml to merge these together.</span></span> <span data-ttu-id="53984-134">Esse arquivo de composição é usado pelas ferramentas de desenvolvimento do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="53984-134">This compose file is used by Visual Studio development tools.</span></span>   
- <span data-ttu-id="53984-135">**docker-compose.dev.release.yml**: arquivo adicional do Docker Compose para depurar sua definição de versão.</span><span class="sxs-lookup"><span data-stu-id="53984-135">**docker-compose.dev.release.yml**: additional Docker Compose file to debug your release definition.</span></span> <span data-ttu-id="53984-136">Ele montará o volume do depurador, portanto ele não altera o conteúdo da imagem de produção.</span><span class="sxs-lookup"><span data-stu-id="53984-136">It will volume mount the debugger so it doesn't change the contents of the production image.</span></span>  

<span data-ttu-id="53984-137">O arquivo docker-compose.yml contém o nome da imagem que é criada quando o projeto é executado.</span><span class="sxs-lookup"><span data-stu-id="53984-137">The docker-compose.yml file contains the name of the image that is created when project is run.</span></span> 

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

<span data-ttu-id="53984-138">Neste exemplo, `image: user/hellodockertools${TAG}` gera a imagem `user/hellodockertools:dev` quando o aplicativo é executado no modo de **Depuração** e `user/hellodockertools:latest` no modo de **Lançamento**, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="53984-138">In this example, `image: user/hellodockertools${TAG}` generates the image `user/hellodockertools:dev` when the application is run in **Debug** mode and `user/hellodockertools:latest` in **Release** mode respectively.</span></span> 

<span data-ttu-id="53984-139">Você deve alterar o `user` para seu nome de usuário do Hub do Docker se planejar enviar a imagem por push para o Registro.</span><span class="sxs-lookup"><span data-stu-id="53984-139">You will want to change the `user` to your Docker Hub username if you plan to push the image to the registry.</span></span> <span data-ttu-id="53984-140">Por exemplo, `spboyer/hellodockertools`, ou altere a URL do seu Registro privado `privateregistry.domain.com/` dependendo da configuração.</span><span class="sxs-lookup"><span data-stu-id="53984-140">For example, `spboyer/hellodockertools`, or change to your private registry url `privateregistry.domain.com/` depending on your configuration.</span></span>

### <a name="debugging"></a><span data-ttu-id="53984-141">Depuração</span><span class="sxs-lookup"><span data-stu-id="53984-141">Debugging</span></span>

<span data-ttu-id="53984-142">Selecione **Docker** no menu suspenso de depuração na barra de ferramentas e use F5 para iniciar a depuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53984-142">Select **Docker** from the debug dropdown in the toolbar and use F5 to start debugging the application.</span></span> 

- <span data-ttu-id="53984-143">A imagem do microsoft/aspnetcore é adquirida (se ainda não estiver em seu cache)</span><span class="sxs-lookup"><span data-stu-id="53984-143">The microsoft/aspnetcore image is acquired (if not already in your cache)</span></span>
- <span data-ttu-id="53984-144">ASPNETCORE_ENVIRONMENT é definido como Desenvolvimento dentro do contêiner</span><span class="sxs-lookup"><span data-stu-id="53984-144">ASPNETCORE_ENVIRONMENT is set to Development within the container</span></span>
- <span data-ttu-id="53984-145">A PORTA 80 é EXPOSTA e mapeada para uma porta atribuída dinamicamente para o localhost.</span><span class="sxs-lookup"><span data-stu-id="53984-145">PORT 80 is EXPOSED and mapped to a dynamically assigned port for localhost.</span></span> <span data-ttu-id="53984-146">A porta é determinada pelo host do docker e pode ser consultada com o docker ps.</span><span class="sxs-lookup"><span data-stu-id="53984-146">The port is determined by the docker host and can be queried with docker ps.</span></span> 
- <span data-ttu-id="53984-147">Seu aplicativo é copiado para o contêiner</span><span class="sxs-lookup"><span data-stu-id="53984-147">Your application is copied to the container</span></span>
- <span data-ttu-id="53984-148">O navegador padrão é iniciado com o depurador anexado ao contêiner, usando a porta atribuída dinamicamente.</span><span class="sxs-lookup"><span data-stu-id="53984-148">Default browser is launched with the debugger attached to the container, using the dynamically assigned port.</span></span> 

<span data-ttu-id="53984-149">A imagem resultante do Docker criada é a imagem `dev` do seu aplicativo com as imagens `microsoft/aspnetcore` como a imagem base.</span><span class="sxs-lookup"><span data-stu-id="53984-149">The resulting Docker image built is the `dev` image of your application with the `microsoft/aspnetcore` images as the base image.</span></span>
<span data-ttu-id="53984-150">Observação: a imagem de desenvolvimento está vazia, o conteúdo do aplicativo, como configurações de Depuração, usam montagem de volume para fornecer uma experiência iterativa.</span><span class="sxs-lookup"><span data-stu-id="53984-150">Note: the dev image is empty of your app contents as Debug confgurations use volume mounting to provide the iterative experience.</span></span> <span data-ttu-id="53984-151">Para enviar uma imagem por push, use a configuração de Lançamento.</span><span class="sxs-lookup"><span data-stu-id="53984-151">To push an image, use the Release configuration.</span></span>

```console
REPOSITORY                  TAG         IMAGE ID            CREATED         SIZE
spboyer/hellodockertools    dev         0b6e2e44b3df        4 minutes ago   268.9 MB
microsoft/aspnetcore        1.0.1       189ad4312ce7        5 days ago      268.9 MB
```

<span data-ttu-id="53984-152">O aplicativo é executado usando o contêiner que pode ser visto executando o comando `docker ps`.</span><span class="sxs-lookup"><span data-stu-id="53984-152">The application is running using the container which you can see by running the `docker ps` command.</span></span>

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   4 minutes ago       Up 4 minutes        0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

### <a name="edit-and-continue"></a><span data-ttu-id="53984-153">Editar e continuar</span><span class="sxs-lookup"><span data-stu-id="53984-153">Edit and Continue</span></span>

<span data-ttu-id="53984-154">Alterações em arquivos estáticos e/ou arquivos de modelo do razor (.cshtml) são atualizadas automaticamente sem a necessidade de uma etapa de compilação.</span><span class="sxs-lookup"><span data-stu-id="53984-154">Changes to static files and/or razor template files (.cshtml) are automatically updated without the need of a compilation step.</span></span> <span data-ttu-id="53984-155">Faça a alteração, salve e toque em Atualizar no navegador para exibir a atualização.</span><span class="sxs-lookup"><span data-stu-id="53984-155">Make the change, save and tap refresh in the browser to view the update.</span></span>  

<span data-ttu-id="53984-156">Modificações em arquivos de código exigem a compilação e a reinicialização do Kestrel dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="53984-156">Modifications to code files require compiling and a restart of Kestrel within the container.</span></span> <span data-ttu-id="53984-157">Depois de fazer a alteração, use CTRL + F5 para executar o processo e iniciar o aplicativo dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="53984-157">After making the change, use CTRL + F5 to perform the process and start the application within the container.</span></span> <span data-ttu-id="53984-158">O contêiner Docker não é recriado ou interrompido; usando `docker ps` na linha de comando, você pode ver que o contêiner original ainda está em execução a partir de 10 minutos atrás.</span><span class="sxs-lookup"><span data-stu-id="53984-158">The Docker container is not rebuilt or stopped; using `docker ps` in the command line you can see that the original container is still running as of 10 minutes ago.</span></span> 

```console
CONTAINER ID        IMAGE                          COMMAND               CREATED             STATUS              PORTS                   NAMES
3f240cf686c9        spboyer/hellodockertools:dev   "tail -f /dev/null"   10 minutes ago      Up 10 minutes       0.0.0.0:32769->80/tcp   hellodockertools_hellodockertools_1
```

### <a name="publishing-docker-images"></a><span data-ttu-id="53984-159">Publicando imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="53984-159">Publishing Docker images</span></span>

<span data-ttu-id="53984-160">Depois de ter concluído o ciclo de desenvolvimento e depuração do seu aplicativo, o Ferramentas do Visual Studio para Docker ajudará você a criar a imagem de produção do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53984-160">Once you have completed the develop and debug cycle of your application, the Visual Studio Tools for Docker will help you create the production image of your application.</span></span> <span data-ttu-id="53984-161">Altere o menu suspenso de depuração para **Lançamento** e compile o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53984-161">Change the debug dropdown to **Release** and build the application.</span></span> <span data-ttu-id="53984-162">A ferramenta produzirá a imagem com o marcador `:latest` que você pode enviar por push para seu Registro privado ou Hub do Docker.</span><span class="sxs-lookup"><span data-stu-id="53984-162">The tooling will produce the image with the `:latest` tag which you can push to your private registry or Docker Hub.</span></span> 

<span data-ttu-id="53984-163">Usando o `docker images`, você pode ver a lista de imagens.</span><span class="sxs-lookup"><span data-stu-id="53984-163">Using the `docker images` you can see the list of images.</span></span>

```console
REPOSITORY                 TAG                 IMAGE ID            CREATED             SIZE
spboyer/hellodockertools   latest              8184ae38ba91        5 seconds ago       278.4 MB
spboyer/hellodockertools   dev                 0b6e2e44b3df        About an hour ago   268.9 MB
microsoft/aspnetcore       1.0.1               189ad4312ce7        5 days ago          268.9 MB
```

<span data-ttu-id="53984-164">Pode haver uma expectativa para a imagem de produção ou de lançamento serem menores em comparação à imagem de **desenvolvimento**, no entanto, com o uso do mapeamento de volume, o depurador e o aplicativo realmente foram executados em seu computador local e não dentro do contêiner.</span><span class="sxs-lookup"><span data-stu-id="53984-164">There may be an expectation for the production or release image to be smaller in size by comparison to the **dev** image, however through the use of the volume mapping; the debugger and application were actually being run from your local machine and not within the container.</span></span> <span data-ttu-id="53984-165">A imagem **mais recente** empacotou todo o código de aplicativo necessário para executar o aplicativo em um computador host, portanto, o delta é do tamanho do código do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="53984-165">The **latest** image has packaged the entire application code needed to run the application on a host machine, therefore the delta is the size of your application code.</span></span>

