---
title: "Comunicação direta do cliente para microsserviço versus o padrão de Gateway de API"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Comunicação direta do cliente para microsserviço versus o padrão de Gateway de API"
keywords: "Docker, Microservices, o ASP.NET, o contêiner, o Gateway de API"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c8227ec47888c7cf361f34c4c85a09c0666f886e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="direct-client-to-microservice-communication-versus-the-api-gateway-pattern"></a>Comunicação direta do cliente para microsserviço versus o padrão de Gateway de API

Em uma arquitetura microservices, cada microsserviço expõe um conjunto de pontos de extremidade de fine‑grained (normalmente). Esse fato pode afetar a comunicação client‑to‑microservice, conforme explicado nesta seção.

## <a name="direct-client-to-microservice-communication"></a>Comunicação de cliente para microsserviço direta

Uma abordagem possível é usar uma arquitetura de comunicação de cliente para microsserviço direta. Nessa abordagem, um aplicativo cliente pode fazer solicitações diretamente para algumas das microservices, conforme mostrado na Figura 4-12.

![](./media/image12.png)

**Figura 4-12**. Usando uma arquitetura de comunicação de cliente para microsserviço direta

Nessa abordagem. cada microsserviço tem um ponto de extremidade público, às vezes, com uma porta TCP diferente para cada microsserviço. Um exemplo de uma URL para um serviço específico pode ser a URL a seguir no Azure:

<http://eshoponcontainers.westus.cloudapp.Azure.com:88 />

Em um ambiente de produção com base em um cluster, o que a URL deve mapear para o balanceador de carga usado no cluster, que por sua vez distribui as solicitações entre os microservices. Em ambientes de produção, você pode ter um controlador de entrega de aplicativo (ADC) como [Azure Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction) entre o microservices e a Internet. Isso funciona como uma camada transparente que não executa balanceamento de carga, apenas protege seus serviços, oferecendo a terminação SSL. Isso aumenta a carga de seus hosts descarregando terminação SSL com uso intensivo de CPU e outras tarefas de roteamentos para o Gateway de aplicativo do Azure. Em qualquer caso, um balanceador de carga e ADC são transparentes de um ponto de vista do aplicativo lógico arquitetura.

Uma arquitetura de comunicação de cliente para microsserviço direta pode ser bom o bastante para um aplicativo baseado em microsserviço pequeno, especialmente se o aplicativo cliente é um aplicativo do lado do servidor web como um aplicativo ASP.NET MVC. No entanto, quando você cria aplicativos grandes e complexos com base em microsserviço (por exemplo, ao lidar com dezenas de tipos de microsserviço), e especialmente quando os aplicativos de cliente remotos aplicativos móveis ou aplicativos de web do SPA, essa abordagem faces alguns problemas.

Ao desenvolver um aplicativo grande com base em microservices, considere as seguintes perguntas:

-   *Como os aplicativos de cliente podem minimizar o número de solicitações para o back-end e reduzir a comunicação verborrágica para vários microservices?*

Interagir com vários microservices para criar uma única tela de interface do usuário aumenta o número de idas e voltas pela Internet. Isso aumenta a latência e a complexidade do lado da interface do usuário. Idealmente, as respostas devem ser agregadas com eficiência no lado do servidor — isso reduz a latência, como voltar várias partes de dados em paralelo e algumas interfaces do usuário podem mostrar dados assim que ele está pronto.

-   *Como você pode controlar resolvem preocupações como autorização, transformações de dados e a distribuição dinâmica de solicitação?*

Implementando a segurança e resolvem preocupações como segurança e a autorização cada microsserviço podem exigir esforço de desenvolvimento significativo. Uma abordagem possível é ter esses serviços no host do Docker ou interna do cluster, para restringir o acesso direto a eles de fora e para implementar essas preocupações abrangentes em um local centralizado, como um Gateway de API.

-   *Como os aplicativos cliente podem se comunicar com serviços que usam protocolos não amigáveis para Internet?*

Protocolos usados no lado do servidor (como AMQP ou protocolos binários) geralmente não têm suporte em aplicativos cliente. Portanto, solicitações devem ser executadas por meio de protocolos como HTTP/HTTPS e convertidas para outros protocolos posteriormente. Um *man-in-the-middle* abordagem pode ajudar nessa situação.

-   *Como você pode formatar uma fachada feita principalmente para aplicativos móveis?*

A API de vários microservices não deve ser bem projetada para as necessidades de diferentes aplicativos clientes. Por exemplo, as necessidades de um aplicativo móvel podem ser diferentes às necessidades de um aplicativo web. Para aplicativos móveis, convém otimizar ainda mais para que as respostas de dados podem ser mais eficientes. Você pode fazer isso, agregar dados de vários microservices e retornar um único conjunto de dados e, às vezes, a eliminação de quaisquer dados na resposta que não é necessária para o aplicativo móvel. E, claro, você pode compactar dados. Novamente, uma API entre o aplicativo móvel e o microservices ou fachada pode ser conveniente para esse cenário.

## <a name="using-an-api-gateway"></a>Usando um Gateway de API

Quando você projetar e criar grandes ou complexos microsserviço aplicativos cliente de vários aplicativos, uma boa abordagem para considerar pode ser um [API Gateway](http://microservices.io/patterns/apigateway.html). Este é um serviço que fornece um único ponto de entrada para determinados grupos de microservices. É semelhante do [padrão Facade](https://en.wikipedia.org/wiki/Facade_pattern) do object‑oriented design, mas nesse caso, ele faz parte de um sistema distribuído. O padrão de Gateway de API, às vezes, também é conhecido como "back-end para front-end" [(BFF)](http://samnewman.io/patterns/architectural/bff/) porque ele é criado ao pensar sobre as necessidades do aplicativo cliente.

Figura 4-13 mostra como um Gateway de API personalizada possam caber em uma arquitetura de microsserviço.
É importante destacar que esse diagrama, você usa um único serviço de Gateway de API personalizado voltada para o múltiplo e aplicativos cliente diferentes. Que o fato pode ser um risco importante porque o serviço de Gateway de API será crescendo e em evolução com base em vários requisitos diferentes dos aplicativos cliente. Eventualmente, ele será inflado devido a essas necessidades diferentes e efetivamente pode ser muito semelhante a um aplicativo monolítico ou serviço monolítico. É por isso que é muito recomendável dividir o Gateway de API em vários serviços ou vários Gateways API menores, um por tipo de fator de forma, para a instância.

![](./media/image13.png)

**Figura 4-13**. Usando um Gateway de API implementado como um serviço de API da Web personalizado

Neste exemplo, o Gateway de API deve ser implementado como um serviço de API da Web personalizado em execução como um contêiner.

Conforme mencionado, você deve implementar vários Gateways de API para que você possa ter uma fachada diferente para as necessidades de cada aplicativo cliente. Cada Gateway de API pode fornecer uma API personalizada para cada aplicativo de cliente, possivelmente mesmo com base no fator de formulário de cliente com a implementação de código do adaptador específico que sob chama vários microservices interno.

Como um Gateway de API personalizada é geralmente um agregador de dados, você precisa ter cuidado com ele. Geralmente não é recomendável ter um único API Gateway agregar todos os microservices internos do seu aplicativo. Em caso afirmativo, ele atua como um agregador monolítico ou orchestrator e viola a autonomia de microsserviço combinando todos os microservices. Portanto, os Gateways de API deve ser separados com base nos limites de negócios e não agir como um agregador para o aplicativo inteiro.

Às vezes, um Gateway de API granulares podem ser também um microsserviço por si só e ter um domínio ou o nome da empresa e dados relacionados. Limites de API do Gateway ditados pela empresa ou domínio ajudarão a obter um melhor design.

Granularidade na camada de API de Gateway pode ser especialmente útil para mais avançados aplicativos compostos de interface do usuário com base em microservices, como o conceito de um Gateway de API refinada é semelhante a um serviço de composição de interface do usuário. Discutiremos isso mais tarde no [criando composto da interface do usuário com base em microservices](#creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices).

Portanto, para muitos aplicativos de médio e grande-tamanho, usando um Gateway de API personalizada é geralmente uma boa abordagem, mas não como um único agregador monolítico ou exclusivo central Gateway de API personalizada.

Outra abordagem é usar um produto como [gerenciamento do Azure API](https://azure.microsoft.com/services/api-management/) conforme mostrado na Figura 4-14. Essa abordagem não apenas resolve suas necessidades de Gateway de API, mas fornece recursos como a coleta de informações de suas APIs. Se você estiver usando uma solução de gerenciamento de API, um Gateway de API é apenas um componente dentro dessa solução completa de gerenciamento de API.

![](./media/image14.png)

**Figura 4-14**. Usando o gerenciamento de API do Azure para o Gateway de API

Nesse caso, quando usar um produto como o gerenciamento de API do Azure, o fato de que você pode ter um único Gateway de API não é tão arriscado porque esses tipos de Gateways de API são "mais estreito", que significa que não implementam c# código personalizado que pode evoluir até um monolítico componente. 

Esse tipo de produto mais age como um proxy reverso para comunicação de entrada, onde você também pode filtrar as APIs do microservices interno mais se aplicar a autorização para as APIs publicadas nesta camada única.

As informações disponíveis da Ajuda de sistema gerenciamento de API que você obter uma compreensão de como suas APIs estão sendo usados e como eles são executados. Eles fazem isso permitindo que você exibir próximo a relatórios de análise em tempo real e identificando tendências que podem afetar seus negócios. Além disso, você pode ter logs sobre a atividade de solicitação e resposta para análise adicional online e offline.

Gerenciamento de API do Azure, você pode proteger suas APIs usando uma chave, um token e filtragem de IP. Esses recursos permitem que você impor cotas flexíveis e refinadas e limites de taxa, modificar a forma e o comportamento de suas APIs usando políticas e melhorar o desempenho com o cache de resposta.

Este guia e o aplicativo de exemplo de referência (eShopOnContainers), podemos são limitando a arquitetura para uma arquitetura em contêineres mais simples e personalizada para se concentrar em contêineres simples sem o uso de produtos de PaaS, como gerenciamento de API do Azure. Mas, para grandes microsserviço aplicativos que são implantados para o Microsoft Azure, recomendamos que você examine e adotar o gerenciamento de API do Azure como a base para seus Gateways de API.

## <a name="drawbacks-of-the-api-gateway-pattern"></a>Desvantagens do padrão de Gateway de API

-   A desvantagem mais importante é que, quando você implementa um Gateway de API, são acoplamento essa camada com o microservices interno. Acoplamento como isso pode introduzir problemas sérios para seu aplicativo. Clemens Vaster, arquiteto na equipe do barramento de serviço do Azure, refere-se a essa dificuldade potencial como "o novo ESB" em seu "[Messaging e Microservices](https://www.youtube.com/watch?v=rXi5CLjIQ9k)" sessão GOTO 2016.

-   Usar um Gateway de API microservices cria um adicional possível ponto único de falha.

-   Um Gateway de API pode apresentar maior tempo de resposta devido a chamada de rede adicional. No entanto, essa chamada extra normalmente tem impacto menor do que um cliente de interface que é muito tagarela chamar diretamente o microservices interno.

-   Se não expandida corretamente, o Gateway de API pode se tornar um afunilamento.

-   Um Gateway de API requer custos adicionais de desenvolvimento e manutenção futura se inclui lógica personalizada e agregação de dados. Os desenvolvedores devem atualizar o Gateway de API para expor pontos de extremidade de cada microsserviço. Além disso, as alterações de implementação no microservices interno podem causar alterações de código no nível de API de Gateway. No entanto, se o Gateway de API apenas aplicar segurança, logon e controle de versão (como ao usar o gerenciamento de API do Azure), esse custo de desenvolvimento adicional pode não se aplicar.

-   Se o Gateway de API é desenvolvido por uma única equipe, pode haver um afunilamento de desenvolvimento. Essa é outra razão por que uma abordagem melhor é ter vários Gateways de API granular que atender às necessidades do cliente diferentes. Você também pode separar o Gateway de API internamente em várias áreas ou camadas que pertencem a diferentes equipes trabalhando o microservices interno.

## <a name="additional-resources"></a>Recursos adicionais

-   **Charles Richardson. Padrão: API de Gateway / back-end para front-end**
    [*http://microservices.io/patterns/apigateway.html*](http://microservices.io/patterns/apigateway.html)

-   **Gerenciamento de API do Azure**
    [*https://azure.microsoft.com/services/api-management/*](https://azure.microsoft.com/services/api-management/)

-   **Udi Dahan. Composição orientada a serviços**\
    [*http://UdiDahan.com/2014/07/30/Service-Oriented-Composition-with-Video/*](http://udidahan.com/2014/07/30/service-oriented-composition-with-video/)

-   **Clemens Vasters. Mensagens e Microservices em GOTO 2016** (vídeo) [ *https://www.youtube.com/watch?v=rXi5CLjIQ9k*](https://www.youtube.com/watch?v=rXi5CLjIQ9k)


>[!div class="step-by-step"]
[Anterior] (identificar-microsserviço-domínio-modelo-boundaries.md) [Avançar] (comunicação-em-microsserviço-architecture.md)
