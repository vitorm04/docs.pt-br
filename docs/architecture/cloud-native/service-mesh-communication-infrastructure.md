---
title: Infraestrutura de comunicação de malha de serviço
description: Saiba como as tecnologias de malha de serviço simplificam a comunicação de microserviços nativa em nuvem
author: robvet
ms.date: 03/03/2020
ms.openlocfilehash: 8bb57e990dbf1baf8c246fe4aacfbb2904a251e6
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805757"
---
# <a name="service-mesh-communication-infrastructure"></a>Infraestrutura de comunicação de malha de serviço

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Ao longo deste capítulo, exploramos os desafios da comunicação de microserviços. Dissemos que as equipes de desenvolvimento precisam ser sensíveis à forma como os serviços back-end se comunicam entre si. Idealmente, quanto menos comunicação entre serviços, melhor. No entanto, a evasão nem sempre é possível, pois os serviços back-end muitas vezes dependem uns dos outros para concluir as operações.

Exploramos diferentes abordagens para implementar comunicação HTTP síncrona e mensagens assíncronas. Em cada um dos casos, o desenvolvedor é sobrecarregado com a implementação do código de comunicação. O código de comunicação é complexo e demorado. Decisões incorretas podem levar a problemas significativos de desempenho.

Uma abordagem mais moderna para a comunicação de microserviços gira em torno de uma nova e rápida tecnologia intitulada *Service Mesh*. Uma [malha de serviço](https://www.nginx.com/blog/what-is-a-service-mesh/) é uma camada de infra-estrutura configurável com recursos incorporados para lidar com comunicação de serviço para serviço, resiliência e muitas preocupações transversais. Ele move a responsabilidade por essas preocupações para fora dos microserviços e para a camada de malha de serviço. A comunicação é abstraída de seus microsserviços.

Um componente-chave de uma malha de serviço é um proxy. Em um aplicativo nativo da nuvem, uma instância de um proxy é tipicamente colocado com cada microserviço. Enquanto executam em processos separados, os dois estão intimamente ligados e compartilham o mesmo ciclo de vida. Este padrão, conhecido como [padrão Sidecar,](https://docs.microsoft.com/azure/architecture/patterns/sidecar)é mostrado na Figura 4-24.

![Malha de serviço com um carro lateral](./media/service-mesh-with-side-car.png)

**Figura 4-24**. Malha de serviço com um carro lateral

Observe na figura anterior como as mensagens são interceptadas por um proxy que é executado ao lado de cada microserviço. Cada proxy pode ser configurado com regras de tráfego específicas para o microserviço. Ele entende as mensagens e pode encaminhá-las através de seus serviços e do mundo exterior.

Juntamente com o gerenciamento da comunicação serviço-serviço, a Malha de Serviços oferece suporte para detecção de serviços e balanceamento de carga.

Uma vez configurada, uma malha de serviço é altamente funcional. A malha recupera um pool correspondente de instâncias de um ponto final de descoberta de serviço. Ele envia uma solicitação para uma instância de serviço específica, registrando o tipo de latência e resposta do resultado. Ele escolhe a instância mais provável para retornar uma resposta rápida com base em diferentes fatores, incluindo a latência observada para solicitações recentes.

Uma malha de serviço gerencia as preocupações de tráfego, comunicação e rede no nível do aplicativo. Ele entende mensagens e pedidos. Uma malha de serviço normalmente se integra com um orquestrador de contêineres. Kubernetes suporta uma arquitetura extensível na qual uma malha de serviço pode ser adicionada.

No capítulo 6, mergulhamos profundamente nas tecnologias service mesh, incluindo uma discussão sobre sua arquitetura e implementações de código aberto disponíveis.

## <a name="summary"></a>Resumo

Neste capítulo, discutimos padrões de comunicação nativos da nuvem. Começamos examinando como os clientes front-end se comunicam com microsserviços back-end. Ao longo do caminho, falamos sobre plataformas API Gateway e comunicação em tempo real. Em seguida, vimos como os microserviços se comunicam com outros serviços back-end. Analisamos tanto a comunicação HTTP síncrona quanto as mensagens assíncronas entre os serviços. Cobrimos o gRPC, uma tecnologia próxima no mundo nativo da nuvem. Finalmente, introduzimos uma nova e rápida tecnologia intitulada Service Mesh que pode simplificar a comunicação de microserviços.

Especial ênfase foi nos serviços gerenciados do Azure que podem ajudar a implementar a comunicação em sistemas nativos da nuvem:

- [Gateway de aplicativo azure](https://docs.microsoft.com/azure/application-gateway/overview)
- [Gerenciamento de API do Azure](https://azure.microsoft.com/services/api-management/)
- [Serviço Azure SignalR](https://azure.microsoft.com/services/signalr-service/)
- [Filas de Armazenamento do Azure](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction)
- [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview)
- [Grade de Eventos Azure](https://docs.microsoft.com/azure/event-grid/overview)
- [Hub de eventos azure](https://azure.microsoft.com/services/event-hubs/)

Em seguida, passamos para dados distribuídos em sistemas nativos da nuvem e os benefícios e desafios que ele apresenta.

### <a name="references"></a>Referências

- [.NET Microservices: Arquitetura para aplicativos .NET contêiner](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)

- [Projetando comunicação interserviço para microserviços](https://docs.microsoft.com/azure/architecture/microservices/design/interservice-communication)

- [Azure SignalR Service, um serviço totalmente gerenciado para adicionar funcionalidade em tempo real](https://azure.microsoft.com/blog/azure-signalr-service-a-fully-managed-service-to-add-real-time-functionality/)

- [Controlador de entrada de gateway azure API](https://azure.github.io/application-gateway-kubernetes-ingress/)

- [Sobre a Ingress no Azure Kubernetes Service (AKS)](https://vincentlauzon.com/2018/10/10/about-ingress-in-azure-kubernetes-service-aks/)

- [Documentação gRPC](https://grpc.io/docs/guides/)

- [gRPC para desenvolvedores do WCF](https://docs.microsoft.com/dotnet/architecture/grpc-for-wcf-developers/)

- [Comparando os serviços gRPC com as APIs HTTP](https://docs.microsoft.com/aspnet/core/grpc/comparison?view=aspnetcore-3.0)

- [Construindo serviços gRPC com vídeo .NET](https://channel9.msdn.com/Shows/The-Cloud-Native-Show/Building-Microservices-with-gRPC-and-NET)

>[!div class="step-by-step"]
>[Próximo](grpc.md)
>[anterior](database-per-microservice.md)
