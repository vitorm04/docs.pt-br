---
ms.openlocfilehash: 2b88ab7cfdd7a0a0a770b305ecd0200afd9a9b4b
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441538"
---
### <a name="authorization-resource-in-endpoint-routing-is-httpcontext"></a><span data-ttu-id="b2eaf-101">Autorização: o recurso no roteamento de ponto de extremidade é HttpContext</span><span class="sxs-lookup"><span data-stu-id="b2eaf-101">Authorization: Resource in endpoint routing is HttpContext</span></span>

<span data-ttu-id="b2eaf-102">Ao usar o roteamento de ponto de extremidade no ASP.NET Core 3,1, o recurso usado para autorização é o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-102">When using endpoint routing in ASP.NET Core 3.1, the resource used for authorization is the endpoint.</span></span> <span data-ttu-id="b2eaf-103">Essa abordagem não era suficiente para obter acesso aos dados da rota ( <xref:Microsoft.AspNetCore.Routing.RouteData> ).</span><span class="sxs-lookup"><span data-stu-id="b2eaf-103">This approach was insufficient for gaining access to the route data (<xref:Microsoft.AspNetCore.Routing.RouteData>).</span></span> <span data-ttu-id="b2eaf-104">Anteriormente no MVC, um <xref:Microsoft.AspNetCore.Http.HttpContext> recurso foi passado, o que permite o acesso ao ponto de extremidade ( <xref:Microsoft.AspNetCore.Http.Endpoint> ) e aos dados de rota.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-104">Previously in MVC, an <xref:Microsoft.AspNetCore.Http.HttpContext> resource was passed in, which allows access to both the endpoint (<xref:Microsoft.AspNetCore.Http.Endpoint>) and the route data.</span></span> <span data-ttu-id="b2eaf-105">Essa alteração garante que o recurso passado para autorização seja sempre o `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="b2eaf-105">This change ensures that the resource passed to authorization is always the `HttpContext`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2eaf-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b2eaf-106">Version introduced</span></span>

<span data-ttu-id="b2eaf-107">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="b2eaf-107">5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b2eaf-108">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="b2eaf-108">Old behavior</span></span>

<span data-ttu-id="b2eaf-109">Ao usar o roteamento de ponto de extremidade e os atributos de middleware de autorização ( <xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware> ) ou [[autorizar]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) , o recurso passado para autorização é o ponto de extremidade correspondente.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-109">When using endpoint routing and the authorization middleware (<xref:Microsoft.AspNetCore.Authorization.AuthorizationMiddleware>) or [[Authorize]](xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute) attributes, the resource passed to authorization is the matching endpoint.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b2eaf-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="b2eaf-110">New behavior</span></span>

<span data-ttu-id="b2eaf-111">O roteamento do ponto de extremidade passa a `HttpContext` para a autorização.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-111">Endpoint routing passes the `HttpContext` to authorization.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b2eaf-112">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b2eaf-112">Reason for change</span></span>

<span data-ttu-id="b2eaf-113">Você pode acessar o ponto de extremidade do `HttpContext` .</span><span class="sxs-lookup"><span data-stu-id="b2eaf-113">You can get to the endpoint from the `HttpContext`.</span></span> <span data-ttu-id="b2eaf-114">No entanto, não havia como ir do ponto de extremidade para coisas como os dados de rota.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-114">However, there was no way to get from the endpoint to things like the route data.</span></span> <span data-ttu-id="b2eaf-115">Houve uma perda na funcionalidade do roteamento sem ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-115">There was a loss in functionality from non-endpoint routing.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2eaf-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b2eaf-116">Recommended action</span></span>

<span data-ttu-id="b2eaf-117">Se seu aplicativo usar o recurso de ponto de extremidade, chame <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> no `HttpContext` para continuar acessando o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b2eaf-117">If your app uses the endpoint resource, call <xref:Microsoft.AspNetCore.Http.EndpointHttpContextExtensions.GetEndpoint%2A> on the `HttpContext` to continue accessing the endpoint.</span></span>

<span data-ttu-id="b2eaf-118">No ASP.NET Core 5,0 Preview 8 e posterior, você pode reverter para o comportamento antigo com o <xref:System.AppContext.SetSwitch%2A> .</span><span class="sxs-lookup"><span data-stu-id="b2eaf-118">In ASP.NET Core 5.0 Preview 8 and later, you can revert to the old behavior with <xref:System.AppContext.SetSwitch%2A>.</span></span> <span data-ttu-id="b2eaf-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b2eaf-119">For example:</span></span>

```csharp
AppContext.SetSwitch(
    "Microsoft.AspNetCore.Authorization.SuppressUseHttpContextAsAuthorizationResource",
    isEnabled: true);
```

#### <a name="category"></a><span data-ttu-id="b2eaf-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="b2eaf-120">Category</span></span>

<span data-ttu-id="b2eaf-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2eaf-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2eaf-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b2eaf-122">Affected APIs</span></span>

<span data-ttu-id="b2eaf-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="b2eaf-123">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
