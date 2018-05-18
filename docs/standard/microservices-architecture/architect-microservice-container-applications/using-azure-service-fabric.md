---
title: Usando o Azure Service Fabric
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Usando o Azure Service Fabric
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: d65968e3d37f53cceee55120110ad4bb3c13d304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="using-azure-service-fabric"></a>Usando o Azure Service Fabric

O Azure Service Fabric surgiu da transição realizada pela Microsoft do fornecimento de produtos de caixa, que normalmente eram monolíticos em estilo, para o fornecimento de serviços. A experiência de criar e operar grandes serviços em grande escala, como o Banco de Dados SQL do Azure, Azure Cosmos DB, Barramento de Serviço do Microsoft Azure ou o Back-end do Cortana, modelou o Service Fabric. A plataforma evoluiu ao longo do tempo conforme mais serviços a adotaram. Mais importante, o Service Fabric precisava ser executado não apenas no Azure, mas também em implantações autônomas do Windows Server.

O objetivo do Service Fabric é resolver os difíceis problemas de criação e execução de um serviço e de utilização de recursos de infraestrutura com eficiência para que as equipes possam resolver problemas de negócios usando uma abordagem de microsserviços.

O Service Fabric fornece duas amplas áreas para ajudá-lo a criar aplicativos que usam uma abordagem de microsserviços:

-   Uma plataforma que fornece serviços de sistema para implantar, dimensionar, atualizar, detectar, reiniciar serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade. Esses serviços de sistema em vigor habilitam muitas características de microsserviços descritas anteriormente.

-   APIs de programação, ou estruturas, para ajudá-lo a criar aplicativos como microsserviços: [Reliable Actors e Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Claro, é possível escolher qualquer código para criar seu microsserviço, mas essas APIs simplificam o trabalho e integram-se à plataforma em um nível mais profundo. Dessa forma, é possível obter informações de integridade e de diagnóstico ou aproveitar o gerenciamento de estado confiável.

O Service Fabric é independente em relação à maneira como você cria seu serviço, e é possível usar qualquer tecnologia. No entanto, ele fornece APIs de programação internas que facilitam a criação de microsserviços.

Conforme mostrado na Figura 4-26, é possível criar e executar microsserviços no Service Fabric como processos simples ou como contêineres do Docker. Também é possível combinar microsserviços baseados em contêineres com microsserviços baseados em processos dentro do mesmo cluster do Service Fabric.

![](./media/image30.png)

**Figura 4-26**. Implantando microsserviços como processos ou como contêineres no Azure Service Fabric

Os clusters do Service Fabric baseados em hosts Linux e do Windows podem executar contêineres Linux do Docker e contêineres do Windows, respectivamente.

Para obter informações atualizadas sobre o suporte a contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

O Service Fabric é um bom exemplo de uma plataforma em que é possível definir uma arquitetura lógica diferente (microsserviços de negócios ou Contextos limitados) à da implementação física que foram introduzidos na seção [Arquitetura lógica versus arquitetura física](#logical-architecture-versus-physical-architecture). Por exemplo, se você implementar [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) no [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), que serão introduzidos na seção [Microsserviços sem estado versus com estado](#stateless-versus-stateful-microservices) posteriormente, será possível ter um conceito de microsserviço de negócios com vários serviços físicos.

Conforme mostrado na Figura 4-27, e com base em uma perspectiva de microsserviço lógico/de negócios, ao implementar um serviço confiável com estado do Service Fabric, geralmente será necessário implementar dois níveis de serviços. O primeiro é o serviço confiável com estado de back-end, que manipula várias partições (cada partição é um serviço com estado). O segundo é o serviço de front-end, ou serviço de Gateway, responsável pelo roteamento e agregação de dados entre várias partições ou instâncias de serviço com estado. Esse serviço de Gateway também manipula a comunicação do cliente com loops de repetição que acessam o serviço de back-end.
Ele será denominado serviço de Gateway se você implementar seu serviço personalizado ou, de maneira alternativa, também é possível usar o [serviço de Proxy reverso](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) do Service Fabric pronto para uso.

![](./media/image31.png)

**Figura 4-27**. Microsserviço de negócios com várias instâncias de serviço com estado e um front-end de gateway personalizado

Em qualquer caso, quando você usa os Reliable Services com estado do Service Fabric, você também tem um microsserviço lógico ou de negócios (Contexto limitado) geralmente composto por vários serviços físicos. Cada um deles, o serviço de Gateway e o serviço de Partição, pode ser implementado como serviços da API Web ASP.NET, conforme mostrado na Figura 4-26.

No Service Fabric, é possível agrupar e implantar grupos de serviços como um [Aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orquestrador ou do cluster. Portanto, o aplicativo do Service Fabric poderia ser mapeado para esse limite autônomo de microsserviço lógico e de negócios ou Contexto limitado também para você poder implantar esses serviços de maneira autônoma.

## <a name="service-fabric-and-containers"></a>Service Fabric e contêineres

Com relação a contêineres no Service Fabric, também é possível implantar serviços em imagens de contêiner dentro de um cluster do Service Fabric. Como mostra a Figura 4-28, na maioria das vezes, haverá apenas um contêiner por serviço.

![](./media/image32.png)

**Figura 4-28**. Microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados "sidecar" (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis no Service Fabric. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, pode ser um único serviço com um único modelo de dados, mas, em alguns outros casos, talvez seja necessário ter vários serviços físicos também.

Desde meados de 2017, no Service Fabric, não é possível implantar Serviços confiáveis com estado do SF em contêineres — é possível apenas implantar serviços sem estado e serviços de ator em contêineres. Mas observe que é possível combinar serviços em processos e serviços em contêineres no mesmo aplicativo do Service Fabric, conforme mostrado na Figura 4-29.

![](./media/image33.png)

**Figura 4-29**. Microsserviço de negócios mapeado para um aplicativo do Service Fabric com contêineres e serviços com estado

Para obter informações sobre o suporte a contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Microsserviços com estado versus sem estado

Conforme mencionado anteriormente, cada microsserviço (Contexto limitado lógico) deve ter seu próprio modelo de domínio (dados e lógica). No caso de microsserviços sem estado, os bancos de dados serão externos, empregando opções relacionais, como SQL Server, ou opções NoSQL, como o MongoDB ou o Azure Cosmos DB.

Mas os próprios serviços também podem ter estado no Service Fabric, o que significa que os dados residem dentro do microsserviço. Esses dados podem existir não só no mesmo servidor, como dentro do processo de microsserviço, na memória e persistentes em discos rígidos e replicados em outros nós. A Figura 4-30 mostra as diferentes abordagens.

![](./media/image34.png)

**Figura 4-30**. Microsserviços com estado versus sem estado

Uma abordagem sem estado é perfeitamente válida e mais fácil de ser implementada do que microsserviços com estado, uma vez que ela é semelhante a padrões tradicionais e já conhecidos. Mas microsserviços sem estado impõem latência entre o processo e as fontes de dados. Eles também envolvem mais movimentação de partes quando você está tentando aprimorar o desempenho com cache e filas adicionais. O resultado é que você pode acabar com arquiteturas complexas que têm muitas camadas.

Por outro lado, [microsserviços com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) podem se destacar em cenários avançados, pois não há latência entre a lógica e os dados de domínio. O processamento de dados pesado, os back-ends de jogos, os bancos de dados como serviço e outros cenários de baixa latência se beneficiam de serviços com estado, que usam o estado local para obter um acesso mais rápido.

Serviços sem estado e com estado são complementares. Por exemplo, é possível ver na Figura 4-30, no diagrama à direita, que um serviço com estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem estado que funcione como um serviço de gateway que saiba como tratar cada partição com base nas chaves de partição.

Os serviços com estado têm desvantagens. Elas impõem um nível de complexidade que permite a expansão. A funcionalidade que normalmente seria implementada por sistemas de banco de dados externos deve ser orientada para tarefas como replicação de dados entre microsserviços com estado e particionamento de dados. No entanto, essa é uma das áreas em que um orquestrador como o [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seus [Reliable Services com estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ser de maior utilidade – simplificando o desenvolvimento e o ciclo de vida de microsserviços com estado que usam a [API de Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem serviços com estado, que dão suporte a padrão de ator e que melhoram a tolerância a falhas e a latência entre os dados e a lógica de negócios são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [Akka.NET](https://getakka.net/). No momento, ambas as estruturas estão melhorando o suporte para Docker.

Observe que os contêineres do Docker são sem estado. Se você desejar implementar um serviço com estado, será necessária uma das estruturas adicionais prescritivas e de nível mais alto descritas anteriormente. 

>[!div class="step-by-step"]
[Anterior] (scalable-available-multi-container-microservice-applications.md) [Próximo] (../docker-application-development-process/index.md)
