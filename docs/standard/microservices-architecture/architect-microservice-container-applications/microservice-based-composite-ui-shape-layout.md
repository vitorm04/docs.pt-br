---
title: Criando a interface do usuário composta baseada em microsserviços
description: A arquitetura de microsserviços não se destina apenas ao back-end. Obtenha uma visão rápida e saiba como usá-la no front-end.
ms.date: 09/20/2018
ms.openlocfilehash: 55cb2a8096cc8122c94cae50af4384e9392868cf
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644586"
---
# <a name="creating-composite-ui-based-on-microservices"></a>Criando a interface do usuário composta baseada em microsserviços

A arquitetura de microsserviços geralmente começa com a manipulação de dados e de lógica do lado do servidor. No entanto, uma abordagem mais avançada é criar sua interface do usuário de aplicativo com base em microsserviços também. Isso significa ter uma interface do usuário de composição produzida pelos microsserviços, em vez de ter microsserviços no servidor e apenas um aplicativo cliente monolítico consumindo os microsserviços. Com essa abordagem, os microsserviços que você criar poderão estar completos com lógica e representação visual.

A Figura 4-20 mostra a abordagem mais simples de apenas consumir microsserviços de um aplicativo cliente monolítico. Obviamente, é possível ter um serviço MVC ASP.NET no meio termo produzindo o HTML e o JavaScript. A figura é uma simplificação que destaca que você tem uma única interface do usuário do cliente (monolítica) consumindo microsserviços, que se concentram apenas em lógica e nos dados, e não na forma da interface do usuário (HTML e JavaScript).

![Um aplicativo monolítico de interface do usuário se conectando a microsserviços individuais.](./media/image20.png)

**Figura 4-20**. Um aplicativo de interface do usuário monolítico consumindo microsserviços de back-end

Em contraste, uma interface do usuário de composição é gerada precisamente e composta pelos próprios microsserviços. Alguns do microsserviços promovem a forma visual de áreas específicas da interface do usuário. A principal diferença é que você tem componentes de interface do usuário do cliente (classes TypeScript, por exemplo) com base em modelos, sendo que o ViewModel da interface do usuário de modelagem de dados para esses modelos é obtido de cada microsserviço.

Em tempo de inicialização do aplicativo cliente, cada um dos componentes de interface do usuário do cliente (classes TypeScript, por exemplo) se registra com um microsserviço de infraestrutura capaz de fornecer ViewModels para um determinado cenário. Se o microsserviço alterar a forma, a interface do usuário também será alterada.

A Figura 4-21 mostra uma versão dessa abordagem de interface do usuário de composição. Isso é simplificado porque você pode ter outros microsserviços que estão agregando partes granulares com base em diferentes técnicas. Isso depende se você está criando uma abordagem tradicional da Web (ASP.NET MVC) ou um SPA (Aplicativo de Página Única).

![No aplicativo de interface do usuário composta, cada seção da interface do usuário é gerada por um microsserviço de composição de interface do usuário, que funciona como um minigateway.](./media/image21.png)

**Figura 4-21**. Exemplo de um aplicativo de interface do usuário de composição formatado por microsserviços de back-end

Cada um desses microsserviços de composição de interface do usuário seria semelhante a um Gateway de API pequeno. Mas, nesse caso, cada um é responsável por uma pequena área da interface do usuário.

Uma abordagem de interface do usuário composta que é controlada por microsserviços pode ser mais desafiadora ou menos, dependendo de quais tecnologias de interface do usuário estão sendo usadas. Por exemplo, você não usará as mesmas técnicas para criar um aplicativo Web tradicional que você usa para criar um SPA ou para o aplicativo móvel nativo (como acontece durante o desenvolvimento de aplicativos Xamarin, que podem ser mais desafiadores para essa abordagem).

O aplicativo de exemplo [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) usa a abordagem de interface do usuário monolítica por vários motivos. Primeiro, é uma introdução a microsserviços e contêineres. Uma interface do usuário de composição é mais avançada, mas também requer mais complexidade ao criar e desenvolver a interface do usuário. Em segundo lugar, o eShopOnContainers também oferece um aplicativo móvel nativo baseado no Xamarin, que tornaria isso mais complexo no lado C\# do cliente.

No entanto, recomendamos que você use as seguintes referências para saber mais sobre a interface do usuário de composição com base em microsserviços.

## <a name="additional-resources"></a>Recursos adicionais

- **Interface do usuário composta usando o ASP.NET (Particular’s Workshop)** \
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga. O front-end monolítico na arquitetura de microsserviços** \
  <https://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti. O segredo de uma composição melhor de interface do usuário** \
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic. Incluindo componentes Web de front-end em microsserviços** \
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Gerenciando o front-end na arquitetura de microsserviços** \
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[Anterior](microservices-addressability-service-registry.md)
>[Próximo](resilient-high-availability-microservices.md)
