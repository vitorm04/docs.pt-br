---
title: Criar ASP.NET Core aplicativos implantados como contêineres do Linux em clusters AKS/kubernetes
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.date: 08/06/2020
ms.openlocfilehash: 4b04e5d56c73918c665ad6e2825205870aac9606
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916439"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="07db3-103">Crie ASP.NET Core aplicativos implantados como contêineres do Linux em um orquestrador AKS/kubernetes</span><span class="sxs-lookup"><span data-stu-id="07db3-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="07db3-104">O AKS (Serviço de Kubernetes do Azure) é um serviço de orquestração do Kubernetes gerenciado pelo Azure que simplifica o gerenciamento e a implantação de contêiner.</span><span class="sxs-lookup"><span data-stu-id="07db3-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="07db3-105">Os principais recursos do AKS são:</span><span class="sxs-lookup"><span data-stu-id="07db3-105">AKS main features are:</span></span>

- <span data-ttu-id="07db3-106">Um plano de controle hospedado no Azure</span><span class="sxs-lookup"><span data-stu-id="07db3-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="07db3-107">Atualizações automatizadas</span><span class="sxs-lookup"><span data-stu-id="07db3-107">Automated upgrades</span></span>
- <span data-ttu-id="07db3-108">Autorrecuperação</span><span class="sxs-lookup"><span data-stu-id="07db3-108">Self-healing</span></span>
- <span data-ttu-id="07db3-109">Dimensionamento configurável pelo usuário</span><span class="sxs-lookup"><span data-stu-id="07db3-109">User-configurable scaling</span></span>
- <span data-ttu-id="07db3-110">Experiência de usuário mais simples para desenvolvedores e operadores de cluster.</span><span class="sxs-lookup"><span data-stu-id="07db3-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="07db3-111">Os exemplos a seguir exploram a criação de um aplicativo ASP.NET Core 3,1 que é executado no Linux e é implantado em um cluster AKS no Azure, enquanto o desenvolvimento é feito usando o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="07db3-111">The following examples explore the creation of an ASP.NET Core 3.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="07db3-112">Criando o projeto de ASP.NET Core usando o Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="07db3-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="07db3-113">O ASP.NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no GitHub.</span><span class="sxs-lookup"><span data-stu-id="07db3-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="07db3-114">Ele é multiplataforma e dá suporte ao Windows, macOS e Linux, bem como pode ser usado em dispositivos, na nuvem e em cenários inseridos/de IoT.</span><span class="sxs-lookup"><span data-stu-id="07db3-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="07db3-115">Este exemplo usa alguns projetos simples baseados em modelos do Visual Studio, de modo que você não precisa de muito conhecimento adicional para criar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="07db3-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="07db3-116">Você só precisa criar o projeto usando um modelo padrão que inclui todos os elementos para executar um pequeno projeto com uma API REST e um aplicativo Web com páginas Razor, usando a tecnologia ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="07db3-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 3.1 technology.</span></span>

![Adicione uma nova janela de projeto no Visual Studio selecionando o aplicativo Web ASP.NET Core.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="07db3-118">**Figura 4-35**.</span><span class="sxs-lookup"><span data-stu-id="07db3-118">**Figure 4-35**.</span></span> <span data-ttu-id="07db3-119">Criar um aplicativo Web ASP.NET Core no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="07db3-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="07db3-120">Para criar o projeto de exemplo no Visual Studio, selecione **arquivo**  >  **novo**  >  **projeto**, selecione o tipo de projeto **Web** e, em seguida, o modelo de **aplicativo Web ASP.NET Core** .</span><span class="sxs-lookup"><span data-stu-id="07db3-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="07db3-121">Você também pode pesquisar o modelo se precisar dele.</span><span class="sxs-lookup"><span data-stu-id="07db3-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="07db3-122">Em seguida, insira o nome do aplicativo e o local, conforme mostrado na próxima imagem.</span><span class="sxs-lookup"><span data-stu-id="07db3-122">Then enter the application name and location as shown in the next image.</span></span>

![Insira o nome do projeto e o local.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="07db3-124">**Figura 4-36**.</span><span class="sxs-lookup"><span data-stu-id="07db3-124">**Figure 4-36**.</span></span> <span data-ttu-id="07db3-125">Insira o nome do projeto e o local no Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="07db3-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="07db3-126">Verifique se você selecionou ASP.NET Core 3,1 como a estrutura.</span><span class="sxs-lookup"><span data-stu-id="07db3-126">Verify that you've selected ASP.NET Core 3.1 as the framework.</span></span> <span data-ttu-id="07db3-127">O .NET Core 3,1 está incluído na versão mais recente do Visual Studio 2019 e é automaticamente instalado e configurado para você quando você instala o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="07db3-127">.NET Core 3.1 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![Caixa de diálogo do Visual Studio para selecionar o tipo de um aplicativo Web do ASP.NET Core com a opção de API selecionada.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="07db3-129">**Figura 4-37**.</span><span class="sxs-lookup"><span data-stu-id="07db3-129">**Figure 4-37**.</span></span> <span data-ttu-id="07db3-130">Selecionando o ASP.NET CORE 3,1 e o tipo de projeto de API Web</span><span class="sxs-lookup"><span data-stu-id="07db3-130">Selecting ASP.NET CORE 3.1 and Web API project type</span></span>

<span data-ttu-id="07db3-131">Observe que o suporte ao Docker não está habilitado agora, apenas para mostrar que ele pode ser feito após a criação do projeto.</span><span class="sxs-lookup"><span data-stu-id="07db3-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="07db3-132">Se você tiver qualquer versão anterior do .NET Core, poderá baixar e instalar a versão 3,1 do <https://dotnet.microsoft.com/download> .</span><span class="sxs-lookup"><span data-stu-id="07db3-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="07db3-133">Para mostrar que você pode "Encaixer" seu projeto a qualquer momento, você adicionará suporte ao Docker agora.</span><span class="sxs-lookup"><span data-stu-id="07db3-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="07db3-134">Então, clique com o botão direito do mouse no nó do projeto em Gerenciador de soluções e selecione **Adicionar**  >  **suporte ao Docker** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="07db3-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opção de menu de contexto para adicionar suporte do Docker a um projeto existente: clique com o botão direito do mouse (no projeto) > adicionar > suporte do Docker.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="07db3-136">**Figura 4-38**.</span><span class="sxs-lookup"><span data-stu-id="07db3-136">**Figure 4-38**.</span></span> <span data-ttu-id="07db3-137">Adicionando suporte ao Docker a um projeto existente</span><span class="sxs-lookup"><span data-stu-id="07db3-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="07db3-138">Para concluir a adição de suporte ao Docker, você pode escolher Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="07db3-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="07db3-139">Nesse caso, selecione **Linux**.</span><span class="sxs-lookup"><span data-stu-id="07db3-139">In this case, select **Linux**.</span></span>

![Caixa de diálogo de opção para selecionar o sistema operacional de destino para o Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="07db3-141">**Figura 4-39**.</span><span class="sxs-lookup"><span data-stu-id="07db3-141">**Figure 4-39**.</span></span> <span data-ttu-id="07db3-142">Como selecionar contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="07db3-142">Selecting Linux containers.</span></span>

<span data-ttu-id="07db3-143">Com essas etapas simples, você tem seu aplicativo ASP.NET Core 3,1 em execução em um contêiner do Linux.</span><span class="sxs-lookup"><span data-stu-id="07db3-143">With these simple steps, you have your ASP.NET Core 3.1 application running on a Linux container.</span></span>

<span data-ttu-id="07db3-144">De forma semelhante, você também pode adicionar um projeto **webapp** muito simples (Figura 4-40) para consumir o ponto de extremidade da API Web, embora os detalhes não sejam discutidos aqui.</span><span class="sxs-lookup"><span data-stu-id="07db3-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="07db3-145">Depois disso, você adiciona suporte ao Orchestrator para seu projeto **WebApi** , conforme mostrado a seguir, na imagem 4-40.</span><span class="sxs-lookup"><span data-stu-id="07db3-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![Adicionando suporte ao Orchestrator ao projeto WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="07db3-147">**Figura 4-40**.</span><span class="sxs-lookup"><span data-stu-id="07db3-147">**Figure 4-40**.</span></span> <span data-ttu-id="07db3-148">Adicionando suporte ao Orchestrator ao projeto *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="07db3-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="07db3-149">Quando você escolhe a `Docker Compose` opção, o que é adequado para o desenvolvimento local, o Visual Studio adiciona o projeto de composição do Docker, com os arquivos Docker-Compose, conforme mostrado na imagem 4-41.</span><span class="sxs-lookup"><span data-stu-id="07db3-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Docker-Compose adicionado à solução](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="07db3-151">**Figura 4-41**.</span><span class="sxs-lookup"><span data-stu-id="07db3-151">**Figure 4-41**.</span></span> <span data-ttu-id="07db3-152">Adicionando suporte ao Orchestrator ao projeto *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="07db3-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="07db3-153">Os arquivos iniciais adicionados são semelhantes a estes:</span><span class="sxs-lookup"><span data-stu-id="07db3-153">The initial files added are similar to these ones:</span></span>

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

<span data-ttu-id="07db3-154">Para que seu aplicativo seja executado com Docker Compose você só precisa fazer alguns ajustes para`docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="07db3-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

<span data-ttu-id="07db3-155">Agora você pode executar seu aplicativo com a tecla **F5** ou usando o botão **Play** ou a tecla **Ctrl + F5** , selecionando o projeto Docker-Compose, conforme mostrado na imagem 4-42.</span><span class="sxs-lookup"><span data-stu-id="07db3-155">Now you can run your application with **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![Executando o projeto Docker-Compose com o Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="07db3-157">**Figura 4-42**.</span><span class="sxs-lookup"><span data-stu-id="07db3-157">**Figure 4-42**.</span></span> <span data-ttu-id="07db3-158">Adicionando suporte ao Orchestrator ao projeto *WebApi* .</span><span class="sxs-lookup"><span data-stu-id="07db3-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="07db3-159">Ao executar o aplicativo Docker-Compose, conforme explicado, você obtém:</span><span class="sxs-lookup"><span data-stu-id="07db3-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="07db3-160">As imagens criadas e os contêineres criados de acordo com o arquivo Docker-Compose.</span><span class="sxs-lookup"><span data-stu-id="07db3-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="07db3-161">O navegador é aberto no endereço configurado na caixa de diálogo "Propriedades" do `docker-compose` projeto.</span><span class="sxs-lookup"><span data-stu-id="07db3-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="07db3-162">A janela do **contêiner** aberta (no Visual Studio 2019 versão 16,4 e posterior).</span><span class="sxs-lookup"><span data-stu-id="07db3-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="07db3-163">Suporte do depurador para todos os projetos na solução, conforme mostrado nas imagens a seguir.</span><span class="sxs-lookup"><span data-stu-id="07db3-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="07db3-164">Navegador aberto:</span><span class="sxs-lookup"><span data-stu-id="07db3-164">Browser opened:</span></span>

![Exibição de navegador com aplicativo Web em execução](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="07db3-166">**Figura 4-43**.</span><span class="sxs-lookup"><span data-stu-id="07db3-166">**Figure 4-43**.</span></span> <span data-ttu-id="07db3-167">Janela do navegador com um aplicativo em execução em vários contêineres.</span><span class="sxs-lookup"><span data-stu-id="07db3-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="07db3-168">Janela contêineres:</span><span class="sxs-lookup"><span data-stu-id="07db3-168">Containers window:</span></span>

![Janela "contêineres" do Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="07db3-170">**Figura 4-44**.</span><span class="sxs-lookup"><span data-stu-id="07db3-170">**Figure 4-44**.</span></span> <span data-ttu-id="07db3-171">Janela "contêineres" do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="07db3-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="07db3-172">A janela **contêineres** permite exibir contêineres em execução, procurar imagens disponíveis, exibir variáveis de ambiente, logs e mapeamentos de porta, inspecionar o sistema de arquivos, anexar um depurador ou abrir uma janela de terminal dentro do ambiente de contêiner.</span><span class="sxs-lookup"><span data-stu-id="07db3-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="07db3-173">Como você pode ver, a integração entre o Visual Studio 2019 e o Docker é totalmente orientada à produtividade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="07db3-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="07db3-174">É claro que você também pode listar as imagens usando o `docker images` comando.</span><span class="sxs-lookup"><span data-stu-id="07db3-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="07db3-175">Você deve ver as `webapi` `webapp` imagens e com as `dev` marcas criadas pela implantação automática do nosso projeto com o Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="07db3-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![A saída do console do comando imagens do Docker mostra uma lista com: repositório, marca, ID da imagem, criado (Data) e tamanho.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="07db3-177">**Figura 4-45**.</span><span class="sxs-lookup"><span data-stu-id="07db3-177">**Figure 4-45**.</span></span> <span data-ttu-id="07db3-178">Exibição de imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="07db3-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="07db3-179">Registrar a solução em um ACR (registro de contêiner do Azure)</span><span class="sxs-lookup"><span data-stu-id="07db3-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="07db3-180">Você pode carregar as imagens no [ACR (registro de contêiner do Azure)](https://azure.microsoft.com/services/container-registry/), mas também pode usar o Hub do Docker ou qualquer outro registro, para que as imagens possam ser implantadas no cluster AKs desse registro.</span><span class="sxs-lookup"><span data-stu-id="07db3-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="07db3-181">Criar uma instância de ACR</span><span class="sxs-lookup"><span data-stu-id="07db3-181">Create an ACR instance</span></span>

<span data-ttu-id="07db3-182">Execute o seguinte comando na **CLI do AZ**:</span><span class="sxs-lookup"><span data-stu-id="07db3-182">Run the following command from the **az cli**:</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="07db3-183">Criar a imagem no modo de versão</span><span class="sxs-lookup"><span data-stu-id="07db3-183">Create the image in Release mode</span></span>

<span data-ttu-id="07db3-184">Agora, você criará a imagem no modo de **liberação** (pronto para produção) alterando para **lançamento**, conforme mostrado na Figura 4-46 e executando o aplicativo como fazia antes.</span><span class="sxs-lookup"><span data-stu-id="07db3-184">You'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-46, and running the application as you did before.</span></span>

![Opção de barra de ferramentas no VS para build no modo de versão.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="07db3-186">**Figura 4-46**.</span><span class="sxs-lookup"><span data-stu-id="07db3-186">**Figure 4-46**.</span></span> <span data-ttu-id="07db3-187">Como selecionar o modo de versão</span><span class="sxs-lookup"><span data-stu-id="07db3-187">Selecting Release Mode</span></span>

<span data-ttu-id="07db3-188">Se você executar o `docker images` comando, verá as duas imagens criadas, uma para `debug` (**dev**) e outra para o `release` modo (**mais recente**).</span><span class="sxs-lookup"><span data-stu-id="07db3-188">If you execute the `docker images` command, you'll see both images created, one for `debug` (**dev**) and the other for `release` (**latest**) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="07db3-189">Criar uma marca para a imagem</span><span class="sxs-lookup"><span data-stu-id="07db3-189">Create a new Tag for the Image</span></span>

<span data-ttu-id="07db3-190">Cada imagem de contêiner precisa ser marcada com o nome do `loginServer` do registro.</span><span class="sxs-lookup"><span data-stu-id="07db3-190">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="07db3-191">Essa marca é usada para roteamento ao enviar imagens de contêiner por push a um registro da imagem.</span><span class="sxs-lookup"><span data-stu-id="07db3-191">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="07db3-192">Você pode exibir o nome `loginServer` do portal do Azure com as informações do Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="07db3-192">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Exibição de navegador do nome do registro de contêiner do Azure, no canto superior direito.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="07db3-194">**Figura 4-47**.</span><span class="sxs-lookup"><span data-stu-id="07db3-194">**Figure 4-47**.</span></span> <span data-ttu-id="07db3-195">Exibição do nome do Registro</span><span class="sxs-lookup"><span data-stu-id="07db3-195">View of the name of the Registry</span></span>

<span data-ttu-id="07db3-196">Ou executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07db3-196">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Saída do console do comando acima.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="07db3-198">**Figura 4-48**.</span><span class="sxs-lookup"><span data-stu-id="07db3-198">**Figure 4-48**.</span></span> <span data-ttu-id="07db3-199">Obter o nome do registro usando **AZ CLI**</span><span class="sxs-lookup"><span data-stu-id="07db3-199">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="07db3-200">Em ambos os casos, você obterá o nome.</span><span class="sxs-lookup"><span data-stu-id="07db3-200">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="07db3-201">Em nosso exemplo, `exploredocker.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="07db3-201">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="07db3-202">Agora você pode marcar a imagem, usando a imagem mais recente (a imagem de versão), com o comando:</span><span class="sxs-lookup"><span data-stu-id="07db3-202">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="07db3-203">Depois de executar o comando `docker tag`, liste as imagens com o comando `docker images` e você deverá ver a imagem com a nova marca.</span><span class="sxs-lookup"><span data-stu-id="07db3-203">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Saída de console do comando de imagens do Docker.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="07db3-205">**Figura 4-49**.</span><span class="sxs-lookup"><span data-stu-id="07db3-205">**Figure 4-49**.</span></span> <span data-ttu-id="07db3-206">Exibição de imagens marcadas</span><span class="sxs-lookup"><span data-stu-id="07db3-206">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="07db3-207">Efetue push da imagem no ACR do Azure</span><span class="sxs-lookup"><span data-stu-id="07db3-207">Push the image into the Azure ACR</span></span>

<span data-ttu-id="07db3-208">Faça logon no Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="07db3-208">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="07db3-209">Efetue push da imagem no ACR do Azure usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07db3-209">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="07db3-210">Esse comando demora um pouco para carregar as imagens, mas fornece comentários sobre o processo.</span><span class="sxs-lookup"><span data-stu-id="07db3-210">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="07db3-211">Na imagem a seguir, você pode ver a saída de uma imagem concluída e outra em andamento.</span><span class="sxs-lookup"><span data-stu-id="07db3-211">In the following image you can see the output from one image completed and another in progress.</span></span>

![Saída do console do comando Docker Push.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="07db3-213">**Figura 4-50**.</span><span class="sxs-lookup"><span data-stu-id="07db3-213">**Figure 4-50**.</span></span> <span data-ttu-id="07db3-214">Saída do console do comando Push.</span><span class="sxs-lookup"><span data-stu-id="07db3-214">Console output from the push command.</span></span>

<span data-ttu-id="07db3-215">Para implantar seu aplicativo de vários contêineres em seu cluster do AKS, você precisa `.yaml` de alguns arquivos de manifesto que tenham, a maioria das propriedades obtidas dos `docker-compose.yml` `docker-compose.override.yml` arquivos e.</span><span class="sxs-lookup"><span data-stu-id="07db3-215">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> <span data-ttu-id="07db3-216">Os `.yml` arquivos anteriores só habilitam as `HTTP` portas, usando o `ASPNETCORE_URLS` parâmetro, para evitar problemas com o certificado ausente no aplicativo de exemplo.</span><span class="sxs-lookup"><span data-stu-id="07db3-216">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="07db3-217">Você pode ver como criar o Cluster do AKS para esta amostra na seção [**Implantar no AKS (Serviço de Kubernetes do Azure)**](deploy-azure-kubernetes-service.md) neste guia.</span><span class="sxs-lookup"><span data-stu-id="07db3-217">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="07db3-218">Agora você está quase pronto para implantar usando **kubectl**, mas primeiro você deve obter as credenciais do cluster AKs com este comando:</span><span class="sxs-lookup"><span data-stu-id="07db3-218">Now you're almost ready to deploy using **kubectl**, but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Saída do console do comando acima: "Explore-Docker-AKS" mesclado como o contexto atual em C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="07db3-220">**Figura 4-51**.</span><span class="sxs-lookup"><span data-stu-id="07db3-220">**Figure 4-51**.</span></span> <span data-ttu-id="07db3-221">Obter credenciais de AKS para o ambiente kubectl.</span><span class="sxs-lookup"><span data-stu-id="07db3-221">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="07db3-222">Você também precisa permitir que o cluster AKS Extraia imagens do ACR, usando este comando:</span><span class="sxs-lookup"><span data-stu-id="07db3-222">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="07db3-223">O comando anterior pode levar alguns minutos para ser concluído.</span><span class="sxs-lookup"><span data-stu-id="07db3-223">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="07db3-224">Em seguida, use o `kubectl apply` comando para iniciar as implantações e, em seguida, `kubectl get all` obtenha a lista de objetos de cluster.</span><span class="sxs-lookup"><span data-stu-id="07db3-224">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Saída do console dos comandos acima: implantações aplicadas.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="07db3-227">**Figura 4-52**.</span><span class="sxs-lookup"><span data-stu-id="07db3-227">**Figure 4-52**.</span></span> <span data-ttu-id="07db3-228">Implantação em kubernetes</span><span class="sxs-lookup"><span data-stu-id="07db3-228">Deployment to Kubernetes</span></span>

<span data-ttu-id="07db3-229">Você precisará aguardar um pouco até que o balanceador de carga obtenha o IP externo, verificando `kubectl get services` e, em seguida, o aplicativo deve estar disponível nesse endereço, conforme mostrado na próxima imagem:</span><span class="sxs-lookup"><span data-stu-id="07db3-229">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![Exibição de navegador do aplicativo implantado no AKS](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="07db3-231">**Figura 4-53**.</span><span class="sxs-lookup"><span data-stu-id="07db3-231">**Figure 4-53**.</span></span> <span data-ttu-id="07db3-232">Implantação em kubernetes</span><span class="sxs-lookup"><span data-stu-id="07db3-232">Deployment to Kubernetes</span></span>

<span data-ttu-id="07db3-233">Quando a implantação for concluída, você poderá acessar a [interface do usuário da Web do amKubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) com um proxy local, usando um túnel SSH.</span><span class="sxs-lookup"><span data-stu-id="07db3-233">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="07db3-234">Primeiro, você deve criar um ClusterRoleBinding com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="07db3-234">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="07db3-235">E, em seguida, esse comando para iniciar o proxy:</span><span class="sxs-lookup"><span data-stu-id="07db3-235">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="07db3-236">Uma janela do navegador deve ser aberta em `http://127.0.0.1:8001` com uma exibição semelhante a esta:</span><span class="sxs-lookup"><span data-stu-id="07db3-236">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Exibição de navegador do painel do Kubernetes mostrando Implantações, Pods, Conjuntos de Réplicas e Serviços.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="07db3-238">**Figura 4-54**.</span><span class="sxs-lookup"><span data-stu-id="07db3-238">**Figure 4-54**.</span></span> <span data-ttu-id="07db3-239">Exibição de informações de cluster do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="07db3-239">View Kubernetes cluster information</span></span>

<span data-ttu-id="07db3-240">Agora você tem seu aplicativo ASP.NET Core, executado em contêineres do Linux e implantado em um cluster AKS no Azure.</span><span class="sxs-lookup"><span data-stu-id="07db3-240">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="07db3-241">Para obter mais informações sobre implantação com o Kubernetes, consulte: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="07db3-241">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="07db3-242">[Anterior](set-up-windows-containers-with-powershell.md) 
>  [Avançar](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="07db3-242">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
