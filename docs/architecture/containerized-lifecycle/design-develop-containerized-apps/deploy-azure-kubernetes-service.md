---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Saiba como implantar um aplicativo usando o Serviço de Kubernetes do Azure.
ms.date: 08/06/2020
ms.openlocfilehash: ba9887c0a4837c16a60ebeb006416c0fa8c105e0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163590"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a><span data-ttu-id="12f24-103">Implantar no AKS (Serviço de Kubernetes do Azure)</span><span class="sxs-lookup"><span data-stu-id="12f24-103">Deploy to Azure Kubernetes Service (AKS)</span></span>

<span data-ttu-id="12f24-104">Você pode interagir com o AKS usando seu sistema operacional cliente preferencial (Windows, macOS ou Linux) com a interface de linha de comando do Azure (CLI do Azure) instalada.</span><span class="sxs-lookup"><span data-stu-id="12f24-104">You can interact with AKS using your preferred client operating system (Windows, macOS, or Linux) with Azure command-line interface(Azure CLI) installed.</span></span> <span data-ttu-id="12f24-105">Para obter mais detalhes, consulte [CLI do Azure documentação](/cli/azure/?view=azure-cli-latest) e [Guia de instalação](/cli/azure/install-azure-cli?view=azure-cli-latest) para os ambientes disponíveis.</span><span class="sxs-lookup"><span data-stu-id="12f24-105">For more details, refer [Azure CLI documentation](/cli/azure/?view=azure-cli-latest) and [Installation guide](/cli/azure/install-azure-cli?view=azure-cli-latest) for the available environments.</span></span>

## <a name="create-the-aks-environment-in-azure"></a><span data-ttu-id="12f24-106">Criar o ambiente do AKS no Azure</span><span class="sxs-lookup"><span data-stu-id="12f24-106">Create the AKS environment in Azure</span></span>

<span data-ttu-id="12f24-107">Existem várias maneiras de criar o Ambiente do AKS.</span><span class="sxs-lookup"><span data-stu-id="12f24-107">There are several ways to create the AKS Environment.</span></span> <span data-ttu-id="12f24-108">Isso pode ser feito usando comandos CLI do Azure ou o portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="12f24-108">It can be done by using Azure CLI commands or by using the Azure portal.</span></span>

<span data-ttu-id="12f24-109">Aqui você pode explorar alguns exemplos usando o CLI do Azure para criar o cluster e o portal do Azure para examinar os resultados.</span><span class="sxs-lookup"><span data-stu-id="12f24-109">Here you can explore some examples using the Azure CLI to create the cluster and the Azure portal to review the results.</span></span> <span data-ttu-id="12f24-110">Você também precisará ter o Kubectl e o Docker em seu computador de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="12f24-110">You also need to have Kubectl and Docker in your development machine.</span></span>

## <a name="create-the-aks-cluster"></a><span data-ttu-id="12f24-111">Criar o cluster do AKS</span><span class="sxs-lookup"><span data-stu-id="12f24-111">Create the AKS cluster</span></span>

<span data-ttu-id="12f24-112">Crie o cluster AKS usando este comando (o grupo de recursos deve existir):</span><span class="sxs-lookup"><span data-stu-id="12f24-112">Create the AKS cluster using this command (the resource group must exist):</span></span>

```console
az aks create --resource-group explore-docker-aks-rg --name explore-docker-aks --node-vm-size Standard_B2s --node-count 1 --generate-ssh-keys --location westeurope
```

> [!NOTE]
> <span data-ttu-id="12f24-113">Os `--node-vm-size` `--node-count` valores de parâmetro e são bons o suficiente para um aplicativo de exemplo/dev.</span><span class="sxs-lookup"><span data-stu-id="12f24-113">The `--node-vm-size` and `--node-count` parameter values are good enough for a sample/dev application.</span></span>

<span data-ttu-id="12f24-114">Após a conclusão do trabalho de criação, você poderá ver:</span><span class="sxs-lookup"><span data-stu-id="12f24-114">After the creation job finishes, you can see:</span></span>

- <span data-ttu-id="12f24-115">O cluster AKS criado no grupo de recursos inicial</span><span class="sxs-lookup"><span data-stu-id="12f24-115">The AKS cluster created in the initial resource group</span></span>
- <span data-ttu-id="12f24-116">Um novo grupo de recursos relacionado, que contém os recursos relacionados ao cluster AKS, conforme mostrado nas imagens a seguir.</span><span class="sxs-lookup"><span data-stu-id="12f24-116">A new, related resource group, containing the resources related to the AKS cluster, as show in the following images.</span></span>

<span data-ttu-id="12f24-117">O grupo de recursos inicial, com o cluster AKS:</span><span class="sxs-lookup"><span data-stu-id="12f24-117">The initial resource group, with the AKS cluster:</span></span>

![Exibição de navegador do grupo de recursos do AKS.](media/deploy-azure-kubernetes-service/aks-cluster-view.png)

<span data-ttu-id="12f24-119">**Figura 4-17**.</span><span class="sxs-lookup"><span data-stu-id="12f24-119">**Figure 4-17**.</span></span> <span data-ttu-id="12f24-120">Exibição do Grupo de Recursos do AKS do Azure.</span><span class="sxs-lookup"><span data-stu-id="12f24-120">AKS Resource Group view from Azure.</span></span>

<span data-ttu-id="12f24-121">O grupo de recursos de cluster AKS:</span><span class="sxs-lookup"><span data-stu-id="12f24-121">The AKS cluster resource group:</span></span>

![Exibição de navegador do grupo de recursos do AKS do Azure.](media/deploy-azure-kubernetes-service/aks-resource-group-view.png)

<span data-ttu-id="12f24-123">**Figura 4-18**.</span><span class="sxs-lookup"><span data-stu-id="12f24-123">**Figure 4-18**.</span></span> <span data-ttu-id="12f24-124">Exibição do AKS do Azure.</span><span class="sxs-lookup"><span data-stu-id="12f24-124">AKS view from Azure.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="12f24-125">Em geral, você não deve precisar modificar os recursos no grupo de recursos de cluster AKS.</span><span class="sxs-lookup"><span data-stu-id="12f24-125">In general, you shouldn't need to modify the resources in the AKS cluster resource group.</span></span> <span data-ttu-id="12f24-126">Por exemplo, o grupo de recursos é excluído quando você exclui o cluster AKS.</span><span class="sxs-lookup"><span data-stu-id="12f24-126">For example, the resource group is deleted when you delete the AKS cluster.</span></span>

<span data-ttu-id="12f24-127">Você também pode exibir o nó criado usando `Azure CLI` e `Kubectl`.</span><span class="sxs-lookup"><span data-stu-id="12f24-127">You can also view the node created using `Azure CLI` and `Kubectl`.</span></span>

<span data-ttu-id="12f24-128">Em primeiro lugar, obtendo as credenciais:</span><span class="sxs-lookup"><span data-stu-id="12f24-128">First, getting the credentials:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Saída do console do comando acima: "Explore-Docker-AKS" mesclado como o contexto atual em/Home/Miguel/.Kube/config.](media/deploy-azure-kubernetes-service/get-credentials-command-result.png)

<span data-ttu-id="12f24-130">**Figura 4-19**.</span><span class="sxs-lookup"><span data-stu-id="12f24-130">**Figure 4-19**.</span></span> <span data-ttu-id="12f24-131">Resultado do comando `aks get-credentials`.</span><span class="sxs-lookup"><span data-stu-id="12f24-131">`aks get-credentials` command result.</span></span>

<span data-ttu-id="12f24-132">E, em seguida, obtendo nós do Kubectl:</span><span class="sxs-lookup"><span data-stu-id="12f24-132">And then, getting nodes from Kubectl:</span></span>

```console
kubectl get nodes
```

![Saída do console do comando acima: lista de nós com status, idade (tempo em execução) e versão](media/deploy-azure-kubernetes-service/kubectl-get-nodes-command-result.png)

<span data-ttu-id="12f24-134">**Figura 4-20**.</span><span class="sxs-lookup"><span data-stu-id="12f24-134">**Figure 4-20**.</span></span> <span data-ttu-id="12f24-135">Resultado do comando `kubectl get nodes`.</span><span class="sxs-lookup"><span data-stu-id="12f24-135">`kubectl get nodes` command result.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="12f24-136">[Anterior](orchestrate-high-scalability-availability.md) 
>  [Avançar](docker-apps-development-environment.md)</span><span class="sxs-lookup"><span data-stu-id="12f24-136">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-development-environment.md)</span></span>
