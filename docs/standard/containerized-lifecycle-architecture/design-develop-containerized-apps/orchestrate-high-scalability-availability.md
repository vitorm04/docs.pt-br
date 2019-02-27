---
title: Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Aplicativos de produção real precisam ser implantados e gerenciados com orquestradores que lidam com a integridade, a carga de trabalho e ciclos de vida de todos os contêineres.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: e1ff3282c1fdf952177a1faa957398c33045a01c
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836151"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Orquestrar microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade

Usando orquestradores para aplicativos prontos para produção é essencial se seu aplicativo baseado em microsserviços ou dividido em vários contêineres. Conforme apresentado anteriormente, em uma abordagem baseada em microsserviço, cada microsserviço tem seu próprio modelo e dados para que seja autônomo de um ponto de vista de desenvolvimento e implantação. No entanto, se o seu aplicativo for mais tradicional, composto por diversos serviços (como o SOA), também haverá vários contêineres ou serviços que abrangem um único aplicativo de negócios e precisam ser implantados como um sistema distribuído. Esses tipos de sistemas são difíceis de escalar horizontalmente e gerenciar; portanto, um orquestrador é absolutamente necessário para ter um aplicativo pronto para produção, escalonável e com vários contêineres.

Figura 4 a 6 ilustra uma implantação em um cluster de um aplicativo composto por vários microsserviços (contêineres).

![Aplicativos do Docker compostos em um cluster: você pode usar um contêiner para cada instância de serviço. Contêineres do Docker são "unidades de implantação" e um contêiner é uma instância de um host do Docker. Um host lida com vários contêineres](./media/image6.png)

**Figura 4-6**. Um cluster de contêineres

Parece ser uma abordagem lógica. Mas como você está lidando com balanceamento de carga, roteamento e orquestração desses aplicativos compostos?

A interface de linha de comando do Docker (CLI) atende às necessidades de gerenciamento de um contêiner em um host, mas fica aquém quando se trata de gerenciar vários contêineres implantados em diversos hosts de aplicativos distribuídos mais complexos. Na maioria dos casos, você precisa de uma plataforma de gerenciamento que será automaticamente iniciar contêineres, expandir os contêineres com várias instâncias por imagem, suspendê-las ou desligá-los quando necessário e também controlem como eles acessam recursos como a rede e dados armazenamento.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos simples e em direção a aplicativos empresariais com microsserviços, você deve ativar a orquestração e as plataformas de clustering.

De um arquitetura e desenvolvimento ponto de Vista, se você estiver criando grandes, empresas, baseado em microsserviços, aplicativos, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

- **Clusters e orquestradores.** Quando você precisar dimensionar aplicativos em vários hosts do Docker, como com um aplicativo grande baseado em microsserviços, é fundamental ser capaz de gerenciar todos esses hosts como um cluster único, abstraindo a complexidade da plataforma subjacente. É isso que os clusters e orquestradores de contêineres fazem. O Kubernetes e o Azure Service Fabric são exemplos de orquestradores. O Kubernetes está disponível no Azure por meio do Serviço de Kubernetes do Azure.

- **Agendadores.** *Agendando* significa ter a capacidade de um administrador para iniciar os contêineres em um cluster, para que os agendadores também fornecem uma interface do usuário para fazer isso. O agendador do cluster tem diversas responsabilidades: usar os recursos de cluster de forma eficiente, definir as restrições fornecidas pelo usuário, balancear a carga dos contêineres em nós ou hosts de maneira eficaz, ser robusto contra erros e, ao mesmo tempo, oferecer alta disponibilidade.

Os conceitos de "cluster" e "agendador" estão intimamente relacionados, então os produtos oferecidos por diferentes fornecedores geralmente têm as duas capacidades. A seção a seguir mostra a plataforma mais importante e opções de software para clusters e agendadores. Esses orquestradores amplamente são oferecidos em nuvens públicas, como o Azure.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Plataformas de software para clustering, orquestração e agendamento de contêineres

| Plataforma | Comentários |
|:---:|:---|
| **Kubernetes** <br/> ![Logotipo do Kubernetes](./media/kubernetes-logo.png) | O [*Kubernetes*](https://kubernetes.io/) é um produto de software livre que oferece funcionalidades que variam da infraestrutura do cluster e do agendamento de contêiner a capacidades de orquestração. Com ele, é possível automatizar a implantação, o escalonamento e as operações de contêineres de aplicativo em clusters de hosts. <br/> <br/> O *Kubernetes* oferece uma infraestrutura centrada no contêiner que agrupa contêineres de aplicativo em unidades lógicas para facilitar o gerenciamento e a descoberta. <br/> <br/> O *Kubernetes* é maduro no Linux e menos maduro no Windows. |
| **Serviço de Kubernetes do Azure (AKS)** <br/> ![Logotipo do serviço de Kubernetes do Azure](./media/aks-logo.png) | O [Serviço de Kubernetes do Azure (AKS)](https://azure.microsoft.com/services/kubernetes-service/) é um serviço de orquestração de contêiner de Kubernetes gerenciado no Azure que simplifica o gerenciamento, a implantação e as operações do cluster do Kubernetes. |
| **Azure Service Fabric** <br/> ![Logotipo da malha de serviço do Azure](./media/service-fabric-logo.png) | O [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microsserviços da Microsoft para criação de aplicativos. Ele é um [orquestrador](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. O Service Fabric pode implantar serviços como contêineres ou como processos simples. Ele pode até combinar serviços em processos com serviços em contêineres no mesmo aplicativo e cluster. <br/> <br/> Os clusters do *Service Fabric* podem ser implantados no Azure, localmente ou em qualquer nuvem. No entanto, a implantação no Azure é simplificada com uma abordagem gerenciada. <br/> <br/> O *Service Fabric* oferece [modelos de programação do Service Fabric](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) prescritivos adicionais e opcionais, tais como [serviços com estado](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) e [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/). <br/> <br/> O *Service Fabric* é maduro no Windows (com anos de desenvolvimento) e menos maduro no Linux. <br/> <br/> Contêineres do Linux e Windows são compatíveis com o Service Fabric desde 2017. |
| **Malha de malha do serviço do Azure** <br/> ![Logotipo de malha de malha do serviço do Azure](./media/azure-service-fabric-mesh-logo.png) | [*Malha do Azure Service Fabric* ](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) oferece a mesma confiabilidade, desempenho crítico e dimensionamento do Service Fabric, mas também oferece uma plataforma totalmente gerenciada e sem servidor. Você não precisa gerenciar um cluster, VMs, armazenamento ou configuração de rede. Você se concentra apenas no desenvolvimento do seu aplicativo. <br/> <br/> *Malha do serviço Fabric* dá suporte a contêineres do Windows e Linux, permitindo que você desenvolva com qualquer linguagem de programação e a estrutura de sua escolha.

## <a name="using-container-based-orchestrators-in-azure"></a>Usar orquestradores baseados em contêiner no Azure

Vários fornecedores de nuvem oferecem suporte a contêineres do além de clusters do Docker e suporte de orquestração, incluindo Azure, o Amazon EC2 Container Service e o Google Container Engine. O Azure fornece suporte a cluster e o orchestrator por meio do serviço de Kubernetes do Azure (AKS), o Azure Service Fabric e a malha do Azure Service Fabric de Docker.

## <a name="using-azure-kubernetes-service"></a>Usando o Serviço de Kubernetes do Azure

Um cluster Kubernetes de pools de vários hosts do Docker e os expõe como um único host virtual, para que você possa implantar vários contêineres no cluster e a expansão com qualquer número de instâncias de contêiner. O cluster lidará com todos os detalhes complexos de gerenciamento, como escalabilidade, integridade e assim por diante.

O AKS é uma maneira de simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais no Azure pré-configuradas para executar aplicativos em contêineres. Ao utilizar uma configuração otimizada de ferramentas de software livre conhecidas de agendamento e orquestração, o AKS permite o uso de habilidades existentes ou recorre ao grande e crescente conhecimento da comunidade para implantar e gerenciar aplicativos baseados em contêiner no Microsoft Azure.

O Serviço de Kubernetes do Azure otimiza a configuração de ferramentas de software livre e tecnologias conhecidas do Docker especificamente para o Azure. É uma solução aberta que oferece portabilidade para contêineres e configuração de aplicativo. Selecione o tamanho, a quantidade de hosts e as ferramentas de orquestrador e deixe o AKS cuidar de todo o resto.

![Estrutura de cluster Kubernetes: Há um nó mestre que manipula o DNS, Agendador, proxy, etc. e vários nós de trabalho, que hospedam os contêineres.](media/image36.png)

**Figura 4-7**. Topologia e estrutura simplificadas do cluster Kubernetes

Figura 4 a 7 mostra a estrutura de um cluster Kubernetes em que um nó mestre (VM) controla a maioria da coordenação do cluster, e você pode implantar contêineres para o restante de nós que são gerenciados como um único pool de ponto de vista do aplicativo. Isso permite que você dimensione para milhares ou até mesmo dezenas de milhares de contêineres.

## <a name="development-environment-for-kubernetes"></a>Ambiente de desenvolvimento para Kubernetes

No ambiente de desenvolvimento que [Docker anunciada em julho de 2018](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), Kubernetes também pode executar em um único computador de desenvolvimento (Windows 10 ou macOS) apenas instalando [área de trabalho do Docker](https://www.docker.com/community-edition). Posteriormente, você pode implantar para a nuvem (AKS) para obter mais testes de integração, conforme mostrado na Figura 4 a 8.

![O Docker anunciou o suporte a computador de desenvolvimento para clusters Kubernetes em julho de 2018 com o Docker Desktop.](media/kubernetes-development-environment.png)

**Figura 4-8**. Executando Kubernetes no computador de desenvolvimento e na nuvem

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Começar com o serviço de Kubernetes do Azure (AKS)

Para começar a usar AKS, implante um cluster do AKS do portal do Azure ou usando a CLI. Para saber mais sobre como implantar um cluster do Serviço de Contêiner do Azure, veja [Implantar um cluster do AKS (Serviço de Kubernetes do Azure)](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Nenhum valor é cobrado pelos softwares instalados por padrão como parte do AKS. Todas as opções padrão são implementadas com software livre. O AKS está disponível para várias máquinas virtuais no Azure. Somente as instâncias de computação escolhidas serão cobradas, bem como outros recursos de infraestrutura consumidos, como armazenamento e rede. Não há cobranças adicionais pelo AKS.

Para implementação ainda mais informações sobre implantação no Kubernetes com base em `kubectl` e originais `.yaml` arquivos, consulte a postagem no [Configurando o eShopOnContainers no AKS (serviço de Kubernetes do Azure)](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Implantar com gráficos do Helm em clusters de Kubernetes

Ao implantar um aplicativo em um cluster Kubernetes, você pode usar o original `kubectl.exe` ferramenta CLI usando arquivos de implantação com base no formato nativo (`.yaml` arquivos), como já mencionado na seção anterior. No entanto, para aplicativos mais complexos do Kubernetes, como ao implantar aplicativos complexos baseados em microsserviço, é recomendável usar [Helm](https://helm.sh/).

Gráficos do Helm ajuda você a definir, versão, instalação, compartilhamento, atualização ou reversão até mesmo o aplicativo mais complexo do Kubernetes.

Indo mais além, o uso do Helm também é recomendável porque ambientes adicionais do Kubernetes no Azure, tais como [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces), também são baseados em gráficos do Helm.

Helm é mantido pela [Foundation de computação nativa de nuvem (CNCF)](https://www.cncf.io/) em colaboração com a Microsoft, Google, Bitnami e a comunidade de Colaborador do Helm.

Para obter mais informações implementação nos gráficos do Helm e o Kubernetes, consulte a postagem no [usando gráficos do Helm para implantar o eShopOnContainers em AKS](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Use espaços de desenvolvimento do Azure para você Kubernetes ciclo de vida do aplicativo

O [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) fornece uma experiência de desenvolvimento rápida e iterativa do Kubernetes para equipes. Com uma configuração mínima de computador de desenvolvimento, você pode executar e depurar contêineres iterativamente diretamente no AKS (Serviço de Kubernetes do Azure). Você pode desenvolver no Windows, Mac ou Linux usando ferramentas familiares como o Visual Studio, Visual Studio Code ou a linha de comando.

Conforme mencionado, os espaços de desenvolvimento do Azure usa gráficos Helm ao implantar aplicativos baseados em contêiner.

Espaços de desenvolvimento do Azure ajuda as equipes de desenvolvimento a serem mais produtivos no Kubernetes, pois permite que você itere rapidamente e depurar o código diretamente em um cluster Kubernetes global no Azure apenas usando o Visual Studio 2017 ou Visual Studio Code. Esse cluster Kubernetes no Azure é um cluster Kubernetes gerenciado compartilhado, de modo que sua equipe pode trabalhar conjuntamente de forma colaborativa. Você pode desenvolver o código de forma isolada, depois implantar no cluster global e realizar testes de ponta a ponta com outros componentes sem replicar ou criar dependências fictícias.

Conforme mostrado na Figura 4 a 9, o recurso diferenciador mais nos espaços de desenvolvimento do Azure é a capacidade de criar "espaços" que podem ser executados integrados ao restante da implantação global no cluster.

![O Azure Dev Spaces pode misturar e combinar microsserviços de produção transparentemente com a instância de contêiner de desenvolvimento, para facilitar o teste de novas versões.](media/image38.png)

**Figura 4-9**. Usando vários espaços no Azure Dev Spaces

Basicamente, você pode configurar um espaço de desenvolvimento compartilhado no Azure. Cada desenvolvedor pode se concentrar em apenas em sua parte do aplicativo e iterativamente podem desenvolver código "previamente confirmado" em um espaço de desenvolvimento que já contém todos os outros serviços e recursos que dependem de seus cenários de nuvem. As dependências estão sempre atualizadas e os desenvolvedores trabalham de uma forma que reflete a produção.

Espaços de desenvolvimento do Azure oferece o conceito de um espaço, o que lhe permite trabalhar isoladamente e sem medo de interromper os membros da equipe. Esse recurso se baseia nos prefixos de URL; Se você usar um prefixo de espaço de desenvolvimento na URL de solicitação de um contêiner, espaços de desenvolvimento do Azure executa uma versão especial do contêiner em que ele implantado para esse espaço, se houver. Caso contrário, ele executará a versão global/consolidada.

Você pode ver os [página de wiki de eShopOnContainers em espaços de desenvolvimento do Azure](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) para obter uma visão prática em um exemplo concreto.

Para obter mais informações, consulte o artigo sobre [desenvolvimento em equipe com espaços de desenvolvimento do Azure](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Recursos adicionais

- **Introdução ao AKS (Serviço de Kubernetes do Azure)** \
  [*https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal*](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

- **Azure Dev Spaces** \
  [*https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces*](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces)

- **Kubernetes.** O site oficial. \
  [*https://kubernetes.io/*](https://kubernetes.io/)

## <a name="using-azure-service-fabric"></a>Usando o Azure Service Fabric

O Azure Service Fabric surgiu da transição da Microsoft do fornecimento de produtos de "caixa", que eram normalmente monolíticos em estilo, no fornecimento de serviços. A experiência de criar e operar serviços grandes em grande escala, como o banco de dados SQL do Azure, Azure Cosmos DB, barramento de serviço do Azure ou back-end do Cortana, modelou o Service Fabric. A plataforma evoluiu ao longo do tempo conforme mais serviços a adotaram. Mais importante, o Service Fabric precisava ser executado não apenas no Azure, mas também em implantações autônomas do Windows Server.

O objetivo do Service Fabric é resolver os difíceis problemas de criação e execução de um serviço e de utilização de recursos de infraestrutura com eficiência para que as equipes possam resolver problemas de negócios usando uma abordagem de microsserviços.

O Service Fabric fornece duas amplas áreas para ajudá-lo a criar aplicativos que usam uma abordagem de microsserviços:

- Uma plataforma que fornece serviços de sistema para implantar, dimensionar, atualizar, detectar, reiniciar serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade. Esses serviços de sistema em vigor habilitam muitas características de microsserviços descritas anteriormente.

- APIs de programação, ou estruturas, para ajudá-lo a criar aplicativos como microsserviços: [Reliable Actors e Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). É possível escolher qualquer código para criar seu microsserviço, mas essas APIs simplificam o trabalho e integram-se à plataforma em um nível mais profundo. Dessa forma, é possível obter informações de integridade e de diagnóstico ou aproveitar o gerenciamento de estado confiável.

O Service Fabric é independente em relação à maneira como você cria seu serviço, e é possível usar qualquer tecnologia. No entanto, ele fornece APIs de programação internas que facilitam a criação de microsserviços.

Conforme mostrado na Figura 4 a 10, você pode criar e executar microsserviços no Service Fabric como processos simples ou como contêineres do Docker. Também é possível combinar microsserviços baseados em contêineres com microsserviços baseados em processos dentro do mesmo cluster do Service Fabric.

![Clusters de malha de comparação de serviço do Azure: Microsserviços como processos em que cada nó executa um processo para cada microsserviço; Microsserviços como contêineres onde cada nó executa o Docker com vários contêineres, um contêiner por microsserviço.](./media/azure-service-fabric-cluster-types.png)

**Figura 4-10**. Implantando microsserviços como processos ou como contêineres no Azure Service Fabric

Os clusters do Service Fabric baseados em hosts Linux e do Windows podem executar contêineres Linux do Docker e contêineres do Windows, respectivamente.

Para obter informações atualizadas sobre o suporte a contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric é um bom exemplo de uma plataforma em que você pode definir uma arquitetura lógica diferente (microsserviços de negócios ou contextos limitados) da implementação física. Por exemplo, se você implementar [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) na [do Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), que são introduzidos na próxima seção, "[sem estado versus microsserviços com estado](#stateless-versus-stateful-microservices), "você tem um conceito de microsserviço de negócios com vários serviços físicos.

Conforme mostrado na Figura 4-10 e com base em uma perspectiva de microsserviço lógico/de negócios, ao implementar um serviço do Service Fabric com monitoração de estado confiável, você geralmente precisará implementar dois níveis de serviços. O primeiro é o serviço confiável com estado de back-end, que manipula várias partições (cada partição é um serviço com estado). O segundo é o serviço de front-end, ou serviço de Gateway, responsável pelo roteamento e agregação de dados entre várias partições ou instâncias de serviço com estado. Esse serviço de Gateway também manipula a comunicação do cliente com loops de repetição que acessam o serviço de back-end. Ele é chamado de serviço de Gateway, se você implementar seu serviço personalizado, ou como alternativa, você também pode usar a malha de serviço out of box [proxy reverso](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![O Service Fabric tem prescrição para dar suporte a vários serviços confiáveis com estado em contêineres.](./media/service-fabric-stateful-business-microservice.png)

**Figura 4-11**. Microsserviço de negócios com várias instâncias de serviço com monitoração de estado e um front-end do gateway personalizado

Em qualquer caso, quando você usa o Service Fabric Reliable Services com monitoração de estado, você também tem um lógico ou de negócio microsserviço (contexto limitado) que é composto de vários serviços físicos. Cada um dos-los, o serviço de Gateway e o serviço de partição pode ser implementada como serviços da API Web do ASP.NET, conforme mostrado na Figura 4-11.

No Service Fabric, é possível agrupar e implantar grupos de serviços como um [Aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orquestrador ou do cluster. Portanto, o aplicativo do Service Fabric poderia ser mapeado para esse limite autônomo de microsserviço lógico e de negócios ou Contexto limitado também para você poder implantar esses serviços de maneira autônoma.

### <a name="service-fabric-and-containers"></a>Service Fabric e contêineres

Com relação a contêineres no Service Fabric, também é possível implantar serviços em imagens de contêiner dentro de um cluster do Service Fabric. Como mostra a Figura 4 a 12, quase sempre haverá apenas um contêiner por serviço.

![Um aplicativo do Service Fabric pode executar vários contêineres acessando um banco de dados externo e todo o conjunto seria o limite lógico de um Microsserviço de negócios](./media/azure-service-fabric-business-microservice.png)

**Figura 4-12**. Microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados “sidecar” (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis no Service Fabric. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, poderia ser um único serviço com um único modelo de dados, mas, em alguns outros casos, talvez seja necessário ter vários serviços físicos também.

Observe que você pode misturar serviços em processos e serviços em contêineres no mesmo aplicativo do Service Fabric, conforme mostrado na Figura 4-13.

![Um aplicativo do service fabric executando os serviços e contêineres no mesmo nó.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Figura 4-13**. Microsserviço de negócios mapeado para um aplicativo do Service Fabric com contêineres e serviços com estado

Para obter informações sobre o suporte a contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microsserviços com estado versus sem estado

Conforme mencionado anteriormente, cada microsserviço (Contexto limitado lógico) deve ter seu próprio modelo de domínio (dados e lógica). No caso de microsserviços sem estado, os bancos de dados serão externos, empregando opções relacionais, como SQL Server, ou opções NoSQL, como o Azure Cosmos DB ou o MongoDB.

Mas os próprios serviços também podem ter estado no Service Fabric, o que significa que os dados residem dentro do microsserviço. Esses dados podem existir não só no mesmo servidor, como dentro do processo de microsserviço, na memória e persistentes em discos rígidos e replicados em outros nós. A Figura 4-30 mostra as diferentes abordagens.

![Nos serviços sem monitoração de estado, o estado (persistência, banco de dados) é mantido fora do microsserviço. Nos serviços com monitoração de estado, estado é mantido dentro do microsserviço.](./media/stateless-vs-stateful-microservices.png)

**Figura 4-14**. Microsserviços com estado versus sem estado

Uma abordagem sem estado é perfeitamente válida e mais fácil de ser implementada do que microsserviços com estado, uma vez que ela é semelhante a padrões tradicionais e já conhecidos. Mas microsserviços sem estado impõem latência entre o processo e as fontes de dados. Eles também envolvem mais movimentação de partes quando você está tentando aprimorar o desempenho com cache e filas adicionais. O resultado é que você pode acabar com arquiteturas complexas que têm muitas camadas.

Por outro lado, [microsserviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) podem se destacar em cenários avançados, pois não há latência entre a lógica e os dados de domínio. O processamento de dados pesado, os back-ends de jogos, os bancos de dados como serviço e outros cenários de baixa latência se beneficiam de serviços com estado, que usam o estado local para obter um acesso mais rápido.

Serviços sem estado e com estado são complementares. Por exemplo, como você pode ver no diagrama à direita na Figura 4-31, um serviço com estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem estado que funcione como um serviço de gateway que saiba como tratar cada partição com base nas chaves de partição.

Os serviços com estado têm desvantagens. Elas impõem um nível de complexidade alta para ser expandida. A funcionalidade que normalmente seria implementada por sistemas de banco de dados externos deve ser orientada para tarefas como replicação de dados entre microsserviços com estado e particionamento de dados. No entanto, essa é uma das áreas em que um orquestrador como o [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seus [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ser de maior utilidade – simplificando o desenvolvimento e o ciclo de vida de microsserviços com estado que usam a [API de Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem serviços com estado, que dão suporte a padrão de ator e que melhoram a tolerância a falhas e a latência entre os dados e a lógica de negócios são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [Akka.NET](https://getakka.net/). No momento, ambas as estruturas estão melhorando o suporte para Docker.

Lembre-se de que os contêineres do Docker são sem estado. Se você desejar implementar um serviço com estado, será necessária uma das estruturas adicionais prescritivas e de nível mais alto descritas anteriormente.

## <a name="using-azure-service-fabric-mesh"></a>Usando a Malha do Azure Service Fabric

Malha do Azure Service Fabric é um serviço totalmente gerenciado que permite aos desenvolvedores criar e implantar aplicativos de missão crítica sem gerenciar qualquer infraestrutura. Use a Malha do Service Fabric para compilar e executar aplicativos de microsserviços distribuídos e seguros dimensionados sob demanda.

Conforme mostrado na Figura 4-15, os aplicativos hospedados na malha do serviço Fabric executar e dimensionar sem que você se preocupar sobre a infraestrutura ligá-la.

![Um aplicativo de vários contêiner em execução na área de trabalho do Docker pode ser implantado para a malha do Azure Service Fabric sem se preocupar sobre infraestrutura.](media/image39.png)

**Figura 4-15**. Implantação de um aplicativo de microsserviço/contêineres à Malha do Service Fabric

Nos bastidores, a Malha do Service Fabric é composta por clusters de milhares de computadores. Todas as operações de cluster estão ocultas do desenvolvedor. Você simplesmente precisa fazer upload dos contêineres e recursos específicos necessários, dos requisitos de disponibilidade e dos limites de recursos. A Malha do Service Fabric aloca automaticamente a infraestrutura solicitada pela implantação do aplicativo e também manipula falhas de infraestrutura, certificando de que seus aplicativos estão altamente disponíveis. Só é necessário se preocupar com a integridade e com a capacidade de resposta do seu aplicativo, não com a infraestrutura.

Para obter mais informações, consulte o [documentação de malha do serviço Fabric](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Escolha de orquestradores no Azure

A tabela a seguir fornece orientação sobre qual orquestrador deve ser usado dependendo das cargas de trabalho e do foco no sistema operacional.

![Serviços de Kubernetes do Azure é mais maduro no Linux que no Windows e é usado principalmente para a implantação de microsserviços com base em contêineres. O Azure Service Fabric (cluster e malha) está mais maduro no Windows do que no Linux, comumente usado para microsserviços baseados em contêineres, microsserviços baseados em processos simples e serviços com estado.](media/image40.png)

**Figura 4-16**. Seleção do orquestrador em diretrizes do Azure

>[!div class="step-by-step"]
>[Anterior](soa-applications.md)
>[Próximo](deploy-azure-kubernetes-service.md)
