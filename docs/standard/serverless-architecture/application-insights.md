---
title: Application Insights – aplicativos sem servidor
description: Application Insights é uma plataforma de diagnóstico sem servidor que permite que os desenvolvedores a detectar, realizar triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4884d483de07c1c2077f7280b6b77c6059572c0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051216"
---
# <a name="telemetry-with-application-insights"></a>Telemetria com o Application Insights

[Application Insights](https://docs.microsoft.com/azure/application-insights) é uma plataforma de diagnóstico sem servidor que permite que os desenvolvedores a detectar, realizar triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços. Você pode ativar Application Insights para aplicativos de funções basta apertar um botão no portal. O Application Insights fornece todos esses recursos sem ter que configurar um servidor ou configurar seu próprio banco de dados. Todos os recursos do Application Insights são fornecidos como um serviço que integra-se automaticamente aos seus aplicativos.

![Logotipo do aplicativo Insights](./media/application-insights-logo.png)

Adicionar o Application Insights para aplicativos existentes é tão fácil quanto adicionar uma chave de instrumentação às configurações do aplicativo. Com o Application Insights, você pode:

* Criar gráficos personalizados e alertas com base em métricas como o número de invocações de função, o tempo necessário para executar uma função e exceções
* Analisar falhas e exceções do servidor
* Analisar desempenho pela operação e medir o tempo necessário para chamar as dependências de terceiros
* Monitorar o uso de CPU, memória e taxas de todos os servidores que hospedam seus aplicativos de funções
* Exibir uma transmissão ao vivo de métricas, incluindo a contagem de solicitação e a latência para seus aplicativos de funções
* Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) para pesquisar, consultar e criar gráficos personalizados em seus dados de função

![Gerenciador de métricas](./media/metrics-explorer.png)

Além da telemetria interna, também é possível gerar telemetria personalizada. O trecho de código a seguir cria um cliente de telemetria personalizada usando a chave de instrumentação definida para o aplicativo de funções:

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

O código a seguir mede quanto tempo demora para inserir uma nova linha em uma [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instância:

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

O gráfico de desempenho resultante é mostrado:

![Telemetria personalizada](./media/custom-telemetry.png)

A telemetria personalizada revela o tempo médio para inserir uma nova linha é 32.6 milissegundos.

O Application Insights fornece uma maneira poderosa e conveniente fazer logon telemetria detalhada sobre seus aplicativos sem servidor. Você tem controle total sobre o nível de rastreamento e registro em log que é fornecido. Você pode rastrear estatísticas personalizadas, como eventos, dependências e exibição de página. Por fim, os recursos avançados de análise permitem que você escreva consultas que faça perguntas importantes e geram gráficos e insights avançados.

Para obter mais informações, consulte [monitorar o Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).

>[!div class="step-by-step"]
>[Anterior](azure-functions.md)
>[Próximo](logic-apps.md)