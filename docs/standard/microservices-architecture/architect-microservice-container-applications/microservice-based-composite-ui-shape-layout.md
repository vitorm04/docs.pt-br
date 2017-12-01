---
title: "Criar interface de usuário composta com base em microservices, incluindo layout gerados por vários microservices e forma visual de interface do usuário"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar interface de usuário composta com base em microservices, incluindo layout gerados por vários microservices e forma visual de interface do usuário"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4b32fed5eb0de02b01665efa4368eb83e3fda08d
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2017
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>Criar interface de usuário composta com base em microservices, incluindo layout gerados por vários microservices e forma visual de interface do usuário

Arquitetura de Microservices geralmente começa com dados e lógica de tratamento de lado do servidor. No entanto, é uma abordagem mais avançada projetar seu aplicativo na que interface do usuário com base em microservices também. Isso significa que ter uma interface de usuário composto produzido por microservices, em vez de ter microservices no servidor e apenas um aplicativo cliente monolítico consumindo o microservices. Com essa abordagem, o microservices que você criar pode ser concluída com lógica e representação visual.

Figura 4-20 mostra a abordagem mais simples de consumo apenas microservices de um aplicativo cliente monolítico. Obviamente, você pode ter um serviço ASP.NET MVC entre produzindo o HTML e JavaScript. A figura é uma simplificação que destaca a que você tenha um único cliente (monolítico) da interface do usuário consumindo microservices, que se concentrar apenas em lógica e os dados e não na forma de interface do usuário (HTML e JavaScript).

![](./media/image20.png)

**Figura 4-20**. Um aplicativo de interface do usuário monolítico consumindo microservices de back-end

Em contraste, uma interface do usuário composto com precisão é gerado e composto pelo microservices próprios. Alguns do microservices da unidade de forma visual de áreas específicas da interface do usuário. A principal diferença é que você tem componentes de interface do usuário do cliente (classes TS, por exemplo) com base em modelos, e vem de ViewModel UI modelagem de dados para os modelos de cada microsserviço.

Em tempo de inicialização do aplicativo cliente, cada um dos componentes de interface do usuário do cliente (classes TypeScript, por exemplo) se registra com um microsserviço de infraestrutura capaz de fornecer ViewModels para um determinado cenário. Se o microsserviço altera a forma, a interface do usuário também será alterada.

Figura 4-21 mostra uma versão dessa abordagem composto de interface do usuário. Isso é simplificado, porque você pode ter outros microservices que são partes granulares com base em diferentes técnicas de agregação — depende se você estiver criando uma abordagem tradicional da web (ASP.NET MVC) ou um SPA (aplicativo de página única).

![](./media/image21.png)

**Figura 4-21**. Exemplo de um aplicativo de interface do usuário composto formatado por microservices de back-end

Cada um desses microservices de composição de interface do usuário seria semelhante a um Gateway de API pequeno. Mas, nesse caso, cada um é responsável por uma pequena área de interface do usuário.

Uma abordagem de interface do usuário composta que é controlada pelo microservices pode ser mais difícil ou menos assim, dependendo de quais tecnologias de interface do usuário você está usando. Por exemplo, você não usará as mesmas técnicas para criar um aplicativo da web tradicional que você usa para criar um SPA ou para o aplicativo móvel nativo (como acontece durante o desenvolvimento de aplicativos Xamarin, que podem ser mais difícil para essa abordagem).

O [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) aplicativo de exemplo usa o método de interface do usuário monolítico por vários motivos. Primeiro, é uma introdução ao microservices e contêineres. Uma interface do usuário composto é mais avançado, mas também requer mais complexidade ao projetar e desenvolver a interface do usuário. Em segundo lugar, eShopOnContainers também fornece um aplicativo móvel nativo com base em Xamarin, o que seria tornar mais complexo no cliente C\# lado.

No entanto, recomendamos que você use as seguintes referências para saber mais sobre a composição da que interface do usuário com base em microservices.

## <a name="additional-resources"></a>Recursos adicionais

-   **Interface de usuário composta usando o ASP.NET (do específico Workshop)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga. O front-end monolítico na arquitetura do Microservices**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti. O segredo de composição de interface de usuário melhor**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic. Incluir componentes da Web de front-end em Microservices**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Gerenciando o front-end na arquitetura de Microservices**\
    [*http://Allegro.Tech/2016/03/Managing-frontend-in-the-microservices-Architecture.HTML*](http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[Anterior] (microservices-Endereçabilidade-serviço-registry.md) [Avançar] (resiliente-alta-disponibilidade-microservices.md)
