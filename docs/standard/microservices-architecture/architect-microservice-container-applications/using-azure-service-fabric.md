---
title: Usando o Azure Service Fabric
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Usando o Azure Service Fabric"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: aa15f9cf9bc60e9e70607da921f2ce2c75e39ec2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="using-azure-service-fabric"></a>Usando o Azure Service Fabric

Azure Service Fabric surgiu de transição da Microsoft do fornecimento de produtos de caixa, que foram normalmente monolíticos em estilo, para o fornecimento de serviços. A experiência de criar e operar a grandes serviços em grande escala, como banco de dados do SQL Azure, o banco de dados do Azure Cosmos, barramento de serviço do Azure ou back-end do Cortana, em forma de malha do serviço. A plataforma desenvolvidos ao longo do tempo conforme mais e mais serviços adotaram. É importante, Service Fabric precisava executar não apenas no Azure, mas também em implantações do Windows Server autônomo.

É o objetivo de serviço de malha resolver os problemas de disco rígidos de criação e execução de um serviço e utilizando os recursos de infraestrutura com eficiência, para que as equipes podem resolver problemas de negócios usando uma abordagem de microservices.

Serviço de malha fornece duas áreas amplas para ajudá-lo a criar aplicativos que usam uma abordagem microservices:

-   Uma plataforma que fornece serviços para implantar, dimensionar, atualizar, detectar, reinicie os serviços com falha, descobrir o local do serviço, gerenciar o estado e monitorar a integridade do sistema. Esses serviços de sistema em vigor permitem que muitas das características de microservices descrito anteriormente.

-   APIs de programação ou estruturas, para ajudá-lo a criar aplicativos como microservices: [serviços confiáveis e atores confiáveis](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Obviamente, você pode escolher qualquer código para criar seu microsserviço, mas essas APIs que o trabalho mais simples e integram-se com a plataforma em um nível mais profundo. Dessa forma, você pode obter a integridade e informações de diagnóstico ou você pode tirar proveito do gerenciamento de estado confiável.

Service Fabric é agnóstico em relação a como você pode criar seu serviço, e você pode usar qualquer tecnologia. No entanto, ele fornece APIs de programação internos que facilitam a compilação microservices.

Conforme mostrado na Figura 4-26, você pode criar e executar microservices na malha do serviço como processos simples ou como contêineres do Docker. Também é possível misturar com base em contêiner microservices com microservices em processo dentro do mesmo cluster do Service Fabric.

![](./media/image30.png)

**Figura 4-26**. Implantando microservices como processos ou contêineres no Azure Service Fabric

Clusters de malha do serviço com base em hosts Linux e Windows podem executar contêineres do Docker Linux e Windows, respectivamente.

Para obter informações atualizadas sobre o suporte de contêineres no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

O Service Fabric é um bom exemplo de uma plataforma em que você pode definir uma arquitetura lógica diferente (microservices de negócios ou contextos limitada) que a implementação física que foram introduzidos no [arquitetura lógica e física arquitetura](#logical-architecture-versus-physical-architecture) seção. Por exemplo, se você implementar [serviços confiáveis com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) na [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), que é introduzido na seção [sem monitoração de estado versus microservices com monitoração de estado](#stateless-versus-stateful-microservices) posteriormente, você pode ter um conceito de microsserviço de negócios com vários serviços físicos.

Conforme mostrado na Figura 4-27 e pensar em uma perspectiva de microsserviço de lógica de negócios, ao implementar um serviço confiável do serviço de malha com monitoração de estado, você geralmente precisará implementar duas camadas de serviços. A primeira é o serviço back-end com monitoração de estado confiável, que trata de várias partições (cada partição é um serviço com monitoração de estado). O segundo é o serviço front-end ou o serviço de Gateway, responsável por agregação de roteamento e os dados em várias partições ou instâncias de serviço com monitoração de estado. Esse serviço de Gateway também gerencia a comunicação de cliente com loops de repetição acessando o serviço de back-end.
Ele é chamado de serviço de Gateway se você implementar seu serviço personalizado ou alternatevely, você também pode usar a malha de serviço fora da caixa [o serviço de Proxy Inverter](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Figura 4-27**. Microsserviço de negócios com várias instâncias de serviço com monitoração de estado e um gateway personalizado front-end

Em qualquer caso, quando você usa serviços confiáveis do serviço de malha com monitoração de estado, você também tem um lógico ou de negócio microsserviço (contexto limitado) que normalmente é composto de vários serviços físicos. Cada-los, o serviço de Gateway e serviço de partição pode ser implementada como serviços de API da Web ASP.NET, conforme mostrado na Figura 4-26.

Na malha do serviço, você pode agrupar e implantar grupos de serviços como um [aplicativo do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), que é a unidade de empacotamento e implantação do orchestrator ou cluster. Portanto, o aplicativo de malha do serviço pôde ser mapeado para esse empresariais e limites de microsserviço lógico ou contexto limitado, assim, para que você pode implantar esses serviços de forma autônoma.

## <a name="service-fabric-and-containers"></a>Serviço de malha e contêineres

Em relação a contêineres na malha do serviço, você também pode implantar os serviços em imagens de contêiner em um cluster do Service Fabric. Como mostra a Figura 4-28, na maioria das vezes haverá apenas um contêiner por serviço.

![](./media/image32.png)

**Figura 4-28**. Microsserviço de negócios com vários serviços (contêineres) no Service Fabric

No entanto, os contêineres chamados "secundário" (dois contêineres que devem ser implantados juntos como parte de um serviço lógico) também são possíveis na malha do serviço. O mais importante é que um microsserviço de negócios é o limite lógico em torno de vários elementos coesos. Em muitos casos, pode ser um único serviço com um único modelo de dados, mas em alguns outros casos, talvez seja necessário físicos vários serviços também.

Desde meados de 2017, na malha do serviço não é possível implantar serviços de monitoração de estado confiável SF em contêineres — você pode implantar somente serviços sem monitoração de estado e serviços de ator em contêineres. Mas observe que você pode combinar serviços em processos e serviços em contêineres no mesmo aplicativo de malha do serviço, conforme mostrado na Figura 4-29.

![](./media/image33.png)

**Figura 4-29**. Mapeado para um aplicativo de malha do serviço com contêineres e serviços com monitoração de estado de microsserviço de negócios

Para obter mais informações sobre o suporte de contêiner no Azure Service Fabric, consulte [Service Fabric e contêineres](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Sem monitoração de estado versus microservices com monitoração de estado

Como mencionado anteriormente, cada microsserviço (contexto lógico limitada) deve ter seu modelo de domínio (dados e lógica). No caso de microservices sem monitoração de estado, os bancos de dados será externos, empregando relacionais opções como o SQL Server ou NoSQL opções como MongoDB ou banco de dados do Azure Cosmos.

Mas os próprios serviços também podem ser com monitoração de estado na malha do serviço, o que significa que os dados que residem dentro de microsserviço. Esses dados podem existir não apenas no mesmo servidor, mas dentro do processo de microsserviço, na memória e mantidos em discos rígidos e replicadas para outros nós. Figura 4-30 mostra as abordagens diferentes.

![](./media/image34.png)

**Figura 4-30**. Sem monitoração de estado versus microservices com monitoração de estado

Uma abordagem sem monitoração de estado é perfeitamente válida e é mais fácil de implementar do que microservices com monitoração de estado, pois a abordagem é semelhante aos padrões tradicionais e bem conhecidos. Mas sem monitoração de estado microservices impor a latência entre as processo e fontes de dados. Eles também envolvem mais movendo partes quando você está tentando melhorar o desempenho com filas e cache adicional. O resultado é que você pode acabar com arquiteturas complexas que têm muitos níveis.

Por outro lado, [microservices com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) o excel em cenários avançados, porque não há nenhuma latência entre a lógica do domínio e os dados. Processamento de dados pesado, jogos volta termina, bancos de dados como um serviço, e todos os outros cenários de baixa latência beneficiam services com monitoração de estado, que permitem que o estado local para acesso mais rápido.

Serviços com e sem monitoração de estado são complementares. Por exemplo, você pode ver na Figura 4-30, no diagrama à direita, que um serviço com monitoração de estado pode ser dividido em várias partições. Para acessar essas partições, talvez seja necessário um serviço sem monitoração de estado atuando como um serviço de gateway que sabe como tratar cada partição com base nas chaves de partição.

Serviços com monitoração de estado tem desvantagens. Elas impõem um nível de complexidade que permite a expansão. A funcionalidade que normalmente poderia ser implementada por sistemas de banco de dados externo deve ser abordada para tarefas como a replicação de dados em microservices com monitoração de estado e particionamento de dados. No entanto, essa é uma das áreas onde um orquestrador que [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) com seus [serviços confiáveis com monitoração de estado](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) pode ajudar a maior parte —, simplificando o desenvolvimento e o ciclo de vida de monitoração de estado microservices usando o [API de serviços confiável](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) e [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Outras estruturas de microsserviço que permitem que os serviços com monitoração de estado, que oferece suporte a padrões de ator e que melhoram a tolerância a falhas e a latência entre a lógica de negócios e os dados são Microsoft [Orleans](https://github.com/dotnet/orleans), da Microsoft Research e [ Akka.NET](http://getakka.net/). Ambas as estruturas atualmente estão aumentando o suporte para Docker.

Observe que contêineres do Docker são sem monitoração de estado. Se você quiser implementar um serviço com monitoração de estado, você precisa de um das estruturas de nível mais alto e prescritivas adicionais observadas anteriormente. 

>[!div class="step-by-step"]
[Anterior] (scalable-available-multi-container-microservice-applications.md) [Avançar] (... /docker-Application-Development-Process/index.MD)
