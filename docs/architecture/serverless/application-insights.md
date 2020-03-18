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
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="c2d9a-103">Telemetria com o Application Insights</span><span class="sxs-lookup"><span data-stu-id="c2d9a-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="c2d9a-104">[O Application Insights](https://docs.microsoft.com/azure/application-insights) é uma plataforma de diagnóstico sem servidor que permite aos desenvolvedores detectar, triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="c2d9a-105">Você pode ativar o Application Insights para aplicativos de função simplesmente invertendo um interruptor no portal.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="c2d9a-106">O Application Insights fornece todos esses recursos sem que você tenha que configurar um servidor ou configurar seu próprio banco de dados.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="c2d9a-107">Todos os recursos do Application Insights são fornecidos como um serviço que se integra automaticamente com seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logotipo do Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="c2d9a-109">Adicionar insights de aplicativos aos aplicativos existentes é tão fácil quanto adicionar uma chave de instrumentação às configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="c2d9a-110">Com insights de aplicativos você pode:</span><span class="sxs-lookup"><span data-stu-id="c2d9a-110">With Application Insights you can:</span></span>

- <span data-ttu-id="c2d9a-111">Crie gráficos e alertas personalizados com base em métricas como número de invocações de função, o tempo necessário para executar uma função e exceções</span><span class="sxs-lookup"><span data-stu-id="c2d9a-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="c2d9a-112">Analisar falhas e exceções de servidores</span><span class="sxs-lookup"><span data-stu-id="c2d9a-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="c2d9a-113">Perfurar o desempenho por operação e medir o tempo que leva para chamar dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="c2d9a-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="c2d9a-114">Monitore o uso da CPU, memória e taxas em todos os servidores que hospedam seus aplicativos de função</span><span class="sxs-lookup"><span data-stu-id="c2d9a-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="c2d9a-115">Exibir uma transmissão ao vivo de métricas, incluindo contagem de solicitações e latência para seus aplicativos de função</span><span class="sxs-lookup"><span data-stu-id="c2d9a-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="c2d9a-116">Use [o Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) para pesquisar, consultar e criar gráficos personalizados sobre os dados da função</span><span class="sxs-lookup"><span data-stu-id="c2d9a-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Metrics Explorer](./media/metrics-explorer.png)

<span data-ttu-id="c2d9a-118">Além da telemetria incorporada, também é possível gerar telemetria personalizada.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="c2d9a-119">O seguinte trecho de código cria um cliente de telemetria personalizado usando a chave de instrumentação definida para o aplicativo de função:</span><span class="sxs-lookup"><span data-stu-id="c2d9a-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="c2d9a-120">O código a seguir mede quanto tempo leva para inserir uma nova linha em uma instância [de armazenamento de tabela do Azure:](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="c2d9a-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="c2d9a-121">O gráfico de desempenho resultante é mostrado:</span><span class="sxs-lookup"><span data-stu-id="c2d9a-121">The resulting performance graph is shown:</span></span>

![Telemetria personalizada](./media/custom-telemetry.png)

<span data-ttu-id="c2d9a-123">A telemetria personalizada revela que o tempo médio para inserir uma nova linha é de 32,6 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="c2d9a-124">O Application Insights fornece uma maneira poderosa e conveniente de registrar telemetria detalhada sobre seus aplicativos sem servidor.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="c2d9a-125">Você tem controle total sobre o nível de rastreamento e registro fornecido.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="c2d9a-126">Você pode acompanhar estatísticas personalizadas, como eventos, dependências e exibição de página.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="c2d9a-127">Finalmente, as análises poderosas permitem escrever consultas que fazem perguntas importantes e geram gráficos e insights avançados.</span><span class="sxs-lookup"><span data-stu-id="c2d9a-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="c2d9a-128">Para saber mais, consulte [Monitorar Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="c2d9a-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c2d9a-129">[Próximo](azure-functions.md)
>[anterior](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="c2d9a-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
