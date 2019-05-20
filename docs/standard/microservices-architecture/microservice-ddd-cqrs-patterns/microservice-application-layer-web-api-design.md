---
title: Projetando a camada de aplicativos de microsserviço e a API Web
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Uma breve menção dos princípios SOLID para a criação da camada de aplicativo.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639502"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Projetar a camada de aplicativos de microsserviço e a API Web

## <a name="use-solid-principles-and-dependency-injection"></a>Usar princípios SOLID e Injeção de Dependência

Os princípios SOLID são técnicas críticas para serem usadas em qualquer aplicativo moderno e crítico, como desenvolver um microsserviço com padrões DDD. SOLID é um acrônimo que agrupa cinco princípios fundamentais:

- Princípio da Responsabilidade única

- Princípio do aberto/fechado

- Princípio da Substituição de Liskov

- Princípio da Segregação de interface

- Princípio da Inversão de dependência

SOLID trata-se da maneira como você cria as camadas internas do microsserviço ou do aplicativo e do desacoplamento das dependências entre eles. Ele não está relacionado ao domínio, mas ao design técnico do aplicativo. O princípio final, o princípio de Inversão de dependência, permite a você desacoplar a camada de infraestrutura do restante das camadas, que permite uma melhor implementação desacoplada das camadas DDD.

DI (Injeção de Dependência) é uma maneira de implementar o princípio de Inversão de Dependência. É uma técnica para obter um acoplamento flexível entre objetos e suas dependências. Em vez de criar uma instância de colaboradores diretamente ou usar referências estáticas (ou seja, usar novos...), os objetos de que uma classe precisa para executar suas ações são fornecidos (ou "injetados") na classe. Geralmente, as classes declararão suas dependências por meio de seu construtor, possibilitando que elas sigam o princípio de Dependências Explícitas. Geralmente, a Injeção de Dependência baseia-se em contêineres IoC (Inversão de Controle) específicos. O ASP.NET Core fornece um contêiner IoC interno simples, mas também é possível usar seu contêiner IoC favorito, como Autofac ou Ninject.

Seguindo os princípios SOLID, as classes naturalmente tenderão a ser pequenas, bem fatoradas e facilmente testadas. Mas como é possível saber se muitas dependências estão sendo injetadas suas classes? Se você usar a DI por meio do construtor, será fácil detectar isso apenas observando o número de parâmetros para o construtor. Se houver mais dependências, isso geralmente será um sinal (um [code smell](https://deviq.com/code-smells/)) de que sua classe está tentando fazer muito mais e está provavelmente violando o princípio de Responsabilidade única.

Seria preciso outro guia para abordar o SOLID em detalhes. Portanto, este guia exige que você tenha apenas um conhecimento mínimo sobre estes tópicos.

#### <a name="additional-resources"></a>Recursos adicionais

- **SOLID: princípios OOP fundamentais** \
  <https://deviq.com/solid/>

- **Inversão de Contêineres de Controle e o padrão de Injeção de Dependência** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. New is Glue** \ ("New" é como cola)
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Anterior](nosql-database-persistence-infrastructure.md)
> [Próximo](microservice-application-layer-implementation-web-api.md)
