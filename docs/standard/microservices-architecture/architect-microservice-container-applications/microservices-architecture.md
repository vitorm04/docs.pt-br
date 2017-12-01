---
title: "Arquitetura de microsserviços"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Arquitetura de Microservices"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a>Arquitetura de microsserviços

Como o nome implica, uma arquitetura de microservices é uma abordagem para criar um aplicativo de servidor como um conjunto de serviços pequenos. Cada serviço é executado em seu próprio processo e se comunica com outros processos usando protocolos como HTTP/HTTPS, o WebSocket, ou [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Cada microsserviço implementa um domínio de ponta a ponta específico ou a capacidade de negócios dentro de um determinado limite de contexto, e cada um deve ser desenvolvida de forma autônoma e ser implantadas independentemente. Por fim, cada microsserviço deve possuir seu modelo de dados de domínio relacionadas e a lógica do domínio (Soberania e gerenciamento de dados descentralizado) com base em tecnologias de armazenamento de dados diferente (SQL, NoSQL) e linguagens de programação diferentes.

O tamanho deve ser um microsserviço? Ao desenvolver um microsserviço, o tamanho não deve ser o ponto importante. Em vez disso, o ponto importante deve ser criar livremente acoplada serviços para que você tenha a autonomia de desenvolvimento, implantação e escala, para cada serviço. É claro que, ao identificar e criando microservices, experimente para torná-los tão pequenas quanto possível, desde que você não tem muitas dependências diretas com outros microservices. Mais importante do que o tamanho de microsserviço é seu independência de outros serviços e a coesão interno deve ter.

Por que uma arquitetura de microservices? Em resumo, ele fornece a agilidade de longo prazo. Microservices habilitar melhor sustentabilidade em sistemas complexas, grandes e altamente escalonável, permitindo que você crie aplicativos com base em vários serviços independentemente implantáveis que possuem ciclos de vida granulares e autônomos.

Como benefício adicional, microservices pode expandir independentemente. Em vez de ter um único aplicativo monolítico que você deve expandir como uma unidade, em vez disso, você pode expandir microservices específico. Dessa forma, você pode dimensionar a área funcional que precisa de mais processamento de energia ou rede largura de banda para dar suporte a demanda, em vez de expandir outras áreas do aplicativo que não precisam ser dimensionados. Isso significa que uma economia porque você precisa de menos hardware.

![](./media/image6.png)

**Figura 4-6**. Implantação monolítica versus a abordagem microservices

Como mostra a Figura 4-6, a abordagem microservices permite alterações agile e rápida iteração de cada microsserviço, porque você pode alterar áreas pequenas específicas dos aplicativos complexos, grandes e escalonáveis.

A arquitetura de integração contínua de habilita aplicativos microservices refinada e práticas recomendadas de fornecimento contínuo. Ele também acelera a entrega de novas funções no aplicativo. Composição refinada de aplicativos também permite que você execute e teste microservices isolamento e evolui-los a autonomia mantendo limpar contratos entre eles. Desde que você não altere a interfaces ou contratos, você pode alterar a implementação interna de qualquer microsserviço ou adicionar novas funcionalidades sem quebrar outras microservices.

Estes são os aspectos importantes para habilitar o sucesso em entrar em produção com um sistema baseado em microservices:

-   Verificações de integridade e monitoramento de serviços e infraestrutura.

-   Infraestrutura escalonável para os serviços (ou seja, nuvem e orchestrators).

-   Design de segurança e a implementação em vários níveis: autenticação, autorização, gerenciamento de segredos, comunicação segura, etc.

-   Entrega rápido de aplicativos, geralmente com diferentes equipes focando microservices diferentes.

-   Práticas recomendadas de CI/CD e DevOps e infraestrutura.

Desses, apenas as três primeiras são abordadas ou introduzidas neste guia. Os dois últimos pontos, que estão relacionados ao ciclo de vida do aplicativo, são abordados em adicional [em contêineres Docker ciclo de vida do Microsoft Platform e ferramentas](https://aka.ms/dockerlifecycleebook) livro eletrônico.

## <a name="additional-resources"></a>Recursos adicionais

-   **Mark Russinovich. Microservices: Uma revolução de aplicativo da plataforma de nuvem**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler. Microservices**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler. Pré-requisitos de Microsserviço**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Parte da nuvem de computação**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre. Em contêineres de Docker o ciclo de vida do aplicativo com o Microsoft Platform e ferramentas** (que pode ser baixado e-book) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Anterior] (serviço-orientado-architecture.md) [Avançar] (dados-Soberania-por-microservice.md)
