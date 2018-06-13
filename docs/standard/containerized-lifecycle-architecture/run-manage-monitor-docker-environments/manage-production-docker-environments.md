---
title: Gerenciar ambientes de Docker de produção
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 5ecf1fbc164ff4170951894abc071908f45178d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573875"
---
# <a name="manage-production-docker-environments"></a>Gerenciar ambientes de Docker de produção

Cluster de gerenciamento e orquestração é o processo de controle de um grupo de hosts. Isso pode envolver adicionando e removendo hosts do cluster, obtendo informações sobre o estado atual dos hosts e contêineres e iniciar e parar processos. Coordenação e gerenciamento de cluster estão ligadas ao agendamento porque o Agendador deve ter acesso a cada host no cluster para agendar serviços. Por esse motivo, a mesma ferramenta geralmente é usada para fins de ambos.

## <a name="container-service-and-management-tools"></a>Ferramentas de serviço e gerenciamento de contêiner

Contêiner de serviço fornece a rápida implantação de soluções de clustering e a coordenação de contêiner do código-fonte aberto populares. Ele usa imagens do Docker para garantir que seus contêineres de aplicativos são totalmente portáteis. Usando o serviço de contêiner, você pode implantar o controlador de domínio/OS (com Mesosphere e Apache Mesos) e o Docker Swarm clusters com modelos do Azure Resource Manager ou o portal do Azure para garantir que você pode dimensionar a esses aplicativos para milhares — mesmo dezenas de milhares — de contêineres.

Implantar esses clusters usando conjuntos de escala de máquina Virtual do Azure, e os clusters tirar proveito das ofertas de rede e armazenamento do Azure. Para acessar o serviço de contêiner, você precisa de uma assinatura do Azure. Com o serviço de contêiner, você pode tirar proveito dos recursos de nível empresarial do Azure e ainda manter a portabilidade de aplicativo, incluindo nas camadas de orquestração.

Tabela 6-1 lista as ferramentas de gerenciamento comuns relacionadas à sua orchestrators, agendadores e plataforma de clustering.

Ferramentas de gerenciamento do Docker tabela 6-1:


| Ferramentas de gerenciamento      | Descrição           | Orchestrators relacionados |
|-----------------------|-----------------------|-----------------------|
| Serviço de contêiner\(gerenciamento de interface do usuário no portal do Azure) | [Serviço de contêiner](https://azure.microsoft.com/en-us/services/container-service/) fornece uma forma fácil de obter iniciado de maneira [implantar um cluster de contêiner no Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment) com base em orchestrators populares como Mesosphere DC/OS, Kubernetes e Docker Swarm. <br /><br /> Serviço de contêiner otimiza a configuração dessas plataformas. Basta selecionar o tamanho, o número de hosts e a opção de ferramentas do orchestrator e serviço de contêiner manipula todo o resto. | Mesosphere DC/OS <br /><br /> Kubernetes <br /><br /> Docker Swarm |
| Plano de controle Universal docker\(local ou nuvem) | [Plano de controle Universal docker](https://docs.docker.com/v1.11/ucp/overview/) é a solução de gerenciamento de cluster de nível empresarial do Docker. Ele ajuda você a gerenciar todo o cluster de um único local. <br /><br /> Plano de controle Universal docker é incluído como parte do produto comercial chamado Datacenter Docker que fornece o Docker Swarm, Docker Universal plano de controle e registro confiável do Docker. <br /><br /> Docker Datacenter pode ser instalado no local ou de uma nuvem pública como o Azure foi provisionado. | Docker Swarm\(suportados pelo serviço de contêiner) |
| Nuvem de docker\(também conhecido como Tutum; nuvem SaaS) | [Nuvem de docker](https://docs.docker.com/docker-cloud/) é um serviço de gerenciamento hospedado (SaaS) que fornece recursos de orquestração e um registro de Docker build e instalações de teste para as imagens de aplicativo Dockerized, ferramentas para ajudá-lo a configurar e gerenciar sua infraestrutura de host e recursos de implantação para ajudá-lo a automatizar implantar suas imagens à sua infraestrutura concreta. Você pode se conectar a sua conta de SaaS Docker nuvem em sua infraestrutura de serviço de contêiner executando um cluster de Docker Swarm. | Docker Swarm\(suportados pelo serviço de contêiner) |
| Mesosphere maratona\(local ou nuvem) | [Maratona](https://mesosphere.github.io/marathon/docs/marathon-ui.html) é uma plataforma de orquestração e Agendador de contêiner do nível de produção do Mesosphere controlador de domínio/OS e Apache Mesos. <br /><br /> Ele funciona com Mesos (SO/DC é baseado em Apache Mesos) para controle de longa execução de serviços e fornece um [web da interface do usuário para o gerenciamento de processo e o contêiner](https://mesosphere.github.io/marathon/docs/marathon-ui.html). Ele fornece uma ferramenta de gerenciamento de interface do usuário da web | Mesosphere DC/OS\(com base no Apache Mesos; compatível com o serviço de contêiner) |
| Kubernetes do Google | [Kubernetes](http://kubernetes.io/docs/user-guide/ui/#dashboard-access) abrange orquestrar, agendamento e infraestrutura de cluster. É uma plataforma de código-fonte aberto para automatizar a implantação, dimensionar e operações de contêineres de aplicativos em clusters de hosts, fornecendo a infra-estrutura centrada no contêiner. | Google Kubernetes\(suportados pelo serviço de contêiner) |

## <a name="azure-service-fabric"></a>Azure Service Fabric

Outra opção de gerenciamento e implantação de cluster é o Azure Service Fabric. [Service Fabric](https://azure.microsoft.com/en-us/services/service-fabric/) é uma plataforma microservices da Microsoft que inclui a coordenação de contêiner, bem como desenvolvedor de modelos para criar aplicativos altamente escalonáveis microservices de programação. Malha do serviço oferece suporte a Docker nas versões atuais de visualização do Linux, como no [visualização do Service Fabric no Linux](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere)e para contêineres do Windows [na próxima versão](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

A seguir está as ferramentas de gerenciamento de malha do serviço:

-   [Portal do Azure para Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-creation-via-portal) operações relacionadas ao cluster (criar/atualizar/excluir) um cluster ou configurar sua infraestrutura (VMs, balanceador de carga de rede, etc.)

-   [Azure Service Fabric Explorer](https://docs.microsoft.com/azure/service-fabric/service-fabric-visualizing-your-cluster) é uma ferramenta de interface do usuário do web especializados que fornece informações e certas operações no cluster do Service Fabric do ponto de vista do/VMs de nós e de aplicativos e serviços de ponto de vista.


>[!div class="step-by-step"]
[Anterior] (run-microservices-based-applications-in-production.md) [Avançar] (monitor-em contêineres-aplicativo-services.md)
