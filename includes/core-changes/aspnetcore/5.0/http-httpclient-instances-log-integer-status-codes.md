---
ms.openlocfilehash: f1556fac0e8aa79c87cd5e74c1b603582ff5db1b
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160524"
---
### <a name="http-httpclient-instances-created-by-ihttpclientfactory-log-integer-status-codes"></a><span data-ttu-id="2ac8f-101">HTTP: instâncias de HttpClient criadas por códigos de status de inteiro de log IHttpClientFactory</span><span class="sxs-lookup"><span data-stu-id="2ac8f-101">HTTP: HttpClient instances created by IHttpClientFactory log integer status codes</span></span>

<span data-ttu-id="2ac8f-102"><xref:System.Net.Http.HttpClient> instâncias criadas por <xref:System.Net.Http.IHttpClientFactory> códigos de status HTTP de log como inteiros em vez de com nomes de código de status.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-102"><xref:System.Net.Http.HttpClient> instances created by <xref:System.Net.Http.IHttpClientFactory> log HTTP status codes as integers instead of with status code names.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ac8f-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2ac8f-103">Version introduced</span></span>

<span data-ttu-id="2ac8f-104">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="2ac8f-104">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2ac8f-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="2ac8f-105">Old behavior</span></span>

<span data-ttu-id="2ac8f-106">O registro em log usa as descrições textuais dos códigos de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-106">Logging uses the textual descriptions of HTTP status codes.</span></span> <span data-ttu-id="2ac8f-107">Considere as seguintes mensagens de log:</span><span class="sxs-lookup"><span data-stu-id="2ac8f-107">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - OK
End processing HTTP request after 70.0862ms - OK
```

#### <a name="new-behavior"></a><span data-ttu-id="2ac8f-108">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="2ac8f-108">New behavior</span></span>

<span data-ttu-id="2ac8f-109">O registro em log usa os valores inteiros dos códigos de status HTTP.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-109">Logging uses the integer values of HTTP status codes.</span></span> <span data-ttu-id="2ac8f-110">Considere as seguintes mensagens de log:</span><span class="sxs-lookup"><span data-stu-id="2ac8f-110">Consider the following log messages:</span></span>

```output
Received HTTP response after 56.0044ms - 200
End processing HTTP request after 70.0862ms - 200
```

#### <a name="reason-for-change"></a><span data-ttu-id="2ac8f-111">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="2ac8f-111">Reason for change</span></span>

<span data-ttu-id="2ac8f-112">O comportamento original desse log é inconsistente com outras partes do ASP.NET Core que sempre usaram valores inteiros.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-112">The original behavior of this logging is inconsistent with other parts of ASP.NET Core that have always used integer values.</span></span> <span data-ttu-id="2ac8f-113">A inconsistência torna os logs difíceis de consultar por meio de sistemas de registro estruturado, como [Elasticsearch](https://www.elastic.co/elasticsearch/).</span><span class="sxs-lookup"><span data-stu-id="2ac8f-113">The inconsistency makes logs difficult to query via structured logging systems such as [Elasticsearch](https://www.elastic.co/elasticsearch/).</span></span> <span data-ttu-id="2ac8f-114">Para obter mais contexto, consulte [dotnet/Extensions # 1549](https://github.com/dotnet/extensions/issues/1549).</span><span class="sxs-lookup"><span data-stu-id="2ac8f-114">For more context, see [dotnet/extensions#1549](https://github.com/dotnet/extensions/issues/1549).</span></span>

<span data-ttu-id="2ac8f-115">O uso de valores inteiros é mais flexível que o texto, pois permite consultas em intervalos de valores.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-115">Using integer values is more flexible than text because it allows queries on ranges of values.</span></span>

<span data-ttu-id="2ac8f-116">A adição de outro valor de log para capturar o código de status inteiro foi considerada.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-116">Adding another log value to capture the integer status code was considered.</span></span> <span data-ttu-id="2ac8f-117">Infelizmente, isso introduziria outra inconsistência com o restante do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-117">Unfortunately, doing so would introduce another inconsistency with the rest of ASP.NET Core.</span></span> <span data-ttu-id="2ac8f-118">O log de HttpClient e o servidor HTTP/log de hospedagem usam o mesmo `StatusCode` nome de chave já.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-118">HttpClient logging and HTTP server/hosting logging use the same `StatusCode` key name already.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ac8f-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2ac8f-119">Recommended action</span></span>

<span data-ttu-id="2ac8f-120">A melhor opção é atualizar as consultas de log para usar os valores inteiros de códigos de status.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-120">The best option is to update logging queries to use the integer values of status codes.</span></span> <span data-ttu-id="2ac8f-121">Essa opção pode causar alguma dificuldade para gravar consultas em várias versões de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-121">This option may cause some difficulty writing queries across multiple ASP.NET Core versions.</span></span> <span data-ttu-id="2ac8f-122">No entanto, o uso de inteiros para essa finalidade é muito mais flexível para consultar logs.</span><span class="sxs-lookup"><span data-stu-id="2ac8f-122">However, using integers for this purpose is much more flexible for querying logs.</span></span>

<span data-ttu-id="2ac8f-123">Se você precisar forçar a compatibilidade com o comportamento antigo e usar códigos de status textuais, substitua o `IHttpClientFactory` log pelo seu próprio:</span><span class="sxs-lookup"><span data-stu-id="2ac8f-123">If you need to force compatibility with the old behavior and use textual status codes, replace the `IHttpClientFactory` logging with your own:</span></span>

1. <span data-ttu-id="2ac8f-124">Copie as versões 3,1 do .NET Core das seguintes classes em seu projeto:</span><span class="sxs-lookup"><span data-stu-id="2ac8f-124">Copy the .NET Core 3.1 versions of the following classes into your project:</span></span>

    * [<span data-ttu-id="2ac8f-125">LoggingHttpMessageHandlerBuilderFilter</span><span class="sxs-lookup"><span data-stu-id="2ac8f-125">LoggingHttpMessageHandlerBuilderFilter</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandlerBuilderFilter.cs)
    * [<span data-ttu-id="2ac8f-126">LoggingHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="2ac8f-126">LoggingHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingHttpMessageHandler.cs)
    * [<span data-ttu-id="2ac8f-127">LoggingScopeHttpMessageHandler</span><span class="sxs-lookup"><span data-stu-id="2ac8f-127">LoggingScopeHttpMessageHandler</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/LoggingScopeHttpMessageHandler.cs)
    * [<span data-ttu-id="2ac8f-128">HttpHeadersLogValue</span><span class="sxs-lookup"><span data-stu-id="2ac8f-128">HttpHeadersLogValue</span></span>](https://github.com/dotnet/extensions/blob/release/3.1/src/HttpClientFactory/Http/src/Logging/HttpHeadersLogValue.cs)

1. <span data-ttu-id="2ac8f-129">Renomeie as classes para evitar conflitos com tipos públicos no pacote NuGet [Microsoft. Extensions. http](https://www.nuget.org/packages/Microsoft.Extensions.Http) .</span><span class="sxs-lookup"><span data-stu-id="2ac8f-129">Rename the classes to avoid conflicts with public types in the [Microsoft.Extensions.Http](https://www.nuget.org/packages/Microsoft.Extensions.Http) NuGet package.</span></span>

1. <span data-ttu-id="2ac8f-130">Substitua a implementação interna de `LoggingHttpMessageHandlerBuilderFilter` pela sua própria no método do projeto `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="2ac8f-130">Replace the built-in implementation of `LoggingHttpMessageHandlerBuilderFilter` with your own in the project's `Startup.ConfigureServices` method.</span></span> <span data-ttu-id="2ac8f-131">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="2ac8f-131">For example:</span></span>

    ```csharp
    public void ConfigureServices(IServiceCollection services)
    {
        // Other service registrations go first. Code omitted for brevity.

        // Place the following after all AddHttpClient registrations.
        services.RemoveAll<IHttpMessageHandlerBuilderFilter>();

        services.AddSingleton<IHttpMessageHandlerBuilderFilter,
                              MyLoggingHttpMessageHandlerBuilderFilter>();
    }
    ```

#### <a name="category"></a><span data-ttu-id="2ac8f-132">Categoria</span><span class="sxs-lookup"><span data-stu-id="2ac8f-132">Category</span></span>

<span data-ttu-id="2ac8f-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2ac8f-133">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ac8f-134">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2ac8f-134">Affected APIs</span></span>

<xref:System.Net.Http.HttpClient?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:System.Net.Http.HttpClient`

-->
