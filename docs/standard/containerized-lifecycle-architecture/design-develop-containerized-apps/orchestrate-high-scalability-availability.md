---
title: Orquestrando microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade
description: Containerized Docker Application Lifecycle with Microsoft Platform and Tools (Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: fa64562808bba9c9dea5a5eedc367af7decf83b7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126894"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Orquestrando microsserviços e aplicativos de vários contêineres para alta escalabilidade e disponibilidade

O uso de orquestradores em aplicativos prontos para produção é essencial se o aplicativo for baseado em microsserviços ou simplesmente dividido em vários contêineres. Conforme apresentado anteriormente, em uma abordagem baseada em microsserviço, cada microsserviço tem seu próprio modelo e dados para que seja autônomo de um ponto de vista de desenvolvimento e implantação. Mas, mesmo se você tiver um aplicativo mais tradicional é composto de vários serviços (como o SOA), você também terá vários contêineres ou serviços que compõem um único aplicativo de negócios que precisam ser implantados como um sistema distribuído. Esses tipos de sistemas são complexos para escalar horizontalmente e gerenciar; Portanto, com certeza você precisa um orquestrador se você quiser ter um aplicativo de vários contêineres pronto para produção e escalonável.

Figura 4 a 6 ilustra uma implantação em um cluster de um aplicativo composto por vários microsserviços (contêineres).

![](./media/image6.png)

Figura 4 a 6: Um cluster de contêineres

Parece ser uma abordagem lógica. Mas como você está lidando com balanceamento de carga, roteamento e orquestração desses aplicativos compostos?

A interface de linha de comando do Docker (CLI) atende às necessidades de gerenciamento de um contêiner em um host, mas fica aquém quando se trata de gerenciar vários contêineres implantados em diversos hosts de aplicativos distribuídos mais complexos. Na maioria dos casos, você precisa de uma plataforma de gerenciamento que será automaticamente iniciar contêineres, suspendê-las, ou desligá-los quando necessário e também controlem como eles acessam recursos como o rede e armazenamento de dados.

Para ir além do gerenciamento de contêineres individuais ou aplicativos compostos muito simples e em direção a aplicativos empresariais com microsserviços, é necessário adotar a orquestração e as plataformas de clustering.

De um arquitetura e desenvolvimento ponto de Vista, se você estiver criando grandes, empresas, baseado em microsserviços, aplicativos, é importante entender as seguintes plataformas e produtos que dão suporte a cenários avançados:

-   **Clusters e orquestradores** quando você precisar dimensionar – os aplicativos em vários hosts do Docker, como com um aplicativo grande baseado em microsserviços, é fundamental ser capaz de gerenciar todos esses hosts como um único cluster por abstraindo a complexidade da plataforma subjacente. Esse é o que os clusters de contêiner e orquestradores fornecem. Exemplos de orquestradores são Docker Swarm, Mesosphere DC/OS, Kubernetes (os três primeiros disponíveis por meio do serviço de contêiner do Azure) e Azure Service Fabric.

-   **Agendadores** *agendamento* significa ter a capacidade de um administrador para iniciar contêineres em um cluster para que elas também fornecem uma interface do usuário. Um agendador de cluster tem diversas responsabilidades: usar os recursos de cluster com eficiência, para definir as restrições fornecidas pelo usuário, com eficiência os contêineres de balanceamento de carga em nós ou hosts e para ser robusto contra erros, fornecendo alto disponibilidade.

Os conceitos de "cluster" e "agendador" estão intimamente relacionados, então os produtos oferecidos por diferentes fornecedores geralmente têm as duas capacidades. Tabela 4-1 mostra a plataforma mais importante e opções de software para clusters e agendadores. Geralmente, esses clusters são oferecidos em nuvens públicas, como o Azure.

Tabela 4-1: Plataformas de software para clustering, orquestração e agendamento de contêineres

| Plataforma | Descrição |
|---|---|
| Docker Swarm<br/> ![Logotipo do Docker Swarm](./media/image7.png) | O docker Swarm fornece a capacidade de cluster e agendar contêineres do Docker. Por meio do Swarm, é possível transformar um pool de hosts do Docker em um único host virtual. Os clientes podem fazer solicitações de API ao Swarm da mesma forma que os hosts, o que significa que Swarm facilita para os aplicativos sejam dimensionados para vários hosts. <br /><br /> O Docker Swarm é um produto da empresa Docker. <br /><br /> O Docker v1.12 ou versões posteriores podem executar o Modo Swarm nativo e interno. |
| Mesosphere DC/OS<br/>![Logotipo do Mesosphere DC/OS](./media/image8.png) |  O Mesosphere Enterprise DC/OS, baseado no Apache Mesos, é uma plataforma pronta para produção para contêineres em execução e aplicativos distribuídos. <br /><br /> O DC/OS abstrai uma coleção de recursos disponíveis no cluster e os disponibiliza para componentes criados nele. Geralmente, o Marathon é usado como agendador integrado ao DC/OS. |
| Google Kubernetes<br />![Logotipo do Google Kubernetes](./media/image9.png) | O Kubernetes é um software livre que oferece funcionalidades que variam da infraestrutura do cluster e do agendamento de contêiner a capacidades de orquestração. Com ele, você pode automatizar a implantação, dimensionamento e operações de contêineres de aplicativos em clusters de hosts. <br /><br /> O Kubernetes oferece uma infraestrutura centrada no contêiner que agrupa contêineres de aplicativo em unidades lógicas para facilitar o gerenciamento e a descoberta. |
| Azure Service Fabric<br />![Logotipo do Azure Service Fabric](./media/image10.png) | O [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) é uma plataforma de microsserviços da Microsoft para criação de aplicativos. Ele é um [orquestrador](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) de serviços e cria clusters de computadores. Por padrão, o Service Fabric implanta e ativa esses serviços como processos, mas o Service Fabric pode implantar serviços nas imagens de contêiner do Docker. Mais importante, você pode misturar serviços em processos com serviços em contêineres no mesmo aplicativo. <br /><br /> A partir de maio de 2017, o recurso de malha de serviço que dá suporte a serviços de implantação como contêineres do Docker está em estado de visualização. <br /><br /> Você pode desenvolver serviços do Service Fabric em várias maneiras, usando o [modelos de programação do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) à implantação [executáveis de convidado](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) , bem como contêineres. O Service Fabric dá suporte a modelos de aplicativo prescritivas como [serviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Usar orquestradores baseados em contêiner no Azure

Vários fornecedores de nuvem oferecem suporte a contêineres do além de clusters do Docker e suporte de orquestração, incluindo Azure, o Amazon EC2 Container Service e o Google Container Engine. O Azure fornece suporte a cluster e o orchestrator por meio do serviço de contêiner do Azure, Docker conforme explicado na próxima seção.

Outra opção é usar o Azure Service Fabric, que também dá suporte a Docker com base em contêineres do Linux e Windows. Service Fabric é executado no Azure ou qualquer outra nuvem, bem como [locais](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Usar o Serviço de Contêiner do Azure

Um cluster do Docker cria um pool de diversos hosts e os expõe como um host virtual único. Assim, é possível implantar vários contêineres no cluster. O cluster lidará com todos os detalhes técnicos complexos de gerenciamento, como escalabilidade e a integridade. Figura 4 a 7 representa como um cluster do Docker para aplicativos compostos é mapeado para o serviço de contêiner.

O serviço de contêiner fornece uma maneira de simplificar a criação, configuração e gerenciamento de um cluster de VMs que são pré-configuradas para executar aplicativos em contêineres. Usando uma configuração otimizada de ferramentas populares de agendamento e orquestração de código-fonte aberto, o serviço de contêiner lhe dá a capacidade de usar suas habilidades existentes ou desenhar em um corpo grande e crescente Conhecimento da comunidade para implantar e gerenciar com base em contêiner aplicativos no Azure.

O serviço de contêiner otimiza a configuração de ferramentas de código-fonte aberto de clustering do Docker e tecnologias populares especialmente para o Azure. É uma solução aberta que oferece portabilidade para contêineres e configuração de aplicativo. Selecione o tamanho, a quantidade de hosts e as ferramentas de orquestrador e deixe o Serviço de Contêiner cuidar de todo o resto.

O serviço de contêiner usa imagens do Docker para garantir que seus contêineres de aplicativo sejam totalmente portáteis. Ele dá suporte à sua escolha de plataformas de orquestração de código-fonte aberto como DC/OS, Kubernetes e Docker Swarm para garantir que esses aplicativos podem ser dimensionados para milhares ou até mesmo dezenas de milhares de contêineres.

Com o serviço de contêiner do Azure, você pode aproveitar os recursos de nível empresarial do Azure e ainda manter a portabilidade do aplicativo, inclusive nas camadas de orquestração.

![](./media/image11.png)

Figura 4 a 7: Opções de clusters no Serviço de Contêiner do Azure

Conforme mostrado na Figura 4 a 8, o serviço de contêiner é simplesmente a infraestrutura fornecida pelo Azure para implantar o Docker Swarm, Kubernetes ou DC/SO, mas ele não implementa outros orquestradores. Portanto, o serviço de contêiner é não um orquestrador, como tal; ele é apenas uma infraestrutura que aproveita orquestradores de software livre existentes para contêineres.

![](./media/image12.png)

Figura 4 a 8: Orquestradores no serviço de contêiner

De uma perspectiva de uso, o objetivo do serviço de contêiner é fornecer um ambiente de hospedagem de contêiner usando tecnologias e ferramentas de código-fonte aberto populares. Para isso, ele expõe os pontos de extremidade padrão da API do orquestrador escolhido. Usando esses pontos de extremidade, você pode usar qualquer software que pode se comunicar com esses pontos de extremidade. Por exemplo, no caso do ponto de extremidade com Docker Swarm, você pode optar por usar a CLI do Docker. No DC/OS, você pode usar a CLI do DC/OS.

### <a name="getting-started-with-container-service"></a>Introdução ao serviço de contêiner

Para começar a usar o serviço de contêiner, você deve implantar um cluster do serviço de contêiner do portal do Azure usando um modelo do Azure Resource Manager ou o [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Modelos disponíveis: [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes) e [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Você pode modificar os modelos de início rápido para incluir a configuração do Azure avançada ou adicional.

**Obter mais informações** para saber mais sobre como implantar um cluster do serviço de contêiner, no site do Azure, leia [implantar um cluster do serviço de contêiner do Azure](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Nenhum valor é cobrado pelos softwares instalados por padrão como parte do ACS. Todas as opções padrão são implementadas com software livre.

O serviço de contêiner está disponível atualmente para Standard A, D, DS, G e VMs Linux da série GS no Azure. Você é cobrado somente para as instâncias de computação que você escolher, bem como os outros recursos de infraestrutura consumidos, como armazenamento e rede. Há não há cobranças incrementais para o serviço de contêiner em si.

### <a name="additional-resources"></a>Recursos adicionais

Estes são os locais onde você pode encontrar informações adicionais:

-   Introdução às soluções com o serviço de contêiner de hospedagem de contêineres de Docker:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Visão geral do docker Swarm:  
    <https://docs.docker.com/swarm/overview/>

-   Visão geral do modo swarm:  
    <https://docs.docker.com/engine/swarm/>

-   Visão geral do mesosphere DC/OS:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (o site oficial):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Usando o Service Fabric

O Service Fabric surgiu da transição da Microsoft do fornecimento de produtos de "caixa", que eram normalmente monolíticos em estilo, no fornecimento de serviços. A experiência de criar e operar serviços grandes em grande escala, como Azure Document DB, banco de dados SQL, barramento de serviço do Azure ou back-end do Cortana, modelou o Service Fabric. A plataforma evoluiu ao longo do tempo conforme mais serviços a adotaram. Mais importante, o Service Fabric precisava ser executado não apenas no Azure, mas também em implantações autônomas do Windows Server.

O objetivo do Service Fabric é resolver os problemas difíceis de criação e execução de um serviço e utilização de recursos de infraestrutura com eficiência para que as equipes possam resolver problemas de negócios usando uma abordagem de microsserviços.

O Service Fabric fornece duas amplas áreas para ajudá-lo a criar aplicativos que usam uma abordagem de microsserviços:

-   Uma plataforma que fornece serviços de sistema para implantar, dimensionar, atualizar, detectar, reiniciar serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade. Esses serviços do sistema em vigor oferecem muitas das características de microsserviços descritas anteriormente.

-   APIs de programação, ou estruturas, para ajudá-lo a criar aplicativos como microsserviços: [Reliable Actors e Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Claro, é possível escolher qualquer código para criar seu microsserviço, mas essas APIs simplificam o trabalho e integram-se à plataforma em um nível mais profundo. Dessa forma, é possível obter informações de integridade e de diagnóstico ou aproveitar o gerenciamento de estado confiável.

O Service Fabric é independente em relação à maneira como você cria seu serviço, e é possível usar qualquer tecnologia. No entanto, ele fornece APIs de programação internas que facilitam a criação de microsserviços.

Figura 4 a 9 demonstra como você pode criar e executar microsserviços no Service Fabric como processos simples ou como contêineres do Docker. Também é possível combinar microsserviços baseados em contêineres com microsserviços baseados em processos dentro do mesmo cluster do Service Fabric.

![](./media/image13.png)

Figura 4 a 9: Implantando microsserviços como processos ou como contêineres no Azure Service Fabric

Clusters do Service Fabric com base em hosts Linux e Windows podem executar contêineres do Linux do Docker e do Windows.

**Obter mais informações** para obter informações atualizadas sobre o suporte a contêineres no Service Fabric, no site do Azure, leia [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

O Service Fabric é um bom exemplo de uma plataforma com a qual você pode definir uma arquitetura lógica diferente (microsserviços de negócios ou contextos limitados) da implementação física. Por exemplo, se você implementar [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) na [do Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), que são introduzidos na próxima seção, "[sem estado versus microsserviços com estado](#stateless-versus-stateful-microservices), "você tem um conceito de microsserviço de negócios com vários serviços físicos.

Conforme mostrado na Figura 4-10 e com base em uma perspectiva de microsserviço lógico/de negócios, ao implementar um serviço do Service Fabric com monitoração de estado confiável, você geralmente precisará implementar dois níveis de serviços. A primeira é o serviço back-end com estado confiável, que manipula várias partições. O segundo é o serviço de front-end ou serviço de Gateway, responsável pelo roteamento e agregação de dados entre várias partições ou instâncias de serviço com monitoração de estado. Esse serviço de Gateway também manipula a comunicação do lado do cliente com loops de repetição que acessam o serviço de back-end usado em conjunto com o Service Fabric [proxy reverso](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Figura 4-10: Microsserviço de negócios com vários serviços com e sem estado no Service Fabric

Em qualquer caso, quando você usa os Reliable Services com estado do Service Fabric, você também tem um microsserviço lógico ou de negócios (Contexto limitado) geralmente composto por vários serviços físicos. Cada um dos-los, o serviço de Gateway e o serviço de partição pode ser implementada como serviços da API Web do ASP.NET, conforme mostrado na Figura 4 a 10.

No Service Fabric, é possível agrupar e implantar grupos de serviços como um [Aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orquestrador ou do cluster. Portanto, o aplicativo do Service Fabric pode ser mapeado também esse comerciais autônomas e limites de microsserviço lógico ou contexto limitado.

### <a name="service-fabric-and-containers"></a>Service Fabric e contêineres

Com relação a contêineres no Service Fabric, você também pode implantar serviços em imagens de contêiner em um cluster do Service Fabric. Figura 4-11 ilustra que a maior parte do tempo, haverá apenas um contêiner por serviço.

![](./media/image15.png)

Figura 4-11: Microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados "sidecar" (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis no Service Fabric. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, pode ser um único serviço com um único modelo de dados, mas em alguns outros casos, você pode ter vários serviços físicos, também.

No momento deste texto (abril de 2017), no Service Fabric não é possível implantar SF de serviços confiáveis com estado em contêineres — você pode implantar apenas os contêineres de convidado, serviços sem monitoração de estado ou serviços de ator em contêineres. Mas observe que você pode misturar serviços em processos e serviços em contêineres no mesmo aplicativo do Service Fabric, conforme mostrado na Figura 4 a 12.

![](./media/image16.png)

Figura 4-12: Microsserviço de negócios mapeado para um aplicativo do Service Fabric com contêineres e serviços com estado

O suporte também é diferente dependendo se você estiver usando contêineres do Docker em contêineres do Linux ou Windows. Suporte para contêineres no Service Fabric estará em constante expansão em versões futuras. Para obter notícias atualizadas sobre o suporte de contêiner no Service Fabric, no site do Azure, leia [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microsserviços com estado versus sem estado

Conforme mencionado anteriormente, cada microsserviço (Contexto limitado lógico) deve ter seu próprio modelo de domínio (dados e lógica). No caso de microsserviços sem monitoração de estado, os bancos de dados serão externos, empregando opções relacionais como o SQL Server, ou opções NoSQL, como MongoDB ou Azure DocumentDB.

Mas os próprios serviços também podem ser com estado, o que significa que os dados residem dentro do microsserviço. Esses dados podem existir não só no mesmo servidor, mas dentro do processo de microsserviço, na memória e persistentes em unidades e replicado para outros nós. Figura 4-13 mostra as diferentes abordagens.

![](./media/image17.png)

Figura 4-13: Microsserviços com estado versus sem estado

Uma abordagem sem estado é perfeitamente válida e é mais fácil de implementar do que microsserviços com estado porque a abordagem é semelhante aos padrões tradicionais e já conhecidos. Mas microsserviços sem estado impõem latência entre o processo e as fontes de dados. Eles também envolvem mais movimentação de partes quando você está tentando aprimorar o desempenho com cache e filas adicionais. O resultado é que você pode acabar com arquiteturas complexas que têm muitas camadas.

Em contraste, [microsserviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) podem se destacar em cenários avançados porque não há nenhuma latência entre a lógica de domínio e os dados. Processamento de dados pesado, jogos back-ends, bancos de dados como um serviço e outros cenários de baixa latência todos se beneficiam de serviços com monitoração de estado, que fornecem o estado local para acesso mais rápido.

Serviços sem estado e com estado são complementares. Por exemplo, um serviço com estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem estado que funcione como um serviço de gateway que saiba como tratar cada partição com base nas chaves de partição.

Os serviços com estado têm desvantagens. Elas impõem um nível de complexidade que lhes permite escalar horizontalmente. A funcionalidade que normalmente seria implementada por sistemas de banco de dados externos deve ser orientada para tarefas como replicação de dados entre microsserviços com estado e particionamento de dados. No entanto, essa é uma das áreas onde como um orquestrador [do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seu [reliable services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ajudar a maioria dos — simplificando o desenvolvimento e o ciclo de vida de monitoração de estado microsserviços usando o [API dos Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem serviços com estado, que dão suporte a padrão de ator e que melhoram a tolerância a falhas e a latência entre os dados e a lógica de negócios são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [Akka.NET](https://getakka.net/). No momento, ambas as estruturas estão melhorando o suporte para Docker.

Observe que os contêineres do Docker são sem estado. Se você desejar implementar um serviço com estado, será necessária uma das estruturas adicionais prescritivas e de nível mais alto descritas anteriormente. No entanto, a partir da redação deste artigo, os serviços com monitoração de estado no Service Fabric não têm suporte como contêineres, apenas como microsserviços simples. Suporte de serviços confiáveis em contêineres estará disponível em versões futuras do Service Fabric.

>[!div class="step-by-step"]
>[Anterior](soa-applications.md)
>[Próximo](docker-apps-development-environment.md)