---
title: Faça login com o Azure SDK para .NET
description: Saiba como ativar o registro com o Azure SDK para bibliotecas de clientes .NET
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
# <a name="logging-with-the-azure-sdk-for-net"></a><span data-ttu-id="ba8b3-103">Faça login com o Azure SDK para .NET</span><span class="sxs-lookup"><span data-stu-id="ba8b3-103">Logging with the Azure SDK for .NET</span></span>

<span data-ttu-id="ba8b3-104">O [Azure SDK](https://azure.microsoft.com/downloads/) para bibliotecas de clientes .NET inclui a capacidade de registrar operações de biblioteca de clientes.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-104">The [Azure SDK](https://azure.microsoft.com/downloads/) for .NET client libraries includes the ability to log client library operations.</span></span> <span data-ttu-id="ba8b3-105">Isso permite monitorar solicitações e respostas de I/O que as bibliotecas de clientes estão fazendo aos serviços do Azure.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-105">This allows you to monitor I/O requests and responses that client libraries are making to Azure services.</span></span> <span data-ttu-id="ba8b3-106">Normalmente, os registros são usados para depurar ou diagnosticar problemas de comunicação.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-106">Typically, the logs are used to debug or diagnose communication issues.</span></span> <span data-ttu-id="ba8b3-107">Este artigo descreve três abordagens para permitir o registro com o Azure SDK para .NET:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-107">This article describes three approaches to enable logging with the Azure SDK for .NET:</span></span>

- <span data-ttu-id="ba8b3-108">Faça login na janela do console</span><span class="sxs-lookup"><span data-stu-id="ba8b3-108">Log to the console window</span></span>
- <span data-ttu-id="ba8b3-109">Faça log a rastreamentos de diagnóstico .NET</span><span class="sxs-lookup"><span data-stu-id="ba8b3-109">Log to .NET diagnostics traces</span></span>
- <span data-ttu-id="ba8b3-110">Configurar o registro personalizado</span><span class="sxs-lookup"><span data-stu-id="ba8b3-110">Configure custom logging</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ba8b3-111">Este artigo se aplica a bibliotecas de clientes que usam as versões mais recentes do Azure SDK para .NET.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-111">This article applies to client libraries that use the most recent versions of the Azure SDK for .NET.</span></span> <span data-ttu-id="ba8b3-112">Para ver se uma biblioteca é suportada, consulte a lista de [versões mais recentes do Azure SDK](https://azure.github.io/azure-sdk/releases/latest/index.html).</span><span class="sxs-lookup"><span data-stu-id="ba8b3-112">To see if a library is supported, refer to the list of [Azure SDK latest releases](https://azure.github.io/azure-sdk/releases/latest/index.html).</span></span> <span data-ttu-id="ba8b3-113">Se o seu aplicativo estiver usando uma versão mais antiga das bibliotecas clientes Do Azure SDK, consulte instruções específicas na documentação de serviço aplicável.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-113">If your application is using an older version of the Azure SDK client libraries, refer to specific instructions in the applicable service documentation.</span></span>

## <a name="log-information"></a><span data-ttu-id="ba8b3-114">Informações do log</span><span class="sxs-lookup"><span data-stu-id="ba8b3-114">Log information</span></span>

<span data-ttu-id="ba8b3-115">O SDK registra as seguintes informações, higienizando a consulta do parâmetro e os valores do cabeçalho para remover dados pessoais.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-115">The SDK logs the following information, sanitizing parameter query and header values to remove personal data.</span></span>

<span data-ttu-id="ba8b3-116">Entrada de log de solicitação HTTP:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-116">HTTP request log entry:</span></span>

- <span data-ttu-id="ba8b3-117">ID Exclusiva</span><span class="sxs-lookup"><span data-stu-id="ba8b3-117">Unique ID</span></span>
- <span data-ttu-id="ba8b3-118">Método HTTP</span><span class="sxs-lookup"><span data-stu-id="ba8b3-118">HTTP method</span></span>
- <span data-ttu-id="ba8b3-119">URI</span><span class="sxs-lookup"><span data-stu-id="ba8b3-119">URI</span></span>
- <span data-ttu-id="ba8b3-120">Cabeçalhos de solicitação de saída</span><span class="sxs-lookup"><span data-stu-id="ba8b3-120">Outgoing request headers</span></span>

<span data-ttu-id="ba8b3-121">Entrada do registro de resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-121">HTTP response log entry:</span></span>

- <span data-ttu-id="ba8b3-122">Duração da operação de I/O (tempo decorrido)</span><span class="sxs-lookup"><span data-stu-id="ba8b3-122">Duration of I/O operation (time elapsed)</span></span>
- <span data-ttu-id="ba8b3-123">ID de solicitação</span><span class="sxs-lookup"><span data-stu-id="ba8b3-123">Request ID</span></span>
- <span data-ttu-id="ba8b3-124">Código de status HTTP</span><span class="sxs-lookup"><span data-stu-id="ba8b3-124">HTTP status code</span></span>
- <span data-ttu-id="ba8b3-125">Frase de razão HTTP</span><span class="sxs-lookup"><span data-stu-id="ba8b3-125">HTTP reason phrase</span></span>
- <span data-ttu-id="ba8b3-126">Cabeçalhos de resposta</span><span class="sxs-lookup"><span data-stu-id="ba8b3-126">Response headers</span></span>
- <span data-ttu-id="ba8b3-127">Informações de erro, quando aplicável</span><span class="sxs-lookup"><span data-stu-id="ba8b3-127">Error information, when applicable</span></span>

<span data-ttu-id="ba8b3-128">Para conteúdo de solicitação e resposta:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-128">For request and response content:</span></span>

- <span data-ttu-id="ba8b3-129">Fluxo de conteúdo como texto ou bytes, dependendo do cabeçalho tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-129">Content stream as text or bytes depending on the Content-Type header.</span></span>
     > <span data-ttu-id="ba8b3-130">[! NOTA} O registro de conteúdo é desativado por padrão.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-130">[!NOTE} Content logging is disabled by default.</span></span> <span data-ttu-id="ba8b3-131">Para habilitá-lo, configurado `Diagnostics.IsLoggingContentEnabled` para `true` dentro `ClientOptions`.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-131">To enable it, set `Diagnostics.IsLoggingContentEnabled` to `true` in `ClientOptions`.</span></span>

<span data-ttu-id="ba8b3-132">Os registros de eventos são de saída geralmente em um desses três níveis:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-132">Event logs are output usually at one of these three levels:</span></span>

- <span data-ttu-id="ba8b3-133">Informativo para eventos de solicitação e resposta</span><span class="sxs-lookup"><span data-stu-id="ba8b3-133">Informational for request and response events</span></span>
- <span data-ttu-id="ba8b3-134">Aviso para erros</span><span class="sxs-lookup"><span data-stu-id="ba8b3-134">Warning for errors</span></span>
- <span data-ttu-id="ba8b3-135">Verbose para mensagens detalhadas e registro de conteúdo</span><span class="sxs-lookup"><span data-stu-id="ba8b3-135">Verbose for detailed messages and content logging</span></span>

## <a name="enable-logging-with-built-in-methods"></a><span data-ttu-id="ba8b3-136">Habilite o registro com métodos incorporados</span><span class="sxs-lookup"><span data-stu-id="ba8b3-136">Enable logging with built-in methods</span></span>

<span data-ttu-id="ba8b3-137">O Azure SDK for .NET client libraryes registra eventos para ETW (Event Tracing for Windows) via [ `EventSource` classe](/dotnet/api/system.diagnostics.tracing.eventsource), o que é típico de .NET.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-137">The Azure SDK for .NET client libraries log events to Event Tracing for Windows (ETW) via the [`EventSource` class](/dotnet/api/system.diagnostics.tracing.eventsource), which is typical for .NET.</span></span> <span data-ttu-id="ba8b3-138">As fontes de eventos permitem que você use login estruturado no código do aplicativo com uma sobrecarga mínima de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-138">Event sources allow you to use structured logging in your application code with a minimal performance overhead.</span></span> <span data-ttu-id="ba8b3-139">Para ter acesso a esses registros de eventos, você precisa registrar ouvintes de eventos.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-139">To gain access to these event logs, you need to register event listeners.</span></span>

<span data-ttu-id="ba8b3-140">O SDK inclui `Azure.Core.Diagnostics.AzureEventSourceListener` a classe (definida no pacote Azure.Core NuGet), que contém dois métodos `CreateConsoleLogger` `CreateTraceLogger`estáticos que simplificam o registro abrangente para o seu aplicativo .NET: e .</span><span class="sxs-lookup"><span data-stu-id="ba8b3-140">The SDK includes the `Azure.Core.Diagnostics.AzureEventSourceListener` class (defined in the Azure.Core NuGet package), which contains two static methods that simplify comprehensive logging for your .NET application: `CreateConsoleLogger` and `CreateTraceLogger`.</span></span> <span data-ttu-id="ba8b3-141">Esses métodos tomam um parâmetro opcional que especifica um nível de registro.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-141">These methods take an optional parameter that specifies a log level.</span></span>

### <a name="log-to-the-console-window"></a><span data-ttu-id="ba8b3-142">Faça login na janela do console</span><span class="sxs-lookup"><span data-stu-id="ba8b3-142">Log to the console window</span></span>

<span data-ttu-id="ba8b3-143">Um princípio central do Azure SDK para bibliotecas de clientes .NET é simplificar a capacidade de visualizar logs abrangentes em tempo real.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-143">A core tenet of the Azure SDK for .NET client libraries is to simplify the ability to view comprehensive logs in real time.</span></span> <span data-ttu-id="ba8b3-144">O `CreateConsoleLogger` método permite enviar logs para a janela do console com uma única linha de código:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-144">The `CreateConsoleLogger` method allows you to send logs to the console window with a single line of code:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateConsoleLogger();
```

### <a name="log-to-diagnostic-traces"></a><span data-ttu-id="ba8b3-145">Log para rastreamentos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ba8b3-145">Log to diagnostic traces</span></span>

<span data-ttu-id="ba8b3-146">Se você implementar ouvintes de `CreateTraceLogger` rastreamento, poderá usar o método para[`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)registrar o mecanismo padrão de rastreamento de eventos .NET ().</span><span class="sxs-lookup"><span data-stu-id="ba8b3-146">If you implement trace listeners, you can use the `CreateTraceLogger` method to log to the standard .NET event tracing mechanism ([`System.Diagnostics.Tracing`](https://docs.microsoft.com/dotnet/api/system.diagnostics.tracing)).</span></span> <span data-ttu-id="ba8b3-147">Para obter mais informações sobre o rastreamento de eventos em .NET, consulte [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span><span class="sxs-lookup"><span data-stu-id="ba8b3-147">For more information on event tracing in .NET, see [Trace Listeners](https://docs.microsoft.com/dotnet/framework/debug-trace-profile/trace-listeners).</span></span> <span data-ttu-id="ba8b3-148">Este exemplo especifica um nível de log de verbose:</span><span class="sxs-lookup"><span data-stu-id="ba8b3-148">This example specifies a log level of verbose:</span></span>

```csharp
using AzureEventSourceListener listener = AzureEventSourceListener.CreateTraceLogger(EventLevel.Verbose);
```

## <a name="configure-custom-logging"></a><span data-ttu-id="ba8b3-149">Configurar o registro personalizado</span><span class="sxs-lookup"><span data-stu-id="ba8b3-149">Configure custom logging</span></span>

<span data-ttu-id="ba8b3-150">Como mencionado acima, você precisa registrar ouvintes de eventos para receber mensagens de log do Azure SDK para .NET.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-150">As mentioned above, you need to register event listeners to receive log messages from the Azure SDK for .NET.</span></span> <span data-ttu-id="ba8b3-151">Se você não quiser implementar um registro abrangente usando um dos métodos simplificados acima, você pode construir uma instância da classe e passar-lhe `AzureEventSourceListener` uma função de retorno de chamada que você escreve.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-151">If you don’t want to implement comprehensive logging using one the simplified methods above, you can construct an instance of the `AzureEventSourceListener` class and pass it a callback function that you write.</span></span> <span data-ttu-id="ba8b3-152">Este método receberá mensagens de registro que você pode processar como for necessário.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-152">This method will receive log messages that you can process however you need to.</span></span> <span data-ttu-id="ba8b3-153">Além disso, ao construir a instância, você pode especificar os níveis de registro a serem incluemos.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-153">In addition, when you construct the instance, you can specify the log levels to include.</span></span>

<span data-ttu-id="ba8b3-154">O exemplo a seguir cria um ouvinte de eventos que faz logon no console com uma mensagem personalizada e é filtrado para eventos principais do Azure do verbose de nível.</span><span class="sxs-lookup"><span data-stu-id="ba8b3-154">The following example creates an event listener that logs to the console with a custom message, and is filtered to Azure core events of the level verbose.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="ba8b3-155">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="ba8b3-155">Next steps</span></span>

- [<span data-ttu-id="ba8b3-156">Habilite o registro de diagnósticos para aplicativos no Azure App Service</span><span class="sxs-lookup"><span data-stu-id="ba8b3-156">Enable diagnostics logging for apps in Azure App Service</span></span>](https://docs.microsoft.com/azure/app-service/troubleshoot-diagnostic-logs)
- <span data-ttu-id="ba8b3-157">Revise as opções [de registro e auditoria de segurança do Azure](https://docs.microsoft.com/azure/security/fundamentals/log-audit)</span><span class="sxs-lookup"><span data-stu-id="ba8b3-157">Review [Azure security logging and auditing](https://docs.microsoft.com/azure/security/fundamentals/log-audit) options</span></span>
- <span data-ttu-id="ba8b3-158">Saiba como trabalhar com os logs da [plataforma Azure](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span><span class="sxs-lookup"><span data-stu-id="ba8b3-158">Learn how to work with [Azure platform logs](https://docs.microsoft.com/azure/azure-monitor/platform/platform-logs-overview)</span></span>
- <span data-ttu-id="ba8b3-159">Leia mais sobre [o registro e rastreamento do .NET Core](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span><span class="sxs-lookup"><span data-stu-id="ba8b3-159">Read more about [.NET Core logging and tracing](https://docs.microsoft.com/dotnet/core/diagnostics/logging-tracing)</span></span>
