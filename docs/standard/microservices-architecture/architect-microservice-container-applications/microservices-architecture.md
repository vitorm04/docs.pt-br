---
title: Arquitetura de microsserviços
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Arquitetura de microsserviços
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 78d3903e7ed4abf27e78812de87ccbcb9f733663
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="microservices-architecture"></a>Arquitetura de microsserviços

Como o nome implica, uma arquitetura de microsserviços é uma abordagem para criar um aplicativo para servidores como um conjunto de serviços pequenos. Cada serviço é executado em seus próprio processo e comunica-se com outros processos usando protocolos como HTTP/HTTPS, WebSockets ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Cada microsserviço implementa um domínio de ponta a ponta específico ou uma capacidade de negócios dentro de um determinado limite de contexto, e cada um deve ser desenvolvido de forma autônoma e ser implantado independentemente. Por fim, cada microsserviço deve ter seu modelo de dados de domínio relacionado e sua lógica de domínio (gerenciamento de dados decentralizados e de soberania) com base em diferentes tecnologias de armazenamento de dados (SQL, NoSQL) e diferentes linguagens de programação.

Que tamanho deve ter um microsserviço? Ao desenvolver um microsserviço, o tamanho não deve ser o ponto importante. Em vez disso, o ponto importante deve ser criar serviços acoplados livremente para você ter autonomia de desenvolvimento, implantação e escala, para cada serviço. É claro que, ao identificar e criar microsserviços, você deve tentar torná-las o menor possível, desde que você não tenha muitas dependências diretas com outros microsserviços. Mais importante do que o tamanho do microsserviço é a coesão interna que ele deve ter e sua independência de outros serviços.

Por que uma arquitetura de microsserviços? Em resumo, ela oferece agilidade de longo prazo. Os microsserviços permitem melhor facilidade de manutenção em sistemas complexos, grandes e altamente escalonáveis permitindo a criação de aplicativos com base em muitos serviços implantáveis de maneira independente em que cada um tenha ciclos de vida autônomos e granulares.

Como uma vantagem adicional, os microsserviços podem ser aumentados de forma independente. Em vez de ter um único aplicativo monolítico que você deve aumentar como uma unidade, é possível aumentar microsserviços específicos. Desta forma, é possível escalar apenas a área funcional que precisa de mais potência de processamento ou largura de banda de rede para dar suporte à demanda, em vez de aumentar outras áreas do aplicativo que não precisam ser escaladas. Isso significa economias de custo, porque você precisa de menos hardware.

![](./media/image6.png)

**Figura 4-6**. Implantação monolítica versus a abordagem de microsserviços

Como mostra a Figura 4-6, a abordagem de microsserviços permite alterações ágeis e rápida iteração de cada microsserviço, porque é possível alterar áreas pequenas específicas de aplicativos grandes, complexos e escalonáveis.

A arquitetura de aplicativos baseados em microsserviços refinados permite práticas de integração e de entrega contínua. Ela também acelera a entrega de novas funções no aplicativo. A composição refinada de aplicativos também permite a você executar e testar microsserviços em isolamento e evoluí-los de maneira autônoma ao manter contratos claros entre eles. Desde que você não altere a interfaces ou contratos, é possível alterar a implementação interna de qualquer microsserviço ou adicionar novas funcionalidades sem interromper outros microsserviços.

A seguir estão os aspectos importantes para habilitar o sucesso na entrada em produção com um sistema baseado em microsserviços:

-   Monitoramento e verificações de integridade dos serviços e da infraestrutura.

-   Infraestrutura escalonável dos serviços (ou seja, nuvem e orquestradores).

-   Design de segurança e implementação em vários níveis: autenticação, autorização, gerenciamento de segredos, comunicação segura, etc.

-   Entrega rápida de aplicativos, geralmente com diferentes equipes focando-se em diferentes microsserviços.

-   DevOps e práticas e infraestrutura CI/CD.

Dessas, apenas as três primeiras serão abordadas ou introduzidas neste guia. Os dois últimos pontos, que estão relacionados ao ciclo de vida do aplicativo, são abordados no livro eletrônico adicional [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Ciclo de vida do aplicativo Docker em contêineres com Microsoft Platform e ferramentas).

## <a name="additional-resources"></a>Recursos adicionais

-   **Mark Russinovich. Microsserviços: Uma revolução de aplicativos com tecnologia de nuvem**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler. Microsserviços**
    [*https://www.martinfowler.com/articles/microservices.html*](https://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler. Pré-requisitos de microsserviços**
    [*https://martinfowler.com/bliki/MicroservicePrerequisites.html*](https://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Computação em nuvem em partes**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre. Ciclo de vida de aplicativo do Docker em contêineres com a plataforma e as ferramentas da Microsoft (e-book para download)**[*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Anterior] (service-oriented-architecture.md) [Próximo] (data-sovereignty-per-microservice.md)
