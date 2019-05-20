---
title: Capacidade de endereçamento de microsserviços e o Registro do serviço
description: Entenda a função dos Registros de imagem de contêiner na arquitetura de microsserviços.
ms.date: 09/20/2018
ms.openlocfilehash: 5b601f19b60a8e989977e7135138add7644bd7b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639964"
---
# <a name="microservices-addressability-and-the-service-registry"></a>Capacidade de endereçamento de microsserviços e o Registro do serviço

Cada microsserviço tem um nome exclusivo (URL) usado para resolver sua localização. O microsserviço precisa ser endereçável independentemente do local em que está sendo executado. Se você tiver que pensar em qual computador está executando um microsserviço específico, as coisas poderão se complicar rapidamente. Da mesma forma que o DNS resolve uma URL para um determinado computador, seu microsserviço precisa ter um nome exclusivo para que seu local atual seja detectável. Os microsserviços precisam de nomes endereçáveis que os tornem independentes da infraestrutura na qual eles estão sendo executados. Isso implica que há uma interação entre a maneira como seu serviço é implantado e como ele é detectado, porque deve haver um [Registro do serviço](https://microservices.io/patterns/service-registry.html). Do mesmo modo, quando um computador falha, o serviço de Registro deve ser capaz de indicar o local em que o serviço está sendo executado no momento.

O [padrão de Registro de serviço](https://microservices.io/patterns/service-registry.html) é uma parte importante da descoberta de serviço. O Registro é um banco de dados que contém os locais de rede das instâncias de serviço. Um Registro de serviço precisa ser atualizado e estar altamente disponível. Os clientes podem armazenar locais de rede em cache obtidos do Registro de serviço. No entanto, essas informações eventualmente ficam desatualizadas e os clientes não podem mais descobrir instâncias de serviço. Consequentemente, um Registro de serviço consiste em um cluster de servidores que usam um protocolo de replicação para manter a consistência.

Em alguns ambientes de implantação de microsserviço (chamados clusters, a serem abordados em uma seção posterior), a descoberta de serviço é interna. Por exemplo, um ambiente do AKS (Serviço de Contêiner do Azure com Kubernetes) pode manipular o registro e o cancelamento de registro da instância de serviço. Ele também executa um proxy em cada host de cluster que desempenha a função de roteador de descoberta do servidor. Outro exemplo é o Azure Service Fabric, que também fornece um Registro de serviço por meio de seu Serviço de nomenclatura pronto para uso.

Observe que há determinada sobreposição entre o Registro de serviço e o padrão de gateway de API, que ajuda a resolver esse problema também. Por exemplo, o [Proxy Reverso do Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy) é um tipo de implementação de um Gateway de API baseado no Serviço de Nomenclatura do Service Fabric e que ajuda a resolver a resolução de endereço para os serviços internos.

## <a name="additional-resources"></a>Recursos adicionais

- **Chris Richardson. Padrão: Registro de serviço** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0. O Registro de serviço** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker. Descoberta de serviço** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[Anterior](maintain-microservice-apis.md)
>[Próximo](microservice-based-composite-ui-shape-layout.md)
