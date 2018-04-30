---
title: Comunicação direta do cliente para microsserviços versus o padrão de Gateway de API
description: Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Comunicação direta de cliente com microsserviço versus o padrão de Gateway de API
keywords: Docker, Microsserviços, ASP.NET, Contêiner, Gateway de API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fa3f4bb97cf942ee7698b1efa1dcd09b3f2ca571
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>Comunicação direta do cliente para microsserviços versus o padrão de Gateway de API

Em uma arquitetura de microsserviços, cada microsserviço expõe um conjunto de pontos de extremidade (tipicamente) refinados. Esse fato pode afetar a comunicação de cliente com microsserviço conforme explicado nesta seção.

## <a name="direct-client-to-microservice-communication"></a>Comunicação direta de cliente com microsserviço

Uma abordagem possível é usar uma arquitetura de comunicação direta de cliente com microsserviço. Nessa abordagem, um aplicativo cliente pode fazer solicitações diretamente para alguns dos microsserviços, conforme mostra a Figura 4-12.

![](./media/image12.png)

**Figura 4-12**. Usando uma arquitetura de comunicação direta de cliente com microsserviço

Nesta abordagem, cada microsserviço tem um ponto de extremidade público, às vezes, com uma porta TCP diferente para cada microsserviço. Um exemplo de uma URL para um serviço específico pode ser a URL a seguir no Azure:

<http://eshoponcontainers.westus.cloudapp.azure.com:88/>

Em um ambiente de produção com base em um cluster, essa URL mapearia para o balanceador de carga usado no cluster, que, por sua vez, distribui as solicitações entre os microsserviços. Em ambientes de produção, você pode ter um ADC (Controlador de Entrega de Aplicativo) como o [Gateway de Aplicativo do Azure](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) entre os microsserviços e a Internet. Isso funciona como uma camada transparente que não executa balanceamento de carga, mas protege seus serviços ao oferecer terminação SSL. Isso aumenta a carga de seus hosts descarregando terminação SSL com uso intensivo de CPU e outras tarefas de roteamento para o Gateway de Aplicativo do Azure. Em qualquer caso, um balanceador de carga e ADC são transparentes de um ponto de vista da arquitetura do aplicativo lógico.

Uma arquitetura de comunicação direta de cliente com microsserviço pode ser boa o bastante para um aplicativo baseado em microsserviço pequeno, especialmente se o aplicativo cliente for um aplicativo Web do lado do servidor como um aplicativo ASP.NET MVC. No entanto, quando você cria aplicativos grandes e complexos baseados em microsserviço (por exemplo, ao lidar com dezenas de tipos de microsserviço), e especialmente quando os aplicativos cliente são aplicativos móveis remotos ou aplicativos Web do SPA, essa abordagem enfrenta alguns problemas.

Considere as seguintes questões ao desenvolver um aplicativo grande com base em microsserviços:

-   *Como os aplicativos cliente podem minimizar o número de solicitações para o back-end e reduzir a comunicação verborrágica com vários microsserviços?*

Interagir com vários microsserviços para criar uma única tela de interface do usuário aumenta o número de viagens de ida e volta pela Internet. Isso aumenta a latência e a complexidade do lado da interface do usuário. Idealmente, as respostas devem ser agregadas com eficiência no lado do servidor; isso reduz a latência, já que várias partes de dados voltam em paralelo e algumas interfaces do usuário podem mostrar dados assim que eles estão prontos.

-   *Como você pode lidar com preocupações abrangentes, como autorização, transformações de dados e despacho de solicitação dinâmica?*

Implementar preocupações relativas a segurança e abrangentes, como segurança e autorização em cada microsserviço, pode exigir um esforço significativo de desenvolvimento. Uma abordagem possível é ter esses serviços no host do Docker ou no cluster interno para restringir o acesso direto a eles do lado de fora e para implementar essas preocupações abrangentes em um local centralizado, como um Gateway de API.

-   *Como os aplicativos cliente podem se comunicar com serviços que usam protocolos não amigáveis à Internet?*

Protocolos usados no lado do servidor (como AMQP ou protocolos binários) geralmente não são compatíveis com aplicativos cliente. Portanto, as solicitações devem ser executadas por meio de protocolos como HTTP/HTTPS e convertidas em outros protocolos posteriormente. Uma abordagem *man-in-the-middle* pode ajudar nessa situação.

-   *Como você pode formatar uma fachada feita especialmente para aplicativos móveis?*

A API de vários microsserviços podem não ser bem projetadas para as necessidades de diferentes aplicativos cliente. Por exemplo, as necessidades de um aplicativo móvel podem ser diferentes das necessidades de um aplicativo Web. Para aplicativos móveis, convém otimizar ainda mais para que as respostas de dados possam ser mais eficientes. Você pode fazer isso agregando dados de vários microsserviços e retornando um único conjunto de dados, e às vezes eliminando quaisquer dados na resposta que não sejam necessários para o aplicativo móvel. E, claro, você pode compactar dados. Novamente, uma API ou fachada entre o aplicativo móvel e os microsserviços pode ser conveniente para esse cenário.

## <a name="using-an-api-gateway"></a>Usando um Gateway de API

Quando você projeta e cria aplicativos grandes ou complexos baseado em microsserviço com vários aplicativos cliente, uma boa abordagem a considerar pode ser um [Gateway de API](https://microservices.io/patterns/apigateway.html). Esse é um serviço que fornece um único ponto de entrada para determinados grupos de microsserviços. É semelhante ao [padrão Fachada](https://en.wikipedia.org/wiki/Facade_pattern) do design orientada a objeto, mas, neste caso, faz parte de um sistema distribuído. O padrão de Gateway de API às vezes também é conhecido como [BFF](https://samnewman.io/patterns/architectural/bff/) ("back-end para front-end"), porque ele é criado pensando nas necessidades do aplicativo cliente.

A Figura 4-13 mostra como um Gateway de API personalizado pode se enquadrar em uma arquitetura baseada em microsserviço.
É importante destacar que, neste diagrama, você usa um único serviço de Gateway de API personalizado voltada para vários aplicativos cliente diferentes. Esse fato pode ser um risco importante, pois seu serviço de Gateway de API estará crescendo e em evolução com base em vários requisitos diferentes dos aplicativos cliente. Eventualmente, ele será inflado devido a essas necessidades diferentes e efetivamente pode ser muito semelhante a um aplicativo monolítico ou serviço monolítico. É por isso que é muito recomendável dividir o Gateway de API em vários serviços ou vários Gateways API menores, um por tipo de fator forma, por exemplo.

![](./media/image13.png)

**Figura 4-13**. Usando um Gateway de API implementado como um serviço de API Web personalizado

Neste exemplo, o Gateway de API deve ser implementado como um serviço de API Web personalizado em execução como um contêiner.

Conforme mencionado, você deve implementar vários Gateways de API para que possa ter uma fachada diferente para as necessidades de cada aplicativo cliente. Cada Gateway de API pode fornecer uma API diferente personalizada para cada aplicativo cliente, possivelmente até mesmo com base no fator forma de cliente implementando código adaptador específico que chama, em segundo plano, vários microsserviços internos.

Uma vez que um Gateway de API personalizado é geralmente um agregador de dados, você precisa ter cuidado com ele. Geralmente, não é recomendável ter um único Gateway de API para agregar todos os microsserviços internos do seu aplicativo. Em caso afirmativo, ele atua como um agregador ou orquestrador monolítico e viola a autonomia de microsserviço acoplando todos os microsserviços. Portanto, os Gateways de API devem estar segregados com base nos limites de negócios e não agir como um agregador para todo o aplicativo.

Às vezes, um Gateway de API granular também pode ser um microsserviço em si e ter, inclusive, um domínio ou nome da empresa e dados relacionados. Ter os limites de API do Gateway determinados pela empresa ou domínio ajudará a obter um melhor design.

A granularidade na camada de API de Gateway pode ser especialmente útil para mais avançados aplicativos compostos de interface do usuário com base em microsserviços, pois o conceito de um Gateway de API refinado é semelhante a um serviço de composição de interface do usuário. Discutiremos isso mais tarde em [Criando uma interface do usuário composta com base em microsserviços](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

Portanto, para muitos aplicativos de médio e grande porte, usar um Gateway de API personalizado costuma ser uma boa abordagem, mas não como um único agregador monolítico ou Gateway de API personalizado central exclusivo.

Outra abordagem é usar um produto como [Gerenciamento de API do Azure](https://azure.microsoft.com/services/api-management/) conforme mostra a Figura 4-14. Essa abordagem não apenas resolve suas necessidades de Gateway de API, mas fornece recursos como coleta de percepções das suas APIs. Se você estiver usando uma solução de gerenciamento de API, um Gateway de API será apenas um componente nessa solução completa de gerenciamento de API.

![](./media/image14.png)

**Figura 4-14**. Usando o Gerenciamento de API do Azure para o Gateway de API

Neste caso, ao usar um produto como o Gerenciamento de API do Azure, o fato de que você pode ter um único Gateway de API não é tão arriscado, pois esses tipos de Gateways de API são "mais finos", o que significa que não implementam código C# personalizado que pode evoluir para um componente monolítico. 

Esse tipo de produto atua mais como um proxy reverso para comunicação de entrada, em que você também pode filtrar as APIs dos microsserviços internos e aplicar a autorização para as APIs publicadas nesta camada única.

As informações disponíveis do sistema Gerenciamento de API ajudam a entender como as suas APIs estão sendo usadas e como elas são executadas. Isso ocorre porque você pode exibir relatórios de análise quase em tempo real e identificar tendências que podem afetar seus negócios. Além disso, você pode ter logs sobre a atividade de solicitação e resposta para mais análises online e offline.

Com o Gerenciamento de API do Azure, você pode proteger suas APIs usando uma chave, um token e filtragem de IP. Esses recursos permitem que você imponha cotas flexíveis e refinadas e limites de taxa, modifique a forma e o comportamento de suas APIs usando políticas e melhore o desempenho com o cache de resposta.

Neste guia e no aplicativo de exemplo de referência (eShopOnContainers), estamos limitando a arquitetura a uma arquitetura em contêiner mais simples e personalizada para focar em contêineres simples sem o uso de produtos PaaS como Gerenciamento de API do Azure. Mas, para grandes aplicativos baseados em microsserviço implantados no Microsoft Azure, recomendamos que você examine e adote o Gerenciamento de API do Azure como base para seus Gateways de API.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Desvantagens do padrão de Gateway de API

-   A desvantagem mais importante é que, quando você implementa um Gateway de API, está acoplando essa camada aos microsserviços internos. Um acoplamento como este pode introduzir problemas sérios no seu aplicativo. Clemens Vasters, arquiteto na equipe de Barramento de Serviço do Azure, refere-se a essa possível dificuldade como "o novo ESB" em sua sessão "[Mensagens e microsserviços](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" em GOTO 2016.

-   Usar um Gateway de API de microsserviços cria um possível ponto único de falha adicional.

-   Um Gateway de API pode apresentar um maior tempo de resposta devido à chamada de rede adicional. No entanto, essa chamada extra normalmente tem um menor impacto do que ter uma interface do cliente verborrágica demais chamando diretamente os microsserviços internos.

-   Se não for dimensionado corretamente, o Gateway de API poderá se tornar um gargalo.

-   Um Gateway de API requer custos adicionais de desenvolvimento e manutenção futura se incluir lógica personalizada e agregação de dados. Os desenvolvedores devem atualizar o Gateway de API para expor cada ponto de extremidade do microsserviço. Além disso, as alterações de implementação nos microsserviços internos podem causar alterações de código no nível do Gateway da API. No entanto, se o Gateway de API estiver apenas aplicando segurança, logon e controle de versão (como ao usar o Gerenciamento de API do Azure), esse custo de desenvolvimento adicional poderá não se aplicar.

-   Se o Gateway de API for desenvolvido por uma única equipe, poderá haver um gargalo de desenvolvimento. Esse é outro motivo pelo qual uma abordagem melhor é ter vários Gateways de API refinados que respondam às diferentes necessidades do cliente. Você também pode separar o Gateway de API internamente em várias áreas ou camadas de propriedade de diferentes equipes trabalhando em microsserviços internos.

## <a name="additional-resources"></a>Recursos adicionais

-   **Charles Richardson. Padrão: Gateway de API / Back- end para front-end**
    [*https://microservices.io/patterns/apigateway.html*](https://microservices.io/patterns/apigateway.html)

-   **Gerenciamento de API do Azure**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **Udi Dahan. Composição orientada a serviços**\
    [*http://udidahan.com/2014/07/30/service-oriented-composition-with-video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters. Mensagens e microsserviços no GOTO 2016** (vídeo) [*https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Anterior] (identify-microservice-domain-model-boundaries.md) [Próximo] (communication-in-microservice-architecture.md)
