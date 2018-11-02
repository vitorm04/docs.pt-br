---
title: Projetando a camada de aplicativos de microsserviço e a API Web
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Projetando a camada de aplicativos de microsserviço e a API Web
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: a8c03f99accf75f60fe6c21a0f09f304214b4a6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194092"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Projetando a camada de aplicativos de microsserviço e a API Web

## <a name="using-solid-principles-and-dependency-injection"></a>Usando princípios SOLID e injeção de dependência

Os princípios SOLID são técnicas críticas para serem usadas em qualquer aplicativo moderno e crítico, como desenvolver um microsserviço com padrões DDD. SOLID é um acrônimo que agrupa cinco princípios fundamentais:

-   Princípio da Responsabilidade única

-   Princípio do aberto/fechado

-   Princípio da Substituição de Liskov

-   Princípio da Segregação de interface

-   Princípio da Inversão de dependência

SOLID trata-se da maneira como você cria as camadas internas do microsserviço ou do aplicativo e do desacoplamento das dependências entre eles. Ele não está relacionado ao domínio, mas ao design técnico do aplicativo. O princípio final, o princípio de Inversão de dependência, permite a você desacoplar a camada de infraestrutura do restante das camadas, que permite uma melhor implementação desacoplada das camadas DDD.

DI (Injeção de Dependência) é uma maneira de implementar o princípio de Inversão de Dependência. É uma técnica para obter um acoplamento flexível entre objetos e suas dependências. Em vez de criar uma instância de colaboradores diretamente, ou usar referências estáticas, os objetos de que uma classe precisa a fim de executar suas ações são fornecidas (ou "injetadas na") classe. Geralmente, as classes declararão suas dependências por meio de seu construtor, possibilitando que elas sigam o princípio de Dependências Explícitas. Geralmente a DI é baseada em contêineres IoC (Inversão de controle) específicos. O ASP.NET Core fornece um contêiner IoC interno simples, mas também é possível usar seu contêiner IoC favorito, como Autofac ou Ninject.

Seguindo os princípios SOLID, as classes naturalmente tenderão a ser pequenas, bem fatoradas e facilmente testadas. Mas como é possível saber se muitas dependências estão sendo injetadas suas classes? Se você usar a DI por meio do construtor, será fácil detectar isso apenas observando o número de parâmetros para o construtor. Se houver mais dependências, isso geralmente será um sinal (um [code smell](https://deviq.com/code-smells/)) de que sua classe está tentando fazer muito mais e está provavelmente violando o princípio de Responsabilidade única.

Seria preciso outro guia para abordar o SOLID em detalhes. Portanto, este guia exige que você tenha apenas um conhecimento mínimo sobre estes tópicos.

#### <a name="additional-resources"></a>Recursos adicionais

-   **SOLID: princípios OOP fundamentais**
    [*https://deviq.com/solid/*](https://deviq.com/solid/%20)

-   **Inversão de Contêineres de Controle e o padrão de Injeção de Dependência**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. New is Glue (New é como cola)**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Anterior](nosql-database-persistence-infrastructure.md)
[Próximo](microservice-application-layer-implementation-web-api.md)
