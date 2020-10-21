---
ms.openlocfilehash: 0dfe04ba1313480f15a8e7a7e26da613799180b2
ms.sourcegitcommit: dfcbc096ad7908cd58a5f0aeabd2256f05266bac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2020
ms.locfileid: "92332869"
---
### <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="780b5-101">ASP.NET Core aplicativos permitem a desserialização de números entre aspas</span><span class="sxs-lookup"><span data-stu-id="780b5-101">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="780b5-102">A partir do .NET 5,0, os aplicativos ASP.NET Core usam as opções de desserialização padrão conforme especificado por <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="780b5-102">Starting in .NET 5.0, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="780b5-103">O <xref:System.Text.Json.JsonSerializerDefaults.Web> conjunto de opções inclui <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> a configuração para <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="780b5-103">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="780b5-104">Essa alteração significa que ASP.NET Core aplicativos desserializarão com êxito os números representados como cadeias de caracteres JSON, em vez de lançar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="780b5-104">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings, instead of throwing an exception.</span></span>

#### <a name="change-description"></a><span data-ttu-id="780b5-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="780b5-105">Change description</span></span>

<span data-ttu-id="780b5-106">No .NET Core 3,0-3,1, <xref:System.Text.Json.JsonSerializer> lança uma <xref:System.Text.Json.JsonException> durante a desserialização se encontrar um número entre aspas em uma carga JSON.</span><span class="sxs-lookup"><span data-stu-id="780b5-106">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="780b5-107">Os números entre aspas são usados para mapear com propriedades de número em grafos de objeto.</span><span class="sxs-lookup"><span data-stu-id="780b5-107">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="780b5-108">No .NET Core 3,0-3,1, os números são lidos somente de <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span><span class="sxs-lookup"><span data-stu-id="780b5-108">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="780b5-109">A partir do .NET 5,0, os números entre aspas em cargas JSON são considerados válidos, por padrão, para os aplicativos ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="780b5-109">Starting in .NET 5.0, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="780b5-110">Nenhuma exceção é lançada durante a desserialização de números entre aspas.</span><span class="sxs-lookup"><span data-stu-id="780b5-110">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="780b5-111">Não há nenhuma alteração de comportamento para o padrão, autônomo <xref:System.Text.Json.JsonSerializer> ou <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="780b5-111">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="780b5-112">Isso tecnicamente não é uma alteração significativa, pois torna um cenário mais permissivo, em vez de mais restritivo (ou seja, ele tem sucesso em impor um número de uma cadeia de caracteres JSON em vez de gerar uma exceção).</span><span class="sxs-lookup"><span data-stu-id="780b5-112">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="780b5-113">No entanto, como essa é uma alteração comportamental significativa que afeta muitos aplicativos ASP.NET Core, ele está documentado aqui.</span><span class="sxs-lookup"><span data-stu-id="780b5-113">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="780b5-114">Os <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A> <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A> métodos de extensão e também usam o <xref:System.Text.Json.JsonSerializerDefaults.Web> conjunto de opções de serialização.</span><span class="sxs-lookup"><span data-stu-id="780b5-114">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="780b5-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="780b5-115">Version introduced</span></span>

<span data-ttu-id="780b5-116">5.0</span><span class="sxs-lookup"><span data-stu-id="780b5-116">5.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="780b5-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="780b5-117">Reason for change</span></span>

<span data-ttu-id="780b5-118">Vários usuários solicitaram uma opção para a manipulação de números mais permissivos no <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="780b5-118">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="780b5-119">Esse comentário indica que muitos produtores JSON (por exemplo, serviços na Web) emitem números entre aspas.</span><span class="sxs-lookup"><span data-stu-id="780b5-119">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="780b5-120">Ao permitir que números entre aspas sejam lidos (desserializados), os aplicativos .NET podem analisar com êxito essas cargas, por padrão, em contextos da Web.</span><span class="sxs-lookup"><span data-stu-id="780b5-120">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="780b5-121">A configuração é exposta por meio <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> do para que você possa especificar as mesmas opções em diferentes camadas de aplicativo, por exemplo, cliente, servidor e compartilhado.</span><span class="sxs-lookup"><span data-stu-id="780b5-121">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="780b5-122">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="780b5-122">Recommended action</span></span>

<span data-ttu-id="780b5-123">Se essa alteração for interrompida, por exemplo, se você depender da manipulação de número estrito para validação, poderá reabilitar o comportamento anterior.</span><span class="sxs-lookup"><span data-stu-id="780b5-123">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="780b5-124">Defina a <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> opção como <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="780b5-124">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="780b5-125">Para os aplicativos de API Web e MVC do ASP.NET Core, você pode configurar a opção no `Startup` usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="780b5-125">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

#### <a name="category"></a><span data-ttu-id="780b5-126">Categoria</span><span class="sxs-lookup"><span data-stu-id="780b5-126">Category</span></span>

- <span data-ttu-id="780b5-127">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="780b5-127">ASP.NET Core</span></span>
- <span data-ttu-id="780b5-128">Serialização</span><span class="sxs-lookup"><span data-stu-id="780b5-128">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="780b5-129">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="780b5-129">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

-->
