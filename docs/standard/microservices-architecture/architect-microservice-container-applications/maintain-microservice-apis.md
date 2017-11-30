---
title: "Criando, desenvolvendo e controle de versão de microsserviço APIs e contratos"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criando, desenvolvendo e controle de versão de microsserviço APIs e contratos"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 433711c3479eafd52bf9f5d53faf8e5707c6c624
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="creating-evolving-and-versioning-microservice-apis-and-contracts"></a>Criando, desenvolvendo e controle de versão de microsserviço APIs e contratos

Um API de microsserviço é um contrato entre o serviço e seus clientes. Você poderá desenvolver um microsserviço independentemente somente se você não interromper seu contrato de API, o motivo pelo qual o contrato é tão importante. Se você alterar o contrato, isso afetará os aplicativos cliente ou seu Gateway de API.

A natureza da definição de API depende no protocolo que você está usando. Por exemplo, se você estiver usando o sistema de mensagens (como [AMQP](https://www.amqp.org/)), a API consiste em tipos de mensagem. Se você estiver usando HTTP e os serviços RESTful, a API consiste as URLs e os formatos de solicitação e resposta JSON.

No entanto, mesmo se você estiver certo sobre o contrato inicial, uma API de serviço precisará alterar ao longo do tempo. Quando isso acontece, e especialmente se a sua API é uma API pública consumida por vários aplicativos cliente — normalmente não pode forçar todos os clientes devem atualizar para o novo contrato de API. Normalmente, você precisa implantar novas versões de um serviço de forma que as versões antigas e novas de um contrato de serviço são executados simultaneamente. Portanto, é importante ter uma estratégia para o controle de versão do serviço.

Quando as alterações de API são pequenas, como se você adicionar atributos ou parâmetros para sua API, os clientes que usam uma API mais antiga devem alternar e trabalhar com a nova versão do serviço. Você poderá fornecer valores padrão para todos os atributos ausentes que são necessários e os clientes poderá ignorar os atributos de resposta extra.

No entanto, às vezes você precisa fazer alterações principais e incompatíveis para uma API de serviço. Porque você não poderá forçar a aplicativos cliente ou serviços para atualizar imediatamente para a nova versão, um serviço deve dar suporte a versões mais antigas da API para um determinado período. Se você estiver usando um mecanismo baseado em HTTP, como REST, uma abordagem é inserir o número de versão de API na URL ou em um cabeçalho HTTP. Em seguida, você pode decidir entre implementar ambas as versões do serviço simultaneamente na mesma instância do serviço, ou implantar instâncias diferentes que cada lidar com uma versão da API. Uma boa abordagem para isso é o [padrão mediador](https://en.wikipedia.org/wiki/Mediator_pattern) (por exemplo, [MediatR biblioteca](https://github.com/jbogard/MediatR)) para separar as versões diferentes de implementação em manipuladores independentes.

Por fim, se você estiver usando uma arquitetura REST, [hipermídia](https://www.infoq.com/articles/mark-baker-hypermedia) é a melhor solução para controle de versão de seus serviços e permitindo auxiliando APIs.

## <a name="additional-resources"></a>Recursos adicionais

-   **Scott Hanselman. Controle de versão do núcleo da API da Web RESTful ASP.NET facilitado**
    <http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

-   **Controle de versão de uma API da web RESTful**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Controle de versão, hipermídia e REST**
    <https://www.infoq.com/articles/roy-fielding-on-versioning>


>[!div class="step-by-step"]
[Anterior] (assíncrona-mensagem-com base-communication.md) [Avançar] (microservices-Endereçabilidade-serviço-registry.md)
