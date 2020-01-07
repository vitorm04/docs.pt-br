---
ms.openlocfilehash: 89af89d3580fd1396335a0cd8964b46c13d7637e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344280"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="238ee-101">Autorização: IAllowAnonymous removido de AuthorizationFilterContext. Filters</span><span class="sxs-lookup"><span data-stu-id="238ee-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="238ee-102">A partir de ASP.NET Core 3,0, o MVC não adiciona [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) para atributos [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) que foram descobertos em controladores e métodos de ação.</span><span class="sxs-lookup"><span data-stu-id="238ee-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="238ee-103">Essa alteração é abordada localmente para derivações de <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, mas é uma alteração significativa para <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> e <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementações.</span><span class="sxs-lookup"><span data-stu-id="238ee-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="238ee-104">Essas implementações encapsuladas em um atributo [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) são uma maneira [popular](https://stackoverflow.com/a/41348219/608220) e com suporte para obter autorização baseada em atributo fortemente tipada quando a configuração e a injeção de dependência são necessárias.</span><span class="sxs-lookup"><span data-stu-id="238ee-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="238ee-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="238ee-105">Version introduced</span></span>

<span data-ttu-id="238ee-106">3.0</span><span class="sxs-lookup"><span data-stu-id="238ee-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="238ee-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="238ee-107">Old behavior</span></span>

<span data-ttu-id="238ee-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> apareceu na coleção [AuthorizationFilterContext. Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) .</span><span class="sxs-lookup"><span data-stu-id="238ee-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="238ee-109">O teste da presença da interface era uma abordagem válida para substituir ou desabilitar o filtro em métodos individuais do controlador.</span><span class="sxs-lookup"><span data-stu-id="238ee-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="238ee-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="238ee-110">New behavior</span></span>

<span data-ttu-id="238ee-111">`IAllowAnonymous` não aparece mais na coleção de `AuthorizationFilterContext.Filters`.</span><span class="sxs-lookup"><span data-stu-id="238ee-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="238ee-112">`IAsyncAuthorizationFilter` implementações que dependem do comportamento antigo normalmente causam respostas intermitentes HTTP 401 não autorizadas ou HTTP 403 Proibido.</span><span class="sxs-lookup"><span data-stu-id="238ee-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="238ee-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="238ee-113">Reason for change</span></span>

<span data-ttu-id="238ee-114">Uma nova estratégia de roteamento de ponto de extremidade foi introduzida no ASP.NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="238ee-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="238ee-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="238ee-115">Recommended action</span></span>

<span data-ttu-id="238ee-116">Pesquise os metadados do ponto de extremidade para `IAllowAnonymous`.</span><span class="sxs-lookup"><span data-stu-id="238ee-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="238ee-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="238ee-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="238ee-118">Um exemplo dessa técnica é visto neste [método HasAllowAnonymous](https://github.com/aspnet/AspNetCore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="238ee-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/aspnet/AspNetCore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="238ee-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="238ee-119">Category</span></span>

<span data-ttu-id="238ee-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="238ee-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="238ee-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="238ee-121">Affected APIs</span></span>

<span data-ttu-id="238ee-122">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="238ee-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
