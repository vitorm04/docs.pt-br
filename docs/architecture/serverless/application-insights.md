---
title: Insights de aplicativos - Aplicativos sem servidor
description: O Application Insights é uma plataforma de diagnóstico sem servidor que permite aos desenvolvedores detectar, triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522736"
---
# <a name="telemetry-with-application-insights"></a>Telemetria com o Application Insights

[O Application Insights](https://docs.microsoft.com/azure/application-insights) é uma plataforma de diagnóstico sem servidor que permite aos desenvolvedores detectar, triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços. Você pode ativar o Application Insights para aplicativos de função simplesmente invertendo um interruptor no portal. O Application Insights fornece todos esses recursos sem que você tenha que configurar um servidor ou configurar seu próprio banco de dados. Todos os recursos do Application Insights são fornecidos como um serviço que se integra automaticamente com seus aplicativos.

![Logotipo do Application Insights](./media/application-insights-logo.png)

Adicionar insights de aplicativos aos aplicativos existentes é tão fácil quanto adicionar uma chave de instrumentação às configurações do aplicativo. Com insights de aplicativos você pode:

- Crie gráficos e alertas personalizados com base em métricas como número de invocações de função, o tempo necessário para executar uma função e exceções
- Analisar falhas e exceções de servidores
- Perfurar o desempenho por operação e medir o tempo que leva para chamar dependências de terceiros
- Monitore o uso da CPU, memória e taxas em todos os servidores que hospedam seus aplicativos de função
- Exibir uma transmissão ao vivo de métricas, incluindo contagem de solicitações e latência para seus aplicativos de função
- Use [o Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) para pesquisar, consultar e criar gráficos personalizados sobre os dados da função

![Metrics Explorer](./media/metrics-explorer.png)

Além da telemetria incorporada, também é possível gerar telemetria personalizada. O seguinte trecho de código cria um cliente de telemetria personalizado usando a chave de instrumentação definida para o aplicativo de função:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

O código a seguir mede quanto tempo leva para inserir uma nova linha em uma instância [de armazenamento de tabela do Azure:](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

O gráfico de desempenho resultante é mostrado:

![Telemetria personalizada](./media/custom-telemetry.png)

A telemetria personalizada revela que o tempo médio para inserir uma nova linha é de 32,6 milissegundos.

O Application Insights fornece uma maneira poderosa e conveniente de registrar telemetria detalhada sobre seus aplicativos sem servidor. Você tem controle total sobre o nível de rastreamento e registro fornecido. Você pode acompanhar estatísticas personalizadas, como eventos, dependências e exibição de página. Finalmente, as análises poderosas permitem escrever consultas que fazem perguntas importantes e geram gráficos e insights avançados.

Para saber mais, consulte [Monitorar Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Próximo](azure-functions.md)
>[anterior](logic-apps.md)
