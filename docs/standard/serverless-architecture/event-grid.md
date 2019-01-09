---
title: Grade de eventos do Azure - aplicativos sem servidor
description: A grade de eventos do Azure é uma solução sem servidor para entrega de eventos confiável e o roteamento em grande escala em um modelo de pagamento por evento.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: a10fc6a47322de5db40870b1b727edc5559a27f6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145857"
---
# <a name="event-grid"></a>Grade de eventos

[A grade de eventos do Azure](/azure/event-grid/overview) fornece infraestrutura sem servidor para aplicativos baseados em eventos. Você pode publicar na grade de eventos de qualquer origem e consumir mensagens de qualquer plataforma. Grade de eventos também tem suporte interno para eventos de recursos do Azure para simplificar a integração com seus aplicativos. Por exemplo, você pode assinar eventos de armazenamento de blob para notificar seu aplicativo quando um arquivo for carregado. Seu aplicativo, em seguida, pode publicar uma mensagem de grade de evento personalizado que é consumida por outra nuvem ou aplicativos locais. Grade de eventos foi criada para lidar com confiança de grande escala. Você obtém os benefícios da publicação e assinar mensagens sem a sobrecarga de configurar a infraestrutura necessária.

![Logotipo da grade de eventos](./media/event-grid-logo.png)

Os principais recursos da grade de eventos incluem:

* Roteamento de eventos totalmente gerenciado.
* Perto de entrega de eventos em tempo real em escala.
* Cobertura mais ampla dentro e fora do Azure.

## <a name="scenarios"></a>Cenários

Grade de eventos aborda vários cenários diferentes. Esta seção aborda três dos mais comuns.

### <a name="ops-automation"></a>Automação de operações

![Automação de operações](./media/ops-automation.png)

Grade de eventos pode ajudar a automação de velocidade e simplificar a aplicação de políticas, notificando [automação do Azure](https://docs.microsoft.com/azure/automation) quando a infraestrutura é provisionada.

### <a name="application-integration"></a>Integração de aplicativos

![Integração de aplicativos](./media/app-integration.png)

Você pode usar a grade de eventos para conectar seu aplicativo a outros serviços. Usando protocolos HTTP padrão, aplicativos herdados ainda podem ser facilmente modificados para publicar mensagens da grade de eventos. Ganchos da Web estão disponíveis para outros serviços e plataformas para consumir mensagens da grade de eventos.

### <a name="serverless-apps"></a>Aplicativos sem servidor

![Aplicativos sem servidor](./media/serverless-apps.png)

Grade de eventos pode disparar o Azure Functions, aplicativos lógicos ou seu próprio código personalizado. Uma grande vantagem de usar a grade de eventos é que ele usa um *push* mecanismo para enviar mensagens quando ocorrerem eventos. A arquitetura de push consome menos recursos e dimensiona melhor do que *sondagem* mecanismos. Sondagem deve verificar se há atualizações em intervalos regulares.

## <a name="event-grid-vs-other-azure-messaging-services"></a>Grade de eventos versus outros serviços de mensagens do Azure

O Azure fornece vários serviços de sistema de mensagens, incluindo [dos Hubs de eventos](https://docs.microsoft.com/azure/event-hubs) e [do barramento de serviço](https://docs.microsoft.com/azure/service-bus-messaging). Cada foi projetado para tratar de um conjunto específico de casos de uso. O diagrama a seguir fornece uma visão geral das diferenças entre os serviços.

![Comparação de mensagens do Azure](./media/azure-messaging-services.png)

Para obter uma comparação mais detalhada, consulte [comparam os serviços de mensagens](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).

## <a name="performance-targets"></a>Metas de desempenho

Usando a grade de eventos, você pode tirar proveito do desempenho seguinte garantias:

* Subsecond latência de ponta a ponta no 99 º percentil.
* disponibilidade de 99,99%.
* 10 milhões de eventos por segundo por região.
* assinaturas de 100 milhões por região.
* latência do publicador de 50 ms.
* repetição de 24 horas com retirada exponencial para entrega garantida na janela de 1 dia.
* Failover regional transparente.

## <a name="event-grid-schema"></a>Esquema de grade de eventos

Grade de eventos usa um esquema padrão para encapsular eventos personalizados. O esquema é como um envelope que encapsula o elemento de dados personalizados. Aqui está um exemplo de mensagem de grade de eventos:

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

Tudo sobre a mensagem é o padrão, exceto o `data` propriedade. Você pode inspecionar a mensagem e usar o `eventType` e `dataVersion` desserializar a parte personalizada de carga.

## <a name="azure-resources"></a>Recursos do Azure

Uma grande vantagem de usar a grade de eventos é que as mensagens automática produzidas pelo Azure. No Azure, recursos de publicar automaticamente um *tópico* que permite que você assine para vários eventos. A tabela a seguir lista os tipos de recursos, tipos de mensagens e eventos que estão disponíveis automaticamente.

| Recursos do Azure | Tipo de evento | Descrição |
| -------------- | ---------- | ----------- |
| Assinatura do Azure | Microsoft.Resources.ResourceWriteSuccess | Gerado quando um recurso cria ou operação de atualização é bem-sucedida. |
| | Microsoft.Resources.ResourceWriteFailure | Gerado quando um recurso cria ou operação de atualização falhará. |
| | Microsoft.Resources.ResourceWriteCancel | Gerado quando um recurso cria ou operação de atualização é cancelada. |
|  | Microsoft.Resources.ResourceDeleteSuccess | Gerado quando uma operação de exclusão do recurso é bem-sucedida. |
|  | Microsoft.Resources.ResourceDeleteFailure | Gerado quando uma operação de exclusão de recurso falha. |
| | Microsoft.Resources.ResourceDeleteCancel | Gerado quando uma operação de exclusão do recurso é cancelada. Esse evento ocorre quando uma implantação de modelo é cancelada. |
| Armazenamento de BLOBs | Microsoft.Storage.BlobCreated | Gerado quando um blob é criado. |
| | Microsoft.Storage.BlobDeleted | Gerado quando um blob é excluído. |
| Hubs de eventos | Microsoft.EventHub.CaptureFileCreated | Gerado quando um arquivo de captura é criado.
| Hub IoT | Microsoft.Devices.DeviceCreated | Publicado quando um dispositivo é registrado para um hub IoT. |
| | Microsoft.Devices.DeviceDeleted | Publicado quando um dispositivo é excluído de um hub IoT. |
| Grupos de recursos | Microsoft.Resources.ResourceWriteSuccess | Gerado quando um recurso cria ou operação de atualização é bem-sucedida. |
| | Microsoft.Resources.ResourceWriteFailure | Gerado quando um recurso cria ou operação de atualização falhará. |
| | Microsoft.Resources.ResourceWriteCancel | Gerado quando um recurso cria ou operação de atualização é cancelada. |
| | Microsoft.Resources.ResourceDeleteSuccess | Gerado quando uma operação de exclusão do recurso é bem-sucedida. |
| | Microsoft.Resources.ResourceDeleteFailure | Gerado quando uma operação de exclusão de recurso falha. |
| | Microsoft.Resources.ResourceDeleteCancel | Gerado quando uma operação de exclusão do recurso é cancelada. Esse evento ocorre quando uma implantação de modelo é cancelada. |

Para obter mais informações, consulte [esquema de evento de grade de eventos do Azure](https://docs.microsoft.com/azure/event-grid/event-schema).

Você pode acessar a grade de eventos de qualquer tipo de aplicativo, até mesmo um que é executado localmente.

## <a name="conclusion"></a>Conclusão

Neste capítulo, você aprendeu sobre a plataforma do Azure sem servidor que é composta de funções do Azure, aplicativos lógicos e a grade de eventos. Você pode usar esses recursos para criar uma arquitetura de aplicativo totalmente sem servidor, ou criar uma solução híbrida que interage com outros recursos de nuvem e em servidores locais. Combinado com uma plataforma de dados sem servidor como [SQL do Azure](https://docs.microsoft.com/azure/sql-database) ou [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), você pode criar aplicativos nativos de nuvem totalmente gerenciada.

## <a name="recommended-resources"></a>Recursos recomendados

* [Planos de serviço de aplicativo](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [Application Insights](https://docs.microsoft.com/azure/application-insights)
* [Análise do Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [Azure: Traga o seu aplicativo para a nuvem com o Azure Functions sem servidor](https://channel9.msdn.com/events/Connect/2017/E102)
* [Grade de Eventos do Azure](https://docs.microsoft.com/azure/azure-event-grid/overview)
* [Esquema de evento de grade de eventos do Azure](https://docs.microsoft.com/azure/event-grid/event-schema)
* [Hubs de eventos do Azure](https://docs.microsoft.com/azure/event-hubs)
* [Documentação de funções do Azure](https://docs.microsoft.com/azure/azure-functions)
* [Conceitos de associações e gatilhos do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [Aplicativos Lógicos do Azure](https://docs.microsoft.com/azure/logic-apps)
* [Barramento de Serviço do Azure](https://docs.microsoft.com/azure/service-bus-messaging)
* [Armazenamento de tabelas do Azure](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [Comparar functions 1.x e 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [Conectar-se a fontes de dados local com o Gateway de dados local do Azure](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [Criar sua primeira função no portal do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [Criar sua primeira função usando a CLI do Azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [Criar sua primeira função usando o Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [Funções de idiomas com suporte](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [Monitorar Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [Trabalhar com Proxies do Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
>[Anterior](logic-apps.md)
>[Próximo](durable-azure-functions.md)
