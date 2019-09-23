---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Saiba como implantar um aplicativo usando o Serviço de Kubernetes do Azure.
ms.date: 02/15/2019
ms.openlocfilehash: 0aa2f83fbf8f9a8815d65730002943cca748643d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182365"
---
# <a name="deploy-to-azure-kubernetes-service-aks"></a>Implantar no AKS (Serviço de Kubernetes do Azure)

Você pode interagir com o AKS usando o sistema operacional cliente de sua preferência. Aqui vamos mostrar como fazer isso com o Microsoft Windows e uma versão integrada do Ubuntu Linux no Windows usando comandos de Bash.

Os pré-requisitos para antes do uso do AKS são:

- Computador de desenvolvimento do Linux ou Mac
- Computador de desenvolvimento do Windows
  - Modo de desenvolvedor habilitado no Windows
  - Subsistema do Windows para Linux
- CLI do Azure instalada no [Windows, Mac ou Linux](https://docs.microsoft.com/cli/azure/install-azure-cli)

> [!NOTE]
> Para encontrar informações completas sobre:
>
> CLI do Azure: <https://docs.microsoft.com/cli/azure/index>
>
> Subsistema do Windows para Linux: <https://docs.microsoft.com/windows/wsl/about>

## <a name="create-the-aks-environment-in-azure"></a>Criar o ambiente do AKS no Azure

Existem várias maneiras de criar o Ambiente do AKS. Isso pode ser feito usando os comandos da CLI do Azure ou usando o portal do Azure.

Aqui você pode explorar alguns exemplos usando a CLI do Azure para criar o cluster, bem como o portal do Azure para examinar os resultados. Você também precisará ter o Kubectl e o Docker em seu computador de desenvolvimento.  

## <a name="create-the-aks-cluster"></a>Criar o cluster do AKS

Crie o cluster do AKS usando este comando:

```console
az aks create --resource-group MSSampleResourceGroup --name MSSampleClusterK801 --agent-count 1 --generate-ssh-keys --location westus2
```

Após o trabalho de criação ser concluído, você poderá ver o AKS criado no portal do Azure:

O grupo de recursos:

![Exibição de navegador do grupo de recursos do AKS do Azure.](media/aks-resource-group-view.png)

**Figura 4-17**. Exibição do Grupo de Recursos do AKS do Azure.

O cluster do AKS:

![Exibição de navegador do grupo de recursos do AKS.](media/aks-cluster-view.png)

**Figura 4-18**. Exibição do AKS do Azure.

Você também pode exibir o nó criado usando `Azure-CLI` e `Kubectl`.

Em primeiro lugar, obtendo as credenciais:

```console
az aks get-credentials --resource-group MSSampleK8ClusterRG --name MSSampleK8Cluster
```

![Saída de console do comando acima: "MsSampleK8Cluster mesclado como o contexto atual em /root/.kube/config.](media/get-credentials-command-result.png)

**Figura 4-19**. Resultado do comando `aks get-credentials`.

E, em seguida, obtendo nós do Kubectl:

```console
kubectl get nodes
```

![Saída de console do comando acima: Lista de nós com status, idade (tempo decorrido) e versão](media/kubectl-get-nodes-command-result.png)

**Figura 4-20**. Resultado do comando `kubectl get nodes`.

>[!div class="step-by-step"]
>[Anterior](orchestrate-high-scalability-availability.md)
>[Próximo](docker-apps-development-environment.md)
