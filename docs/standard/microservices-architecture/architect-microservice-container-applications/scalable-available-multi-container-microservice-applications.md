---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 25175e2a4409d53be412ae72be5af1c07c3ec68d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199651"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade

O uso de orquestradores em aplicativos prontos para produção é essencial se o aplicativo for baseado em microsserviços ou simplesmente dividido em vários contêineres. Conforme apresentado anteriormente, em uma abordagem baseada em microsserviço, cada microsserviço tem seu próprio modelo e dados para que seja autônomo de um ponto de vista de desenvolvimento e implantação. No entanto, se o seu aplicativo for mais tradicional, composto por diversos serviços (como o SOA), também haverá vários contêineres ou serviços que abrangem um único aplicativo de negócios e precisam ser implantados como um sistema distribuído. Esses tipos de sistemas são difíceis de escalar horizontalmente e gerenciar; portanto, um orquestrador é absolutamente necessário para ter um aplicativo pronto para produção, escalonável e com vários contêineres.

A Figura 4-23 ilustra a implantação de um aplicativo composto por vários microsserviços (contêineres) em um cluster.

![](./media/image23.PNG)

**Figura 4-23**. Um cluster de contêineres

Parece ser uma abordagem lógica. Mas como você lida com o balanceamento de carga, roteamento e orquestração desses aplicativos compostos?

O Docker Engine simples em hosts individuais do Docker atende às necessidades de gerenciamento de instâncias de imagem única em um host, mas fica aquém quando se trata de gerenciar vários contêineres implantados em diversos hosts de aplicativos distribuídos mais complexos. Na maioria dos casos, é necessária uma plataforma de gerenciamento que inicie os contêineres automaticamente, escale horizontalmente os que têm várias instâncias por imagem, suspenda-os ou desligue-os quando preciso e também controlem como eles acessam recursos como a rede e o armazenamento de dados.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos muito simples e em direção a aplicativos empresariais com microsserviços, é necessário adotar a orquestração e as plataformas de clustering.

De uma perspectiva de arquitetura e desenvolvimento, ao criar aplicativos empresariais grandes, compostos e baseados em microsserviços, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

**Clusters e orquestradores**. Quando é preciso escalar horizontalmente os aplicativos em vários hosts do Docker, como um aplicativo grande baseado em microsserviço, é essencial ter a capacidade de gerenciar todos esses hosts como um cluster único, abstraindo a complexidade da plataforma subjacente. É isso que os clusters e orquestradores de contêiner fazem. Azure Service Fabric, Kubernetes, Docker Swarm e Mesosphere DC/OS são exemplos de orquestradores. Esses três últimos são de software livre e estão disponíveis no Azure por meio do Serviço de Contêiner do Azure.

**Agendadores**. *Agendamento* é a capacidade do administrador de iniciar contêineres em um cluster para que eles também forneçam uma interface do usuário. O agendador do cluster tem diversas responsabilidades: usar os recursos de cluster de forma eficiente, definir as restrições fornecidas pelo usuário, balancear a carga dos contêineres em nós ou hosts de maneira eficaz, ser robusto contra erros e, ao mesmo tempo, oferecer alta disponibilidade.

Os conceitos de "cluster" e "agendador" estão intimamente relacionados, então os produtos oferecidos por diferentes fornecedores geralmente têm as duas capacidades. A lista a seguir mostra a plataforma mais importante e opções de software para clusters e agendadores. Geralmente, esses orquestradores são oferecidos em nuvens públicas como o Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plataformas de software para clustering, orquestração e agendamento de contêineres

Kubernetes

![Logotipo do Kubernetes](./media/image24.png)

> O Kubernetes é um software livre que oferece funcionalidades que variam da infraestrutura do cluster e do agendamento de contêiner a capacidades de orquestração. Com ele, é possível automatizar a implantação, o escalonamento e as operações de contêineres de aplicativo em clusters de hosts.
>
> O Kubernetes oferece uma infraestrutura centrada no contêiner que agrupa contêineres de aplicativo em unidades lógicas para facilitar o gerenciamento e a descoberta.
>
> O Kubernetes é maduro no Linux e menos maduro no Windows.

Docker Swarm

![Logotipo do Docker Swarm](./media/image25.png)

> O Docker Swarm permite criar clusters e agendar contêineres do Docker. Por meio do Swarm, é possível transformar um pool de hosts do Docker em um único host virtual. Os clientes podem fazer solicitações de API ao Swarm da mesma forma que os hosts. Isso significa que o Swarm facilita o escalonamento de aplicativos para vários hosts.
>
> O Docker Swarm é um produto da empresa Docker.
>
> O Docker v1.12 ou versões posteriores podem executar o Modo Swarm nativo e interno.

Mesosphere DC/OS

![Logotipo do Mesosphere DC/OS](./media/image26.png)

> O Mesosphere Enterprise DC/OS, baseado no Apache Mesos, é uma plataforma pronta para produção para contêineres em execução e aplicativos distribuídos.
>
> O DC/OS abstrai uma coleção de recursos disponíveis no cluster e os disponibiliza para componentes criados nele. Geralmente, o Marathon é usado como agendador integrado ao DC/OS.
>
> O DC/OS é maduro no Linux e menos maduro no Windows.

Azure Service Fabric

![Logotipo do Azure Service Fabric](./media/image27.png)

> O [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microsserviços da Microsoft para criação de aplicativos. É  [orquestrador](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. O Service Fabric pode implantar serviços como contêineres ou como processos simples. Ele pode até combinar serviços em processos com serviços em contêineres no mesmo aplicativo e cluster.
>
> O Service Fabric oferece [modelos de programação de Service Fabric ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) prescritivos adicionais e opcionais, como [serviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> O Service Fabric é maduro no Windows (com anos de desenvolvimento) e menos maduro no Linux. 
> Contêineres do Linux e Windows são compatíveis com o Service Fabric desde 2017.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Usar orquestradores baseados em contêiner no Microsoft Azure

Diversos provedores de nuvem oferecem suporte a contêineres do Docker e seus clusters e orquestração, como o Microsoft Azure, o Amazon EC2 Container Service e o Google Container Engine. O Microsoft Azure oferece suporte ao cluster e ao orquestrador do Docker por meio do ACS (Serviço de Contêiner do Azure), conforme explicado na seção a seguir.

Outra opção é usar o Microsoft Azure Service Fabric (uma plataforma de microsserviços), que também é compatível com contêineres baseados no Linux e no Windows no Docker. O Service Fabric é executado no Azure ou em qualquer outra nuvem e [localmente](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Usar o Serviço de Contêiner do Azure

Um cluster do Docker cria um pool de diversos hosts e os expõe como um host virtual único. Assim, é possível implantar vários contêineres no cluster. O cluster lidará com todos os detalhes complexos de gerenciamento, como escalabilidade, integridade e assim por diante. A Figura 4-24 mostra como um cluster do Docker para aplicativos compostos é mapeado no ACS (Serviço de Contêiner do Azure).

O ACS é uma maneira de simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais pré-configuradas para executar aplicativos em contêineres. Ao utilizar uma configuração otimizada de ferramentas de software livre conhecidas de agendamento e orquestração, o ACS permite o uso de habilidades existentes ou recorre ao grande e crescente conhecimento da comunidade para implantar e gerenciar aplicativos baseados em contêiner no Microsoft Azure.

O Serviço de Contêiner do Azure otimiza a configuração de ferramentas de software livre e tecnologias conhecidas do Docker especificamente para o Azure. É uma solução aberta que oferece portabilidade para contêineres e configuração de aplicativo. Selecione o tamanho, a quantidade de hosts e as ferramentas de orquestrador e deixe o Serviço de Contêiner cuidar de todo o resto.

![](./media/image28.png)

**Figura 4-24**. Opções de clusters no Serviço de Contêiner do Azure

O ACS utiliza imagens do Docker para garantir que os contêineres de aplicativo sejam totalmente portáteis. Além disso, é compatível com uma variedade de plataformas de orquestração de software livre, como DC/OS (da Apache Mesos), Kubernetes (originalmente criada pelo Google) e Docker Swarm, a fim de garantir que esses aplicativos sejam escalonados para milhares ou, até mesmo, para dezenas de milhares de contêineres.

O Serviço de Contêiner do Azure permite aproveitar os recursos empresariais do Azure e manter a portabilidade do aplicativo, até mesmo nas camadas de orquestração.

![](./media/image29.png)

**Figura 4-25**. Orquestradores do ACS

Conforme mostrado na Figura 4-25, o Serviço de Contêiner do Azure é a infraestrutura fornecida pelo Azure para implantar o DC/OS, o Kubernetes ou o Docker Swarm. No entanto, o ACS não implementa outros orquestradores. Assim, o ACS não é propriamente um orquestrador, mas somente uma infraestrutura que aproveita orquestradores de software livre existentes de contêineres.

De uma perspectiva de uso, o objetivo do Serviço de Contêiner do Azure é oferecer um ambiente de hospedagem de contêiner usando ferramentas e tecnologias conhecidas e de software livre. Para isso, ele expõe os pontos de extremidade padrão da API do orquestrador escolhido. Ao utilizar esses pontos de extremidade, é possível aproveitar qualquer software que se comunique com eles. Por exemplo, no caso do ponto de extremidade do Docker Swarm, você pode optar pela CLI (interface de linha de comando) do Docker. No DC/OS, você pode usar a CLI do DC/OS.

### <a name="getting-started-with-azure-container-service"></a>Introdução ao Serviço de Contêiner do Azure 

Para começar a usar o Serviço de Contêiner do Azure, implante um cluster do Serviço de Contêiner do Azure do Portal do Azure usando um modelo do Azure Resource Manager ou a [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Modelos disponíveis: [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) e [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Os modelos de início rápido podem ser modificados para incluir configurações adicionais ou avançadas do Azure. Para saber mais sobre como implantar um cluster do Serviço de Contêiner do Azure, consulte [Deploy an Azure Container Service cluster](https://docs.microsoft.com/azure/container-service/container-service-deployment) (Implantar um cluster do Serviço de Contêiner do Azure) no site do Azure.

Nenhum valor é cobrado pelos softwares instalados por padrão como parte do ACS. Todas as opções padrão são implementadas com software livre.

Atualmente, o ACS está disponível para Máquinas Virtuais do Linux das séries Standard A, D, DS, G e GS no Azure. Somente as instâncias de computação escolhidas serão cobradas, bem como outros recursos de infraestrutura consumidos, como armazenamento e rede. Não há cobranças adicionais pelo ACS.

## <a name="additional-resources"></a>Recursos adicionais

-   **Introdução a soluções de hospedagem do contêiner do Docker com o Serviço de Contêiner do Azure**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Visão geral do Docker Swarm**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Visão geral do modo Swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Visão geral do Mesosphere DC/OS**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Site oficial.\
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Anterior](resilient-high-availability-microservices.md)
[Próximo](using-azure-service-fabric.md)
