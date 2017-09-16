---
title: "Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS"
description: "Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: d81091bf09d690f5d57ad9a30b5f16de1358ede6
ms.contentlocale: pt-br
ms.lasthandoff: 09/05/2017

---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS

*Crie um modelo de domínio para cada microsserviço ou contexto limitado que reflita o entendimento do domínio da empresa.*

Esta seção concentra-se em microsserviços mais avançados que você implementa quando precisa lidar com subsistemas complexos ou com microsserviços derivados do conhecimento de especialistas no domínio com mudanças constantes nas regras de negócio. Os padrões de arquitetura usados nesta seção são baseados nas abordagens DDD (design controlado por domínio) e CQRS (Segregação de Responsabilidade de Comando e Consulta), conforme é ilustrado na Figura 9-1.

![](./media/image1.png)

**Figura 9-1**. Arquitetura externa de microsserviço versus padrões de arquitetura interna para cada microsserviço

No entanto, a maioria das técnicas de microsserviços controlados por dados, incluindo como implementar um serviço de API Web do ASP.NET Core ou como expor metadados do Swagger com o Swashbuckle, também se aplica aos microsserviços mais avançados implementados internamente com padrões DDD. Esta seção é uma extensão das seções anteriores, pois a maioria das práticas de explicadas anteriormente também se aplicam aqui ou para qualquer tipo de microsserviço.

Esta seção primeiro fornece detalhes sobre os padrões CQRS simplificados usados no aplicativo de referência eShopOnContainers. Posteriormente, você obterá uma visão geral das técnicas de DDD que permitem encontrar padrões comuns que podem ser reutilizados em seus aplicativos.

O DDD é um tópico grande com um conjunto avançado de recursos de aprendizagem. Você pode iniciar com guias como [Domain-Driven Design](https://domainlanguage.com/ddd/) (Design controlado por domínio) do Eric Evans e os materiais adicionais dos autores Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard e muitos outros especialistas em DDD/CQRS. Mas, sobretudo, você precisa tentar aprender como aplicar as técnicas de DDD das sessões de conversa, de quadro de comunicações e de modelagem com os especialistas em seu domínio de negócio concreto.

#### <a name="additional-resources"></a>Recursos adicionais

##### <a name="ddd-domain-driven-design"></a>DDD (design controlado por domínio)

-   **Eric Evans. Domain Language** (Linguagem do domínio) 
    [*http://domainlanguage.com/*](http://domainlanguage.com/)

-   **Martin Fowler. Domain-Driven Design** (Design controlado por domínio) 
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)

-   **Jimmy Bogard. Strengthening your domain: a primer** (Fortalecendo seu domínio: um livro de instruções) 
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)

##### <a name="ddd-books"></a>Guias sobre DDD

-   **Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** (Design controlado por domínio: lidando com a complexidade no núcleo do software) 
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** (Referência de design controlado por domínio: resumos de definições e padrão) 
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)

-   **Vaughn Vernon. Implementing Domain-Driven Design** (Implementando o design controlado por domínio) 
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Vaughn Vernon. Domain-Driven Design Distilled** (Design controlado por domínio em detalhes) 
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)

-   **Jimmy Nilsson. Applying Domain-Driven Design and Patterns** (Aplicando padrões de design controlado por domínio) 
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)

-   **Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** (Guia de arquitetura controlada por domínio em N camadas com o .NET) 
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)

-   **Abel Avram e Floyd Marinescu. Domain-Driven Design Quickly** (Design controlado por domínio rapidamente)
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)

Treinamento em DDD

-   **Julie Lerman e Steve Smith. Domain-Driven Design Fundamentals** (Conceitos básicos de design controlado por domínio) 
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)


>[!div class="step-by-step"]
[Previous] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)

