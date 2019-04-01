---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Descubra as opções para orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade e as possibilidades de Azure Dev Spaces durante o desenvolvimento do ciclo de vida de aplicativos Kubernetes.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 6fa25c1d35e276473f4fcac344efbc5cafbc4b3f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58465432"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade

O uso de orquestradores em aplicativos prontos para produção é essencial se o aplicativo for baseado em microsserviços ou simplesmente dividido em vários contêineres. Conforme apresentado anteriormente, em uma abordagem baseada em microsserviço, cada microsserviço tem seu próprio modelo e dados para que seja autônomo de um ponto de vista de desenvolvimento e implantação. No entanto, se o aplicativo for mais tradicional, composto por diversos serviços (como o SOA), também haverá vários contêineres ou serviços que abrangem um único aplicativo de negócios e precisam ser implantados como um sistema distribuído. Esses tipos de sistemas são difíceis de escalar horizontalmente e gerenciar; portanto, um orquestrador é absolutamente necessário para ter um aplicativo pronto para produção, escalonável e com vários contêineres.

A Figura 4-23 ilustra a implantação de um aplicativo composto por vários microsserviços (contêineres) em um cluster.

![Aplicativos do Docker compostos em um cluster: você pode usar um contêiner para cada instância de serviço. Contêineres do Docker são "unidades de implantação" e um contêiner é uma instância de um host do Docker. Um host lida com vários contêineres](./media/image23.png)

**Figura 4-23**. Um cluster de contêineres

Parece ser uma abordagem lógica. Mas como você lida com o balanceamento de carga, roteamento e orquestração desses aplicativos compostos?

O Docker Engine simples em hosts individuais do Docker atende às necessidades de gerenciamento de instâncias de imagem única em um host, mas fica aquém quando se trata de gerenciar vários contêineres implantados em diversos hosts de aplicativos distribuídos mais complexos. Na maioria dos casos, é necessária uma plataforma de gerenciamento que inicie os contêineres automaticamente, escale horizontalmente os que têm várias instâncias por imagem, suspenda-os ou desligue-os quando preciso e também controlem como eles acessam recursos como a rede e o armazenamento de dados.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos muito simples e em direção a aplicativos empresariais com microsserviços, é necessário adotar a orquestração e as plataformas de clustering.

De uma perspectiva de arquitetura e desenvolvimento, ao criar aplicativos empresariais grandes, compostos e baseados em microsserviços, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

**Clusters e orquestradores.** Quando é preciso expandir os aplicativos em vários hosts do Docker, como um aplicativo grande baseado em microsserviço, é essencial ter a capacidade de gerenciar todos esses hosts como um cluster único, abstraindo a complexidade da plataforma subjacente. É isso que os clusters e orquestradores de contêineres fazem. O Kubernetes e o Azure Service Fabric são exemplos de orquestradores. O Kubernetes está disponível no Azure por meio do Serviço de Kubernetes do Azure.

**Agendadores.** *Agendamento* é a capacidade do administrador de iniciar contêineres em um cluster para que eles também forneçam uma interface do usuário. O agendador do cluster tem diversas responsabilidades: usar os recursos de cluster de forma eficiente, definir as restrições fornecidas pelo usuário, balancear a carga dos contêineres em nós ou hosts de maneira eficaz, ser robusto contra erros e, ao mesmo tempo, oferecer alta disponibilidade.

Os conceitos de "cluster" e "agendador" estão intimamente relacionados, então os produtos oferecidos por diferentes fornecedores geralmente têm as duas capacidades. A lista a seguir mostra a plataforma mais importante e opções de software para clusters e agendadores. Geralmente, esses orquestradores são oferecidos em nuvens públicas como o Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plataformas de software para clustering, orquestração e agendamento de contêineres

### <a name="kubernetes"></a>Kubernetes

![Logotipo do Kubernetes](./media/image24.png)

> O [*Kubernetes*](https://kubernetes.io/) é um produto de software livre que oferece funcionalidades que variam da infraestrutura do cluster e do agendamento de contêiner a capacidades de orquestração. Com ele, é possível automatizar a implantação, o escalonamento e as operações de contêineres de aplicativo em clusters de hosts.
>
> O *Kubernetes* oferece uma infraestrutura centrada no contêiner que agrupa contêineres de aplicativo em unidades lógicas para facilitar o gerenciamento e a descoberta.
>
> O *Kubernetes* é maduro no Linux e menos maduro no Windows.

### <a name="azure-kubernetes-service-aks"></a>AKS (Serviço de Kubernetes do Azure)

![Logotipo do Serviço de Kubernetes do Azure](./media/image41.png)

> O [Serviço de Kubernetes do Azure (AKS)](https://azure.microsoft.com/services/kubernetes-service/) é um serviço de orquestração de contêiner de Kubernetes gerenciado no Azure que simplifica o gerenciamento, a implantação e as operações do cluster do Kubernetes.

### <a name="azure-service-fabric"></a>Azure Service Fabric

![Logotipo do Azure Service Fabric](./media/image27.png)

> O [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microsserviços da Microsoft para criação de aplicativos. Ele é um [orquestrador](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. O Service Fabric pode implantar serviços como contêineres ou como processos simples. Ele pode até combinar serviços em processos com serviços em contêineres no mesmo aplicativo e cluster.
>
> Os clusters do *Service Fabric* podem ser implantados no Azure, localmente ou em qualquer nuvem. No entanto, a implantação no Azure é simplificada com uma abordagem gerenciada.
>
> O *Service Fabric* oferece [modelos de programação do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) prescritivos adicionais e opcionais, tais como [serviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> O *Service Fabric* é maduro no Windows (com anos de desenvolvimento) e menos maduro no Linux.
>
> Contêineres do Linux e Windows são compatíveis com o Service Fabric desde 2017.

### <a name="azure-service-fabric-mesh"></a>Malha do Azure Service Fabric

![Logotipo da Malha do Azure Service Fabric](./media/image35.png)

> A [*Malha do Azure Service Fabric*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) oferece a mesma confiabilidade, desempenho crítico e escala que o Service Fabric, mas oferece uma plataforma totalmente gerenciada e sem servidor. Você não precisa gerenciar um cluster, VMs, armazenamento ou configuração de rede. Você se concentra apenas no desenvolvimento do seu aplicativo.
>
> A *Malha do Service Fabric* dá suporte a contêineres do Windows e do Linux, permitindo que você desenvolva com qualquer linguagem de programação e estrutura de sua escolha.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Usar orquestradores baseados em contêiner no Microsoft Azure

Diversos provedores de nuvem oferecem suporte a contêineres do Docker e seus clusters e orquestração, como o Microsoft Azure, o Amazon EC2 Container Service e o Google Container Engine. O Microsoft Azure fornece suporte ao orquestrador e ao cluster do Docker por meio do AKS (Serviço de Kubernetes do Azure), do Azure Service Fabric e da Malha do Azure Service Fabric.

## <a name="using-azure-kubernetes-service"></a>Usando o Serviço de Kubernetes do Azure

Um cluster do Kubernetes cria um pool de diversos hosts do Docker e os expõe como um host virtual único. Assim, é possível implantar vários contêineres no cluster e expandir com qualquer número de instâncias de contêiner. O cluster lidará com todos os detalhes complexos de gerenciamento, como escalabilidade, integridade e assim por diante.

O AKS é uma maneira de simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais no Azure pré-configuradas para executar aplicativos em contêineres. Ao utilizar uma configuração otimizada de ferramentas de software livre conhecidas de agendamento e orquestração, o AKS permite o uso de habilidades existentes ou recorre ao grande e crescente conhecimento da comunidade para implantar e gerenciar aplicativos baseados em contêiner no Microsoft Azure.

O Serviço de Kubernetes do Azure otimiza a configuração de ferramentas de software livre e tecnologias conhecidas do Docker especificamente para o Azure. É uma solução aberta que oferece portabilidade para contêineres e configuração de aplicativo. Selecione o tamanho, a quantidade de hosts e as ferramentas de orquestrador e deixe o AKS cuidar de todo o resto.

![Estrutura de cluster Kubernetes: há um nó mestre que manipula o DNS, o agendador, o proxy, entre outros e vários nós de trabalho que hospedam os contêineres.](media/image36.png)

**Figura 4-24**. Topologia e estrutura simplificadas do cluster Kubernetes

Na figura 4-24 veja a estrutura de um cluster Kubernetes em que um nó mestre (VM) controla a maior parte da coordenação do cluster e você pode implantar contêineres no restante dos nós que são gerenciados como um único pool de um ponto de vista do aplicativo, permitindo dimensionar para milhares ou até mesmo dezenas de milhares de contêineres.

## <a name="development-environment-for-kubernetes"></a>Ambiente de desenvolvimento para Kubernetes

No ambiente de desenvolvimento, o [Docker anunciou em julho de 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/) que o Kubernetes também pode ser executado em um único computador de desenvolvimento (Windows 10 ou macOS) simplesmente instalando o [Docker Desktop](https://docs.docker.com/install/). Posteriormente, você pode implantar para a nuvem (AKS) para testes de integração posteriores, conforme mostrado na figura 4-25.

![O Docker anunciou o suporte a computador de desenvolvimento para clusters Kubernetes em julho de 2018 com o Docker Desktop.](media/image37.png) 

**Figura 4-25**. Executando Kubernetes no computador de desenvolvimento e na nuvem

## <a name="getting-started-with-azure-kubernetes-service-aks"></a>Introdução ao AKS (Serviço de Kubernetes do Azure) 

Para começar a usar o AKS, implante um cluster do AKS do portal do Azure ou usando a CLI. Para saber mais sobre como implantar um cluster do Serviço de Contêiner do Azure, veja [Implantar um cluster do AKS (Serviço de Kubernetes do Azure)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Nenhum valor é cobrado pelos softwares instalados por padrão como parte do AKS. Todas as opções padrão são implementadas com software livre. O AKS está disponível para várias máquinas virtuais no Azure. Somente as instâncias de computação escolhidas serão cobradas, bem como outros recursos adjacentes de infraestrutura consumidos, como armazenamento e rede. Não há cobranças adicionais pelo AKS.

Para mais informações sobre a implementação na implantação para Kubernetes com base no kubectl e em arquivos .yaml originais, verifique a postagem [Configurando eShopOnContainers no AKS (Serviço de Kubernetes do Azure)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploying-with-helm-charts-into-kubernetes-clusters"></a>Implantando com gráficos do Helm em clusters Kubernetes

Ao implantar um aplicativo em um cluster Kubernetes, você pode usar a ferramenta de CLI kubectl.exe original usando arquivos de implantação com base no formato nativo (arquivos .yaml), conforme já mencionado na seção anterior. No entanto, para aplicativos mais complexos do Kubernetes, como ao implantar aplicativos complexos baseados em microsserviços, é recomendável usar o [Helm](https://helm.sh/).

Os Gráficos do Helm ajudam você a definir, realizar controle de versão, instalar, compartilhar, atualizar ou reverter até mesmo o aplicativo mais complexo do Kubernetes.

Indo mais além, o uso do Helm também é recomendável porque ambientes adicionais do Kubernetes no Azure, tais como [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces), também são baseados em gráficos do Helm.

O Helm é mantido pela [CNCF (Fundação de Computação Nativa na Nuvem)](https://www.cncf.io/), em colaboração com Microsoft, Google, Bitnami e a comunidade de colaboradores do Helm.

Para mais informações sobre a implementação sobre os gráficos do Helm e o Kubernetes, verifique a postagem [Usando gráficos do Helm para implantar o eShopOnContainers no AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-your-kubernetes-application-lifecycle"></a>Usar o Azure Dev Spaces para o ciclo de vida do aplicativo do Kubernetes

O [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) fornece uma experiência de desenvolvimento rápida e iterativa do Kubernetes para equipes. Com uma configuração mínima de computador de desenvolvimento, você pode executar e depurar contêineres iterativamente diretamente no AKS (Serviço de Kubernetes do Azure). Desenvolva em Windows, Mac ou Linux usando ferramentas familiares como o Visual Studio, o Visual Studio Code ou a linha de comando.

Conforme mencionado, o Azure Dev Spaces usa gráficos do Helm ao implantar os aplicativos baseados em contêiner.

O Azure Dev Spaces ajuda as equipes de desenvolvimento a serem mais produtivas no Kubernetes, pois permite que você itere e depure rapidamente o código diretamente em um cluster Kubernetes global no Azure, simplesmente usando o Visual Studio 2017 ou Visual Studio Code. Esse cluster Kubernetes no Azure é um cluster Kubernetes gerenciado compartilhado, de modo que sua equipe pode trabalhar conjuntamente de forma colaborativa. Você pode desenvolver o código de forma isolada, depois implantar no cluster global e realizar testes de ponta a ponta com outros componentes sem replicar ou criar dependências fictícias.

Conforme mostrado na Figura 4-26, o recurso mais diferencial no Azure Dev Spaces é a capacidade de criar "espaços" que podem ser executados integrados ao restante da implantação global no cluster.

![O Azure Dev Spaces pode misturar e combinar microsserviços de produção transparentemente com a instância de contêiner de desenvolvimento, para facilitar o teste de novas versões.](media/image38.png)

**Figura 4-26**. Usando vários espaços no Azure Dev Spaces

Basicamente, você pode configurar um espaço de desenvolvimento compartilhado no Azure. Cada desenvolvedor pode se concentrar apenas em sua parte do aplicativo e pode desenvolver iterativamente um código de pré-confirmação em um espaço de desenvolvimento que já contém todos os outros serviços e recursos de nuvem dos quais seus cenários dependem. As dependências estão sempre atualizadas e os desenvolvedores trabalham de uma forma que reflete a produção.

O Azure Dev Spaces oferece o conceito de um espaço, que permite trabalhar em relativo isolamento e sem medo de interromper o trabalho da equipe. Cada espaço de desenvolvimento faz parte de uma estrutura hierárquica que permite que você substitua um ou muitos microsserviços a partir do espaço de desenvolvimento mestre “top” com seu próprio microsserviço em andamento.

Esse recurso se baseia nos prefixos de URL, portanto, ao usar qualquer prefixo de espaço de desenvolvimento na URL, uma solicitação é enviada do microsserviço de destino caso ele exista no espaço de desenvolvimento; caso contrário, ela é encaminhada até a primeira instância do microsserviço de destino encontrado na hierarquia, chegando ao espaço de desenvolvimento mestre na parte superior em algum momento.

Você pode ver a [página de wiki de eShopOnContainers no Azure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Using-Azure-Dev-Spaces-and-AKS) para obter uma visão prática em um exemplo concreto.

Para obter mais informações, confira o artigo sobre [Desenvolvimento em equipe com o Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Recursos adicionais

- **Introdução ao AKS (Serviço de Kubernetes do Azure)** \
  [https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

- **Azure Dev Spaces** \
  [https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)

- **Kubernetes** O site oficial. \
  [https://kubernetes.io/](https://kubernetes.io/)

>[!div class="step-by-step"]
>[Anterior](resilient-high-availability-microservices.md)
>[Próximo](using-azure-service-fabric.md)
