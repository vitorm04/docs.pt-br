---
title: Organizar microservices e multicontainer aplicativos de alto desempenho e disponibilidade
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 5c7016fa8b731170a63f5d0f9d9bed3b72090be4
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106373"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Organizar microservices e multicontainer aplicativos de alto desempenho e disponibilidade

O uso de orquestradores em aplicativos prontos para produção é essencial se o aplicativo for baseado em microsserviços ou simplesmente dividido em vários contêineres. Conforme apresentado anteriormente, em uma abordagem baseada em microsserviço, cada microsserviço tem seu próprio modelo e dados para que seja autônomo de um ponto de vista de desenvolvimento e implantação. Mas, mesmo se você tiver um aplicativo mais tradicional que é composto de vários serviços (como o SOA), você também terá vários contêineres ou serviços que compõem um aplicativo de negócios único que precisa ser implantado como um sistema distribuído. Esses tipos de sistemas são complexos de expansão e gerenciar; Portanto, absolutamente necessário um orquestrador se desejar ter um aplicativo multicontainer pronto para produção e escalonável.

Figura 4-6 ilustra uma implantação em um cluster de um aplicativo composto de vários microservices (contêineres).

![](./media/image6.png)

Figura 4-6: um cluster de contêineres

Parece ser uma abordagem lógica. Mas como você está lidando com balanceamento de carga, roteamento e organizar esses aplicativos compostos?

A interface de linha de comando do Docker (CLI) atende às necessidades de gerenciamento de um contêiner em um host, mas fica curto quando se trata de gerenciar vários contêineres implantados em vários hosts para aplicativos distribuídos mais complexos. Na maioria dos casos, você precisa de uma plataforma de gerenciamento que será automaticamente contêineres de iniciar, suspender, ou desligá-las quando necessário e idealmente também controlar como eles acessam os recursos como o rede e armazenamento de dados.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos muito simples e em direção a aplicativos empresariais com microsserviços, é necessário adotar a orquestração e as plataformas de clustering.

De um arquitetura e desenvolvimento do ponto de Vista, se você estiver criando grande, empresa, com base em microservices, aplicativos, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

-   **Clusters e orchestrators** quando precisar dimensionar-aplicativos em vários hosts de Docker, como com um aplicativo baseado em microservices grande, é essencial para gerenciar todos os hosts como um único cluster por abstrair a complexidade da plataforma subjacente. É isso que os clusters e orquestradores de contêiner fazem. Exemplos de orchestrators são Docker Swarm Mesosphere DC/OS, Kubernetes (os três primeiros disponíveis por meio do serviço de contêiner do Azure) e do Azure Service Fabric.

-   **Agendadores** *agendamento* significa ter a capacidade de um administrador para iniciar contêineres em um cluster de forma que elas também fornecem uma interface do usuário. Um cluster possui várias responsabilidades: para usar recursos do cluster com eficiência, para definir as restrições fornecidas pelo usuário, para contêineres de balanceamento de carga com eficiência em nós ou hosts e ser robusto contra erros, proporcionando alto disponibilidade.

Os conceitos de "cluster" e "agendador" estão intimamente relacionados, então os produtos oferecidos por diferentes fornecedores geralmente têm as duas capacidades. Tabela 4-1 lista de plataforma mais importante e opções de software que você tem para clusters e agendadores. Esses clusters são geralmente oferecidos em nuvens públicas, como o Azure.

Tabela 4-1: plataformas de Software para o contêiner de clustering, orquestração e agendamento

| Plataforma | Descrição |
|---|---|
| Docker Swarm<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Por docker nuvem fornece a capacidade de cluster e agendar a contêineres do Docker. Por meio do Swarm, é possível transformar um pool de hosts do Docker em um único host virtual. Os clientes podem fazer solicitações de API para por nuvem da mesma forma que eles fazem a hosts, o que significa que por nuvem torna mais fácil para os aplicativos a dimensionar para vários hosts. <br /><br /> O Docker Swarm é um produto da empresa Docker. <br /><br /> O Docker v1.12 ou versões posteriores podem executar o Modo Swarm nativo e interno. |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  O Mesosphere Enterprise DC/OS, baseado no Apache Mesos, é uma plataforma pronta para produção para contêineres em execução e aplicativos distribuídos. <br /><br /> O DC/OS abstrai uma coleção de recursos disponíveis no cluster e os disponibiliza para componentes criados nele. Geralmente, o Marathon é usado como agendador integrado ao DC/OS. |
| Kubernetes do Google<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | O Kubernetes é um software livre que oferece funcionalidades que variam da infraestrutura do cluster e do agendamento de contêiner a capacidades de orquestração. Com ele, você pode automatizar a implantação, dimensionar e operações de contêineres de aplicativos em clusters de hosts. <br /><br /> O Kubernetes oferece uma infraestrutura centrada no contêiner que agrupa contêineres de aplicativo em unidades lógicas para facilitar o gerenciamento e a descoberta. |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | O [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microsserviços da Microsoft para criação de aplicativos. Ele é um [orquestrador](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. Por padrão, o Service Fabric implanta e ativa serviços como processos mas Service Fabric pode implantar os serviços em imagens de contêiner do Docker. O mais importante, é possível combinar serviços em processos com os serviços em contêineres no mesmo aplicativo. <br /><br /> A partir de maio de 2017, o recurso de malha do serviço que dá suporte a serviços de implantação como contêineres do Docker está em estado de visualização. <br /><br /> Você pode desenvolver serviços de malha do serviço de várias maneiras de usar o [modelos de programação do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) à implantação [convidado executáveis](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) , bem como contêineres. Malha do serviço oferece suporte a modelos de aplicativo prescritivas como [services com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Usando com base em contêiner orchestrators no Azure

Vários fornecedores de nuvem oferecem suporte de contêineres do Docker mais clusters do Docker e suporte de orquestração, incluindo Azure, o serviço de contêiner do Amazon EC2 e o mecanismo de contêiner do Google. O Azure fornece Docker suporte a cluster e orchestrator por meio do serviço de contêiner do Azure, conforme explicado na próxima seção.

Outra opção é usar o Azure Service Fabric, que também oferece suporte a Docker com base em contêineres do Linux e Windows. Malha do serviço é executado no Azure ou qualquer outra nuvem, bem como [local](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Usar o Serviço de Contêiner do Azure

Um cluster do Docker cria um pool de diversos hosts e os expõe como um host virtual único. Assim, é possível implantar vários contêineres no cluster. O cluster tratará todos os detalhes de gerenciamento complexas, como escalabilidade e integridade. Figura 4-7 representa como um cluster de Docker para aplicativos compostos mapeia para o serviço de contêiner.

Contêiner de serviço fornece uma maneira para simplificar a criação, configuração e gerenciamento de um cluster de máquinas virtuais que são pré-configurados para executar aplicativos em contêineres. Usando uma configuração otimizada das ferramentas de planejamento e a coordenação de código-fonte aberto populares, contêiner de serviço fornece a capacidade de usar suas habilidades existentes ou desenhe um corpo grande e crescente de experiência de comunidade para implantar e gerenciar com base em contêiner aplicativos no Azure.

Serviço de contêiner otimiza a configuração de tecnologias e ferramentas do Docker clusters código-fonte aberto populares especificamente para o Azure. É uma solução aberta que oferece portabilidade para contêineres e configuração de aplicativo. Selecione o tamanho, a quantidade de hosts e as ferramentas de orquestrador e deixe o Serviço de Contêiner cuidar de todo o resto.

Serviço de contêiner usa imagens do Docker para garantir que seus contêineres de aplicativos são totalmente portáteis. Ele dá suporte a variedade de plataformas de orquestração do código-fonte aberto como controlador de domínio/OS, Kubernetes e Docker Swarm para garantir que esses aplicativos podem ser dimensionados em milhares ou até mesmo dezenas de milhares de contêineres.

Com o serviço de contêiner do Azure, você pode tirar proveito dos recursos de nível empresarial do Azure e ainda manter a portabilidade de aplicativo, incluindo nas camadas de orquestração.

![](./media/image11.png)

Figura 4-7: Clustering opções no serviço de contêiner do Azure

Conforme mostrado na Figura 4-8, o serviço de contêiner é simplesmente a infraestrutura fornecida pelo Azure para implantar o Docker Swarm, Kubernetes ou DC/SO, mas ele não implementa qualquer orchestrator adicional. Portanto, o serviço de contêiner é não um orchestrator, assim; ele é apenas uma infraestrutura que aproveita orchestrators do código-fonte existentes para contêineres.

![](./media/image12.png)

Figura 4-8: Orchestrators no serviço de contêiner

De uma perspectiva de uso, o objetivo do serviço de contêiner é fornecer um ambiente de hospedagem de contêiner usando tecnologias e ferramentas de software livre populares. Para isso, ele expõe os pontos de extremidade padrão da API do orquestrador escolhido. Ao usar esses pontos de extremidade, você pode usar qualquer software que pode se comunicar com esses pontos de extremidade. Por exemplo, no caso do ponto de extremidade Docker Swarm, você pode optar por usar a CLI do Docker. No DC/OS, você pode usar a CLI do DC/OS.

### <a name="getting-started-with-container-service"></a>Guia de Introdução ao serviço de contêiner

Para começar a usar o serviço de contêiner, você implanta um cluster do serviço de contêiner do portal do Azure usando um modelo do Azure Resource Manager ou o [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Modelos disponíveis: [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) e [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Você pode modificar os modelos de início rápido para incluir a configuração do Azure adicional ou avançada.

**Obter mais informações** para saber mais sobre como implantar um cluster do serviço de contêiner, no site do Azure, leia [implantar um cluster do serviço de contêiner do Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Nenhum valor é cobrado pelos softwares instalados por padrão como parte do ACS. Todas as opções padrão são implementadas com software livre.

Serviço de contêiner está disponível atualmente para um padrão, D, DS, G e VMs do Linux série GS no Azure. Você é cobrado somente para as instâncias de computação que você escolher, bem como outros subjacente infraestrutura recursos consumidos, como armazenamento e rede. Não há nenhum incrementais encargos para o serviço de contêiner em si.

### <a name="additional-resources"></a>Recursos adicionais

Estes são os locais onde você pode encontrar informações adicionais:

-   Introdução ao contêiner do Docker hospedagem soluções com o serviço de contêiner:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Visão geral do docker por nuvem:  
    <https://docs.docker.com/swarm/overview/>

-   Visão geral do modo por nuvem:  
    <https://docs.docker.com/engine/swarm/>

-   Visão geral do controlador de domínio/OS mesosphere:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (o site oficial):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Usando o Service Fabric

Serviço de malha surgiu de transição da Microsoft do fornecimento de produtos de "caixa", que foram normalmente monolíticos em estilo, para o fornecimento de serviços. A experiência de criar e operar a grandes serviços em grande escala, como banco de dados do SQL Azure, banco de dados de documento do Azure, barramento de serviço do Azure ou back-end do Cortana, em forma de malha do serviço. A plataforma evoluiu ao longo do tempo conforme mais serviços a adotaram. Mais importante, o Service Fabric precisava ser executado não apenas no Azure, mas também em implantações autônomas do Windows Server.

É o objetivo de serviço de malha resolver os problemas difíceis de criação e execução de um serviço e utilizando os recursos de infraestrutura com eficiência para que as equipes podem resolver problemas de negócios usando uma abordagem de microservices.

O Service Fabric fornece duas amplas áreas para ajudá-lo a criar aplicativos que usam uma abordagem de microsserviços:

-   Uma plataforma que fornece serviços de sistema para implantar, dimensionar, atualizar, detectar, reiniciar serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade. Esses serviços de sistema em vigor oferecem muitas das características de microservices descrito anteriormente.

-   APIs de programação, ou estruturas, para ajudá-lo a criar aplicativos como microsserviços: [Reliable Actors e Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Claro, é possível escolher qualquer código para criar seu microsserviço, mas essas APIs simplificam o trabalho e integram-se à plataforma em um nível mais profundo. Dessa forma, é possível obter informações de integridade e de diagnóstico ou aproveitar o gerenciamento de estado confiável.

O Service Fabric é independente em relação à maneira como você cria seu serviço, e é possível usar qualquer tecnologia. No entanto, ele fornece APIs de programação internas que facilitam a criação de microsserviços.

Figura 4-9 demonstra como você pode criar e executar microservices na malha do serviço, como processos simples ou como contêineres do Docker. Também é possível combinar microsserviços baseados em contêineres com microsserviços baseados em processos dentro do mesmo cluster do Service Fabric.

![](./media/image13.png)

Figura 4-9: Implantando microservices como processos ou contêineres no Azure Service Fabric

Clusters de malha do serviço com base em hosts Linux e Windows podem executar contêineres do Docker Linux e Windows.

**Obter mais informações** para obter informações atualizadas sobre o suporte de contêineres no serviço de malha, no site do Azure, leia [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric é um bom exemplo de uma plataforma com o qual você pode definir uma arquitetura lógica diferente (microservices de negócios ou contextos limitada) que a implementação física. Por exemplo, se você implementar [serviços confiáveis com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) na [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), que é introduzido na próxima seção, "[sem monitoração de estado versus com monitoração de estado microservices](#stateless-versus-stateful-microservices), "você tem um conceito de microsserviço de negócios com vários serviços físicos.

Conforme mostrado na Figura 4-10 e pensar em uma perspectiva de microsserviço de lógica de negócios, ao implementar um serviço confiável do serviço de malha com monitoração de estado, você geralmente precisará implementar duas camadas de serviços. A primeira é o serviço back-end com monitoração de estado confiável, que trata de várias partições. O segundo é o serviço de front-end, ou serviço de Gateway, responsável pelo roteamento e agregação de dados entre várias partições ou instâncias de serviço com estado. Esse serviço de Gateway também gerencia a comunicação de cliente com loops de repetição acessando o serviço de back-end usado em conjunto com a malha do serviço [proxy reverso](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Figura 4-10: microsserviço de negócios com vários serviços com e sem monitoração de estado na malha do serviço

Em qualquer caso, quando você usa os Reliable Services com estado do Service Fabric, você também tem um microsserviço lógico ou de negócios (Contexto limitado) geralmente composto por vários serviços físicos. Cada um dos-los, o serviço de Gateway e o serviço de partição pode ser implementada como serviços de API da Web ASP.NET, conforme mostrado na Figura 4-10.

No Service Fabric, é possível agrupar e implantar grupos de serviços como um [Aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orquestrador ou do cluster. Portanto, o aplicativo de malha do serviço pôde ser mapeado bem para este empresariais e limites de microsserviço lógico ou contexto limitado.

### <a name="service-fabric-and-containers"></a>Service Fabric e contêineres

Em relação a contêineres na malha do serviço, você também pode implantar serviços em imagens de contêiner em um cluster do Service Fabric. Figura 4-11 ilustra que a maior parte do tempo, haverá apenas um contêiner por serviço.

![](./media/image15.png)

Figura 4-11: microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados "secundário" (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis na malha do serviço. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, pode ser um único serviço com um único modelo de dados, mas em alguns outros casos, você pode ter vários serviços físicos, também.

A partir desta documentação (abril de 2017), na malha do serviço não é possível implantar serviços de monitoração de estado confiável SF em contêineres — você pode implantar apenas contêineres de convidado, serviços sem monitoração de estado ou serviços de ator em contêineres. Mas observe que você pode combinar serviços em processos e serviços em contêineres no mesmo aplicativo de malha do serviço, conforme mostrado na Figura 4-12.

![](./media/image16.png)

Figura 4-12: Business microsserviço mapeado para um aplicativo de malha do serviço com contêineres e serviços com monitoração de estado

O suporte também é diferente dependendo se você estiver usando contêineres do Docker no Linux ou contêineres do Windows. Suporte para contêineres na malha do serviço estará em constante expansão em versões futuras. Para obter notícias atualizadas sobre o suporte de contêiner no serviço de malha, no site do Azure, leia [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microsserviços com estado versus sem estado

Conforme mencionado anteriormente, cada microsserviço (Contexto limitado lógico) deve ter seu próprio modelo de domínio (dados e lógica). No caso de microservices sem monitoração de estado, os bancos de dados será externos, empregando relacionais opções como o SQL Server ou NoSQL opções como MongoDB ou DocumentDB do Azure.

Mas os próprios serviços também podem ser com monitoração de estado, o que significa que os dados que residem dentro de microsserviço. Esses dados podem existir não apenas no mesmo servidor, mas dentro do processo de microsserviço, na memória e mantidos em unidades e replicadas para outros nós. Figura 4-13 mostra as abordagens diferentes.

![](./media/image17.png)

Figura 4-13: sem monitoração de estado versus microservices com monitoração de estado

Uma abordagem sem monitoração de estado é perfeitamente válida e é mais fácil de implementar do que com monitoração de estado microservices porque a abordagem é semelhante aos padrões tradicionais e bem conhecidos. Mas microsserviços sem estado impõem latência entre o processo e as fontes de dados. Eles também envolvem mais movimentação de partes quando você está tentando aprimorar o desempenho com cache e filas adicionais. O resultado é que você pode acabar com arquiteturas complexas que têm muitas camadas.

Por outro lado, [microservices com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) o excel em cenários avançados porque não há nenhuma latência entre a lógica do domínio e os dados. Processamento de dados pesado, jogos back-ends, bancos de dados como um serviço e outros cenários de baixa latência todos os benefícios dos serviços com monitoração de estado, que fornecem o estado local para acesso mais rápido.

Serviços sem estado e com estado são complementares. Por exemplo, um serviço com monitoração de estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem estado que funcione como um serviço de gateway que saiba como tratar cada partição com base nas chaves de partição.

Os serviços com estado têm desvantagens. Elas impõem um nível de complexidade que permitirá a expansão. A funcionalidade que normalmente seria implementada por sistemas de banco de dados externos deve ser orientada para tarefas como replicação de dados entre microsserviços com estado e particionamento de dados. No entanto, essa é uma das áreas onde um orquestrador que [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seus [serviços confiáveis com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ajudar a maior parte —, simplificando o desenvolvimento e o ciclo de vida de monitoração de estado microservices usando o [API de serviços confiável](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem serviços com estado, que dão suporte a padrão de ator e que melhoram a tolerância a falhas e a latência entre os dados e a lógica de negócios são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [Akka.NET](https://getakka.net/). No momento, ambas as estruturas estão melhorando o suporte para Docker.

Observe que os contêineres do Docker são sem estado. Se você desejar implementar um serviço com estado, será necessária uma das estruturas adicionais prescritivas e de nível mais alto descritas anteriormente. No entanto, redação deste artigo, os serviços com monitoração de estado na malha do serviço não têm suporte como contêineres, apenas como microservices simples. Suporte a serviços confiáveis nos contêineres estarão disponível em versões futuras do Service Fabric.


>[!div class="step-by-step"]
[Anterior](soa-applications.md)
[Próximo](docker-apps-development-environment.md)
