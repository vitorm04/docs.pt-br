---
title: Criando, evoluindo e fazendo o controle de versão de APIs e de contratos de microsserviços
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Criando, evoluindo e fazendo o controle de versão de APIs e de contratos de microsserviços
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 4b57a0ed8c4e8a4cd36ef5cef4b40de0595f1284
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575870"
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Criando, evoluindo e fazendo o controle de versão de APIs e de contratos de microsserviços

Uma API de microsserviço é um contrato entre o serviço e seus clientes. Você poderá evoluir um microsserviço de forma independente apenas se você não precisar interromper seu contrato de API, que é o motivo pelo qual o contrato é tão importante. Se você alterar o contrato, isso afetará seus aplicativos cliente ou seu Gateway de API.

A natureza da definição de API depende do protocolo que você está usando. Por exemplo, se você estiver usando mensagens (como [AMQP](https://www.amqp.org/)), a API consistirá nos tipos de mensagem. Se você estiver usando serviços HTTP e RESTful, a API consistirá nas URLs e nos formatos JSON de solicitação e de resposta.

No entanto, mesmo se você estiver em dúvida sobre seu contrato inicial, uma API de serviço precisará ser alterada com o tempo. Quando isso acontecer – e, principalmente, se a sua API for uma API pública consumida por vários aplicativos cliente – normalmente não será possível forçar todos os clientes a atualizarem para seu novo contrato de API. Geralmente, é necessário implantar novas versões de um serviço de forma incremental de maneira que versões novas e antigas de um contrato de serviço estejam em execução simultaneamente. Portanto, é importante ter uma estratégia para o controle de versão do serviço.

Quando as alterações na API forem pequenas, como adicionar atributos ou parâmetros à sua API, os clientes que usam uma API mais antiga devem mudar e trabalhar com a nova versão do serviço. Talvez seja possível fornecer valores padrão para quaisquer atributos ausentes que sejam necessários, e os clientes talvez podem ignorar quaisquer atributos de resposta extra.

No entanto, às vezes, é necessário fazer alterações importantes e incompatíveis em uma API de serviço. Como talvez não seja possível forçar serviços ou aplicativos cliente a serem atualizados imediatamente para a nova versão, um serviço deve dar suporte a versões mais antigas da API por algum período. Se você estiver usando um mecanismo baseado em HTTP como REST, uma abordagem deverá inserir o número de versão da API na URL ou no cabeçalho HTTP. Em seguida, é possível decidir entre implementar ambas as versões do serviço simultaneamente dentro da mesma instância de serviço ou implantar instâncias diferentes que lidam com uma versão da API. Uma boa abordagem para isso é o [padrão mediador](https://en.wikipedia.org/wiki/Mediator_pattern) (por exemplo, [biblioteca MediatR](https://github.com/jbogard/MediatR)) para desacoplar as diferentes versões de implementação em manipuladores independentes.

Por fim, se você estiver usando uma arquitetura REST, o [Hypermedia](https://www.infoq.com/articles/mark-baker-hypermedia) será a melhor solução para controlar a versão de seus serviços e permitir APIs capazes de evoluir.

## <a name="additional-resources"></a>Recursos adicionais

-   **Scott Hanselman. Facilitando o controle de versão da API Web RESTful do ASP.NET Core**
    <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **Controle de versão de uma API Web RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Controle de versão, hipermídia e REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[Anterior] (asynchronous-message-based-communication.md) [Próximo] (microservices-addressability-service-registry.md)
