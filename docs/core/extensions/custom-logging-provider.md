---
title: Implementar um provedor de log personalizado no .NET
description: Saiba como implementar um provedor de log personalizado em seus aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.topic: how-to
ms.openlocfilehash: 3a0af6296c2ade15ff1b75dce5a5f99bfe235ebf
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614670"
---
# <a name="implement-a-custom-logging-provider-in-net"></a><span data-ttu-id="1d1e7-103">Implementar um provedor de log personalizado no .NET</span><span class="sxs-lookup"><span data-stu-id="1d1e7-103">Implement a custom logging provider in .NET</span></span>

<span data-ttu-id="1d1e7-104">Há muitos [provedores de log](logging-providers.md) disponíveis para necessidades de log comuns.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-104">There are many [logging providers](logging-providers.md) available for common logging needs.</span></span> <span data-ttu-id="1d1e7-105">Talvez seja necessário implementar um personalizado <xref:Microsoft.Extensions.Logging.ILoggerProvider> quando um dos provedores disponíveis não atender às suas necessidades de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-105">You may need to implement a custom <xref:Microsoft.Extensions.Logging.ILoggerProvider> when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="1d1e7-106">Neste artigo, você aprenderá a implementar um provedor de log personalizado que pode ser usado para colorir logs no console do.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-106">In this article, you'll learn how to implement a custom logging provider that can be used to colorize logs in the console.</span></span>

### <a name="sample-custom-logger-configuration"></a><span data-ttu-id="1d1e7-107">Configuração de agente de log personalizado de exemplo</span><span class="sxs-lookup"><span data-stu-id="1d1e7-107">Sample custom logger configuration</span></span>

<span data-ttu-id="1d1e7-108">O exemplo cria entradas de console de cores diferentes por nível de log e ID de evento usando o seguinte tipo de configuração:</span><span class="sxs-lookup"><span data-stu-id="1d1e7-108">The sample creates different color console entries per log level and event ID using the following configuration type:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerConfiguration.cs":::

<span data-ttu-id="1d1e7-109">O código anterior define o nível padrão como `Information` , a cor para `Green` e o `EventId` é implicitamente `0` .</span><span class="sxs-lookup"><span data-stu-id="1d1e7-109">The preceding code sets the default level to `Information`, the color to `Green`, and the `EventId` is implicitly `0`.</span></span>

### <a name="create-the-custom-logger"></a><span data-ttu-id="1d1e7-110">Criar o agente de log personalizado</span><span class="sxs-lookup"><span data-stu-id="1d1e7-110">Create the custom logger</span></span>

<span data-ttu-id="1d1e7-111">O `ILogger` nome da categoria de implementação normalmente é a origem do log.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-111">The `ILogger` implementation category name is typically the logging source.</span></span> <span data-ttu-id="1d1e7-112">Por exemplo, o tipo em que o agente é criado:</span><span class="sxs-lookup"><span data-stu-id="1d1e7-112">For example, the type where the logger is created:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs":::

<span data-ttu-id="1d1e7-113">O código anterior:</span><span class="sxs-lookup"><span data-stu-id="1d1e7-113">The preceding code:</span></span>

- <span data-ttu-id="1d1e7-114">Cria uma instância de agente por nome de categoria.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-114">Creates a logger instance per category name.</span></span>
- <span data-ttu-id="1d1e7-115">Faz `logLevel == _config.LogLevel` o check-in `IsEnabled` , de modo que cada `logLevel` um tem um agente exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-115">Checks `logLevel == _config.LogLevel` in `IsEnabled`, so each `logLevel` has a unique logger.</span></span> <span data-ttu-id="1d1e7-116">Os agentes também devem ser habilitados para todos os níveis de log mais altos:</span><span class="sxs-lookup"><span data-stu-id="1d1e7-116">Loggers should also be enabled for all higher log levels:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLogger.cs" range="16-17":::

## <a name="custom-logger-provider"></a><span data-ttu-id="1d1e7-117">Provedor de agente personalizado</span><span class="sxs-lookup"><span data-stu-id="1d1e7-117">Custom logger provider</span></span>

<span data-ttu-id="1d1e7-118">O `ILoggerProvider` objeto é responsável pela criação de instâncias de agente.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-118">The `ILoggerProvider` object is responsible for creating logger instances.</span></span> <span data-ttu-id="1d1e7-119">Talvez não seja necessário criar uma instância de agente por categoria, mas isso faz sentido para alguns agentes, como NLog ou log4net.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-119">Maybe it is not needed to create a logger instance per category, but this makes sense for some loggers, like NLog or log4net.</span></span> <span data-ttu-id="1d1e7-120">Fazendo isso, você também pode escolher destinos de saída de log diferentes por categoria, se necessário:</span><span class="sxs-lookup"><span data-stu-id="1d1e7-120">Doing this you are also able to choose different logging output targets per category if needed:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/ColorConsoleLoggerProvider.cs":::

<span data-ttu-id="1d1e7-121">No código anterior, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> cria uma única instância do `ColorConsoleLogger` nome por categoria e a armazena no [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2) .</span><span class="sxs-lookup"><span data-stu-id="1d1e7-121">In the preceding code, <xref:Microsoft.Build.Logging.LoggerDescription.CreateLogger%2A> creates a single instance of the `ColorConsoleLogger` per category name and stores it in the [`ConcurrentDictionary<TKey,TValue>`](/dotnet/api/system.collections.concurrent.concurrentdictionary-2).</span></span>

## <a name="usage-and-registration-of-the-custom-logger"></a><span data-ttu-id="1d1e7-122">Uso e registro do agente de log personalizado</span><span class="sxs-lookup"><span data-stu-id="1d1e7-122">Usage and registration of the custom logger</span></span>

<span data-ttu-id="1d1e7-123">Para adicionar o provedor de log personalizado e o agente correspondente, adicione um <xref:Microsoft.Extensions.Logging.ILoggerProvider> com <xref:Microsoft.Extensions.Logging.ILoggingBuilder> do <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="1d1e7-123">To add the custom logging provider and corresponding logger, add an <xref:Microsoft.Extensions.Logging.ILoggerProvider> with <xref:Microsoft.Extensions.Logging.ILoggingBuilder> from the <xref:Microsoft.Extensions.Hosting.HostingHostBuilderExtensions.ConfigureLogging(Microsoft.Extensions.Hosting.IHostBuilder,System.Action{Microsoft.Extensions.Logging.ILoggingBuilder})?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Program.cs" range="23-39":::

<span data-ttu-id="1d1e7-124">O `ILoggingBuilder` cria uma ou mais `ILogger` instâncias.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-124">The `ILoggingBuilder` creates one or more `ILogger` instances.</span></span> <span data-ttu-id="1d1e7-125">As `ILogger` instâncias são usadas pelo Framework para registrar as informações.</span><span class="sxs-lookup"><span data-stu-id="1d1e7-125">The `ILogger` instances are used by the framework to log the information.</span></span>

<span data-ttu-id="1d1e7-126">Para o código anterior, forneça pelo menos um método de extensão para `ILoggerFactory` :</span><span class="sxs-lookup"><span data-stu-id="1d1e7-126">For the preceding code, provide at least one extension method for the `ILoggerFactory`:</span></span>

:::code language="csharp" source="snippets/configuration/console-custom-logging/Extensions/ColorConsoleLoggerExtensions.cs":::

<span data-ttu-id="1d1e7-127">A execução desse aplicativo simples será processada da seguinte janela do console:</span><span class="sxs-lookup"><span data-stu-id="1d1e7-127">Running this simple application will render similar to the following console window:</span></span>

:::image type="content" source="media/color-console-logger.png" alt-text="Saída de exemplo de agente do console de cores":::

## <a name="see-also"></a><span data-ttu-id="1d1e7-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="1d1e7-129">See also</span></span>

- <span data-ttu-id="1d1e7-130">[Registro em log no .net](logging.md).</span><span class="sxs-lookup"><span data-stu-id="1d1e7-130">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="1d1e7-131">[Provedores de log no .net](logging-providers.md).</span><span class="sxs-lookup"><span data-stu-id="1d1e7-131">[Logging providers in .NET](logging-providers.md).</span></span>
- <span data-ttu-id="1d1e7-132">[Registro em log de alto desempenho no .net](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="1d1e7-132">[High-performance logging in .NET](high-performance-logging.md).</span></span>
