---
ms.openlocfilehash: cd66317bc93343e03a73dec74dff534776ca42e4
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198334"
---
### <a name="http-response-body-infrastructure-changes"></a><span data-ttu-id="52b05-101">HTTP: alterações de infraestrutura de corpo de resposta</span><span class="sxs-lookup"><span data-stu-id="52b05-101">HTTP: Response body infrastructure changes</span></span>

<span data-ttu-id="52b05-102">A infraestrutura que faz o backup de um corpo de resposta HTTP foi alterada.</span><span class="sxs-lookup"><span data-stu-id="52b05-102">The infrastructure backing an HTTP response body has changed.</span></span> <span data-ttu-id="52b05-103">Se você estiver usando `HttpResponse` diretamente, não precisará fazer nenhuma alteração de código.</span><span class="sxs-lookup"><span data-stu-id="52b05-103">If you're using `HttpResponse` directly, you shouldn't need to make any code changes.</span></span> <span data-ttu-id="52b05-104">Leia mais detalhadamente se você estiver encapsulando ou substituindo `HttpResponse.Body` ou acessando `HttpContext.Features`.</span><span class="sxs-lookup"><span data-stu-id="52b05-104">Read further if you're wrapping or replacing `HttpResponse.Body` or accessing `HttpContext.Features`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="52b05-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="52b05-105">Version introduced</span></span>

<span data-ttu-id="52b05-106">3.0</span><span class="sxs-lookup"><span data-stu-id="52b05-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="52b05-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="52b05-107">Old behavior</span></span>

<span data-ttu-id="52b05-108">Havia três APIs associadas ao corpo da resposta HTTP:</span><span class="sxs-lookup"><span data-stu-id="52b05-108">There were three APIs associated with the HTTP response body:</span></span>

- `IHttpResponseFeature.Body`
- `IHttpSendFileFeature.SendFileAsync`
- `IHttpBufferingFeature.DisableResponseBuffering`

#### <a name="new-behavior"></a><span data-ttu-id="52b05-109">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="52b05-109">New behavior</span></span>

<span data-ttu-id="52b05-110">Se você substituir `HttpResponse.Body`, ele substituirá todo o `IHttpResponseBodyFeature` por um wrapper em seu fluxo específico usando `StreamResponseBodyFeature` para fornecer implementações padrão para todas as APIs esperadas.</span><span class="sxs-lookup"><span data-stu-id="52b05-110">If you replace `HttpResponse.Body`, it replaces the entire `IHttpResponseBodyFeature` with a wrapper around your given stream using `StreamResponseBodyFeature` to provide default implementations for all of the expected APIs.</span></span> <span data-ttu-id="52b05-111">A configuração de volta do fluxo original reverte essa alteração.</span><span class="sxs-lookup"><span data-stu-id="52b05-111">Setting back the original stream reverts this change.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="52b05-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="52b05-112">Reason for change</span></span>

<span data-ttu-id="52b05-113">A motivação é combinar as APIs de corpo de resposta em uma única interface de recurso nova.</span><span class="sxs-lookup"><span data-stu-id="52b05-113">The motivation is to combine the response body APIs into a single new feature interface.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="52b05-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="52b05-114">Recommended action</span></span>

<span data-ttu-id="52b05-115">Use `IHttpResponseBodyFeature` em que você estava usando anteriormente `IHttpResponseFeature.Body`, `IHttpSendFileFeature` ou `IHttpBufferingFeature`.</span><span class="sxs-lookup"><span data-stu-id="52b05-115">Use `IHttpResponseBodyFeature` where you previously were using `IHttpResponseFeature.Body`, `IHttpSendFileFeature`, or `IHttpBufferingFeature`.</span></span>

#### <a name="category"></a><span data-ttu-id="52b05-116">Categoria</span><span class="sxs-lookup"><span data-stu-id="52b05-116">Category</span></span>

<span data-ttu-id="52b05-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="52b05-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52b05-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="52b05-118">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Http.Features.IHttpBufferingFeature`
- `P:Microsoft.AspNetCore.Http.Features.IHttpResponseFeature.Body`
- `T:Microsoft.AspNetCore.Http.Features.IHttpSendFileFeature`

-->
