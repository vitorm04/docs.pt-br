---
title: "Endereçamento de Microservices e o registro do serviço"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Endereçamento de Microservices e o registro do serviço"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 19a0200dadfb90a455de690d880f4eeae4772ed7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-addressability-and-the-service-registry"></a>Endereçamento de Microservices e o registro do serviço

Cada microsserviço tem um nome exclusivo (URL) que é usado para resolver seu local. O microsserviço precisa ser endereçável independentemente de onde ele está em execução. Se você precisa pensar sobre o computador que está executando um microsserviço específico, coisas podem apresentar problemas rapidamente. Da mesma forma que o DNS resolve uma URL para um determinado computador, seu microsserviço deve ter um nome exclusivo para que seu local atual é detectável. Microservices necessário endereçável nomes que os tornam independente da infraestrutura de que eles sejam executados em. Isso significa que há uma interação entre como seu serviço é implantado e como ele será descoberto, porque deve haver uma [do registro do serviço](http://microservices.io/patterns/service-registry.html). Do mesmo modo, quando um computador falhar, o serviço de registro deve ser capaz de indicar onde o serviço está sendo executado.

O [padrão de registro de serviço](http://microservices.io/patterns/service-registry.html) é uma parte importante da descoberta de serviço. O registro é um banco de dados que contém os locais de rede de instâncias de serviço. Um registro de serviço precisa ser atualizado e altamente disponível. Os clientes podem armazenar em cache locais de rede obtidos do registro de serviço. No entanto, essas informações eventualmente fica desatualizadas e os clientes não podem descobrir instâncias de serviço. Consequentemente, um registro de serviço consiste em um cluster de servidores que usam um protocolo de replicação para manter a consistência.

Em alguns ambientes de implantação de microsserviço (chamados de clusters, sejam incluídos em uma seção posterior), a descoberta de serviço é interna. Por exemplo, em um ambiente de serviço de contêiner do Azure, Kubernetes DC/SO com maratona pode lidar com o registro da instância de serviço e de cancelamento de registro. Eles também executarem um proxy em cada host de cluster que executa a função do roteador de descoberta do servidor. Outro exemplo é o Azure Service Fabric, que também fornece um registro de serviço por meio de seu serviço de nomes de caixa.

Observe que há certa sobreposição entre o registro do serviço e o padrão de gateway de API, que ajuda a resolve esse problema também. Por exemplo, o [Service Fabric Inverter Proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) é um tipo de implementação de um Gateway de API que é baseado no serviço de nomenclatura de serviço Fabrice e que ajuda a resolver a resolução de endereço para os serviços internos.

## <a name="additional-resources"></a>Recursos adicionais

-   **Carlos Richardson. Padrão: Registro de serviço**
    *http://microservices.io/patterns/service-registry.html*

-   **Auth0. O registro do serviço**
    [*https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/*](https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/)

-   **Gabriel Schenker. Descoberta de serviço**
    [*https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/*](https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/)


>[!div class="step-by-step"]
[Anterior] (mantenha-microsserviço-apis.md) [Avançar] (microservice-based-composite-ui-shape-layout.md)
