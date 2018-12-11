---
title: Gerenciar ambientes de produção do Docker
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: f968b5199f838e35f336dfa8c7d15aa9e5298951
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147288"
---
# <a name="manage-production-docker-environments"></a>Gerenciar ambientes de produção do Docker

Gerenciamento de cluster e a orquestração é o processo de controle de um grupo de hosts. Isso pode envolver a adição e remoção de hosts do cluster, obtendo informações sobre o estado atual de hosts e contêineres e iniciar e parar processos. Orquestração e gerenciamento de cluster estão intimamente vinculados ao agendamento porque o Agendador deve ter acesso a cada host no cluster para agendar serviços. Por esse motivo, a mesma ferramenta geralmente é usada para as duas finalidades.

## <a name="container-service-and-management-tools"></a>Ferramentas de gerenciamento e o serviço de contêiner

O serviço de contêiner fornece implantação rápida de soluções de clustering e a orquestração de contêiner de código-fonte aberto populares. Ele usa imagens do Docker para garantir que seus contêineres de aplicativo sejam totalmente portáteis. Usando o serviço de contêiner, você pode implantar o DC/OS (com Mesosphere e Apache Mesos) e clusters do Docker Swarm com modelos do Azure Resource Manager ou o portal do Azure para garantir que você possa dimensionar esses aplicativos para milhares — até mesmo dezenas de milhares — de contêineres.

Você implanta esses clusters usando conjuntos de dimensionamento de máquina Virtual do Azure e tiram proveito das ofertas de rede e armazenamento do Azure. Para acessar o serviço de contêiner, você precisa de uma assinatura do Azure. Com o serviço de contêiner, você pode aproveitar os recursos de nível empresarial do Azure e ainda manter a portabilidade do aplicativo, inclusive nas camadas de orquestração.

Tabela 6-1 lista as ferramentas de gerenciamento comuns relacionadas à sua plataforma clustering, agendadores e orquestradores.

Tabela 6-1: Ferramentas de gerenciamento do docker


| Ferramentas de gerenciamento      | Descrição           | Orquestradores relacionados |
|-----------------------|-----------------------|-----------------------|
| O serviço de contêiner\(gerenciamento de interface do usuário no portal do Azure) | [O serviço de contêiner](https://azure.microsoft.com/services/container-service/) fornece uma forma fácil de obter iniciado de maneira [implantar um cluster de contêiner no Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) com base em orquestradores populares, como o Mesosphere DC/OS, Kubernetes e Docker Swarm. <br /><br /> O serviço de contêiner otimiza a configuração dessas plataformas. Basta selecionar o tamanho, o número de hosts e escolha as ferramentas do orchestrator e o serviço de contêiner lida com todo o resto. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Plano de controle docker Universal\(no local ou na nuvem) | [Plano de controle docker Universal](https://docs.docker.com/v1.11/ucp/overview/) é a solução de gerenciamento de cluster de nível empresarial do Docker. Ele ajuda você a gerenciar todo o cluster de um único lugar. <br /><br /> Plano de controle docker Universal é incluído como parte do produto comercial chamado Docker Datacenter, que fornece o Docker Swarm, Docker Universal plano de controle e o Docker Trusted Registry. <br /><br /> Docker Datacenter pode ser instalado localmente ou provenientes de uma nuvem pública, como o Azure. | Docker Swarm\(com suporte pelo serviço de contêiner) |
| Docker Cloud\(também conhecido como Tutum; SaaS de nuvem) | [Docker Cloud](https://docs.docker.com/docker-cloud/) é um serviço de gerenciamento hospedado (SaaS) que fornece recursos de orquestração e um registro do Docker com compilação e recursos de teste para imagens do docker no aplicativo, ferramentas para ajudá-lo a configurar e gerenciar sua infraestrutura de host, e os recursos de implantação para ajudá-lo a automatizar a implantação de suas imagens para sua infraestrutura de concreta. Você pode conectar sua conta de SaaS Docker Cloud à sua infraestrutura no serviço de contêiner executando um cluster Docker Swarm. | Docker Swarm\(com suporte pelo serviço de contêiner) |
| Mesosphere Marathon\(no local ou na nuvem) | [Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) é uma plataforma de orquestração e o Agendador de contêiner do nível de produção para o Mesosphere DC/SO e Apache Mesos. <br /><br /> Ele funciona com o Mesos (DC/SO com base no Apache Mesos) para controle de execução longa de serviços e fornece um [interface do usuário da web para o gerenciamento de processo e contêiner](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Ele fornece uma ferramenta de gerenciamento de interface do usuário da web | Mesosphere DC/SO\(com base no Apache Mesos; tem suporte pelo serviço de contêiner) |
| Google Kubernetes | [Kubernetes](https://kubernetes.io/docs/user-guide/ui/#dashboard-access) abrange a orquestração, agendamento e infraestrutura de cluster. É uma plataforma de código-fonte aberto para automatizar a implantação, dimensionamento e operações dos contêineres de aplicativos em clusters de hosts, fornecendo a infraestrutura centrada no contêiner. | Google Kubernetes\(com suporte pelo serviço de contêiner) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Outra opção para gerenciamento e implantação de cluster é o Azure Service Fabric. [O Service Fabric](https://azure.microsoft.com/services/service-fabric/) é uma plataforma de microsserviços da Microsoft que inclui a orquestração de contêiner, bem como desenvolvedor de modelos para criar aplicativos altamente escalonáveis microsserviços de programação. Service Fabric dá suporte a Docker nas versões atuais de visualização do Linux, como mostra a [versão prévia do Service Fabric no Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)e contêineres do Windows [na próxima versão](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

A seguir está as ferramentas de gerenciamento do Service Fabric:

-   [Portal do Azure para o Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operações relacionadas ao cluster (criar/atualizar/excluir) um cluster ou configurar sua infra-estrutura (máquinas virtuais, balanceador de carga, rede, etc.)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) é uma ferramenta de interface do usuário web especializado que fornece insights e determinadas operações em um cluster do Service Fabric do ponto de vista de nós/VMs e de aplicativos e serviços de ponto de vista.

>[!div class="step-by-step"]
>[Anterior](run-microservices-based-applications-in-production.md)
>[Próximo](monitor-containerized-application-services.md)