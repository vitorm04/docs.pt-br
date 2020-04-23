---
title: Registrando em log com o SDK do Azure para .NET
description: Saiba como habilitar o registro em log com o SDK do Azure para bibliotecas de cliente .NET
ms.date: 03/20/2020
ms.custom: azure-sdk-dotnet
ms.author: casoper
author: camsoper
ms.openlocfilehash: b277045a60ef5cc065d77dad84878872dedc963e
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "82071986"
---
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="d29c7-103">Registrando em log com o SDK do Azure para .NET</span><span class="sxs-lookup"><span data-stu-id="d29c7-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="d29c7-104">As bibliotecas de cliente do [SDK do Azure](https://azure.microsoft.com/downloads/) para .net incluem a capacidade de registrar as operações da biblioteca de cliente.</span><span class="sxs-lookup"><span data-stu-id="d29c7-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="d29c7-105">Isso permite que você monitore as solicitações e respostas de e/s que as bibliotecas de cliente estão fazendo para os serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="d29c7-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="d29c7-106">Normalmente, os logs são usados para depurar ou diagnosticar problemas de comunicação.</span><span class="sxs-lookup"><span data-stu-id="d29c7-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="d29c7-107">Este artigo descreve três abordagens para habilitar o registro em log com o SDK do Azure para .NET:</span><span class="sxs-lookup"><span data-stu-id="d29c7-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="d29c7-108">Registrar na janela do console</span><span class="sxs-lookup"><span data-stu-id="d29c7-108">Log to the console window</span></span>
- <span data-ttu-id="d29c7-109">Log para rastreamentos de diagnóstico do .NET</span><span class="sxs-lookup"><span data-stu-id="d29c7-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="d29c7-110">Configurar log personalizado</span><span class="sxs-lookup"><span data-stu-id="d29c7-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d29c7-111">Este artigo se aplica a bibliotecas de cliente que usam as versões mais recentes do SDK do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="d29c7-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="d29c7-112">Para ver se há suporte para uma biblioteca, consulte a lista de [versões mais recentes do SDK do Azure](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="d29c7-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="d29c7-113">Se seu aplicativo estiver usando uma versão mais antiga das bibliotecas de cliente do SDK do Azure, consulte as instruções específicas na documentação do serviço aplicável.</span><span class="sxs-lookup"><span data-stu-id="d29c7-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="d29c7-114">Informações do log</span><span class="sxs-lookup"><span data-stu-id="d29c7-114">Log information</span></span>

<span data-ttu-id="d29c7-115">O SDK registra as informações a seguir, corrigindo a consulta de parâmetro e os valores de cabeçalho para remover dados pessoais.</span><span class="sxs-lookup"><span data-stu-id="d29c7-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="d29c7-116">Entrada do log de solicitação HTTP:</span><span class="sxs-lookup"><span data-stu-id="d29c7-116">HTTP request log entry:</span></span>

- <span data-ttu-id="d29c7-117">ID Exclusiva</span><span class="sxs-lookup"><span data-stu-id="d29c7-117">Unique ID</span></span>
- <span data-ttu-id="d29c7-118">Método HTTP</span><span class="sxs-lookup"><span data-stu-id="d29c7-118">HTTP method</span></span>
- <span data-ttu-id="d29c7-119">URI</span><span class="sxs-lookup"><span data-stu-id="d29c7-119">URI</span></span>
- <span data-ttu-id="d29c7-120">Cabeçalhos de solicitação de saída</span><span class="sxs-lookup"><span data-stu-id="d29c7-120">Outgoing request headers</span></span>

<span data-ttu-id="d29c7-121">Entrada do log de resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="d29c7-121">HTTP response log entry:</span></span>

- <span data-ttu-id="d29c7-122">Duração da operação de e/s (tempo decorrido)</span><span class="sxs-lookup"><span data-stu-id="d29c7-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="d29c7-123">ID de solicitação</span><span class="sxs-lookup"><span data-stu-id="d29c7-123">Request ID</span></span>
- <span data-ttu-id="d29c7-124">Código de status HTTP</span><span class="sxs-lookup"><span data-stu-id="d29c7-124">HTTP status code</span></span>
- <span data-ttu-id="d29c7-125">Frase de motivo HTTP</span><span class="sxs-lookup"><span data-stu-id="d29c7-125">HTTP reason phrase</span></span>
- <span data-ttu-id="d29c7-126">Cabeçalhos de resposta</span><span class="sxs-lookup"><span data-stu-id="d29c7-126">Response headers</span></span>
- <span data-ttu-id="d29c7-127">Informações de erro, quando aplicável</span><span class="sxs-lookup"><span data-stu-id="d29c7-127">Error information, when applicable</span></span>

<span data-ttu-id="d29c7-128">Para conteúdo de solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="d29c7-128">For request and response content:</span></span>

- <span data-ttu-id="d29c7-129">Fluxo de conteúdo como texto ou bytes, dependendo do cabeçalho Content-Type.</span><span class="sxs-lookup"><span data-stu-id="d29c7-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="d29c7-130">[! Observação} o log de conteúdo está desabilitado por padrão.</span><span class="sxs-lookup"><span data-stu-id="d29c7-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="d29c7-131">Para habilitá-lo `Diagnostics.IsLoggingContentEnabled` , `true` defina `ClientOptions`como em.</span><span class="sxs-lookup"><span data-stu-id="d29c7-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="d29c7-132">Os logs de eventos são gerados normalmente em um desses três níveis:</span><span class="sxs-lookup"><span data-stu-id="d29c7-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="d29c7-133">Informações para eventos de solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="d29c7-133">Informational for request and response events</span></span>
- <span data-ttu-id="d29c7-134">Aviso de erros</span><span class="sxs-lookup"><span data-stu-id="d29c7-134">Warning for errors</span></span>
- <span data-ttu-id="d29c7-135">Detalhado para mensagens detalhadas e log de conteúdo</span><span class="sxs-lookup"><span data-stu-id="d29c7-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="d29c7-136">Habilitar o registro em log com métodos internos</span><span class="sxs-lookup"><span data-stu-id="d29c7-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="d29c7-137">O SDK do Azure para bibliotecas de cliente .net registra eventos no rastreamento de eventos para Windows (ETW) por meio da [ `EventSource` classe](/dotnet/api/system.diagnostics.tracing.eventsource), que é típica para .net.</span><span class="sxs-lookup"><span data-stu-id="d29c7-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="d29c7-138">As fontes de eventos permitem que você use o registro em log estruturado em seu código de aplicativo com uma sobrecarga mínima de desempenho.</span><span class="sxs-lookup"><span data-stu-id="d29c7-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="d29c7-139">Para obter acesso a esses logs de eventos, você precisa registrar ouvintes de eventos.</span><span class="sxs-lookup"><span data-stu-id="d29c7-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="d29c7-140">O SDK inclui a `Azure.Core.Diagnostics.AzureEventSourceListener` classe (definida no pacote NuGet do Azure. Core), que contém dois métodos estáticos que simplificam o registro em log abrangente `CreateConsoleLogger` para `CreateTraceLogger`seu aplicativo .net: e.</span><span class="sxs-lookup"><span data-stu-id="d29c7-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="d29c7-141">Esses métodos usam um parâmetro opcional que especifica um nível de log.</span><span class="sxs-lookup"><span data-stu-id="d29c7-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="d29c7-142">Registrar na janela do console</span><span class="sxs-lookup"><span data-stu-id="d29c7-142">Log to the console window</span></span>

<span data-ttu-id="d29c7-143">Uma filosofia principal do SDK do Azure para bibliotecas de cliente .NET é simplificar a capacidade de exibir logs abrangentes em tempo real.</span><span class="sxs-lookup"><span data-stu-id="d29c7-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="d29c7-144">O `CreateConsoleLogger` método permite que você envie logs para a janela do console com uma única linha de código:</span><span class="sxs-lookup"><span data-stu-id="d29c7-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="d29c7-145">Log para rastreamentos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="d29c7-145">Log to diagnostic traces</span></span>

<span data-ttu-id="d29c7-146">Se você implementar os ouvintes de rastreamento, poderá usar `CreateTraceLogger` o método para fazer logon no mecanismo de rastreamento de eventos[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)do .NET padrão ().</span><span class="sxs-lookup"><span data-stu-id="d29c7-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="d29c7-147">Para obter mais informações sobre o rastreamento de eventos no .NET, consulte [ouvintes de rastreamento](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span><span class="sxs-lookup"><span data-stu-id="d29c7-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="d29c7-148">Este exemplo especifica um nível de log detalhado:</span><span class="sxs-lookup"><span data-stu-id="d29c7-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="d29c7-149">Configurar log personalizado</span><span class="sxs-lookup"><span data-stu-id="d29c7-149">Configure custom logging</span></span>

<span data-ttu-id="d29c7-150">Conforme mencionado acima, você precisa registrar ouvintes de eventos para receber mensagens de log do SDK do Azure para .NET.</span><span class="sxs-lookup"><span data-stu-id="d29c7-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="d29c7-151">Se você não quiser implementar o log abrangente usando um dos métodos simplificados acima, poderá construir uma instância da `AzureEventSourceListener` classe e passá-la para uma função de retorno de chamada que você escreve.</span><span class="sxs-lookup"><span data-stu-id="d29c7-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="d29c7-152">Esse método receberá mensagens de log que você pode processar, mas é necessário.</span><span class="sxs-lookup"><span data-stu-id="d29c7-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="d29c7-153">Além disso, ao construir a instância, você pode especificar os níveis de log a serem incluídos.</span><span class="sxs-lookup"><span data-stu-id="d29c7-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="d29c7-154">O exemplo a seguir cria um ouvinte de eventos que faz logon no console com uma mensagem personalizada e é filtrado para os eventos principais do Azure do nível detalhado.</span><span class="sxs-lookup"><span data-stu-id="d29c7-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

```csharp
using AzureEventSourceListener listener = new AzureEventSourceListener((e, message) =>
    {
        // Only log messages from Azure-Core event source
        if (e.EventSource.Name == "Azure-Core")
        {
            Console.WriteLine($"{DateTime.Now} {message}");
        }
    },
    level: EventLevel.Verbose);
```

## <a name="next-steps"></a><span data-ttu-id="d29c7-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d29c7-155">Next steps</span></span>

- [<span data-ttu-id="d29c7-156">Habilitar o log de diagnóstico para aplicativos no serviço Azure App</span><span class="sxs-lookup"><span data-stu-id="d29c7-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="d29c7-157">Examinar o [log de segurança do Azure e as opções de auditoria](https://docs.microsoft.com/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="d29c7-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="d29c7-158">Saiba como trabalhar com [os logs da plataforma Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="d29c7-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="d29c7-159">Leia mais sobre [rastreamento e log do .NET Core](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="d29c7-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
