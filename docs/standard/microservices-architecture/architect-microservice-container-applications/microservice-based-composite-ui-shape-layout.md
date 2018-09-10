---
title: Criando interface do usuário de composição baseada em microsserviços, incluindo forma e layout visuais da interface do usuário gerados por vários microsserviços
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Criando interface do usuário de composição baseada em microsserviços, incluindo forma e layout visuais de interface do usuário gerados por vários microsserviços
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 79b63c376d25725b2bcb6c16cdb4d06e107d5c07
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44275529"
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Criando interface do usuário de composição baseada em microsserviços, incluindo forma e layout visuais da interface do usuário gerados por vários microsserviços

A arquitetura de microsserviços geralmente começa com a manipulação de dados e de lógica do lado do servidor. No entanto, uma abordagem mais avançada é criar sua interface do usuário de aplicativo com base em microsserviços também. Isso significa ter uma interface do usuário de composição produzida pelos microsserviços, em vez de ter microsserviços no servidor e apenas um aplicativo cliente monolítico consumindo os microsserviços. Com essa abordagem, os microsserviços que você criar poderão estar completos com lógica e representação visual.

A Figura 4-20 mostra a abordagem mais simples de apenas consumir microsserviços de um aplicativo cliente monolítico. Obviamente, é possível ter um serviço MVC ASP.NET no meio termo produzindo o HTML e o JavaScript. A figura é uma simplificação que destaca que você tem uma única interface do usuário do cliente (monolítica) consumindo microsserviços, que se concentram apenas em lógica e nos dados, e não na forma da interface do usuário (HTML e JavaScript).

![](./media/image20.png)

**Figura 4-20**. Um aplicativo de interface do usuário monolítico consumindo microsserviços de back-end

Em contraste, uma interface do usuário de composição é gerada precisamente e composta pelos próprios microsserviços. Alguns do microsserviços promovem a forma visual de áreas específicas da interface do usuário. A principal diferença é que você tem componentes de interface do usuário do cliente (classes TS, por exemplo) com base em modelos, e o ViewModel da interface do usuário de modelagem de dados para esses modelos vem de cada microsserviço.

Em tempo de inicialização do aplicativo cliente, cada um dos componentes de interface do usuário do cliente (classes TypeScript, por exemplo) se registra com um microsserviço de infraestrutura capaz de fornecer ViewModels para um determinado cenário. Se o microsserviço alterar a forma, a interface do usuário também será alterada.

A Figura 4-21 mostra uma versão dessa abordagem de interface do usuário de composição. Isso é simplificado, porque você pode ter outros microsserviços que estão agregando partes granulares com base em diferentes técnicas — depende se você está criando uma abordagem da Web tradicional (MVC ASP.NET) ou um SPA (aplicativo de página única).

![](./media/image21.png)

**Figura 4-21**. Exemplo de um aplicativo de interface do usuário de composição formatado por microsserviços de back-end

Cada um desses microsserviços de composição de interface do usuário seria semelhante a um Gateway de API pequeno. Mas, nesse caso, cada um é responsável por uma pequena área da interface do usuário.

Uma abordagem de interface do usuário de composição controlada por microsserviços pode ser mais desafiadora ou menos, dependendo de quais tecnologias de interface do usuário você está usando. Por exemplo, você não usará as mesmas técnicas para criar um aplicativo Web tradicional que você usa para criar um SPA ou para o aplicativo móvel nativo (como acontece durante o desenvolvimento de aplicativos Xamarin, que podem ser mais desafiadores para essa abordagem).

O aplicativo de exemplo [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) usa a abordagem de interface do usuário monolítica por vários motivos. Primeiro, é uma introdução a microsserviços e contêineres. Uma interface do usuário de composição é mais avançada, mas também requer mais complexidade ao criar e desenvolver a interface do usuário. Em segundo lugar, o eShopOnContainers também oferece um aplicativo móvel nativo baseado no Xamarin, que tornaria isso mais complexo no lado C\# do cliente.

No entanto, recomendamos que você use as seguintes referências para saber mais sobre a interface do usuário de composição com base em microsserviços.

## <a name="additional-resources"></a>Recursos adicionais

-   **Interface do usuário composta usando ASP.NET (Particular’s Workshop)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. O front-end monolítico na arquitetura de microsserviços**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. O segredo de uma composição melhor de interface do usuário**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic. Incluindo componentes Web de front-end em microsserviços**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Gerenciando o front-end na arquitetura de microsserviços**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Anterior](microservices-addressability-service-registry.md)
[Próximo](resilient-high-availability-microservices.md)
