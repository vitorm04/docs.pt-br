---
title: Criar aplicativos ASP.NET Core 2.1 implantados como contêineres do Linux em clusters AKS/Kubernetes
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/25/2019
ms.openlocfilehash: c6d778d345466b1b852d06bc01ce40ccfdebf964
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676649"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="4c86f-103">Criar aplicativos ASP.NET Core 2.1 implantados como contêineres do Linux em um orquestrador AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="4c86f-103">Build ASP.NET Core 2.1 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="4c86f-104">Serviços de Kubernetes do Azure (AKS) é gerenciado Kubernetes orquestrações os serviços do Azure que simplificam o gerenciamento e implantação de contêiner.</span><span class="sxs-lookup"><span data-stu-id="4c86f-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="4c86f-105">Principais recursos do AKS são:</span><span class="sxs-lookup"><span data-stu-id="4c86f-105">AKS main features are:</span></span>

- <span data-ttu-id="4c86f-106">Um plano de controle hospedado no Azure</span><span class="sxs-lookup"><span data-stu-id="4c86f-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="4c86f-107">Atualizações automatizadas</span><span class="sxs-lookup"><span data-stu-id="4c86f-107">Automated upgrades</span></span>
- <span data-ttu-id="4c86f-108">Autorrecuperação</span><span class="sxs-lookup"><span data-stu-id="4c86f-108">Self-healing</span></span>
- <span data-ttu-id="4c86f-109">Dimensionamento configuráveis do usuário</span><span class="sxs-lookup"><span data-stu-id="4c86f-109">User configurable scaling</span></span>
- <span data-ttu-id="4c86f-110">Uma experiência de usuário mais simples para desenvolvedores e operadores do cluster.</span><span class="sxs-lookup"><span data-stu-id="4c86f-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="4c86f-111">Os exemplos a seguir explorar a criação de um aplicativo ASP.NET Core 2.1 é executado no Linux e implanta um Cluster AKS no Azure, enquanto o desenvolvimento é feito usando o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4c86f-111">The following examples explore the creation of an ASP.NET Core 2.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a><span data-ttu-id="4c86f-112">Criando o projeto do ASP.NET Core 2.1 usando o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4c86f-112">Creating the ASP.NET Core 2.1 Project using Visual Studio 2017</span></span>

<span data-ttu-id="4c86f-113">ASP.NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no GitHub.</span><span class="sxs-lookup"><span data-stu-id="4c86f-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="4c86f-114">Ele é multiplataforma, que dão suporte a Windows, macOS e Linux e pode ser usado em cenários inseridos/IoT, nuvem e dispositivo.</span><span class="sxs-lookup"><span data-stu-id="4c86f-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="4c86f-115">Este exemplo usa um projeto simples com base em um modelo de API de Web do Visual Studio, que exige qualquer conhecimento adicional para criar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="4c86f-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="4c86f-116">Você só precisará criar o projeto usando um modelo padrão que inclui todos os elementos para executar um pequeno projeto com uma API REST, usando a tecnologia ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="4c86f-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.1 technology.</span></span>

![Adicione janela novo projeto no Visual Studio, selecionando o aplicativo Web ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="4c86f-118">**Figura 4 a 36**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-118">**Figure 4-36**.</span></span> <span data-ttu-id="4c86f-119">Criando um aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4c86f-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="4c86f-120">Para criar o projeto de exemplo no Visual Studio, selecione **arquivo** > **New** > **projeto**, selecione o **Web**tipos de projeto no painel esquerdo, seguido por **aplicativo Web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="4c86f-121">Visual Studio contém modelos para projetos web.</span><span class="sxs-lookup"><span data-stu-id="4c86f-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="4c86f-122">Para nosso exemplo, selecione **API** para criar um aplicativo de API Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4c86f-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="4c86f-123">Verifique se que você tenha selecionado o ASP.NET Core 2.1 como a estrutura.</span><span class="sxs-lookup"><span data-stu-id="4c86f-123">Verify that you've selected ASP.NET Core 2.1 as the framework.</span></span> <span data-ttu-id="4c86f-124">.NET core 2.1 está incluído na última versão do Visual Studio 2017 e é automaticamente instalado e configurado para você quando você instala o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4c86f-124">.NET Core 2.1 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Visual Studio caixa de diálogo para selecionar o tipo de um aplicativo Web do ASP.NET Core com a opção de API selecionada.](media/create-web-api-application.png)

<span data-ttu-id="4c86f-126">**Figura 4-37**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-126">**Figure 4-37**.</span></span> <span data-ttu-id="4c86f-127">Tipo de projeto do ASP.NET CORE 2.1 selecionando e API da Web</span><span class="sxs-lookup"><span data-stu-id="4c86f-127">Selecting ASP.NET CORE 2.1 and Web API project type</span></span>

<span data-ttu-id="4c86f-128">Se você tiver qualquer versão anterior do .NET Core, você pode baixar e instalar a versão 2.1 do <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="4c86f-128">If you have any previous version of .NET Core, you can download and install the 2.1 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="4c86f-129">Você pode adicionar suporte ao Docker ao criar o projeto ou posteriormente, portanto, você pode "colocar no Docker" seu projeto a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="4c86f-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="4c86f-130">Para adicionar suporte ao Docker após a criação do projeto, clique com botão direito no nó do projeto no Gerenciador de soluções e selecione **Add** > **suporte ao Docker** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="4c86f-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opção de menu de contexto para adicionar suporte ao Docker a um projeto existente: Clique com botão direito (no projeto) > Adicionar > suporte do Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="4c86f-132">**Figura 4-38**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-132">**Figure 4-38**.</span></span> <span data-ttu-id="4c86f-133">Adicionando suporte ao Docker ao projeto existente</span><span class="sxs-lookup"><span data-stu-id="4c86f-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="4c86f-134">Para concluir a adição de suporte ao Docker, você pode escolher Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="4c86f-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="4c86f-135">Nesse caso, selecione **Linux**, porque o AKS não dá suporte a contêineres do Windows (como o final de 2018).</span><span class="sxs-lookup"><span data-stu-id="4c86f-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Caixa de diálogo de opção para selecionar o sistema operacional de destino para o Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="4c86f-137">**Figura 4-39**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-137">**Figure 4-39**.</span></span> <span data-ttu-id="4c86f-138">Selecionando os contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="4c86f-138">Selecting Linux containers.</span></span>

<span data-ttu-id="4c86f-139">Com estas etapas simples, você precisa de seu aplicativo ASP.NET Core 2.1 em execução em um contêiner do Linux.</span><span class="sxs-lookup"><span data-stu-id="4c86f-139">With these simple steps, you have your ASP.NET Core 2.1 application running on a Linux container.</span></span>

<span data-ttu-id="4c86f-140">Como você pode ver, a integração entre o Visual Studio 2017 e o Docker é totalmente orientada à produtividade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="4c86f-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="4c86f-141">Agora você pode executar seu aplicativo com o **F5** da chave ou usando o **reproduzir** botão.</span><span class="sxs-lookup"><span data-stu-id="4c86f-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="4c86f-142">Depois de executar o projeto, você pode listar as imagens usando o `docker images` comando.</span><span class="sxs-lookup"><span data-stu-id="4c86f-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="4c86f-143">Você deve ver o `mssampleapplication` imagem criada pela implantação automática do nosso projeto no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="4c86f-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![Console de saída do comando de imagens do docker, mostra uma lista com: Repositório, marca, ID da imagem, criado (Data) e tamanho.](media/docker-images-command.png)

<span data-ttu-id="4c86f-145">**Figura 4-40**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-145">**Figure 4-40**.</span></span> <span data-ttu-id="4c86f-146">Modo de exibição de imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="4c86f-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="4c86f-147">Registre-se a solução no registro de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="4c86f-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="4c86f-148">Carregar a imagem em qualquer registro do Docker, como [registro de contêiner do Azure (ACR)](https://azure.microsoft.com/services/container-registry/) ou Hub do Docker, portanto, as imagens podem ser implantadas no cluster AKS de que o registro.</span><span class="sxs-lookup"><span data-stu-id="4c86f-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="4c86f-149">Nesse caso, estamos está carregando a imagem no registro de contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="4c86f-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="4c86f-150">Criar a imagem no modo de versão</span><span class="sxs-lookup"><span data-stu-id="4c86f-150">Create the image in Release mode</span></span>

<span data-ttu-id="4c86f-151">Agora, vamos criar a imagem no **Release** modo (pronto para produção), alterando para **versão**, conforme mostrado na Figura 4-41 e a execução do aplicativo, como fizemos antes.</span><span class="sxs-lookup"><span data-stu-id="4c86f-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Opção de barra de ferramentas no VS para compilar no modo de versão.](media/select-release-mode.png)

<span data-ttu-id="4c86f-153">**Figura 4-41**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-153">**Figure 4-41**.</span></span> <span data-ttu-id="4c86f-154">Selecionar modo de versão</span><span class="sxs-lookup"><span data-stu-id="4c86f-154">Selecting Release Mode</span></span>

<span data-ttu-id="4c86f-155">Se você executar o `docker image` comando, você verá as duas imagens criadas, um para `debug` e o outro para `release` modo.</span><span class="sxs-lookup"><span data-stu-id="4c86f-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="4c86f-156">Criar uma nova marca para a imagem</span><span class="sxs-lookup"><span data-stu-id="4c86f-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="4c86f-157">Cada imagem de contêiner precisa ser marcada com o `loginServer` nome do registro.</span><span class="sxs-lookup"><span data-stu-id="4c86f-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="4c86f-158">Essa marca é usada para roteamento ao enviar imagens de contêiner para um registro de imagem.</span><span class="sxs-lookup"><span data-stu-id="4c86f-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="4c86f-159">Você pode exibir o `loginServer` nome do portal do Azure, levando as informações do registro de contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="4c86f-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Exibição de navegador do nome do registro de contêiner do Azure, no canto superior direito.](media/loginServer-name.png)

<span data-ttu-id="4c86f-161">**Figura 4-42**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-161">**Figure 4-42**.</span></span> <span data-ttu-id="4c86f-162">Modo de exibição do nome do registro</span><span class="sxs-lookup"><span data-stu-id="4c86f-162">View of the name of the Registry</span></span>

<span data-ttu-id="4c86f-163">Ou executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4c86f-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Console de saída do comando acima.](media/az-cli-loginServer-name.png)

<span data-ttu-id="4c86f-165">**Figura 4-43**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-165">**Figure 4-43**.</span></span> <span data-ttu-id="4c86f-166">Obter o nome do registro usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="4c86f-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="4c86f-167">Em ambos os casos, você obterá o nome.</span><span class="sxs-lookup"><span data-stu-id="4c86f-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="4c86f-168">Em nosso exemplo, `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="4c86f-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="4c86f-169">Agora você pode marcar a imagem, levando a imagem mais recente (a imagem de versão), com o comando:</span><span class="sxs-lookup"><span data-stu-id="4c86f-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="4c86f-170">Depois de executar o `docker tag` de comando, liste as imagens com o `docker images` comando e você deverá ver a imagem com a nova marca.</span><span class="sxs-lookup"><span data-stu-id="4c86f-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Console de saída do comando de imagens do docker.](media/tagged-docker-images-list.png)

<span data-ttu-id="4c86f-172">**Figura 4-44**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-172">**Figure 4-44**.</span></span> <span data-ttu-id="4c86f-173">Modo de exibição de imagens marcadas</span><span class="sxs-lookup"><span data-stu-id="4c86f-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="4c86f-174">A imagem por push o ACR do Azure</span><span class="sxs-lookup"><span data-stu-id="4c86f-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="4c86f-175">Envie a imagem no ACR do Azure, usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="4c86f-175">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="4c86f-176">Esse comando leva algum tempo, mas fornece comentários no processo de carregamento das imagens.</span><span class="sxs-lookup"><span data-stu-id="4c86f-176">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Saída do comando docker por push do console: mostra uma barra de progresso com base em caracteres para cada camada.](media/uploading-image-to-acr.png)

<span data-ttu-id="4c86f-178">**Figura 4-45**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-178">**Figure 4-45**.</span></span> <span data-ttu-id="4c86f-179">Carregando a imagem no ACR</span><span class="sxs-lookup"><span data-stu-id="4c86f-179">Uploading the image to the ACR</span></span>

<span data-ttu-id="4c86f-180">Você pode ver abaixo o resultado que deve ser obter quando o processo for concluído:</span><span class="sxs-lookup"><span data-stu-id="4c86f-180">You can see below the result you should get when the process completes:</span></span>

![O comando de envio por push do docker, concluído, mostrando todas as camadas ou nós de saída de console.](media/uploading-docker-images-complete.png)

<span data-ttu-id="4c86f-182">**Figura 4-46**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-182">**Figure 4-46**.</span></span> <span data-ttu-id="4c86f-183">Exibição de nós</span><span class="sxs-lookup"><span data-stu-id="4c86f-183">View of nodes</span></span>

<span data-ttu-id="4c86f-184">A próxima etapa é implantar seu contêiner em seu cluster AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="4c86f-184">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="4c86f-185">Para fazer isso, você precisa de um arquivo (**implantar o arquivo. yml**) que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4c86f-185">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
> <span data-ttu-id="4c86f-186">Para obter mais informações sobre a implantação com Kubernetes, consulte: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="4c86f-186">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="4c86f-187">Agora você está quase pronto para implantar usando **Kubectl**, mas primeiro você deve obter as credenciais para o Cluster do AKS com este comando:</span><span class="sxs-lookup"><span data-stu-id="4c86f-187">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Console de saída do comando acima: Mesclado "MSSampleK8Cluster como o contexto atual no /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="4c86f-189">**Figura 4-47**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-189">**Figure 4-47**.</span></span> <span data-ttu-id="4c86f-190">obtenção de credenciais</span><span class="sxs-lookup"><span data-stu-id="4c86f-190">getting credentials</span></span>

<span data-ttu-id="4c86f-191">Em seguida, use o `kubectl create` comando para iniciar a implantação.</span><span class="sxs-lookup"><span data-stu-id="4c86f-191">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Saída do comando acima do console: implantação "mssamplesbook" foi criado.](media/kubectl-create-command.png)

<span data-ttu-id="4c86f-194">**Figura 4-48**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-194">**Figure 4-48**.</span></span> <span data-ttu-id="4c86f-195">Implantar no Kubernetes</span><span class="sxs-lookup"><span data-stu-id="4c86f-195">Deploy to Kubernetes</span></span>

<span data-ttu-id="4c86f-196">Quando a implantação for concluída, você pode acessar o console do Kubernetes com um proxy local que você pode acessar temporariamente com este comando:</span><span class="sxs-lookup"><span data-stu-id="4c86f-196">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="4c86f-197">E acessar a url `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="4c86f-197">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Exibição de navegador do painel do Kubernetes, mostrando os Pods, implantações, conjuntos de réplicas e serviços.](media/kubernetes-cluster-information.png)

<span data-ttu-id="4c86f-199">**Figura 4-49**.</span><span class="sxs-lookup"><span data-stu-id="4c86f-199">**Figure 4-49**.</span></span> <span data-ttu-id="4c86f-200">Exibir informações de cluster do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="4c86f-200">View Kubernetes cluster information</span></span>

<span data-ttu-id="4c86f-201">Agora você tem o seu aplicativo estiver implantado no Azure, usando um contêiner do Linux e um Cluster do AKS Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="4c86f-201">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="4c86f-202">Você pode acessar seu aplicativo navegando até o IP público do seu serviço, que pode ser obtido do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="4c86f-202">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="4c86f-203">Você pode ver como criar o Cluster do AKS para este exemplo na seção [ **implantar para o serviço de Kubernetes do Azure (AKS)** ](deploy-azure-kubernetes-service.md) sobre este guia.</span><span class="sxs-lookup"><span data-stu-id="4c86f-203">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4c86f-204">[Anterior](set-up-windows-containers-with-powershell.md)
>[Próximo](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="4c86f-204">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
