---
title: Usando o Azure Service Fabric
description: Entenda quais modelos de aplicativo do Azure Service Fabric você pode usar além de apenas usá-lo para orquestrar contêineres.
ms.date: 09/20/2018
ms.openlocfilehash: 3c629b473a429b64243b5756c96fef6585c939b7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644523"
---
# <a name="using-azure-service-fabric"></a>Usando o Azure Service Fabric

O Azure Service Fabric surgiu da transição realizada pela Microsoft do fornecimento de produtos de caixa, que normalmente eram monolíticos em estilo, para o fornecimento de serviços. A experiência de criar e operar grandes serviços em grande escala, como o Banco de Dados SQL do Azure, o Azure Cosmos DB, o Barramento de Serviço do Azure ou o back-end do Cortana, modelou o Service Fabric. A plataforma evoluiu ao longo do tempo conforme mais serviços a adotaram. Mais importante, o Service Fabric precisava ser executado não apenas no Azure, mas também em implantações autônomas do Windows Server.

O objetivo do Service Fabric é resolver os difíceis problemas de criação e execução de um serviço e de utilização de recursos de infraestrutura com eficiência para que as equipes possam resolver problemas de negócios usando uma abordagem de microsserviços.

O Service Fabric fornece duas amplas áreas para ajudá-lo a criar aplicativos que usam uma abordagem de microsserviços:

- Uma plataforma que fornece serviços de sistema para implantar, dimensionar, atualizar, detectar, reiniciar serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade. Esses serviços de sistema em vigor habilitam muitas características de microsserviços descritas anteriormente.

- APIs de programação ou estruturas para ajudá-lo a criar aplicativos como microsserviços: [Reliable Actors e Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). É possível escolher qualquer código para criar seu microsserviço, mas essas APIs simplificam o trabalho e integram-se à plataforma em um nível mais profundo. Dessa forma, é possível obter informações de integridade e de diagnóstico ou aproveitar o gerenciamento de estado confiável.

O Service Fabric é independente em relação à maneira como você cria seu serviço, e é possível usar qualquer tecnologia. No entanto, ele fornece APIs de programação internas que facilitam a criação de microsserviços.

Conforme mostrado na Figura 4-27, é possível criar e executar microsserviços no Service Fabric como processos simples ou como contêineres do Docker. Também é possível combinar microsserviços baseados em contêineres com microsserviços baseados em processos dentro do mesmo cluster do Service Fabric.

![Comparação de clusters do Azure Service Fabric: Microsserviços como processos, em que cada nó executa um processo para cada microsserviço; microsserviços como contêineres, em que cada nó executa o Docker com vários contêineres, um contêiner por microsserviço.](./media/image30.png)

**Figura 4-27**. Implantando microsserviços como processos ou como contêineres no Azure Service Fabric

Os clusters do Service Fabric baseados em hosts Linux e do Windows podem executar contêineres Linux do Docker e contêineres do Windows, respectivamente.

Para obter informações atualizadas sobre o suporte a contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

O Service Fabric é um bom exemplo de uma plataforma em que é possível definir uma arquitetura lógica diferente (microsserviços de negócios ou Contextos limitados) à da implementação física que foram introduzidos na seção [Arquitetura lógica versus arquitetura física](logical-versus-physical-architecture.md). Por exemplo, se você implementar [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction), introduzidos na seção [Microsserviços sem estado versus com estado](#stateless-versus-stateful-microservices) posteriormente, será possível ter um conceito de microsserviço empresarial com vários serviços físicos.

Conforme mostrado na Figura 4-28 e com base em uma perspectiva de microsserviço lógico/de negócios, ao implementar um serviço confiável com estado do Service Fabric, geralmente será necessário implementar dois níveis de serviços. O primeiro é o serviço confiável com estado de back-end, que manipula várias partições (cada partição é um serviço com estado). O segundo é o serviço de front-end, ou serviço de Gateway, responsável pelo roteamento e agregação de dados entre várias partições ou instâncias de serviço com estado. Esse serviço de Gateway também manipula a comunicação do cliente com loops de repetição que acessam o serviço de back-end. Ele será denominado serviço de Gateway se você implementar seu serviço personalizado ou, de maneira alternativa, também é possível usar o [proxy reverso](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) do Service Fabric pronto para uso.

![](./media/image31.png)

**Figura 4-28**. Microsserviço de negócios com várias instâncias de serviço com estado e um front-end de gateway personalizado

Em qualquer caso, quando você usa os Reliable Services com estado do Service Fabric, você também tem um microsserviço lógico ou empresarial (Contexto delimitado) geralmente composto por vários serviços físicos. Cada um deles, o serviço de Gateway e o serviço de Partição, pode ser implementado como serviços do ASP.NET Web API, conforme mostrado na Figura 4-28.

No Service Fabric, é possível agrupar e implantar grupos de serviços como um [Aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orquestrador ou do cluster. Portanto, o aplicativo do Service Fabric poderia ser mapeado para esse limite autônomo de microsserviço lógico e de negócios ou Contexto limitado também para você poder implantar esses serviços de maneira autônoma.

## <a name="service-fabric-and-containers"></a>Service Fabric e contêineres

Com relação a contêineres no Service Fabric, também é possível implantar serviços em imagens de contêiner dentro de um cluster do Service Fabric. Como mostra a Figura 4-29, na maioria das vezes, haverá apenas um contêiner por serviço.

![Um aplicativo do Service Fabric pode executar vários contêineres que acessam um banco de dados externo e todo o conjunto seria o limite lógico do Microsserviço empresarial](./media/image32.png)

**Figura 4-29**. Microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados “sidecar” (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis no Service Fabric. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, poderia ser um único serviço com um único modelo de dados, mas, em alguns outros casos, talvez seja necessário ter vários serviços físicos também.

Observe que é possível combinar serviços em processos e serviços em contêineres no mesmo aplicativo do Service Fabric, conforme mostrado na Figura 4-30.

![Um aplicativo do Service Fabric executando os serviços e contêineres no mesmo nó.](./media/image33.png)

**Figura 4-30**. Microsserviço de negócios mapeado para um aplicativo do Service Fabric com contêineres e serviços com estado

Para obter informações sobre o suporte a contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microsserviços com estado versus sem estado

Conforme mencionado anteriormente, cada microsserviço (Contexto limitado lógico) deve ter seu próprio modelo de domínio (dados e lógica). No caso de microsserviços sem estado, os bancos de dados serão externos, empregando opções relacionais, como SQL Server, ou opções NoSQL, como o Azure Cosmos DB ou o MongoDB.

Mas os próprios serviços também podem ter estado no Service Fabric, o que significa que os dados residem dentro do microsserviço. Esses dados podem existir não só no mesmo servidor, como dentro do processo de microsserviço, na memória e persistentes em discos rígidos e replicados em outros nós. A Figura 4-30 mostra as diferentes abordagens.

![Em serviços sem estado, o estado (persistência, banco de dados) é mantido fora do microsserviço. Em serviços com estado, os estados são mantidos dentro do microsserviço.](./media/image34.png)

**Figura 4-31**. Microsserviços com estado versus sem estado

Uma abordagem sem estado é perfeitamente válida e mais fácil de ser implementada do que microsserviços com estado, uma vez que ela é semelhante a padrões tradicionais e já conhecidos. Mas microsserviços sem estado impõem latência entre o processo e as fontes de dados. Eles também envolvem mais movimentação de partes quando você está tentando aprimorar o desempenho com cache e filas adicionais. O resultado é que você pode acabar com arquiteturas complexas que têm muitas camadas.

Por outro lado, [microsserviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) podem se destacar em cenários avançados, pois não há latência entre a lógica e os dados de domínio. O processamento de dados pesado, os back-ends de jogos, os bancos de dados como serviço e outros cenários de baixa latência se beneficiam de serviços com estado, que usam o estado local para obter um acesso mais rápido.

Serviços sem estado e com estado são complementares. Por exemplo, é possível ver na Figura 4-31, no diagrama à direita, que um serviço com estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem estado que funcione como um serviço de gateway que saiba como tratar cada partição com base nas chaves de partição.

Os serviços com estado têm desvantagens. Elas impõem um nível de complexidade que permite a expansão. A funcionalidade que normalmente seria implementada por sistemas de banco de dados externos deve ser orientada para tarefas como replicação de dados entre microsserviços com estado e particionamento de dados. No entanto, essa é uma das áreas em que um orquestrador como o [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seus [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ser de maior utilidade – simplificando o desenvolvimento e o ciclo de vida de microsserviços com estado que usam a [API de Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem serviços com estado, que dão suporte a padrão de ator e que melhoram a tolerância a falhas e a latência entre os dados e a lógica de negócios são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [Akka.NET](https://getakka.net/). No momento, ambas as estruturas estão melhorando o suporte para Docker.

Observe que os contêineres do Docker são sem estado. Se você desejar implementar um serviço com estado, será necessária uma das estruturas adicionais prescritivas e de nível mais alto descritas anteriormente.

## <a name="using-azure-service-fabric-mesh"></a>Usando a Malha do Azure Service Fabric 

A Malha do Azure Service Fabric é um serviço totalmente gerenciado que permite que os desenvolvedores criem e implantem aplicativos de missão crítica sem gerenciar nenhuma infraestrutura. Use a Malha do Service Fabric para compilar e executar aplicativos de microsserviços distribuídos e seguros dimensionados sob demanda. 

Conforme mostrado na Figura 4-32, os aplicativos hospedados na Malha do Service Fabric são executados e dimensionados sem que você se preocupe com a infraestrutura que o ativa.

![Um aplicativo de vários contêineres em execução na área de trabalho do Docker pode ser implantado na Malha do Azure Service Fabric sem se preocupar com a infraestrutura.](media/image39.png)

**Figura 4-32**. Implantação de um aplicativo de microsserviço/contêineres à Malha do Service Fabric

Nos bastidores, a Malha do Service Fabric é composta por clusters de milhares de computadores. Todas as operações de cluster estão ocultas do desenvolvedor. Você simplesmente precisa fazer upload dos contêineres e recursos específicos necessários, dos requisitos de disponibilidade e dos limites de recursos. A Malha do Service Fabric aloca automaticamente a infraestrutura solicitada pela implantação do aplicativo e também manipula falhas de infraestrutura, certificando de que seus aplicativos estão altamente disponíveis. Só é necessário se preocupar com a integridade e com a capacidade de resposta do seu aplicativo, não com a infraestrutura.

Para obter mais informações, confira a [documentação da Malha do Service Fabric](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Escolha de orquestradores no Azure

A tabela a seguir fornece orientação sobre qual orquestrador deve ser usado dependendo das cargas de trabalho e do foco no sistema operacional.

![O Serviço de Kubernetes do Azure está mais maduro no Linux do que no Windows e é usado principalmente para implantar microsserviços com base em contêineres. O Azure Service Fabric (cluster e malha) está mais maduro no Windows do que no Linux, comumente usado para microsserviços baseados em contêineres, microsserviços baseados em processos simples e serviços com estado.](media/image40.png)

**Figura 4-33**. Seleção do orquestrador em diretrizes do Azure

>[!div class="step-by-step"]
>[Anterior](scalable-available-multi-container-microservice-applications.md)
>[Próximo](../docker-application-development-process/index.md)
