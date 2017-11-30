---
title: "Organizar microservices e contêiner vários aplicativos de alto desempenho e disponibilidade"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Organizar microservices e contêiner vários aplicativos de alto desempenho e disponibilidade"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ec33901a0ddc9e5b58263440b0e4399e687c6904
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Organizar microservices e contêiner vários aplicativos de alto desempenho e disponibilidade

Usando orchestrators para aplicativos prontos para produção é essencial se seu aplicativo baseado no microservices ou simplesmente dividido em vários contêineres. Conforme apresentado anteriormente, uma abordagem baseada em microsserviço, cada microsserviço possui seu modelo e dados para que é autônomo de um desenvolvimento e implantação de ponto de vista. Mas, mesmo se você tiver um aplicativo mais tradicional que é composto de vários serviços (como o SOA), você também terá vários contêineres ou serviços que compõem um aplicativo de negócios único que precisa ser implantado como um sistema distribuído. Esses tipos de sistemas são complexos de expansão e gerenciar; Portanto, absolutamente necessário um orquestrador se desejar ter um aplicativo de multi-contêiner pronto para produção e escalonável.

Figura 4-23 ilustra uma implantação em um cluster de um aplicativo composto de vários microservices (contêineres).

![](./media/image23.PNG)

**Figura 4-23**. Um cluster de contêineres

Ele se parece com uma abordagem lógica. Mas como você tratamento de balanceamento de carga, roteamento e organizar esses compostas aplicativos?

O mecanismo do Docker simples em hosts de Docker único atende às necessidades de gerenciamento de instâncias de imagem única em um host, mas fica curto quando se trata de gerenciar vários contêineres implantados em vários hosts para aplicativos distribuídos mais complexos. Na maioria dos casos, você precisa de uma plataforma de gerenciamento que será automaticamente contêineres, contêineres de expansão com várias instâncias por imagem de iniciar, suspendê-los ou desligá-las quando necessário e idealmente também controlar como eles acessam os recursos como a rede e os dados armazenamento.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos muito simples e mudança para os maiores aplicativos empresariais com microservices, você deve ativar a coordenação e o clustering de plataformas.

De um arquitetura e desenvolvimento do ponto de Vista, se você estiver criando uma grande empresa composta de aplicativos baseados em microservices, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

**Clusters e orchestrators**. Quando você precisa de expansão de aplicativos em vários hosts de Docker, como quando um aplicativo grande com base em microsserviço, é essencial para gerenciar todos os hosts como um único cluster, abstraindo a complexidade da plataforma subjacente. É o que fornece os clusters de contêiner e orchestrators. São exemplos de orchestrators Azure Service Fabric, Kubernetes, Docker Swarm e Mesosphere DC/OS. As três últimas orchestrators do código-fonte aberto estão disponíveis no Azure por meio do serviço de contêiner do Azure.

**Agendadores**. *Agendando* significa ter a capacidade de um administrador para iniciar contêineres em um cluster de forma que elas também fornecem uma interface do usuário. Um cluster possui várias responsabilidades: para usar recursos do cluster com eficiência, para definir as restrições fornecidas pelo usuário, para contêineres de balanceamento de carga com eficiência em nós ou hosts e ser robusto contra erros, proporcionando alto disponibilidade.

Os conceitos de um cluster e um agendador estão intimamente relacionados, para que os produtos fornecidos por fornecedores diferentes geralmente fornecem os dois conjuntos de recursos. A lista a seguir mostra a plataforma mais importante e opções de software que você tem para clusters e agendadores. Geralmente, essas orchestrators são oferecidos em nuvens públicas, como o Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plataformas de software para o contêiner de clustering, orquestração e agendamento

Kubernetes

![https://PBS.twimg.com/Media/BT\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes é um produto de código-fonte aberto que fornece a funcionalidade que varia de infraestrutura de cluster e agendamento para recursos de orquestração do contêiner. Ele permite automatizar a implantação, dimensionar e operações de contêineres de aplicativos em clusters de hosts.
>
> Kubernetes fornece uma infraestrutura centrada no contêiner que agrupa os contêineres de aplicativos em unidades lógicas para facilitar o gerenciamento e descoberta.
>
> Kubernetes é desenvolvido no Linux, menos maduro no Windows.

Por nuvem de docker

![http://rancher.com/wp-content/Themes/rancher-2016/Assets/images/swarm.PNG?v=2016-07-10-AM](./media/image25.png)

> Docker por nuvem permite que você cluster e agenda a contêineres do Docker. Usando por nuvem, você pode transformar um pool de hosts de Docker em um único host Docker virtual. Os clientes podem fazer solicitações de API para Swarm da mesma forma que eles fazem a hosts, o que significa que o por nuvem facilita para os aplicativos a se expandir para vários hosts.
>
> Por docker nuvem é um produto, a empresa Docker.
>
> V docker 1.12 ou posterior pode executar modo Swarm internos e nativos.

Mesosphere DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.PNG](./media/image26.png)

> Mesosphere Enterprise DC/OS (com base no Apache Mesos) é uma plataforma de pronto para produção para executar contêineres e aplicativos distribuídos.
>
> Controlador de domínio/OS funciona abstração de uma coleção dos recursos disponíveis no cluster e disponibilizar esses recursos para componentes criados sobre ele. Maratona geralmente é usada como um agendador integrado ao controlador de domínio/OS.
>
> Controlador de domínio/sistema operacional é desenvolvido no Linux, menos maduro no Windows.

Malha do serviço do Azure

![https://Azure.microsoft.com/svghandler/Service-Fabric?Width=600&Height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microservices da Microsoft para a criação de aplicativos. É um [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. Serviço de malha pode implantar serviços como contêineres ou processos simples. Ele pode até mesmo mistura services em processos com os serviços em contêineres dentro do mesmo aplicativo e cluster.
>
> Serviço de malha fornece adicionais e opcionais prescritivas [modelos de programação do Service Fabric ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) como [services com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Malha do serviço é desenvolvida no Windows (anos em desenvolvimento no Windows), menos desenvolvida no Linux. 
> Contêineres do Linux e Windows têm suporte no Service Fabric desde 2017.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Usando com base em contêiner orchestrators no Microsoft Azure

Vários fornecedores de nuvem oferecem suporte de contêineres do Docker mais clusters do Docker e suporte de orquestração, incluindo o Microsoft Azure, o serviço de contêiner do Amazon EC2 e o mecanismo de contêiner do Google. O Microsoft Azure fornece Docker suporte a cluster e orchestrator por meio de serviço de contêiner do Azure (ACS), conforme explicado na próxima seção.

Outra opção é usar o Microsoft Azure Service Fabric (uma plataforma microservices), que também oferece suporte a Docker com base em contêineres do Linux e Windows. Malha do serviço é executado no Azure ou qualquer outra nuvem e também executa [local](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Usando o serviço de contêiner do Azure

Um cluster de Docker agrupa vários hosts de Docker e expõe como um único host Docker virtual, para que possa implantar vários contêineres no cluster. O cluster tratará todos os detalhes de gerenciamento complexas, como escalabilidade, integridade e assim por diante. Figura 4-24 representa como um cluster de Docker para aplicativos compostos mapeia para o serviço de contêiner do Azure (ACS).

O ACS fornece uma maneira para simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres. Usando uma configuração otimizada das ferramentas de planejamento e a coordenação de código-fonte aberto populares, ACS permite que você use suas habilidades existentes ou desenhe um corpo grande e crescente de experiência de comunidade para implantar e gerenciar aplicativos de contêiner no Microsoft Azure .

Serviço de contêiner do Azure otimiza a configuração de tecnologias e ferramentas de software livre clusters Docker populares especificamente para o Azure. Você obtém uma solução aberta que oferece portabilidade para seus contêineres e sua configuração de aplicativo. Selecione o tamanho, o número de hosts e as ferramentas do orchestrator e serviço de contêiner manipula todo o resto.

![](./media/image28.png)

**Figura 4-24**. Opções de clusters no serviço de contêiner do Azure

ACS utiliza imagens do Docker para garantir que seus contêineres de aplicativos são totalmente portáteis. Ele dá suporte a variedade de plataformas de orquestração do código-fonte aberto como controlador de domínio/OS (com Apache Mesos), Kubernetes (originalmente criado pelo Google) e Docker Swarm, para garantir que esses aplicativos podem ser aumentados para milhares ou até mesmo dezenas de milhares de contêineres.

O serviço de contêiner do Azure permite que você aproveite os recursos de nível empresarial do Azure e ainda manter a portabilidade de aplicativo, incluindo nas camadas de orquestração.

![](./media/image29.png)

**Figura 4-25**. Orchestrators no ACS

Conforme mostrado na Figura 4-25, o serviço de contêiner do Azure é simplesmente a infraestrutura fornecida pelo Azure para implantar o controlador de domínio/OS, Kubernetes ou Docker Swarm, mas o ACS não implementar qualquer orchestrator adicional. Portanto, o ACS não é um orquestrador como tal, apenas uma infraestrutura que aproveita o orchestrators de código-fonte existentes para contêineres.

De uma perspectiva de uso, o objetivo do serviço de contêiner do Azure é fornecer um ambiente de hospedagem de contêiner usando tecnologias e ferramentas de software livre populares. Para esse fim, ele expõe os pontos de extremidade de API padrão para o orchestrator escolhido. Ao usar esses pontos de extremidade, você pode utilizar qualquer software que pode se comunicar com esses pontos de extremidade. Por exemplo, no caso do ponto de extremidade Docker Swarm, você pode optar por usar a interface de linha de comando do Docker (CLI). Para DC/sistema operacional, você pode optar por usar a CLI do controlador de domínio/OS.

### <a name="getting-started-with-azure-container-service"></a>Guia de Introdução ao serviço de contêiner do Azure 

Para começar a usar o serviço de contêiner do Azure, você deve implantar um cluster do serviço de contêiner do Azure no portal do Azure usando um modelo do Azure Resource Manager ou o [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Modelos disponíveis incluem [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), e [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Os modelos de início rápido podem ser modificados para incluir a configuração do Azure adicional ou avançada. Para obter mais informações sobre como implantar um cluster do serviço de contêiner do Azure, consulte [implantar um cluster do serviço de contêiner do Azure](https://docs.microsoft.com/azure/container-service/container-service-deployment) no site do Azure.

Não há nenhuma taxa para qualquer software instalado por padrão como parte do ACS. Todas as opções padrão são implementadas com o software de código-fonte aberto.

ACS está disponível atualmente para um padrão, D, DS, G, séries GS e máquinas virtuais Linux no Azure. Você é cobrado somente para as instâncias de computação que você escolher, bem como outros subjacente infraestrutura recursos consumidos, como armazenamento e rede. Não há nenhum encargo incremental do ACS em si.

## <a name="additional-resources"></a>Recursos adicionais

-   **Introdução ao contêiner do Docker hospedagem soluções com o serviço de contêiner do Azure**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Visão geral do docker por nuvem**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Visão geral do modo de swarm**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Visão geral do controlador de domínio/OS mesosphere**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** O site oficial. \
    [*http://kubernetes.IO/*](http://kubernetes.io/)


>[!div class="step-by-step"]
[Anterior] (resiliente-alta-disponibilidade-microservices.md) [Avançar] (usando-azure-serviço-fabric.md)
