---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Saiba como implantar um aplicativo usando o serviço Kubernetes do Azure.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 82a1cf7f3cc367bfb8b8f67a130600815f2a21c4
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664959"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="08d0d-103">Implantar o serviço de Kubernetes do Azure (AKS)</span><span class="sxs-lookup"><span data-stu-id="08d0d-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="08d0d-104">Você pode interagir com o AKS usando o sistema operacional cliente preferencial, aqui vamos mostrar como fazê-lo com o Microsoft Windows e uma versão incorporada do Ubuntu Linux no Windows, usando comandos de Bash.</span><span class="sxs-lookup"><span data-stu-id="08d0d-104">You can interact with AKS using your preferred client operating system, here we show how to do it with Microsoft Windows and an embedded version of Ubuntu Linux in Windows, using Bash commands.</span></span>

<span data-ttu-id="08d0d-105">Pré-requisitos para ter antes de usar AKS são:</span><span class="sxs-lookup"><span data-stu-id="08d0d-105">Prerequisites to have before using AKS are:</span></span>

- <span data-ttu-id="08d0d-106">Máquina de desenvolvimento do Linux ou Mac</span><span class="sxs-lookup"><span data-stu-id="08d0d-106">Linux or Mac development machine</span></span>
- <span data-ttu-id="08d0d-107">Máquina de desenvolvimento do Windows</span><span class="sxs-lookup"><span data-stu-id="08d0d-107">Windows development machine</span></span>
  - <span data-ttu-id="08d0d-108">Modo de desenvolvedor habilitado no Windows</span><span class="sxs-lookup"><span data-stu-id="08d0d-108">Developer Mode enabled on Windows</span></span>
  - <span data-ttu-id="08d0d-109">Subsistema do Windows para Linux</span><span class="sxs-lookup"><span data-stu-id="08d0d-109">Windows Subsystem for Linux</span></span>
- <span data-ttu-id="08d0d-110">Azure-CLI instalada em [Windows, Mac ou Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span><span class="sxs-lookup"><span data-stu-id="08d0d-110">Azure-CLI installed on [Windows, Mac or Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)</span></span>

> [!NOTE]
> <span data-ttu-id="08d0d-111">Para obter informações completas sobre:</span><span class="sxs-lookup"><span data-stu-id="08d0d-111">To find complete information about:</span></span>
>
> <span data-ttu-id="08d0d-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span><span class="sxs-lookup"><span data-stu-id="08d0d-112">Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest></span></span>
>
> <span data-ttu-id="08d0d-113">Subsistema do Windows para Linux: <https://docs.microsoft.com/windows/wsl/about></span><span class="sxs-lookup"><span data-stu-id="08d0d-113">Windows Subsystem for Linux: <https://docs.microsoft.com/windows/wsl/about></span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="08d0d-114">Criar o ambiente de AKS no Azure</span><span class="sxs-lookup"><span data-stu-id="08d0d-114">Create the AKS environment in Azure</span></span>

<span data-ttu-id="08d0d-115">Há várias maneiras de criar o ambiente do AKS.</span><span class="sxs-lookup"><span data-stu-id="08d0d-115">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="08d0d-116">Ele pode ser feito usando os comandos da CLI do Azure ou usando o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="08d0d-116">It can be done by using Azure-CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="08d0d-117">Aqui você pode explorar alguns exemplos usando a CLI do Azure para criar o cluster e o portal do Azure para analisar os resultados.</span><span class="sxs-lookup"><span data-stu-id="08d0d-117">Here you can explore some examples using the Azure-CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="08d0d-118">Você também precisará ter o Kubectl e o Docker em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="08d0d-118">You also need to have Kubectl and Docker in your development machine.</span></span>  

## <a name="create-the-aks-cluster"></a><span data-ttu-id="08d0d-119">Criar o cluster do AKS</span><span class="sxs-lookup"><span data-stu-id="08d0d-119">Create the AKS cluster</span></span>

<span data-ttu-id="08d0d-120">Crie o cluster AKS usando este comando:</span><span class="sxs-lookup"><span data-stu-id="08d0d-120">Create the AKS cluster using this command:</span></span>

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

<span data-ttu-id="08d0d-121">Depois que o trabalho de criação for concluído, você pode ver o AKS criado no portal do Azure:</span><span class="sxs-lookup"><span data-stu-id="08d0d-121">After the creation job finishes, you can see the AKS created in the Azure portal:</span></span>

<span data-ttu-id="08d0d-122">O grupo de recursos:</span><span class="sxs-lookup"><span data-stu-id="08d0d-122">The resource group:</span></span>

![Modo de exibição de navegador do grupo de recursos AKS do Azure.](media/aks-resource-group-view.png)

<span data-ttu-id="08d0d-124">**Figura 4-17**.</span><span class="sxs-lookup"><span data-stu-id="08d0d-124">**Figure 4-17**.</span></span> <span data-ttu-id="08d0d-125">Modo de exibição de grupo de recursos do AKS do Azure.</span><span class="sxs-lookup"><span data-stu-id="08d0d-125">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="08d0d-126">O cluster do AKS:</span><span class="sxs-lookup"><span data-stu-id="08d0d-126">The AKS cluster:</span></span>

![Modo de exibição de navegador de um grupo de recursos do AKS.](media/aks-cluster-view.png)

<span data-ttu-id="08d0d-128">**Figura 4-18**.</span><span class="sxs-lookup"><span data-stu-id="08d0d-128">**Figure 4-18**.</span></span> <span data-ttu-id="08d0d-129">Modo de exibição AKS do Azure.</span><span class="sxs-lookup"><span data-stu-id="08d0d-129">AKS view from Azure.</span></span>

<span data-ttu-id="08d0d-130">Você também pode exibir o nó criado usando `Azure-CLI` e `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="08d0d-130">You can also view the node created using `Azure-CLI` and `Kubectl`.</span></span>

<span data-ttu-id="08d0d-131">Em primeiro lugar, obtendo as credenciais:</span><span class="sxs-lookup"><span data-stu-id="08d0d-131">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Console de saída do comando acima: Mesclado "MsSampleK8Cluster como o contexto atual no /root/.kube/config.](media/get-credentials-command-result.png)

<span data-ttu-id="08d0d-133">**Figura 4-19**.</span><span class="sxs-lookup"><span data-stu-id="08d0d-133">**Figure 4-19**.</span></span> <span data-ttu-id="08d0d-134">`aks get-credentials` resultado do comando.</span><span class="sxs-lookup"><span data-stu-id="08d0d-134">`aks get-credentials` command result.</span></span>

<span data-ttu-id="08d0d-135">E, em seguida, obtendo nós de Kubectl:</span><span class="sxs-lookup"><span data-stu-id="08d0d-135">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Console de saída mencionada acima de comando: Lista de nós com status, idade (tempo de execução) e versão](media/kubectl-get-nodes-command-result.png)

<span data-ttu-id="08d0d-137">**Figura 4-20**.</span><span class="sxs-lookup"><span data-stu-id="08d0d-137">**Figure 4-20**.</span></span> <span data-ttu-id="08d0d-138">`kubectl get nodes` resultado do comando.</span><span class="sxs-lookup"><span data-stu-id="08d0d-138">`kubectl get nodes` command result.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="08d0d-139">[Anterior](orchestrate-high-scalability-availability.md)
>[Próximo](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="08d0d-139">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
