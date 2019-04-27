---
title: Gerenciar ambientes de produção do Docker
description: Obtenha a conhecer os principais pontos para gerenciar um ambiente de produção com base em contêiner.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3f8c51b95f52a655de470ac237c51dd4ee9c13eb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61922571"
---
# <a name="manage-production-docker-environments"></a>Gerenciar ambientes de produção do Docker

Gerenciamento de cluster e a orquestração é o processo de controle de um grupo de hosts. Isso pode envolver a adição e remoção de hosts do cluster, obtendo informações sobre o estado atual de hosts e contêineres e iniciar e parar processos. Orquestração e gerenciamento de cluster estão intimamente vinculados ao agendamento porque o Agendador deve ter acesso a cada host no cluster para agendar serviços. Por esse motivo, a mesma ferramenta geralmente é usada para as duas finalidades.

## <a name="container-service-and-management-tools"></a>Ferramentas de gerenciamento e o serviço de contêiner

O serviço de contêiner fornece implantação rápida de soluções de clustering e a orquestração de contêiner de código-fonte aberto populares. Ele usa imagens do Docker para garantir que seus contêineres de aplicativo sejam totalmente portáteis. Usando o serviço de contêiner, você pode implantar o DC/OS (com Mesosphere e Apache Mesos) e clusters do Docker Swarm com modelos do Azure Resource Manager ou o portal do Azure para garantir que você possa dimensionar esses aplicativos para milhares — até mesmo dezenas de milhares — de contêineres.

Você implanta esses clusters usando conjuntos de dimensionamento de máquina Virtual do Azure e tiram proveito das ofertas de rede e armazenamento do Azure. Para acessar o serviço de contêiner, você precisa de uma assinatura do Azure. Com o serviço de contêiner, você pode aproveitar os recursos de nível empresarial do Azure e ainda manter a portabilidade do aplicativo, inclusive nas camadas de orquestração.

Tabela 6-1 lista as ferramentas de gerenciamento comuns relacionadas à sua plataforma clustering, agendadores e orquestradores.

**Tabela 6-1**. Ferramentas de gerenciamento do docker

| Ferramentas de gerenciamento | Descrição | Orquestradores relacionados |
|------------------|-------------|-----------------------|
| [O Azure Monitor para contêineres](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview) | Ferramenta de gerenciamento dedicada do Azure de Kubernetes | Serviços de Kubernetes do Azure (AKS) |
| [Interface do usuário Web Kubernetes (dashboard)](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) | Ferramenta de gerenciamento do Kubernetes, pode monitorar e gerenciar o cluster local do Kubernetes | AKS (Serviço de Kubernetes do Azure)<br/>Kubernetes local |
| [Portal do Azure para o Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal)<br/>[Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) | Versão on-line e da área de trabalho para gerenciar clusters do Service Fabric, no Azure, no local, no desenvolvimento local e outras nuvens | Azure Service Fabric |
| [Contêiner de monitoramento (Monitor do Azure)](https://docs.microsoft.com/azure/azure-monitor/insights/containers) | Gerenciamento de contêiner geral y solução de monitoramento. Pode gerenciar clusters de Kubernetes por meio [do Azure Monitor para contêineres](https://docs.microsoft.com/azure/monitoring/monitoring-container-insights-overview). | Azure Service Fabric<br/>AKS (Serviço de Kubernetes do Azure)<br/>Mesosphere DC/SO e outros. |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Outra opção para gerenciamento e implantação de cluster é o Azure Service Fabric. [O Service Fabric](https://azure.microsoft.com/services/service-fabric/) é uma plataforma de microsserviços da Microsoft que inclui a orquestração de contêiner, bem como desenvolvedor de modelos para criar aplicativos altamente escalonáveis microsserviços de programação. Service Fabric dá suporte ao Docker em contêineres do Linux e Windows e podem ser executados em servidores Windows e Linux.

A seguir está as ferramentas de gerenciamento do Service Fabric:

- [Portal do Azure para o Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operações relacionadas ao cluster (criar/atualizar/excluir) um cluster ou configurar sua infra-estrutura (máquinas virtuais, balanceador de carga, rede, etc.)

- [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) é especializada IU Web da área de trabalho ferramenta de várias plataformas que fornece insights e certas operações no cluster do Service Fabric, do ponto de vista de nós/VMs e de aplicativos e serviços de ponto de vista.

>[!div class="step-by-step"]
>[Anterior](run-microservices-based-applications-in-production.md)
>[Próximo](monitor-containerized-application-services.md)
