---
title: Medir o desempenho usando o EventCounters no .NET Core
description: Neste tutorial, você aprenderá a medir o desempenho usando o EventCounters.
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: 7b4940e17d01e7ec5a50d11e3c818ecdec2d48cf
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024992"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="2ab49-103">Tutorial: medir o desempenho usando o EventCounters no .NET Core</span><span class="sxs-lookup"><span data-stu-id="2ab49-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="2ab49-104">**Este artigo aplica-se a: ✔️** SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="2ab49-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="2ab49-105">Neste tutorial, você aprenderá como um <xref:System.Diagnostics.Tracing.EventCounter> pode ser usado para medir o desempenho com uma alta frequência de eventos.</span><span class="sxs-lookup"><span data-stu-id="2ab49-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="2ab49-106">Você pode usar os [contadores disponíveis](event-counters.md#available-counters) publicados por vários pacotes oficiais do .NET Core, provedores de terceiros ou criar suas próprias métricas para monitoramento.</span><span class="sxs-lookup"><span data-stu-id="2ab49-106">You can use the [available counters](event-counters.md#available-counters) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="2ab49-107">Neste tutorial, você irá:</span><span class="sxs-lookup"><span data-stu-id="2ab49-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="2ab49-108">Implemente um <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="2ab49-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="2ab49-109">Monitorar contadores com [dotnet-contadores](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="2ab49-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ab49-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="2ab49-110">Prerequisites</span></span>

<span data-ttu-id="2ab49-111">O tutorial usa:</span><span class="sxs-lookup"><span data-stu-id="2ab49-111">The tutorial uses:</span></span>

- <span data-ttu-id="2ab49-112">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="2ab49-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="2ab49-113">[dotnet-contadores](dotnet-counters.md) para monitorar os contadores de eventos.</span><span class="sxs-lookup"><span data-stu-id="2ab49-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="2ab49-114">Um aplicativo de [destino de depuração de exemplo](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) para diagnosticar.</span><span class="sxs-lookup"><span data-stu-id="2ab49-114">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="2ab49-115">Obter a origem</span><span class="sxs-lookup"><span data-stu-id="2ab49-115">Get the source</span></span>

<span data-ttu-id="2ab49-116">O aplicativo de exemplo será usado como base para o monitoramento.</span><span class="sxs-lookup"><span data-stu-id="2ab49-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="2ab49-117">O [repositório de ASP.NET Core de exemplo](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) está disponível no navegador de exemplos.</span><span class="sxs-lookup"><span data-stu-id="2ab49-117">The [sample ASP.NET Core repository](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="2ab49-118">Baixe o arquivo zip, extraia-o depois de baixado e abra-o em seu IDE favorito.</span><span class="sxs-lookup"><span data-stu-id="2ab49-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="2ab49-119">Compile e execute o aplicativo para garantir que ele funcione corretamente e, em seguida, interrompa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ab49-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="2ab49-120">Implementar um EventSource</span><span class="sxs-lookup"><span data-stu-id="2ab49-120">Implement an EventSource</span></span>

<span data-ttu-id="2ab49-121">Para eventos que ocorrem a cada poucos milissegundos, você desejará que a sobrecarga por evento seja baixa (menos de um milissegundo).</span><span class="sxs-lookup"><span data-stu-id="2ab49-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="2ab49-122">Caso contrário, o impacto no desempenho será significativo.</span><span class="sxs-lookup"><span data-stu-id="2ab49-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="2ab49-123">O registro em log de um evento significa que você vai escrever algo em disco.</span><span class="sxs-lookup"><span data-stu-id="2ab49-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="2ab49-124">Se o disco não for rápido o suficiente, você perderá eventos.</span><span class="sxs-lookup"><span data-stu-id="2ab49-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="2ab49-125">Você precisa de uma solução diferente de registrar o evento em si.</span><span class="sxs-lookup"><span data-stu-id="2ab49-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="2ab49-126">Ao lidar com um grande número de eventos, conhecer a medida por evento também não é útil.</span><span class="sxs-lookup"><span data-stu-id="2ab49-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="2ab49-127">Na maioria das vezes, tudo o que você precisa é de apenas algumas estatísticas.</span><span class="sxs-lookup"><span data-stu-id="2ab49-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="2ab49-128">Portanto, você pode obter as estatísticas dentro do próprio processo e, em seguida, escrever um evento uma vez em um momento para relatar as estatísticas, o que <xref:System.Diagnostics.Tracing.EventCounter> fará.</span><span class="sxs-lookup"><span data-stu-id="2ab49-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="2ab49-129">Veja abaixo um exemplo de como implementar um <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2ab49-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="2ab49-130">Crie um novo arquivo chamado *MinimalEventCounterSource.cs* e use o trecho de código como sua fonte:</span><span class="sxs-lookup"><span data-stu-id="2ab49-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="2ab49-131">A <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> linha é a <xref:System.Diagnostics.Tracing.EventSource> parte e não faz parte do <xref:System.Diagnostics.Tracing.EventCounter> , ela foi escrita para mostrar que você pode registrar uma mensagem junto com o contador de eventos.</span><span class="sxs-lookup"><span data-stu-id="2ab49-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="2ab49-132">Adicionar um filtro de ação</span><span class="sxs-lookup"><span data-stu-id="2ab49-132">Add an action filter</span></span>

<span data-ttu-id="2ab49-133">O código-fonte de exemplo é um projeto ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ab49-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="2ab49-134">Você pode adicionar um [filtro de ação](/aspnet/core/mvc/controllers/filters#action-filters) globalmente, que registrará o tempo total de solicitação.</span><span class="sxs-lookup"><span data-stu-id="2ab49-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="2ab49-135">Crie um novo arquivo chamado *LogRequestTimeFilterAttribute.cs*e use o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2ab49-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="2ab49-136">O filtro de ação inicia a <xref:System.Diagnostics.Stopwatch> à medida que a solicitação começa e para quando ela é concluída, capturando o tempo decorrido.</span><span class="sxs-lookup"><span data-stu-id="2ab49-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="2ab49-137">O total de milissegundos é registrado na `MinimalEventCounterSource` instância singleton.</span><span class="sxs-lookup"><span data-stu-id="2ab49-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="2ab49-138">Para que esse filtro seja aplicado, você precisa adicioná-lo à coleção de filtros.</span><span class="sxs-lookup"><span data-stu-id="2ab49-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="2ab49-139">No arquivo *Startup.cs* , atualize o `ConfigureServices` método em incluir este filtro.</span><span class="sxs-lookup"><span data-stu-id="2ab49-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="2ab49-140">Monitorar contador de eventos</span><span class="sxs-lookup"><span data-stu-id="2ab49-140">Monitor event counter</span></span>

<span data-ttu-id="2ab49-141">Com a implementação em um <xref:System.Diagnostics.Tracing.EventSource> e o filtro de ação personalizada, compile e inicie o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2ab49-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="2ab49-142">Você registrou a métrica no <xref:System.Diagnostics.Tracing.EventCounter> , mas, a menos que você acesse as estatísticas de dele, isso não é útil.</span><span class="sxs-lookup"><span data-stu-id="2ab49-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="2ab49-143">Para obter as estatísticas, você precisa habilitar o <xref:System.Diagnostics.Tracing.EventCounter> criando um temporizador que é acionado sempre que você deseja os eventos, bem como um ouvinte para capturar os eventos.</span><span class="sxs-lookup"><span data-stu-id="2ab49-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="2ab49-144">Para fazer isso, você pode usar o [dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="2ab49-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="2ab49-145">Use o comando [dotnet-Counters PS](dotnet-counters.md#dotnet-counters-ps) para exibir uma lista de processos .NET que podem ser monitorados.</span><span class="sxs-lookup"><span data-stu-id="2ab49-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="2ab49-146">Usando o identificador de processo da saída do `dotnet-counters ps` comando, você pode começar a monitorar o contador de eventos com o seguinte `dotnet-counters monitor` comando:</span><span class="sxs-lookup"><span data-stu-id="2ab49-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="2ab49-147">Enquanto o `dotnet-counters monitor` comando estiver em execução, mantenha <kbd>F5</kbd> no navegador para começar a emitir solicitações contínuas para o `https://localhost:5001/api/values` ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2ab49-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="2ab49-148">Depois de alguns segundos, pare pressionando <kbd>q</kbd></span><span class="sxs-lookup"><span data-stu-id="2ab49-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="2ab49-149">O `dotnet-counters monitor` comando é ótimo para o monitoramento ativo.</span><span class="sxs-lookup"><span data-stu-id="2ab49-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="2ab49-150">No entanto, talvez você queira coletar essas métricas de diagnóstico para o pós-processamento e a análise.</span><span class="sxs-lookup"><span data-stu-id="2ab49-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="2ab49-151">Para isso, use o `dotnet-counters collect` comando.</span><span class="sxs-lookup"><span data-stu-id="2ab49-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="2ab49-152">O `collect` comando switch é semelhante ao `monitor` comando, mas aceita alguns parâmetros adicionais.</span><span class="sxs-lookup"><span data-stu-id="2ab49-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="2ab49-153">Você pode especificar o nome e o formato do arquivo de saída desejado.</span><span class="sxs-lookup"><span data-stu-id="2ab49-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="2ab49-154">Para um arquivo JSON chamado *diagnostics.jsem* use o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="2ab49-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="2ab49-155">Novamente, enquanto o comando estiver em execução, mantenha <kbd>F5</kbd> no navegador para começar a emitir solicitações contínuas para o `https://localhost:5001/api/values` ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="2ab49-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="2ab49-156">Depois de alguns segundos, pare pressionando <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="2ab49-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="2ab49-157">O *diagnostics.jsno* arquivo é gravado.</span><span class="sxs-lookup"><span data-stu-id="2ab49-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="2ab49-158">No entanto, o arquivo JSON que é gravado não é recuado; para facilitar a leitura, ele é recuado aqui.</span><span class="sxs-lookup"><span data-stu-id="2ab49-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="2ab49-159">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="2ab49-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ab49-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="2ab49-160">EventCounters</span></span>](event-counters.md)
