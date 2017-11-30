---
title: "Criar a camada de aplicativo de microsserviço e a API da Web"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criar a camada de aplicativo de microsserviço e a API da Web"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Criar a camada de aplicativo de microsserviço e a API da Web

## <a name="using-solid-principles-and-dependency-injection"></a>Usando a injeção de dependência e princípios SÓLIDOS

Princípios SÓLIDOS são técnicas críticas a ser usado em qualquer aplicativo moderno e de missão crítica, como desenvolver um microsserviço com padrões DDD. SÓLIDA é um acrônimo que princípios fundamentais de grupos cinco:

-   Princípio da responsabilidade única

-   Abrir/fechado

-   Substituição de Liskov

-   Princípio de diferenciação de inversão

-   Princípio de inversão de dependência

SÓLIDO é mais sobre como criar seu aplicativo ou as camadas de microsserviço interno e desacoplamento dependências entre eles. Ele não está relacionado ao domínio, mas ao design técnico do aplicativo. O princípio final, o princípio de inversão de dependência (DI), permite que você separe a camada de infraestrutura do restante das camadas, que permite uma melhor implementação das camadas DDD separada.

Injeção de dependência é uma maneira de implementar o princípio de inversão de dependência. Essa é uma técnica para a obtenção de um acoplamento fraco entre objetos e suas dependências. Em vez de diretamente a instanciação de parceiros, ou usando referências estáticas, os objetos que precisa de uma classe para realizar suas ações são fornecidos para (ou "injetados") a classe. Geralmente, classes irá declarar suas dependências por meio de seu construtor, possibilitando que siga o princípio de dependências explícitas. Injeção de dependência é normalmente com base em contêineres específicos de inversão de controle (IoC). ASP.NET Core fornece um contêiner IoC interno simples, mas você também pode usar o contêiner IoC favorito, como Autofac ou Ninject.

Seguindo os princípios SÓLIDOS, suas classes tendem naturalmente sejam pequenos, bem fatorada e facilmente testados. Mas como você sabe se muitas dependências estão sendo injetadas suas classes? Se você usar a DI por meio do construtor, será fácil detectar que, apenas observando o número de parâmetros para o construtor. Se houver muitas dependências, isso geralmente é um sinal (um [código cheiro](http://deviq.com/code-smells/)) que sua classe está tentando fazer muito e provavelmente está violando o princípio da responsabilidade única.

Levaria outra guia para cobrir sólido em detalhes. Portanto, este guia exige que você tenha apenas um conhecimento mínimo dos seguintes tópicos.

#### <a name="additional-resources"></a>Recursos adicionais

-   **SÓLIDO: Princípios OOP fundamentais**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inversão de contêineres de controle e o padrão de injeção de dependência**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Novo é liga**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Anterior] (nosql-banco de dados-persistência-infrastructure.md) [Avançar] (microservice-application-layer-implementation-web-api.md)
