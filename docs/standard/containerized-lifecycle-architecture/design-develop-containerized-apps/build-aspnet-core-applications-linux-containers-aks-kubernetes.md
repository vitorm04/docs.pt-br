---
title: Criar aplicativos ASP.NET Core 2.1 implantados como contêineres do Linux em clusters AKS/Kubernetes
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: b03b6fab9dcd53e97c2bc4d7e5c958ca4b931077
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221452"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-akskubernetes-orchestrator"></a><span data-ttu-id="092d3-103">Criar aplicativos ASP.NET Core 2.1 implantados como contêineres do Linux para o orchestrator AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="092d3-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="092d3-104">Serviços de Kubernetes do Azure (AKS) é gerenciado Kubernetes orquestrações os serviços do Azure que simplificam o gerenciamento e implantação de contêiner.</span><span class="sxs-lookup"><span data-stu-id="092d3-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="092d3-105">Principais recursos do AKS são:</span><span class="sxs-lookup"><span data-stu-id="092d3-105">AKS main features are:</span></span>

- <span data-ttu-id="092d3-106">Um plano de controle hospedado no Azure</span><span class="sxs-lookup"><span data-stu-id="092d3-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="092d3-107">Atualizações automatizadas</span><span class="sxs-lookup"><span data-stu-id="092d3-107">Automated upgrades</span></span>
- <span data-ttu-id="092d3-108">Autorrecuperação</span><span class="sxs-lookup"><span data-stu-id="092d3-108">Self-healing</span></span>
- <span data-ttu-id="092d3-109">Dimensionamento configuráveis do usuário</span><span class="sxs-lookup"><span data-stu-id="092d3-109">User configurable scaling</span></span>
- <span data-ttu-id="092d3-110">Uma experiência de usuário mais simples para desenvolvedores e operadores do cluster.</span><span class="sxs-lookup"><span data-stu-id="092d3-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="092d3-111">Os exemplos a seguir explorar a criação de um aplicativo ASP.NET Core 2.1 é executado no Linux e implanta um Cluster AKS no Azure, enquanto o desenvolvimento é feito usando o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="092d3-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="092d3-112">Criando o projeto do ASP.NET Core 2.1 usando o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="092d3-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="092d3-113">ASP.NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no GitHub.</span><span class="sxs-lookup"><span data-stu-id="092d3-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="092d3-114">Ele é multiplataforma e dá suporte ao Windows, macOS e Linux, e pode ser usado em dispositivos, na nuvem e em cenários inseridos/IoT.</span><span class="sxs-lookup"><span data-stu-id="092d3-114">It is cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="092d3-115">Este exemplo usa um projeto simples que baseia-se com base em um modelo de API de Web do Visual Studio, que exige qualquer conhecimento adicional para criar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="092d3-115">This example uses a simple project that's based based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="092d3-116">Você só precisará criar o projeto usando um modelo padrão que inclui todos os elementos para executar um pequeno projeto com uma API REST, usando a tecnologia ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="092d3-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![Adicione janela novo projeto no Visual Studio, selecionando o aplicativo Web ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="092d3-118">**Figura 4 a 36**.</span><span class="sxs-lookup"><span data-stu-id="092d3-118">**Figure 4-36**.</span></span> <span data-ttu-id="092d3-119">Criando um aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="092d3-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="092d3-120">Para criar o projeto de exemplo, você precisa selecionar **arquivo** > **New** > **projeto** no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="092d3-120">To create the sample project, you have to select **File** > **New** > **Project** on Visual Studio.</span></span> <span data-ttu-id="092d3-121">Em seguida, você verá uma lista de modelos de vários tipos de projetos, onde você tem a ser procurado **Web** > **.NET Core** no painel à esquerda.</span><span class="sxs-lookup"><span data-stu-id="092d3-121">Then you'll see a list of templates for several types of projects, where you have to look for **Web** > **.NET Core** on the left panel.</span></span> <span data-ttu-id="092d3-122">Neste exemplo, selecione **aplicativo Web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="092d3-122">For this example select **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="092d3-123">Na próxima caixa de diálogo, verifique se você tiver selecionado o .NET Core e ASP.NET Core 2.1 como a estrutura de destino a superior na máquina, conforme mostrado na Figura 4-37 e, em seguida, selecione a opção de API, para criar um aplicativo de API Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="092d3-123">In the next dialog ensure that you have selected .NET Core and ASP.NET Core 2.1 as the target framework in the top pulldowns, as shown in figure 4-37, and then select the API option, to create an ASP.NET Core Web API application.</span></span>

<span data-ttu-id="092d3-124">O .NET Core 2.1 está incluído no Visual Studio 2017 versão 15.7.0 ou superior e é automaticamente instalado e configurado para você quando você seleciona os **desenvolvimento de plataforma cruzada do .NET Core** carga de trabalho durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="092d3-124">The .NET Core 2.1 is included in Visual Studio 2017 version 15.7.0 or higher and is automatically installed and configured for you when you select the **.NET Core cross-platform development** workload during installation.</span></span>

![Visual Studio caixa de diálogo para selecionar o tipo de um aplicativo Web do ASP.NET Core com a opção de API selecionada.](media/create-web-api-application.png)

<span data-ttu-id="092d3-126">**Figura 4-37**.</span><span class="sxs-lookup"><span data-stu-id="092d3-126">**Figure 4-37**.</span></span> <span data-ttu-id="092d3-127">Tipo de projeto do ASP.NET CORE 2.1 selecionando e API da Web</span><span class="sxs-lookup"><span data-stu-id="092d3-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="092d3-128">Se você tiver qualquer versão anterior do .NET Core, você pode baixar e instalar a versão 2.1 do <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="092d3-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="092d3-129">Você pode adicionar suporte ao Docker ao criar o projeto na etapa anterior, ou posterior, se for necessário depois de iniciar o projeto.</span><span class="sxs-lookup"><span data-stu-id="092d3-129">You can add Docker support when creating the project in the previous step, or later, if the need arises after starting the project.</span></span> <span data-ttu-id="092d3-130">Para adicionar o suporte ao Docker após a criação do projeto, clique com botão direito no arquivo de projeto na **Gerenciador de soluções** e selecione **Add** > **suporte ao Docker** em o menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="092d3-130">To add the Docker support after the project creation, right-click on the project file in the **Solution Explorer** and select **Add** > **Docker support** on the context menu.</span></span>

![Opção de menu de contexto para adicionar suporte ao Docker a um projeto existente: Clique com botão direito (no projeto) > Adicionar > suporte do Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="092d3-132">**Figura 4-38**.</span><span class="sxs-lookup"><span data-stu-id="092d3-132">**Figure 4-38**.</span></span> <span data-ttu-id="092d3-133">Adicionando suporte ao Docker ao projeto existente</span><span class="sxs-lookup"><span data-stu-id="092d3-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="092d3-134">Para concluir a adição de suporte ao Docker, você tem a opção de Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="092d3-134">To complete adding Docker support, you have the choice of Windows or Linux.</span></span> <span data-ttu-id="092d3-135">Nesse caso, selecione **Linux**, porque o AKS não dá suporte a contêineres do Windows (como o final de 2018).</span><span class="sxs-lookup"><span data-stu-id="092d3-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Caixa de diálogo de opção para selecionar o sistema operacional de destino para o Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="092d3-137">**Figura 4-39**.</span><span class="sxs-lookup"><span data-stu-id="092d3-137">**Figure 4-39**.</span></span> <span data-ttu-id="092d3-138">Selecionando os contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="092d3-138">Selecting Linux containers.</span></span>

<span data-ttu-id="092d3-139">Com estas etapas simples, você terá seu aplicativo ASP.NET Core 2.1 em execução em um contêiner do Linux.</span><span class="sxs-lookup"><span data-stu-id="092d3-139">With these simple steps, you will have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="092d3-140">Como você pode ver, a integração entre o Visual Studio 2017 e o Docker é totalmente orientada à produtividade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="092d3-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="092d3-141">Agora você pode pressionar **F5** para compilar e executar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="092d3-141">Now you can press **F5** to build and run your application.</span></span>

<span data-ttu-id="092d3-142">Depois de executar o projeto, você pode listar as imagens usando o `docker images` comando.</span><span class="sxs-lookup"><span data-stu-id="092d3-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="092d3-143">Você deve ver o `mssampleapplication` imagem criada com a implantação automática do nosso projeto no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="092d3-143">You should see the `mssampleapplication` image created with the automatic deploy of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Console de saída do comando de imagens do docker, mostra uma lista com: Repositório, marca, ID da imagem, criado (Data) e tamanho.](media/docker-images-command.png)

<span data-ttu-id="092d3-145">**Figura 4-40**.</span><span class="sxs-lookup"><span data-stu-id="092d3-145">**Figure 4-40**.</span></span> <span data-ttu-id="092d3-146">Modo de exibição de imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="092d3-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="092d3-147">Registre-se a solução no registro de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="092d3-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="092d3-148">Carregar a imagem em qualquer registro do Docker, como [registro de contêiner do Azure (ACR)](https://azure.microsoft.com/services/container-registry/) ou Hub do Docker para que as imagens podem ser implantadas no cluster AKS de que o registro.</span><span class="sxs-lookup"><span data-stu-id="092d3-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="092d3-149">Nesse caso, estamos está carregando a imagem no registro de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="092d3-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="092d3-150">Criar a imagem no modo de versão</span><span class="sxs-lookup"><span data-stu-id="092d3-150">Create the image in Release mode</span></span>

<span data-ttu-id="092d3-151">Criar a imagem no **versão** modo (pronto para produção) alterando a versão, conforme mostrado aqui e pressione F5 para executar o aplicativo novamente.</span><span class="sxs-lookup"><span data-stu-id="092d3-151">Create the image in **Release** Mode (ready for production) changing to Release as shown here and press F5 to run the application again.</span></span>

![Opção de barra de ferramentas no VS para compilar no modo de versão.](media/select-release-mode.png)

<span data-ttu-id="092d3-153">**Figura 4-41**.</span><span class="sxs-lookup"><span data-stu-id="092d3-153">**Figure 4-41**.</span></span> <span data-ttu-id="092d3-154">Selecionar modo de versão</span><span class="sxs-lookup"><span data-stu-id="092d3-154">Selecting Release Mode</span></span>

<span data-ttu-id="092d3-155">Se você executar o `docker image` comando, você verá as duas imagens criadas.</span><span class="sxs-lookup"><span data-stu-id="092d3-155">If you execute the `docker image` command, you'll see both images created.</span></span> <span data-ttu-id="092d3-156">Um para `debug` e outro para `release` modo.</span><span class="sxs-lookup"><span data-stu-id="092d3-156">One for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="092d3-157">Criar uma nova marca para a imagem</span><span class="sxs-lookup"><span data-stu-id="092d3-157">Create a new Tag for the Image</span></span>

<span data-ttu-id="092d3-158">Cada imagem de contêiner precisa ser marcada com o `loginServer` nome do registro.</span><span class="sxs-lookup"><span data-stu-id="092d3-158">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="092d3-159">Essa marca é usada para roteamento ao enviar imagens de contêiner para um registro de imagem.</span><span class="sxs-lookup"><span data-stu-id="092d3-159">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="092d3-160">Você pode exibir o `loginServer` nome do portal do Azure, levando as informações do registro de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="092d3-160">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Exibição de navegador do nome do registro de contêiner do Azure, no canto superior direito.](media/loginServer-name.png)

<span data-ttu-id="092d3-162">**Figura 4-42**.</span><span class="sxs-lookup"><span data-stu-id="092d3-162">**Figure 4-42**.</span></span> <span data-ttu-id="092d3-163">Modo de exibição do nome do registro</span><span class="sxs-lookup"><span data-stu-id="092d3-163">View of the name of the Registry</span></span>

<span data-ttu-id="092d3-164">Ou executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="092d3-164">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Console de saída do comando acima.](media/az-cli-loginServer-name.png)

<span data-ttu-id="092d3-166">**Figura 4-43**.</span><span class="sxs-lookup"><span data-stu-id="092d3-166">**Figure 4-43**.</span></span> <span data-ttu-id="092d3-167">Obter o nome do registro usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="092d3-167">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="092d3-168">Em ambos os casos, você obterá o nome.</span><span class="sxs-lookup"><span data-stu-id="092d3-168">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="092d3-169">Em nosso exemplo, `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="092d3-169">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="092d3-170">Agora você pode marcar a imagem, levando a imagem mais recente (imagem de versão), com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="092d3-170">Now you can tag the image, taking the latest image (Release image), with the following command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="092d3-171">Depois de executar o `docker tag` de comando, liste as imagens com o `docker images` comando.</span><span class="sxs-lookup"><span data-stu-id="092d3-171">After running the `docker tag` command, list the images with the `docker images` command.</span></span> <span data-ttu-id="092d3-172">Você deve ver a imagem com a nova marca.</span><span class="sxs-lookup"><span data-stu-id="092d3-172">You should see the image with the new tag.</span></span>

![Console de saída do comando de imagens do docker.](media/tagged-docker-images-list.png)

<span data-ttu-id="092d3-174">**Figura 4-44**.</span><span class="sxs-lookup"><span data-stu-id="092d3-174">**Figure 4-44**.</span></span> <span data-ttu-id="092d3-175">Modo de exibição de imagens marcadas</span><span class="sxs-lookup"><span data-stu-id="092d3-175">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="092d3-176">A imagem por push o ACR do Azure</span><span class="sxs-lookup"><span data-stu-id="092d3-176">Push the image into the Azure ACR</span></span>

<span data-ttu-id="092d3-177">Envie a imagem no ACR do Azure, usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="092d3-177">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="092d3-178">Esse comando leva algum tempo, mas fornece comentários no processo de carregamento das imagens.</span><span class="sxs-lookup"><span data-stu-id="092d3-178">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Saída do comando docker por push do console: mostra uma barra de progresso com base em caracteres para cada camada.](media/uploading-image-to-acr.png)

<span data-ttu-id="092d3-180">**Figura 4-45**.</span><span class="sxs-lookup"><span data-stu-id="092d3-180">**Figure 4-45**.</span></span> <span data-ttu-id="092d3-181">Carregando a imagem no ACR</span><span class="sxs-lookup"><span data-stu-id="092d3-181">Uploading the image to the ACR</span></span>

<span data-ttu-id="092d3-182">Você pode ver abaixo o resultado que deve ser obter quando o processo for concluído:</span><span class="sxs-lookup"><span data-stu-id="092d3-182">You can see below the result you should get when the process completes:</span></span>

![O comando de envio por push do docker, concluído, mostrando todas as camadas ou nós de saída de console.](media/uploading-docker-images-complete.png)

<span data-ttu-id="092d3-184">**Figura 4-46**.</span><span class="sxs-lookup"><span data-stu-id="092d3-184">**Figure 4-46**.</span></span> <span data-ttu-id="092d3-185">Exibição de nós</span><span class="sxs-lookup"><span data-stu-id="092d3-185">View of nodes</span></span>

<span data-ttu-id="092d3-186">A próxima etapa é implantar seu contêiner em seu cluster AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="092d3-186">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="092d3-187">Para que você precisa de um arquivo (**implantar o arquivo. yml**) que, nesse caso, contém:</span><span class="sxs-lookup"><span data-stu-id="092d3-187">For that you need a file (**.yml deploy file**) that, in this case, contains:</span></span>

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - mane: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> <span data-ttu-id="092d3-188">Para obter mais informações sobre a implantação com Kubernetes, consulte: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="092d3-188">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="092d3-189">Agora você está quase pronto para implantar usando **Kubectl**, mas primeiro você deve obter as credenciais para o Cluster do AKS com este comando:</span><span class="sxs-lookup"><span data-stu-id="092d3-189">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Console de saída do comando acima: Mesclado "MSSampleK8Cluster como o contexto atual no /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="092d3-191">**Figura 4-47**.</span><span class="sxs-lookup"><span data-stu-id="092d3-191">**Figure 4-47**.</span></span> <span data-ttu-id="092d3-192">obtenção de credenciais</span><span class="sxs-lookup"><span data-stu-id="092d3-192">getting credentials</span></span>

<span data-ttu-id="092d3-193">Em seguida, use o `kubectl create` comando para iniciar a implantação.</span><span class="sxs-lookup"><span data-stu-id="092d3-193">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Saída do comando acima do console: implantação "mssamplesbook" foi criado.](media/kubectl-create-command.png)

<span data-ttu-id="092d3-196">**Figura 4-48**.</span><span class="sxs-lookup"><span data-stu-id="092d3-196">**Figure 4-48**.</span></span> <span data-ttu-id="092d3-197">Implantar no Kubernetes</span><span class="sxs-lookup"><span data-stu-id="092d3-197">Deploy to Kubernetes</span></span>

<span data-ttu-id="092d3-198">Quando a implantação for concluída, você pode acessar o console do Kubernetes com um proxy local que você pode acessar temporariamente com este comando:</span><span class="sxs-lookup"><span data-stu-id="092d3-198">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="092d3-199">E acessar a url `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="092d3-199">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Exibição de navegador do painel do Kubernetes, mostrando os Pods, implantações, conjuntos de réplicas e serviços.](media/kubernetes-cluster-information.png)

<span data-ttu-id="092d3-201">**Figura 4-49**.</span><span class="sxs-lookup"><span data-stu-id="092d3-201">**Figure 4-49**.</span></span> <span data-ttu-id="092d3-202">Exibir informações de cluster do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="092d3-202">View Kubernetes cluster information</span></span>

<span data-ttu-id="092d3-203">Agora você tem o seu aplicativo estiver implantado no Azure, usando um contêiner do Linux e um Cluster do AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="092d3-203">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="092d3-204">Você pode acessar seu aplicativo navegando até o IP público do seu serviço, que pode ser obtido do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="092d3-204">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="092d3-205">Você pode ver como criar o Cluster do AKS para este exemplo na seção [ **implantar para o serviço de Kubernetes do Azure (AKS)** ](deploy-azure-kubernetes-service.md) sobre este guia.</span><span class="sxs-lookup"><span data-stu-id="092d3-205">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="092d3-206">[Anterior](set-up-windows-containers-with-powershell.md)
>[Próximo](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="092d3-206">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
