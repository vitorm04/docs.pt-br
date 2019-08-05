---
title: Criar aplicativos ASP.NET Core 2.2 implantados como contêineres do Linux nos clusters do AKS/Kubernetes
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
ms.date: 02/25/2019
ms.openlocfilehash: 89843e0041c12f001f974360da2e5903499155d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68672573"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="c7884-103">Criar aplicativos ASP.NET Core 2.2 implantados como contêineres do Linux em um orquestrador do AKS/Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c7884-103">Build ASP.NET Core 2.2 applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="c7884-104">O AKS (Serviço de Kubernetes do Azure) é um serviço de orquestração do Kubernetes gerenciado pelo Azure que simplifica o gerenciamento e a implantação de contêiner.</span><span class="sxs-lookup"><span data-stu-id="c7884-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="c7884-105">Os principais recursos do AKS são:</span><span class="sxs-lookup"><span data-stu-id="c7884-105">AKS main features are:</span></span>

- <span data-ttu-id="c7884-106">Um plano de controle hospedado no Azure</span><span class="sxs-lookup"><span data-stu-id="c7884-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="c7884-107">Atualizações automatizadas</span><span class="sxs-lookup"><span data-stu-id="c7884-107">Automated upgrades</span></span>
- <span data-ttu-id="c7884-108">Autorrecuperação</span><span class="sxs-lookup"><span data-stu-id="c7884-108">Self-healing</span></span>
- <span data-ttu-id="c7884-109">Escala configurável pelo usuário</span><span class="sxs-lookup"><span data-stu-id="c7884-109">User configurable scaling</span></span>
- <span data-ttu-id="c7884-110">Uma experiência de usuário mais simples para desenvolvedores e operadores de cluster.</span><span class="sxs-lookup"><span data-stu-id="c7884-110">A simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="c7884-111">Os exemplos a seguir exploram a criação de um aplicativo ASP.NET Core 2.2 que é executado no Linux e implanta um cluster do AKS no Azure, enquanto o desenvolvimento é feito usando o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c7884-111">The following examples explore the creation of an ASP.NET Core 2.2 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2017.</span></span>

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a><span data-ttu-id="c7884-112">Como criar o projeto do ASP.NET Core 2.2 usando o Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c7884-112">Creating the ASP.NET Core 2.2 Project using Visual Studio 2017</span></span>

<span data-ttu-id="c7884-113">O ASP.NET Core é uma plataforma de desenvolvimento de uso geral mantida pela Microsoft e pela comunidade .NET no GitHub.</span><span class="sxs-lookup"><span data-stu-id="c7884-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="c7884-114">Ele é multiplataforma e dá suporte ao Windows, macOS e Linux, bem como pode ser usado em dispositivos, na nuvem e em cenários inseridos/de IoT.</span><span class="sxs-lookup"><span data-stu-id="c7884-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="c7884-115">Este exemplo usa um projeto simples com base em um modelo de API Web do Visual Studio, que não precisa de conhecimento adicional para criar o exemplo.</span><span class="sxs-lookup"><span data-stu-id="c7884-115">This example uses a simple project that's based on a Visual Studio Web API template, so you don't need any additional knowledge to create the sample.</span></span> <span data-ttu-id="c7884-116">Você só precisará criar o projeto usando um modelo padrão que inclua todos os elementos para executar um pequeno projeto com uma API REST, usando a tecnologia ASP.NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="c7884-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API, using ASP.NET Core 2.2 technology.</span></span>

![Adicione uma nova janela de projeto no Visual Studio selecionando o aplicativo Web ASP.NET Core.](media/create-aspnet-core-application.png)

<span data-ttu-id="c7884-118">**Figura 4-36**.</span><span class="sxs-lookup"><span data-stu-id="c7884-118">**Figure 4-36**.</span></span> <span data-ttu-id="c7884-119">Como criar um aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c7884-119">Creating ASP.NET Core Application</span></span>

<span data-ttu-id="c7884-120">Para criar o projeto de exemplo no Visual Studio, selecione **Arquivo** > **Novo** > **Projeto**, selecione os tipos de projeto **Web** no painel esquerdo, seguido por **Aplicativo Web ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="c7884-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project types in the left pane, followed by **ASP.NET Core Web Application**.</span></span>

<span data-ttu-id="c7884-121">O Visual Studio lista modelos para projetos Web.</span><span class="sxs-lookup"><span data-stu-id="c7884-121">Visual Studio lists templates for web projects.</span></span> <span data-ttu-id="c7884-122">Para nosso exemplo, selecione **API** para criar um aplicativo ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="c7884-122">For our example, select **API** to create an ASP.NET Web API Application.</span></span>

<span data-ttu-id="c7884-123">Verifique se você selecionou o ASP.NET Core 2.2 como a estrutura.</span><span class="sxs-lookup"><span data-stu-id="c7884-123">Verify that you've selected ASP.NET Core 2.2 as the framework.</span></span> <span data-ttu-id="c7884-124">O .NET Core 2.2 é incluído na última versão do Visual Studio 2017 e é automaticamente instalado e configurado quando você instala o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c7884-124">.NET Core 2.2 is included in the last version of Visual Studio 2017 and is automatically installed and configured for you when you install Visual Studio 2017.</span></span>

![Caixa de diálogo do Visual Studio para selecionar o tipo de um aplicativo Web do ASP.NET Core com a opção de API selecionada.](media/create-web-api-application.png)

<span data-ttu-id="c7884-126">**Figura 4-37**.</span><span class="sxs-lookup"><span data-stu-id="c7884-126">**Figure 4-37**.</span></span> <span data-ttu-id="c7884-127">Como selecionar o tipo de projeto do ASP.NET CORE 2.2 e de API Web</span><span class="sxs-lookup"><span data-stu-id="c7884-127">Selecting ASP.NET CORE 2.2 and Web API project type</span></span>

<span data-ttu-id="c7884-128">Se você tiver uma versão anterior do .NET Core, poderá baixar e instalar a versão 2.2 do <https://www.microsoft.com/net/download/core#/sdk>.</span><span class="sxs-lookup"><span data-stu-id="c7884-128">If you have any previous version of .NET Core, you can download and install the 2.2 version from <https://www.microsoft.com/net/download/core#/sdk>.</span></span>

<span data-ttu-id="c7884-129">Você pode adicionar suporte ao Docker ao criar o projeto ou posteriormente, portanto, você pode converter seu projeto para Docker a qualquer momento.</span><span class="sxs-lookup"><span data-stu-id="c7884-129">You can add Docker support when creating the project or afterwards, so you can "Dockerize" your project at any time.</span></span> <span data-ttu-id="c7884-130">Para adicionar suporte ao Docker após a criação do projeto, clique com o botão direito do mouse no nó do projeto no Gerenciador de Soluções e selecione **Adicionar** > **Suporte ao Docker** no menu de contexto.</span><span class="sxs-lookup"><span data-stu-id="c7884-130">To add Docker support after project creation, right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Opção do menu de contexto para adicionar suporte ao Docker a um projeto existente: Clique com o botão direito do mouse (no projeto) > Adicionar > Suporte do Docker.](media/add-docker-support-to-project.png)

<span data-ttu-id="c7884-132">**Figura 4-38**.</span><span class="sxs-lookup"><span data-stu-id="c7884-132">**Figure 4-38**.</span></span> <span data-ttu-id="c7884-133">Como adicionar suporte ao Docker ao projeto existente</span><span class="sxs-lookup"><span data-stu-id="c7884-133">Adding Docker support to existing project</span></span>

<span data-ttu-id="c7884-134">Para concluir a adição de suporte ao Docker, você pode escolher Windows ou Linux.</span><span class="sxs-lookup"><span data-stu-id="c7884-134">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="c7884-135">Nesse caso, selecione **Linux**, porque o AKS não é compatível com contêineres do Windows (como o de 2018).</span><span class="sxs-lookup"><span data-stu-id="c7884-135">In this case, select **Linux**, because AKS doesn’t support Windows Containers (as of late 2018).</span></span>

![Caixa de diálogo de opção para selecionar o sistema operacional de destino para o Dockerfile.](media/select-linux-docker-support.png)

<span data-ttu-id="c7884-137">**Figura 4-39**.</span><span class="sxs-lookup"><span data-stu-id="c7884-137">**Figure 4-39**.</span></span> <span data-ttu-id="c7884-138">Como selecionar contêineres do Linux.</span><span class="sxs-lookup"><span data-stu-id="c7884-138">Selecting Linux containers.</span></span>

<span data-ttu-id="c7884-139">Com estas etapas simples, você tem seu aplicativo ASP.NET Core 2.2 em execução em um contêiner do Linux.</span><span class="sxs-lookup"><span data-stu-id="c7884-139">With these simple steps, you have your ASP.NET Core 2.2 application running on a Linux container.</span></span>

<span data-ttu-id="c7884-140">Como é possível ver, a integração entre o Visual Studio 2017 e o Docker é totalmente orientada à produtividade do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="c7884-140">As you can see, the integration between Visual Studio 2017 and Docker is totally oriented to the developer’s productivity.</span></span>

<span data-ttu-id="c7884-141">Agora você pode executar seu aplicativo com a tecla **F5** ou usando o botão **Executar**.</span><span class="sxs-lookup"><span data-stu-id="c7884-141">Now you can run your application with the **F5** key or by using the **Play** button.</span></span>

<span data-ttu-id="c7884-142">Depois de executar o projeto, você pode listar as imagens usando o comando `docker images`.</span><span class="sxs-lookup"><span data-stu-id="c7884-142">After running the project, you can list the images using the `docker images` command.</span></span> <span data-ttu-id="c7884-143">Você deve ver a imagem `mssampleapplication` criada pela implantação automática do nosso projeto com o Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="c7884-143">You should see the `mssampleapplication` image created by the automatic deployment of our project with Visual Studio 2017.</span></span>

```console
docker images
```

![A saída de console do comando de imagens do Docker mostra uma lista com: Repositório, Marca, ID da imagem, Criado (data) e Tamanho.](media/docker-images-command.png)

<span data-ttu-id="c7884-145">**Figura 4-40**.</span><span class="sxs-lookup"><span data-stu-id="c7884-145">**Figure 4-40**.</span></span> <span data-ttu-id="c7884-146">Exibição de imagens do Docker</span><span class="sxs-lookup"><span data-stu-id="c7884-146">View of Docker images</span></span>

## <a name="register-the-solution-in-the-azure-container-registry"></a><span data-ttu-id="c7884-147">Registrar a solução no Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="c7884-147">Register the Solution in the Azure Container Registry</span></span>

<span data-ttu-id="c7884-148">Carregue a imagem em um registro do Docker, como o [ACR (Registro de Contêiner do Azure)](https://azure.microsoft.com/services/container-registry/), ou Docker Hub, para que as imagens possam ser implantadas no cluster do AKS desse registro.</span><span class="sxs-lookup"><span data-stu-id="c7884-148">Upload the image to any Docker registry, like [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) or Docker Hub, so the images can be deployed to the AKS cluster from that registry.</span></span> <span data-ttu-id="c7884-149">Neste caso, estamos carregando a imagem para um Registro de Contêiner do Azure.</span><span class="sxs-lookup"><span data-stu-id="c7884-149">In this case, we’re uploading the image to Azure Container Registry.</span></span>

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="c7884-150">Criar a imagem no modo de versão</span><span class="sxs-lookup"><span data-stu-id="c7884-150">Create the image in Release mode</span></span>

<span data-ttu-id="c7884-151">Agora vamos criar a imagem no modo de **Versão** (pronto para produção), alterando para **Versão**, conforme mostrado na Figura 4-41, e executando o aplicativo como fizemos antes.</span><span class="sxs-lookup"><span data-stu-id="c7884-151">We'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-41, and running the application as we did before.</span></span>

![Opção de barra de ferramentas no VS para build no modo de versão.](media/select-release-mode.png)

<span data-ttu-id="c7884-153">**Figura 4-41**.</span><span class="sxs-lookup"><span data-stu-id="c7884-153">**Figure 4-41**.</span></span> <span data-ttu-id="c7884-154">Como selecionar o modo de versão</span><span class="sxs-lookup"><span data-stu-id="c7884-154">Selecting Release Mode</span></span>

<span data-ttu-id="c7884-155">Se executar o comando `docker image`, você verá as duas imagens criadas, uma para `debug` e a outra para o modo `release`.</span><span class="sxs-lookup"><span data-stu-id="c7884-155">If you execute the `docker image` command, you'll see both images created, one for `debug` and the other for `release` mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="c7884-156">Criar uma marca para a imagem</span><span class="sxs-lookup"><span data-stu-id="c7884-156">Create a new Tag for the Image</span></span>

<span data-ttu-id="c7884-157">Cada imagem de contêiner precisa ser marcada com o nome do `loginServer` do registro.</span><span class="sxs-lookup"><span data-stu-id="c7884-157">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="c7884-158">Essa marca é usada para roteamento ao enviar imagens de contêiner por push a um registro da imagem.</span><span class="sxs-lookup"><span data-stu-id="c7884-158">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="c7884-159">Você pode exibir o nome `loginServer` do portal do Azure com as informações do Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="c7884-159">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![Exibição de navegador do nome do registro de contêiner do Azure, no canto superior direito.](media/loginServer-name.png)

<span data-ttu-id="c7884-161">**Figura 4-42**.</span><span class="sxs-lookup"><span data-stu-id="c7884-161">**Figure 4-42**.</span></span> <span data-ttu-id="c7884-162">Exibição do nome do Registro</span><span class="sxs-lookup"><span data-stu-id="c7884-162">View of the name of the Registry</span></span>

<span data-ttu-id="c7884-163">Ou executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c7884-163">Or by running the following command:</span></span>

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Saída do console do comando acima.](media/az-cli-loginServer-name.png)

<span data-ttu-id="c7884-165">**Figura 4-43**.</span><span class="sxs-lookup"><span data-stu-id="c7884-165">**Figure 4-43**.</span></span> <span data-ttu-id="c7884-166">Obtenha o nome do registro usando o PowerShell</span><span class="sxs-lookup"><span data-stu-id="c7884-166">Get the name of the registry using PowerShell</span></span>

<span data-ttu-id="c7884-167">Em ambos os casos, você obterá o nome.</span><span class="sxs-lookup"><span data-stu-id="c7884-167">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="c7884-168">Em nosso exemplo, `mssampleacr.azurecr.io`.</span><span class="sxs-lookup"><span data-stu-id="c7884-168">In our example, `mssampleacr.azurecr.io`.</span></span>

<span data-ttu-id="c7884-169">Agora você pode marcar a imagem, usando a imagem mais recente (a imagem de versão), com o comando:</span><span class="sxs-lookup"><span data-stu-id="c7884-169">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="c7884-170">Depois de executar o comando `docker tag`, liste as imagens com o comando `docker images` e você deverá ver a imagem com a nova marca.</span><span class="sxs-lookup"><span data-stu-id="c7884-170">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Saída de console do comando de imagens do Docker.](media/tagged-docker-images-list.png)

<span data-ttu-id="c7884-172">**Figura 4-44**.</span><span class="sxs-lookup"><span data-stu-id="c7884-172">**Figure 4-44**.</span></span> <span data-ttu-id="c7884-173">Exibição de imagens marcadas</span><span class="sxs-lookup"><span data-stu-id="c7884-173">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="c7884-174">Efetue push da imagem no ACR do Azure</span><span class="sxs-lookup"><span data-stu-id="c7884-174">Push the image into the Azure ACR</span></span>

<span data-ttu-id="c7884-175">Faça logon no Registro de Contêiner do Azure</span><span class="sxs-lookup"><span data-stu-id="c7884-175">Log in to the Azure Container Registry</span></span>

```console
az acr login --name mssampleacr
```

<span data-ttu-id="c7884-176">Efetue push da imagem no ACR do Azure usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="c7884-176">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

<span data-ttu-id="c7884-177">Esse comando demora um pouco para carregar as imagens, mas fornece comentários sobre o processo.</span><span class="sxs-lookup"><span data-stu-id="c7884-177">This command takes a while uploading the images but gives you feedback in the process.</span></span>

![Saída de console do comando docker push: mostra uma barra de progresso com base em caracteres para cada camada.](media/uploading-image-to-acr.png)

<span data-ttu-id="c7884-179">**Figura 4-45**.</span><span class="sxs-lookup"><span data-stu-id="c7884-179">**Figure 4-45**.</span></span> <span data-ttu-id="c7884-180">Como carregar a imagem no ACR</span><span class="sxs-lookup"><span data-stu-id="c7884-180">Uploading the image to the ACR</span></span>

<span data-ttu-id="c7884-181">É possível ver abaixo o resultado que será obtido quando o processo for concluído:</span><span class="sxs-lookup"><span data-stu-id="c7884-181">You can see below the result you should get when the process completes:</span></span>

![Saída de console do comando docker push, concluída, mostrando todas as camadas ou nós.](media/uploading-docker-images-complete.png)

<span data-ttu-id="c7884-183">**Figura 4-46**.</span><span class="sxs-lookup"><span data-stu-id="c7884-183">**Figure 4-46**.</span></span> <span data-ttu-id="c7884-184">Exibição de nós</span><span class="sxs-lookup"><span data-stu-id="c7884-184">View of nodes</span></span>

<span data-ttu-id="c7884-185">A próxima etapa é implantar seu contêiner no cluster de AKS do Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c7884-185">The next step is to deploy your container into your AKS Kubernetes cluster.</span></span> <span data-ttu-id="c7884-186">Para fazer isso, você precisa de um arquivo (**arquivo de implantação .yml**) que contém o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c7884-186">For that, you need a file (**.yml deploy file**) that contains the following:</span></span>

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
        - name: mssample-services-app
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
> <span data-ttu-id="c7884-187">Para obter mais informações sobre implantação com o Kubernetes, consulte: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="c7884-187">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

<span data-ttu-id="c7884-188">Agora você está quase pronto para implantar usando **Kubectl**, mas primeiro você deve obter as credenciais para o Cluster do AKS com este comando:</span><span class="sxs-lookup"><span data-stu-id="c7884-188">Now you're almost ready to deploy using **Kubectl**, but first you must get the credentials to the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Saída de console do comando acima: "MSSampleK8Cluster mesclado como o contexto atual em /root/.kube/config](media/getting-aks-credentials.png)

<span data-ttu-id="c7884-190">**Figura 4-47**.</span><span class="sxs-lookup"><span data-stu-id="c7884-190">**Figure 4-47**.</span></span> <span data-ttu-id="c7884-191">Como obter credenciais</span><span class="sxs-lookup"><span data-stu-id="c7884-191">getting credentials</span></span>

<span data-ttu-id="c7884-192">Em seguida, use o comando `kubectl create` para iniciar a implantação.</span><span class="sxs-lookup"><span data-stu-id="c7884-192">Then, use the `kubectl create` command to launch the deployment.</span></span>

```console
kubectl create -f mssample-deploy.yml
```

![Saída de console do comando acima: implantação "mssamplesbook" criada.](media/kubectl-create-command.png)

<span data-ttu-id="c7884-195">**Figura 4-48**.</span><span class="sxs-lookup"><span data-stu-id="c7884-195">**Figure 4-48**.</span></span> <span data-ttu-id="c7884-196">Implantar para o Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c7884-196">Deploy to Kubernetes</span></span>

<span data-ttu-id="c7884-197">Quando a implantação for concluída, você poderá acessar o console do Kubernetes com um proxy local que pode ser acessado temporariamente com este comando:</span><span class="sxs-lookup"><span data-stu-id="c7884-197">When the deployment completes, you can access the Kubernetes console with a local proxy that you can temporally access with this command:</span></span>

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

<span data-ttu-id="c7884-198">E acessar a URL `http://127.0.0.1:8001`.</span><span class="sxs-lookup"><span data-stu-id="c7884-198">And accessing the url `http://127.0.0.1:8001`.</span></span>

![Exibição de navegador do painel do Kubernetes mostrando Implantações, Pods, Conjuntos de Réplicas e Serviços.](media/kubernetes-cluster-information.png)

<span data-ttu-id="c7884-200">**Figura 4-49**.</span><span class="sxs-lookup"><span data-stu-id="c7884-200">**Figure 4-49**.</span></span> <span data-ttu-id="c7884-201">Exibição de informações de cluster do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="c7884-201">View Kubernetes cluster information</span></span>

<span data-ttu-id="c7884-202">Agora você tem seu aplicativo implantado no Azure usando um contêiner do Linux e um Cluster de Kubernetes do AKS.</span><span class="sxs-lookup"><span data-stu-id="c7884-202">Now you have your application deployed on Azure, using a Linux Container, and an AKS Kubernetes Cluster.</span></span> <span data-ttu-id="c7884-203">Você pode acessar seu aplicativo navegando até o IP público do seu serviço, que pode ser obtido do portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="c7884-203">You can access your app browsing to the public IP of your service, which you can get from the Azure portal.</span></span>

> [!NOTE]
> <span data-ttu-id="c7884-204">Você pode ver como criar o Cluster do AKS para esta amostra na seção [**Implantar no AKS (Serviço de Kubernetes do Azure)** ](deploy-azure-kubernetes-service.md) neste guia.</span><span class="sxs-lookup"><span data-stu-id="c7884-204">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c7884-205">[Anterior](set-up-windows-containers-with-powershell.md)
>[Próximo](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="c7884-205">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
