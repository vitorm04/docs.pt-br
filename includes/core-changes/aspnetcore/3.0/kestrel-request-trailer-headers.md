---
ms.openlocfilehash: b0e1d6d720a1c9b827fb4585606e64b545d395d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394376"
---
### <a name="kestrel-request-trailer-headers-moved-to-new-collection"></a><span data-ttu-id="97d90-101">Kestrel: Solicitar cabeçalhos de trailer movidos para nova coleção</span><span class="sxs-lookup"><span data-stu-id="97d90-101">Kestrel: Request trailer headers moved to new collection</span></span>

<span data-ttu-id="97d90-102">Em versões anteriores, Kestrel adicionou cabeçalhos de reboque em pedaços HTTP/1.1 na coleção de cabeçalhos de solicitação quando o corpo de solicitação foi lido até o fim.</span><span class="sxs-lookup"><span data-stu-id="97d90-102">In prior versions, Kestrel added HTTP/1.1 chunked trailer headers into the request headers collection when the request body was read to the end.</span></span> <span data-ttu-id="97d90-103">Esse comportamento causou preocupações sobre a ambiguidade entre cabeçalhos e reboques.</span><span class="sxs-lookup"><span data-stu-id="97d90-103">This behavior caused concerns about ambiguity between headers and trailers.</span></span> <span data-ttu-id="97d90-104">A decisão foi tomada para mudar os trailers para uma nova coleção.</span><span class="sxs-lookup"><span data-stu-id="97d90-104">The decision was made to move the trailers to a new collection.</span></span>

<span data-ttu-id="97d90-105">Os reboques de solicitação HTTP/2 não estavam disponíveis em ASP.NET Core 2.2, mas agora também estão disponíveis nesta nova coleção no ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="97d90-105">HTTP/2 request trailers were unavailable in ASP.NET Core 2.2 but are now also available in this new collection in ASP.NET Core 3.0.</span></span>

<span data-ttu-id="97d90-106">Novos métodos de extensão de solicitação foram adicionados para acessar esses reboques.</span><span class="sxs-lookup"><span data-stu-id="97d90-106">New request extension methods have been added to access these trailers.</span></span>

<span data-ttu-id="97d90-107">Os reboques HTTP/1.1 estão disponíveis assim que todo o corpo de solicitação tiver sido lido.</span><span class="sxs-lookup"><span data-stu-id="97d90-107">HTTP/1.1 trailers are available once the entire request body has been read.</span></span>

<span data-ttu-id="97d90-108">Os reboques HTTP/2 estão disponíveis assim que são recebidos do cliente.</span><span class="sxs-lookup"><span data-stu-id="97d90-108">HTTP/2 trailers are available once they're received from the client.</span></span> <span data-ttu-id="97d90-109">O cliente não enviará os reboques até que todo o corpo de solicitação tenha sido pelo menos protegido pelo servidor.</span><span class="sxs-lookup"><span data-stu-id="97d90-109">The client won't send the trailers until the entire request body has been at least buffered by the server.</span></span> <span data-ttu-id="97d90-110">Você pode precisar ler o corpo de solicitação para liberar espaço de buffer.</span><span class="sxs-lookup"><span data-stu-id="97d90-110">You may need to read the request body to free up buffer space.</span></span> <span data-ttu-id="97d90-111">Os reboques estão sempre disponíveis se você ler o corpo de solicitação até o final.</span><span class="sxs-lookup"><span data-stu-id="97d90-111">Trailers are always available if you read the request body to the end.</span></span> <span data-ttu-id="97d90-112">Os trailers marcam a extremidade do corpo.</span><span class="sxs-lookup"><span data-stu-id="97d90-112">The trailers mark the end of the body.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="97d90-113">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="97d90-113">Version introduced</span></span>

<span data-ttu-id="97d90-114">3.0</span><span class="sxs-lookup"><span data-stu-id="97d90-114">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="97d90-115">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="97d90-115">Old behavior</span></span>

<span data-ttu-id="97d90-116">Solicitar cabeçalhos de `HttpRequest.Headers` reboque seria adicionado à coleção.</span><span class="sxs-lookup"><span data-stu-id="97d90-116">Request trailer headers would be added to the `HttpRequest.Headers` collection.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="97d90-117">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="97d90-117">New behavior</span></span>

<span data-ttu-id="97d90-118">Os cabeçalhos do trailer `HttpRequest.Headers` não estão **presentes** na coleção.</span><span class="sxs-lookup"><span data-stu-id="97d90-118">Request trailer headers **aren't present** in the `HttpRequest.Headers` collection.</span></span> <span data-ttu-id="97d90-119">Use os seguintes `HttpRequest` métodos de extensão para acessá-los:</span><span class="sxs-lookup"><span data-stu-id="97d90-119">Use the following extension methods on `HttpRequest` to access them:</span></span>

- <span data-ttu-id="97d90-120">`GetDeclaredTrailers()`- Recebe o cabeçalho "Trailer" que lista quais reboques esperar após o corpo.</span><span class="sxs-lookup"><span data-stu-id="97d90-120">`GetDeclaredTrailers()` - Gets the request "Trailer" header that lists which trailers to expect after the body.</span></span>
- <span data-ttu-id="97d90-121">`SupportsTrailers()`- Indica se a solicitação suporta o recebimento de cabeçalhos de reboque.</span><span class="sxs-lookup"><span data-stu-id="97d90-121">`SupportsTrailers()` - Indicates if the request supports receiving trailer headers.</span></span>
- <span data-ttu-id="97d90-122">`CheckTrailersAvailable()`- Determina se a solicitação suporta reboques e se eles estão disponíveis para leitura.</span><span class="sxs-lookup"><span data-stu-id="97d90-122">`CheckTrailersAvailable()` - Determines if the request supports trailers and if they're available for reading.</span></span>
- <span data-ttu-id="97d90-123">`GetTrailer(string trailerName)`- Recebe o cabeçalho de fuga solicitado da resposta.</span><span class="sxs-lookup"><span data-stu-id="97d90-123">`GetTrailer(string trailerName)` - Gets the requested trailing header from the response.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="97d90-124">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="97d90-124">Reason for change</span></span>

<span data-ttu-id="97d90-125">Os trailers são uma característica fundamental em cenários como o gRPC.</span><span class="sxs-lookup"><span data-stu-id="97d90-125">Trailers are a key feature in scenarios like gRPC.</span></span> <span data-ttu-id="97d90-126">A fusão dos reboques para solicitar cabeçalhos foi confuso para os usuários.</span><span class="sxs-lookup"><span data-stu-id="97d90-126">Merging the trailers in to request headers was confusing to users.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="97d90-127">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="97d90-127">Recommended action</span></span>

<span data-ttu-id="97d90-128">Use os métodos de `HttpRequest` extensão relacionados ao reboque para acessar reboques.</span><span class="sxs-lookup"><span data-stu-id="97d90-128">Use the trailer-related extension methods on `HttpRequest` to access trailers.</span></span>

#### <a name="category"></a><span data-ttu-id="97d90-129">Categoria</span><span class="sxs-lookup"><span data-stu-id="97d90-129">Category</span></span>

<span data-ttu-id="97d90-130">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="97d90-130">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="97d90-131">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="97d90-131">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Http.HttpRequest.Headers?displayProperty=nameWithType>

<!--

#### Affected APIs

`P:Microsoft.AspNetCore.Http.HttpRequest.Headers`

-->
