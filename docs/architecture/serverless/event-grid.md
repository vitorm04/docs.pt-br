---
title: Azure Event Grid - Aplicativos sem servidor
description: O Azure Event Grid é uma solução sem servidor para entrega e roteamento de eventos confiáveis em grande escala em um modelo de pagamento por evento.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522720"
---
# <a name="event-grid"></a>Grade de Eventos

[O Azure Event Grid](/azure/event-grid/overview) fornece infra-estrutura sem servidor para aplicativos baseados em eventos. Você pode publicar no Event Grid de qualquer fonte e consumir mensagens de qualquer plataforma. Event Grid também tem suporte integrado para eventos a partir de recursos do Azure para agilizar a integração com seus aplicativos. Por exemplo, você pode se inscrever em eventos de armazenamento blob para notificar seu aplicativo quando um arquivo é carregado. Seu aplicativo pode então publicar uma mensagem personalizada da grade de eventos que é consumida por outros aplicativos em nuvem ou no local. Event Grid foi construído para lidar de forma confiável em grande escala. Você tem os benefícios de publicar e assinar mensagens sem a sobrecarga de configurar a infra-estrutura necessária.

![Logotipo da Grade de Eventos](./media/event-grid-logo.png)

As principais características da grade de eventos incluem:

- Roteamento de eventos totalmente gerenciado.
- Entrega de eventos quase em tempo real em escala.
- Ampla cobertura dentro e fora do Azure.

## <a name="scenarios"></a>Cenários

Event Grid aborda vários cenários diferentes. Esta seção abrange três das mais comuns.

### <a name="ops-automation"></a>Automação de operações

![Automação de operações](./media/ops-automation.png)

O Event Grid pode ajudar a acelerar a automação e simplificar a aplicação de políticas, notificando [a Automação Do Azure](https://docs.microsoft.com/azure/automation) quando a infra-estrutura é provisionada.

### <a name="application-integration"></a>Integração de aplicativos

![Integração de aplicativos](./media/app-integration.png)

Você pode usar event grid para conectar seu aplicativo a outros serviços. Usando protocolos HTTP padrão, até mesmo aplicativos legados podem ser facilmente modificados para publicar mensagens da Event Grid. Os ganchos web estão disponíveis para outros serviços e plataformas para consumir mensagens do Event Grid.

### <a name="serverless-apps"></a>Aplicativos sem servidor

![Aplicativos sem servidor](./media/serverless-apps.png)

Event Grid pode ativar funções do Azure, aplicativos lógicos ou seu próprio código personalizado. Um grande benefício do uso do Event Grid é que ele usa um mecanismo *de push* para enviar mensagens quando ocorrem eventos. A arquitetura push consome menos recursos e escalas melhor do que os mecanismos *de votação.* A votação deve verificar se há atualizações em um intervalo regular.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Event Grid vs. outros serviços de mensagens do Azure

O Azure fornece vários serviços de mensagens, incluindo [Event Hubs](https://docs.microsoft.com/azure/event-hubs) e [Service Bus.](https://docs.microsoft.com/azure/service-bus-messaging) Cada um foi projetado para abordar um conjunto específico de casos de uso. O diagrama a seguir fornece uma visão geral de alto nível das diferenças entre os serviços.

![Comparação de mensagens azure](./media/azure-messaging-services.png)

Para obter uma comparação mais aprofundada, consulte [Comparar serviços de mensagens](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Destinos de desempenho

Usando a Grade de Eventos, você pode aproveitar as seguintes garantias de desempenho:

- Latência de ponta a ponta no percentil 99.
- disponibilidade de 99,99%.
- 10 milhões de eventos por segundo por região.
- 100 milhões de assinaturas por região.
- Latência de editores de 50 ms.
- Retente de 24 horas com recuo exponencial para entrega garantida na janela de 1 dia.
- Failover regional transparente.

## <a name="event-grid-schema"></a>Esquema da Grade de Eventos

Event Grid usa um esquema padrão para encerrar eventos personalizados. O esquema é como um envelope que envolve seu elemento de dados personalizado. Aqui está uma mensagem de event grid de exemplo:

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

Tudo sobre a mensagem `data` é padrão, exceto a propriedade. Você pode inspecionar a `eventType` mensagem e usar o e `dataVersion` desserializar a parte personalizada da carga.

## <a name="azure-resources"></a>Recursos do Azure

Um grande benefício do uso do Event Grid são as mensagens automáticas produzidas pelo Azure. No Azure, os recursos são publicados automaticamente em um *tópico* que permite que você se inscreva para vários eventos. A tabela a seguir lista os tipos de recursos, tipos de mensagens e eventos disponíveis automaticamente.

| Recursos do Azure | Tipo de evento | Descrição |
| -------------- | ---------- | ----------- |
| Assinatura do Azure | Microsoft.Resources.ResourceWriteSuccess | Gerado quando um recurso cria ou operação de atualização será bem-sucedida. |
| | Microsoft.Resources.ResourceWriteFailure | Gerado quando um recurso cria ou operação de atualização será falha. |
| | Microsoft.Resources.ResourceWriteCancel | Gerado quando um recurso cria ou operação de atualização é cancelada. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Gerado quando um recurso cria ou operação de atualização é bem-sucedida. |
|  | Microsoft.Resources.ResourceDeleteFailure | Gerado quando um recurso cria ou operação de atualização é falha. |
| | Microsoft.Resources.ResourceDeleteCancel | Gerado quando um recurso cria ou operação de atualização é cancelada. Esse evento ocorre quando a implantação de um modelo é cancelada. |
| Armazenamento de blob | Microsoft.Storage.BlobCreated | Gerado quando um blob é criado. |
| | Microsoft.Storage.BlobDeleted | Gerado quando um blob é deletado. |
| Hubs de Eventos | Microsoft.EventHub.CaptureFileCriado | Criado quando um arquivo de captura é criado.
| Hub IoT | Microsoft.Devices.DeviceCreated | Publicado quando um dispositivo é registrado para um Hub IoT. |
| | Microsoft.Devices.DeviceDeleted | Publicado quando um dispositivo é excluído de um Hub IoT. |
| Grupos de recursos | Microsoft.Resources.ResourceWriteSuccess | Gerado quando um recurso cria ou operação de atualização será bem-sucedida. |
| | Microsoft.Resources.ResourceWriteFailure | Gerado quando um recurso cria ou operação de atualização será falha. |
| | Microsoft.Resources.ResourceWriteCancel | Gerado quando um recurso cria ou operação de atualização é cancelada. |
| | Microsoft.Resources.ResourceDeleteSuccess | Gerado quando um recurso cria ou operação de atualização é bem-sucedida. |
| | Microsoft.Resources.ResourceDeleteFailure | Gerado quando um recurso cria ou operação de atualização é falha. |
| | Microsoft.Resources.ResourceDeleteCancel | Gerado quando um recurso cria ou operação de atualização é cancelada. Esse evento ocorre quando a implantação de um modelo é cancelada. |

Para obter mais informações, consulte [o esquema de eventos da Azure Event Grid](https://docs.microsoft.com/azure/event-grid/event-schema).

Você pode acessar o Event Grid a partir de qualquer tipo de aplicativo, mesmo um que seja executado no local.

## <a name="conclusion"></a>Conclusão

Neste capítulo você aprendeu sobre a plataforma sem servidor Azure que é composta por Funções Do Zure, Aplicativos lógicos e Grade de Eventos. Você pode usar esses recursos para construir uma arquitetura de aplicativo totalmente sem servidor ou criar uma solução híbrida que interaja com outros recursos de nuvem e servidores locais. Combinado com uma plataforma de dados sem servidor, como [o Azure SQL](https://docs.microsoft.com/azure/sql-database) ou [o CosmosDB,](https://docs.microsoft.com/azure/cosmos-db/introduction)você pode criar aplicativos nativos na nuvem totalmente gerenciados.

## <a name="recommended-resources"></a>Recursos recomendados

- [Planos de serviço de aplicativos](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [Application Insights](https://docs.microsoft.com/azure/application-insights)
- [Análise do Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [Azure: traga seu aplicativo para a nuvem com funções do Azure sem servidor](https://channel9.msdn.com/events/Connect/2017/E102)
- [Grade de Eventos Azure](https://docs.microsoft.com/azure/event-grid/overview)
- [Esquema de eventos da Grade de Eventos do Azure](https://docs.microsoft.com/azure/event-grid/event-schema)
- [Hubs de eventos do Azure](https://docs.microsoft.com/azure/event-hubs)
- [Documentação de Funções do Azure](https://docs.microsoft.com/azure/azure-functions)
- [Conceitos de gatilhos e de associações do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [Aplicativos azure logic](https://docs.microsoft.com/azure/logic-apps)
- [Ônibus de serviço azure](https://docs.microsoft.com/azure/service-bus-messaging)
- [Armazenamento de mesa azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [Comparar funções 1.x e 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [Conectar-se a fontes de dados locais com o Gateway de Dados Local do Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [Criar sua primeira função no portal do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [Criar sua primeira função usando a CLI do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [Criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [Funções suportadas idiomas](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [Monitorar Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [Trabalhe com Proxies do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Próximo](logic-apps.md)
>[anterior](durable-azure-functions.md)
