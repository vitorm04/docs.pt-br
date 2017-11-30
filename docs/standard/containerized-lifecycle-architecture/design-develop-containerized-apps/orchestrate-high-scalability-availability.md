---
title: Organizar microservices e multicontainer aplicativos de alto desempenho e disponibilidade
description: "Ciclo de vida de aplicativo de Docker em contêineres com ferramentas e plataformas da Microsoft"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: ea492de1c4709eb7bafe65fcf288482da9855240
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2017
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Organizar microservices e multicontainer aplicativos de alto desempenho e disponibilidade

Usando orchestrators para aplicativos prontos para produção é essencial se seu aplicativo baseado no microservices ou simplesmente dividido em vários contêineres. Conforme apresentado anteriormente, uma abordagem baseada em microsserviço, cada microsserviço possui seu modelo e dados para que é autônomo de um desenvolvimento e implantação de ponto de vista. Mas, mesmo se você tiver um aplicativo mais tradicional que é composto de vários serviços (como o SOA), você também terá vários contêineres ou serviços que compõem um aplicativo de negócios único que precisa ser implantado como um sistema distribuído. Esses tipos de sistemas são complexos de expansão e gerenciar; Portanto, absolutamente necessário um orquestrador se desejar ter um aplicativo multicontainer pronto para produção e escalonável.

Figura 4-6 ilustra uma implantação em um cluster de um aplicativo composto de vários microservices (contêineres).

![](./media/image6.png)

Figura 4-6: um cluster de contêineres

Ele se parece com uma abordagem lógica. Mas como você está lidando com balanceamento de carga, roteamento e organizar esses aplicativos compostos?

A interface de linha de comando do Docker (CLI) atende às necessidades de gerenciamento de um contêiner em um host, mas fica curto quando se trata de gerenciar vários contêineres implantados em vários hosts para aplicativos distribuídos mais complexos. Na maioria dos casos, você precisa de uma plataforma de gerenciamento que será automaticamente contêineres de iniciar, suspender, ou desligá-las quando necessário e idealmente também controlar como eles acessam os recursos como o rede e armazenamento de dados.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos muito simples e mudança para os maiores aplicativos empresariais com microservices, você deve ativar a coordenação e o clustering de plataformas.

De um arquitetura e desenvolvimento do ponto de Vista, se você estiver criando grande, empresa, com base em microservices, aplicativos, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

-   **Clusters e orchestrators** quando precisar dimensionar-aplicativos em vários hosts de Docker, como com um aplicativo baseado em microservices grande, é essencial para gerenciar todos os hosts como um único cluster por abstrair a complexidade da plataforma subjacente. É o que fornece os clusters de contêiner e orchestrators. Exemplos de orchestrators são Docker Swarm Mesosphere DC/OS, Kubernetes (os três primeiros disponíveis por meio do serviço de contêiner do Azure) e do Azure Service Fabric.

-   **Agendadores** *agendamento* significa ter a capacidade de um administrador para iniciar contêineres em um cluster de forma que elas também fornecem uma interface do usuário. Um cluster possui várias responsabilidades: para usar recursos do cluster com eficiência, para definir as restrições fornecidas pelo usuário, para contêineres de balanceamento de carga com eficiência em nós ou hosts e ser robusto contra erros, proporcionando alto disponibilidade.

Os conceitos de um cluster e um agendador estão intimamente relacionados, para que os produtos fornecidos por fornecedores diferentes geralmente fornecem os dois conjuntos de recursos. Tabela 4-1 lista de plataforma mais importante e opções de software que você tem para clusters e agendadores. Esses clusters são geralmente oferecidos em nuvens públicas, como o Azure.

Tabela 4-1: plataformas de Software para o contêiner de clustering, orquestração e agendamento

| Plataforma | Descrição |
|---|---|
| Por nuvem de docker<br/> ![http://rancher.com/wp-content/Themes/rancher-2016/Assets/images/swarm.PNG?v=2016-07-10-AM](./media/image7.png) | Por docker nuvem fornece a capacidade de cluster e agendar a contêineres do Docker. Usando por nuvem, você pode transformar um pool de hosts de Docker em um único host Docker virtual. Os clientes podem fazer solicitações de API para por nuvem da mesma forma que eles fazem a hosts, o que significa que por nuvem torna mais fácil para os aplicativos a dimensionar para vários hosts. <br /><br /> Por docker nuvem é um produto, a empresa Docker. <br /><br /> V docker 1.12 ou posterior pode executar modo Swarm internos e nativos. |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.PNG](./media/image8.png) |  Mesosphere Enterprise DC/OS (com base no Apache Mesos) é uma plataforma de pronto para produção para executar contêineres e aplicativos distribuídos. <br /><br /> Controlador de domínio/OS funciona abstração de uma coleção dos recursos disponíveis no cluster e disponibilizar esses recursos para componentes criados sobre ele. Maratona geralmente é usada como um agendador integrado ao controlador de domínio/OS. |
| Kubernetes do Google<br />![https://PBS.twimg.com/Media/BT\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes é um produto de código-fonte aberto que fornece a funcionalidade que varia de infraestrutura de cluster e agendamento para recursos de orquestração do contêiner. Com ele, você pode automatizar a implantação, dimensionar e operações de contêineres de aplicativos em clusters de hosts. <br /><br /> Kubernetes fornece uma infraestrutura centrada no contêiner que agrupa os contêineres de aplicativos em unidades lógicas para facilitar o gerenciamento e descoberta. |
| Malha do serviço do Azure<br />![https://Azure.microsoft.com/svghandler/Service-Fabric?Width=600&Height=315](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microservices da Microsoft para a criação de aplicativos. É um [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. Por padrão, o Service Fabric implanta e ativa serviços como processos mas Service Fabric pode implantar os serviços em imagens de contêiner do Docker. O mais importante, é possível combinar serviços em processos com os serviços em contêineres no mesmo aplicativo. <br /><br /> A partir de maio de 2017, o recurso de malha do serviço que dá suporte a serviços de implantação como contêineres do Docker está em estado de visualização. <br /><br /> Você pode desenvolver serviços de malha do serviço de várias maneiras de usar o [modelos de programação do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) à implantação [convidado executáveis](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) , bem como contêineres. Malha do serviço oferece suporte a modelos de aplicativo prescritivas como [services com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Usando com base em contêiner orchestrators no Azure

Vários fornecedores de nuvem oferecem suporte de contêineres do Docker mais clusters do Docker e suporte de orquestração, incluindo Azure, o serviço de contêiner do Amazon EC2 e o mecanismo de contêiner do Google. O Azure fornece Docker suporte a cluster e orchestrator por meio do serviço de contêiner do Azure, conforme explicado na próxima seção.

Outra opção é usar o Azure Service Fabric, que também oferece suporte a Docker com base em contêineres do Linux e Windows. Malha do serviço é executado no Azure ou qualquer outra nuvem, bem como [local](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Usando o serviço de contêiner do Azure

Um cluster de Docker agrupa vários hosts de Docker e expõe como um único host Docker virtual, para que possa implantar vários contêineres no cluster. O cluster tratará todos os detalhes de gerenciamento complexas, como escalabilidade e integridade. Figura 4-7 representa como um cluster de Docker para aplicativos compostos mapeia para o serviço de contêiner.

Contêiner de serviço fornece uma maneira para simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres. Usando uma configuração otimizada das ferramentas de planejamento e a coordenação de código-fonte aberto populares, contêiner de serviço fornece a capacidade de usar suas habilidades existentes ou desenhe um corpo grande e crescente de experiência de comunidade para implantar e gerenciar com base em contêiner aplicativos no Azure.

Serviço de contêiner otimiza a configuração de tecnologias e ferramentas do Docker clusters código-fonte aberto populares especificamente para o Azure. Você obtém uma solução aberta que oferece portabilidade para seus contêineres e sua configuração de aplicativo. Selecione o tamanho, o número de hosts e as ferramentas do orchestrator e serviço de contêiner manipula todo o resto.

Serviço de contêiner usa imagens do Docker para garantir que seus contêineres de aplicativos são totalmente portáteis. Ele dá suporte a variedade de plataformas de orquestração do código-fonte aberto como controlador de domínio/OS, Kubernetes e Docker Swarm para garantir que esses aplicativos podem ser dimensionados em milhares ou até mesmo dezenas de milhares de contêineres.

Com o serviço de contêiner do Azure, você pode tirar proveito dos recursos de nível empresarial do Azure e ainda manter a portabilidade de aplicativo, incluindo nas camadas de orquestração.

![](./media/image11.png)

Figura 4-7: Clustering opções no serviço de contêiner do Azure

Conforme mostrado na Figura 4-8, o serviço de contêiner é simplesmente a infraestrutura fornecida pelo Azure para implantar o Docker Swarm, Kubernetes ou DC/SO, mas ele não implementa qualquer orchestrator adicional. Portanto, o serviço de contêiner é não um orchestrator, assim; ele é apenas uma infraestrutura que aproveita orchestrators do código-fonte existentes para contêineres.

![](./media/image12.png)

Figura 4-8: Orchestrators no serviço de contêiner

De uma perspectiva de uso, o objetivo do serviço de contêiner é fornecer um ambiente de hospedagem de contêiner usando tecnologias e ferramentas de software livre populares. Para esse fim, ele expõe os pontos de extremidade de API padrão para o orchestrator escolhido. Ao usar esses pontos de extremidade, você pode usar qualquer software que pode se comunicar com esses pontos de extremidade. Por exemplo, no caso do ponto de extremidade Docker Swarm, você pode optar por usar a CLI do Docker. Para DC/sistema operacional, você pode optar por usar a CLI do controlador de domínio/OS.

### <a name="getting-started-with-container-service"></a>Guia de Introdução ao serviço de contêiner

Para começar a usar o serviço de contêiner, você implanta um cluster do serviço de contêiner do portal do Azure usando um modelo do Azure Resource Manager ou o [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Modelos disponíveis incluem [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), e [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Você pode modificar os modelos de início rápido para incluir a configuração do Azure adicional ou avançada.

**Obter mais informações** para saber mais sobre como implantar um cluster do serviço de contêiner, no site do Azure, leia [implantar um cluster do serviço de contêiner do Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Não há nenhuma taxa para qualquer software instalado por padrão como parte do ACS. Todas as opções padrão são implementadas com o software de código-fonte aberto.

Serviço de contêiner está disponível atualmente para um padrão, D, DS, G e VMs do Linux série GS no Azure. Você é cobrado somente para as instâncias de computação que você escolher, bem como outros subjacente infraestrutura recursos consumidos, como armazenamento e rede. Não há nenhum incrementais encargos para o serviço de contêiner em si.

### <a name="additional-resources"></a>Recursos adicionais

Estes são os locais onde você pode encontrar informações adicionais:

-   Introdução ao contêiner do Docker hospedagem soluções com o serviço de contêiner:  
    https://docs.microsoft.com/Azure/container-Service/kubernetes/container-Service-Intro-kubernetes>

-   Visão geral do docker por nuvem:  
    <https://docs.docker.com/swarm/Overview/>

-   Visão geral do modo por nuvem:  
    <https://docs.docker.com/Engine/swarm/>

-   Visão geral do controlador de domínio/OS mesosphere:    
    <https://docs.mesosphere.com/1.7/Overview/>

-   Kubernetes (o site oficial):  
    <http://kubernetes.IO/>

## <a name="using-service-fabric"></a>Usando o Service Fabric

Serviço de malha surgiu de transição da Microsoft do fornecimento de produtos de "caixa", que foram normalmente monolíticos em estilo, para o fornecimento de serviços. A experiência de criar e operar a grandes serviços em grande escala, como banco de dados do SQL Azure, banco de dados de documento do Azure, barramento de serviço do Azure ou back-end do Cortana, em forma de malha do serviço. A plataforma desenvolvidos ao longo do tempo conforme mais e mais serviços adotaram. É importante, Service Fabric precisava executar não apenas no Azure, mas também em implantações do Windows Server autônomo.

É o objetivo de serviço de malha resolver os problemas difíceis de criação e execução de um serviço e utilizando os recursos de infraestrutura com eficiência para que as equipes podem resolver problemas de negócios usando uma abordagem de microservices.

Serviço de malha fornece duas áreas amplas para ajudá-lo a criar aplicativos que usam uma abordagem microservices:

-   Uma plataforma que fornece serviços para implantar, dimensionar, atualizar, detectar, reinicie os serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade do sistema. Esses serviços de sistema em vigor oferecem muitas das características de microservices descrito anteriormente.

-   APIs de programação ou estruturas, para ajudá-lo a criar aplicativos como microservices: [serviços confiáveis e atores confiáveis](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Obviamente, você pode escolher qualquer código para criar seu microsserviço, mas essas APIs que o trabalho mais simples e integram-se com a plataforma em um nível mais profundo. Dessa forma, você pode obter a integridade e informações de diagnóstico ou você pode tirar proveito do gerenciamento de estado confiável.

Service Fabric é agnóstico em relação a como você pode criar seu serviço, e você pode usar qualquer tecnologia. No entanto, ele fornece APIs de programação internos que facilitam a compilação microservices.

Figura 4-9 demonstra como você pode criar e executar microservices na malha do serviço, como processos simples ou como contêineres do Docker. Também é possível misturar com base em contêiner microservices com microservices em processo dentro do mesmo cluster do Service Fabric.

![](./media/image13.png)

Figura 4-9: Implantando microservices como processos ou contêineres no Azure Service Fabric

Clusters de malha do serviço com base em hosts Linux e Windows podem executar contêineres do Docker Linux e Windows.

**Obter mais informações** para obter informações atualizadas sobre o suporte de contêineres no serviço de malha, no site do Azure, leia [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric é um bom exemplo de uma plataforma com o qual você pode definir uma arquitetura lógica diferente (microservices de negócios ou contextos limitada) que a implementação física. Por exemplo, se você implementar [serviços confiáveis com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) na [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), que é introduzido na próxima seção, "[sem monitoração de estado versus com monitoração de estado microservices](#stateless-versus-stateful-microservices), "você tem um conceito de microsserviço de negócios com vários serviços físicos.

Conforme mostrado na Figura 4-10 e pensar em uma perspectiva de microsserviço de lógica de negócios, ao implementar um serviço confiável do serviço de malha com monitoração de estado, você geralmente precisará implementar duas camadas de serviços. A primeira é o serviço back-end com monitoração de estado confiável, que trata de várias partições. O segundo é o serviço front-end ou o serviço de Gateway, responsável por agregação de roteamento e os dados em várias partições ou instâncias de serviço com monitoração de estado. Esse serviço de Gateway também gerencia a comunicação de cliente com loops de repetição acessando o serviço de back-end usado em conjunto com a malha do serviço [proxy reverso](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Figura 4-10: microsserviço de negócios com vários serviços com e sem monitoração de estado na malha do serviço

Em qualquer caso, quando você usa serviços confiáveis do serviço de malha com monitoração de estado, você também tem um lógico ou de negócio microsserviço (contexto limitado) que normalmente é composto de vários serviços físicos. Cada um dos-los, o serviço de Gateway e o serviço de partição pode ser implementada como serviços de API da Web ASP.NET, conforme mostrado na Figura 4-10.

Na malha do serviço, você pode agrupar e implantar grupos de serviços como um [aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orchestrator ou cluster. Portanto, o aplicativo de malha do serviço pôde ser mapeado bem para este empresariais e limites de microsserviço lógico ou contexto limitado.

### <a name="service-fabric-and-containers"></a>Serviço de malha e contêineres

Em relação a contêineres na malha do serviço, você também pode implantar serviços em imagens de contêiner em um cluster do Service Fabric. Figura 4-11 ilustra que a maior parte do tempo, haverá apenas um contêiner por serviço.

![](./media/image15.png)

Figura 4-11: microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados "secundário" (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis na malha do serviço. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, pode ser um único serviço com um único modelo de dados, mas em alguns outros casos, você pode ter vários serviços físicos, também.

A partir desta documentação (abril de 2017), na malha do serviço não é possível implantar serviços de monitoração de estado confiável SF em contêineres — você pode implantar apenas contêineres de convidado, serviços sem monitoração de estado ou serviços de ator em contêineres. Mas observe que você pode combinar serviços em processos e serviços em contêineres no mesmo aplicativo de malha do serviço, conforme mostrado na Figura 4-12.

![](./media/image16.png)

Figura 4-12: Business microsserviço mapeado para um aplicativo de malha do serviço com contêineres e serviços com monitoração de estado

O suporte também é diferente dependendo se você estiver usando contêineres do Docker no Linux ou contêineres do Windows. Suporte para contêineres na malha do serviço estará em constante expansão em versões futuras. Para obter notícias atualizadas sobre o suporte de contêiner no serviço de malha, no site do Azure, leia [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Sem monitoração de estado versus microservices com monitoração de estado

Como mencionado anteriormente, cada microsserviço (contexto lógico limitada) deve ter seu modelo de domínio (dados e lógica). No caso de microservices sem monitoração de estado, os bancos de dados será externos, empregando relacionais opções como o SQL Server ou NoSQL opções como MongoDB ou DocumentDB do Azure.

Mas os próprios serviços também podem ser com monitoração de estado, o que significa que os dados que residem dentro de microsserviço. Esses dados podem existir não apenas no mesmo servidor, mas dentro do processo de microsserviço, na memória e mantidos em unidades e replicadas para outros nós. Figura 4-13 mostra as abordagens diferentes.

![](./media/image17.png)

Figura 4-13: sem monitoração de estado versus microservices com monitoração de estado

Uma abordagem sem monitoração de estado é perfeitamente válida e é mais fácil de implementar do que com monitoração de estado microservices porque a abordagem é semelhante aos padrões tradicionais e bem conhecidos. Mas sem monitoração de estado microservices impor a latência entre as processo e fontes de dados. Eles também envolvem mais movendo partes quando você está tentando melhorar o desempenho com filas e cache adicional. O resultado é que você pode acabar com arquiteturas complexas que têm muitos níveis.

Por outro lado, [microservices com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) o excel em cenários avançados porque não há nenhuma latência entre a lógica do domínio e os dados. Processamento de dados pesado, jogos back-ends, bancos de dados como um serviço e outros cenários de baixa latência todos os benefícios dos serviços com monitoração de estado, que fornecem o estado local para acesso mais rápido.

Serviços com e sem monitoração de estado são complementares. Por exemplo, um serviço com monitoração de estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem monitoração de estado atuando como um serviço de gateway que sabe como tratar cada partição com base nas chaves de partição.

Serviços com monitoração de estado tem desvantagens. Elas impõem um nível de complexidade que permitirá a expansão. A funcionalidade que normalmente poderia ser implementada por sistemas de banco de dados externo deve ser abordada para tarefas como a replicação de dados em microservices com monitoração de estado e particionamento de dados. No entanto, essa é uma das áreas onde um orquestrador que [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seus [serviços confiáveis com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ajudar a maior parte —, simplificando o desenvolvimento e o ciclo de vida de monitoração de estado microservices usando o [API de serviços confiável](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem que os serviços com monitoração de estado, que oferece suporte a padrões de ator e que melhoram a tolerância a falhas e a latência entre a lógica de negócios e os dados são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [ Akka.NET](http://getakka.net/). Ambas as estruturas atualmente estão aumentando o suporte para Docker.

Observe que contêineres do Docker são sem monitoração de estado. Se você quiser implementar um serviço com monitoração de estado, você precisa de um das estruturas de nível mais alto e prescritivas adicionais observadas anteriormente. No entanto, redação deste artigo, os serviços com monitoração de estado na malha do serviço não têm suporte como contêineres, apenas como microservices simples. Suporte a serviços confiáveis nos contêineres estarão disponível em versões futuras do Service Fabric.


>[!div class="step-by-step"]
[Anterior] (soa-applications.md) [Avançar] (docker-aplicativos-desenvolvimento-environment.md)
