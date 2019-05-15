---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Saiba como implantar um aplicativo usando o serviço Kubernetes do Azure.
ms.date: 02/15/2019
ms.openlocfilehash: 88e76b4b0a3686f4227a6aee1b7fbd2bfe55fdcc
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644624"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Implantar no AKS (Serviço de Kubernetes do Azure)

Você pode interagir com o AKS usando o sistema operacional cliente preferencial, aqui vamos mostrar como fazê-lo com o Microsoft Windows e uma versão incorporada do Ubuntu Linux no Windows, usando comandos de Bash.

Pré-requisitos para ter antes de usar AKS são:

- Máquina de desenvolvimento do Linux ou Mac
- Máquina de desenvolvimento do Windows
  - Modo de desenvolvedor habilitado no Windows
  - Subsistema do Windows para Linux
- Azure-CLI instalada em [Windows, Mac ou Linux](https://docs.microsoft.com/cli/azure/install-azure-cli?view=azure-cli-latest)

> [!NOTE]
> Para obter informações completas sobre:
>
> Azure-CLI: <https://docs.microsoft.com/cli/azure/index?view=azure-cli-latest>
>
> Subsistema do Windows para Linux: <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Criar o ambiente de AKS no Azure

Há várias maneiras de criar o ambiente do AKS. Ele pode ser feito usando os comandos da CLI do Azure ou usando o portal do Azure.

Aqui você pode explorar alguns exemplos usando a CLI do Azure para criar o cluster e o portal do Azure para analisar os resultados. Você também precisará ter o Kubectl e o Docker em seu computador de desenvolvimento.  

## <a name="create-the-aks-cluster"></a>Criar o cluster do AKS

Crie o cluster AKS usando este comando:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Depois que o trabalho de criação for concluído, você pode ver o AKS criado no portal do Azure:

O grupo de recursos:

![Modo de exibição de navegador do grupo de recursos AKS do Azure.](media/aks-resource-group-view.png)

**Figura 4-17**. Modo de exibição de grupo de recursos do AKS do Azure.

O cluster do AKS:

![Modo de exibição de navegador de um grupo de recursos do AKS.](media/aks-cluster-view.png)

**Figura 4-18**. Modo de exibição AKS do Azure.

Você também pode exibir o nó criado usando `Azure-CLI` e `Kubectl`.

Em primeiro lugar, obtendo as credenciais:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Console de saída do comando acima: Mesclado "MsSampleK8Cluster como o contexto atual no /root/.kube/config.](media/get-credentials-command-result.png)

**Figura 4-19**. `aks get-credentials` resultado do comando.

E, em seguida, obtendo nós de Kubectl:

```console
kubectl get nodes
```

![Console de saída mencionada acima de comando: Lista de nós com status, idade (tempo de execução) e versão](media/kubectl-get-nodes-command-result.png)

**Figura 4-20**. `kubectl get nodes` resultado do comando.

>[!div class="step-by-step"]
>[Anterior](orchestrate-high-scalability-availability.md)
>[Próximo](docker-apps-development-environment.md)
