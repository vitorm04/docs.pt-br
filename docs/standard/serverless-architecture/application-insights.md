---
title: Application Insights – aplicativos sem servidor
description: Application Insights é uma plataforma de diagnóstico sem servidor que permite que os desenvolvedores a detectar, realizar triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b4884d483de07c1c2077f7280b6b77c6059572c0
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53154249"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="a01c0-103">Telemetria com o Application Insights</span><span class="sxs-lookup"><span data-stu-id="a01c0-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="a01c0-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) é uma plataforma de diagnóstico sem servidor que permite que os desenvolvedores a detectar, realizar triagem e diagnosticar problemas em aplicativos web, aplicativos móveis, aplicativos de desktop e microsserviços.</span><span class="sxs-lookup"><span data-stu-id="a01c0-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="a01c0-105">Você pode ativar Application Insights para aplicativos de funções basta apertar um botão no portal.</span><span class="sxs-lookup"><span data-stu-id="a01c0-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="a01c0-106">O Application Insights fornece todos esses recursos sem ter que configurar um servidor ou configurar seu próprio banco de dados.</span><span class="sxs-lookup"><span data-stu-id="a01c0-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="a01c0-107">Todos os recursos do Application Insights são fornecidos como um serviço que integra-se automaticamente aos seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="a01c0-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logotipo do aplicativo Insights](./media/application-insights-logo.png)

<span data-ttu-id="a01c0-109">Adicionar o Application Insights para aplicativos existentes é tão fácil quanto adicionar uma chave de instrumentação às configurações do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="a01c0-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="a01c0-110">Com o Application Insights, você pode:</span><span class="sxs-lookup"><span data-stu-id="a01c0-110">With Application Insights you can:</span></span>

* <span data-ttu-id="a01c0-111">Criar gráficos personalizados e alertas com base em métricas como o número de invocações de função, o tempo necessário para executar uma função e exceções</span><span class="sxs-lookup"><span data-stu-id="a01c0-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
* <span data-ttu-id="a01c0-112">Analisar falhas e exceções do servidor</span><span class="sxs-lookup"><span data-stu-id="a01c0-112">Analyze failures and server exceptions</span></span>
* <span data-ttu-id="a01c0-113">Analisar desempenho pela operação e medir o tempo necessário para chamar as dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="a01c0-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
* <span data-ttu-id="a01c0-114">Monitorar o uso de CPU, memória e taxas de todos os servidores que hospedam seus aplicativos de funções</span><span class="sxs-lookup"><span data-stu-id="a01c0-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
* <span data-ttu-id="a01c0-115">Exibir uma transmissão ao vivo de métricas, incluindo a contagem de solicitação e a latência para seus aplicativos de funções</span><span class="sxs-lookup"><span data-stu-id="a01c0-115">View a live stream of metrics including request count and latency for your function apps</span></span>
* <span data-ttu-id="a01c0-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) para pesquisar, consultar e criar gráficos personalizados em seus dados de função</span><span class="sxs-lookup"><span data-stu-id="a01c0-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Gerenciador de métricas](./media/metrics-explorer.png)

<span data-ttu-id="a01c0-118">Além da telemetria interna, também é possível gerar telemetria personalizada.</span><span class="sxs-lookup"><span data-stu-id="a01c0-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="a01c0-119">O trecho de código a seguir cria um cliente de telemetria personalizada usando a chave de instrumentação definida para o aplicativo de funções:</span><span class="sxs-lookup"><span data-stu-id="a01c0-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="a01c0-120">O código a seguir mede quanto tempo demora para inserir uma nova linha em uma [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instância:</span><span class="sxs-lookup"><span data-stu-id="a01c0-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="a01c0-121">O gráfico de desempenho resultante é mostrado:</span><span class="sxs-lookup"><span data-stu-id="a01c0-121">The resulting performance graph is shown:</span></span>

![Telemetria personalizada](./media/custom-telemetry.png)

<span data-ttu-id="a01c0-123">A telemetria personalizada revela o tempo médio para inserir uma nova linha é 32.6 milissegundos.</span><span class="sxs-lookup"><span data-stu-id="a01c0-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="a01c0-124">O Application Insights fornece uma maneira poderosa e conveniente fazer logon telemetria detalhada sobre seus aplicativos sem servidor.</span><span class="sxs-lookup"><span data-stu-id="a01c0-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="a01c0-125">Você tem controle total sobre o nível de rastreamento e registro em log que é fornecido.</span><span class="sxs-lookup"><span data-stu-id="a01c0-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="a01c0-126">Você pode rastrear estatísticas personalizadas, como eventos, dependências e exibição de página.</span><span class="sxs-lookup"><span data-stu-id="a01c0-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="a01c0-127">Por fim, os recursos avançados de análise permitem que você escreva consultas que faça perguntas importantes e geram gráficos e insights avançados.</span><span class="sxs-lookup"><span data-stu-id="a01c0-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="a01c0-128">Para obter mais informações, consulte [monitorar o Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="a01c0-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a01c0-129">[Anterior](azure-functions.md)
>[Próximo](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a01c0-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>