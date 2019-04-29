---
title: Etapas no fluxo de trabalho de DevOps loop externo para um aplicativo de Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 2cd769ce9013a8521c53f36b44ea260ceccd48b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795340"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>Criar pipelines de CI/CD nos Azure DevOps Services para um aplicativo .NET Core 2.0 em contêineres e implantar em um cluster do Kubernetes

Figura 5 a 12, você pode ver o cenário de DevOps de ponta a ponta que abrange o gerenciamento de código, compilação de código, compilação de imagens do Docker, imagens do Docker por push para um registro de Docker e, finalmente, a implantação em um cluster Kubernetes no Azure.

![Fluxo de trabalho: É iniciado no computador de desenvolvimento. Enviar por push para um repositório inicia a tarefa de build/CI usando uma imagem personalizada que é enviada para um registro de Docker e, em seguida, é usada pela tarefa de CD/implantar, por fim, enviar por push para o AKS.](media/docker-workflow-ci-cd-aks.png)

**Figura 5-12**. Cenário de CI/CD, criação de imagens do Docker e implantar um cluster Kubernetes no Azure

É importante destacar que o dois pipelines e dos build/CI/CD do produto, são conectados por meio de registro do Docker (como o Hub do Docker ou registro de contêiner do Azure). O registro do Docker é uma das principais diferenças em comparação comparadas um processo de CI/CD tradicional sem o Docker.

Conforme mostrado na Figura 5-13, a primeira fase é o pipeline de build/CI. Nos serviços de DevOps do Azure, você pode criar pipelines de build/CD que compilar o código, criar as imagens do Docker e enviar por push para um registro de Docker, como o Hub do Docker ou registro de contêiner do Azure.

![Exibição de navegador do DevOps do Azure, definição de tarefa do processo de compilação.](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**Figura 5-13**. Pipeline de build/CI no DevOps do Azure criando imagens do Docker e enviar imagens por push para um registro de Docker

A segunda fase é criar um pipeline de lançamento/implantação. Nos serviços de DevOps do Azure, você pode facilmente criar um pipeline de implantação, direcionando um cluster Kubernetes usando as tarefas de Kubernetes para os serviços de DevOps do Azure, conforme mostrado na Figura 5-14.

![Exibição de navegador do DevOps do Azure, implante a definição de tarefa do Kubernetes.](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**Figura 5-14**. Pipeline de lançamento/CD na implantação de serviços de DevOps do Azure para um cluster Kubernetes

> [! Instruções passo a passo] Implantando eShopModernized para Kubernetes:
>
> Para obter uma explicação detalhada de pipelines do Azure DevOps CI/CD, implantação de Kubernetes, consulte esta postagem: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[Anterior](docker-application-outer-loop-devops-workflow.md)
>[Próximo](../run-manage-monitor-docker-environments/index.md)
