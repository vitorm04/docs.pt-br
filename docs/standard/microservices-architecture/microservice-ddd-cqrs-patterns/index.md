---
title: Lidando com a complexidade de negócios em um microsserviço com padrões DDD e CQRS
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Entenda como lidar com cenários de negócios complexos aplicando padrões DDD e CQRS
ms.date: 10/08/2018
ms.openlocfilehash: d311641e2ac73205c04c3f1147b54991585ce851
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639806"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a>Lidar com a complexidade dos negócios em um microsserviço com padrões DDD e CQRS

*Crie um modelo de domínio para cada microsserviço ou contexto limitado que reflita o entendimento do domínio da empresa.*

Esta seção concentra-se em microsserviços mais avançados que você implementa quando precisa lidar com subsistemas complexos ou com microsserviços derivados do conhecimento de especialistas no domínio com mudanças constantes nas regras de negócio. Os padrões de arquitetura usados nesta seção são baseados nas abordagens DDD (design controlado por domínio) e CQRS (Segregação de Responsabilidade de Comando e Consulta), conforme é ilustrado na Figura 7-1.

![Diferença entre arquitetura externa: padrões de microsserviço, gateways de API, comunicação resilientes, pub/sub etc. e a arquitetura interna: controlado por dados/CRUD, padrões de DDD, injeção de dependência, várias bibliotecas etc.](./media/image1.png)

**Figura 7-1**. Arquitetura externa de microsserviço versus padrões de arquitetura interna para cada microsserviço

No entanto, a maioria das técnicas de microsserviços controlados por dados, incluindo como implementar um serviço de API Web do ASP.NET Core ou como expor metadados com Swashbuckle ou NSwag, também se aplica aos microsserviços mais avançados implementados internamente com padrões DDD. Esta seção é uma extensão das seções anteriores, pois a maioria das práticas de explicadas anteriormente também se aplicam aqui ou para qualquer tipo de microsserviço.

Esta seção primeiro fornece detalhes sobre os padrões CQRS simplificados usados no aplicativo de referência eShopOnContainers. Posteriormente, você obterá uma visão geral das técnicas de DDD que permitem encontrar padrões comuns que podem ser reutilizados em seus aplicativos.

O DDD é um tópico grande com um conjunto avançado de recursos de aprendizagem. Você pode iniciar com guias como [Domain-Driven Design](https://domainlanguage.com/ddd/) (Design controlado por domínio) do Eric Evans e os materiais adicionais dos autores Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard e muitos outros especialistas em DDD/CQRS. Mas, sobretudo, você precisa tentar aprender como aplicar as técnicas de DDD das sessões de conversa, de quadro de comunicações e de modelagem com os especialistas em seu domínio de negócio concreto.

#### <a name="additional-resources"></a>Recursos adicionais

##### <a name="ddd-domain-driven-design"></a>DDD (design controlado por domínio)

- **Eric Evans. Idioma do domínio** \
  <https://domainlanguage.com/>

- **Martin Fowler. Design orientado por domínio** \
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- **Jimmy Bogard. Como reforçar seu domínio: informações elementares** \
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a>Guias sobre DDD

- **Eric Evans. Design orientado por domínio: Lidar com a complexidade no núcleo do software** \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Eric Evans. Referências de design controlado por domínio: Resumos de padrão e definições** \
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- **Vaughn Vernon. Implementação de um design orientado por domínio** \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Vaughn Vernon. Design orientado por domínio condensado** \
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- **Jimmy Nilsson. Aplicação de design e padrões orientados por domínio** \
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- **Cesar de la Torre. Guia de arquitetura orientado por domínio em N camadas com o .NET** \
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- **Abel Avram e Floyd Marinescu. Design orientado por domínio rapidamente** \
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- **Scott Millett, Nick Tune – Padrões, princípios e práticas recomendadas do design orientado por domínio** \
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a>Treinamento em DDD

- **Julie Lerman e Steve Smith. Conceitos básicos sobre o design orientado por domínio** \
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
>[Anterior](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[Próximo](apply-simplified-microservice-cqrs-ddd-patterns.md)
