---
ms.openlocfilehash: 0c88d40e34d2d6458bb463a09d716dea42b711fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901585"
---
### <a name="authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters"></a><span data-ttu-id="ce9d5-101">Autorização: IAllowAnonymous removido do AuthorizationFilterContext.Filters</span><span class="sxs-lookup"><span data-stu-id="ce9d5-101">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>

<span data-ttu-id="ce9d5-102">A partir de ASP.NET O Núcleo 3.0, o MVC não adiciona [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) para [atributos [AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) que foram descobertos em controladores e métodos de ação.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-102">As of ASP.NET Core 3.0, MVC doesn't add [AllowAnonymousFilters](xref:Microsoft.AspNetCore.Mvc.Authorization.AllowAnonymousFilter) for [[AllowAnonymous]](xref:Microsoft.AspNetCore.Authorization.AllowAnonymousAttribute) attributes that were discovered on controllers and action methods.</span></span> <span data-ttu-id="ce9d5-103">Esta mudança é tratada localmente <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>para derivativos de , <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> mas é uma mudança de ruptura para e implementações.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-103">This change is addressed locally for derivatives of <xref:Microsoft.AspNetCore.Authorization.AuthorizeAttribute>, but it's a breaking change for <xref:Microsoft.AspNetCore.Mvc.Filters.IAsyncAuthorizationFilter> and <xref:Microsoft.AspNetCore.Mvc.Filters.IAuthorizationFilter> implementations.</span></span> <span data-ttu-id="ce9d5-104">Tais implementações envoltas em um atributo [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) são uma maneira [popular](https://stackoverflow.com/a/41348219/608220) e suportada para obter uma autorização fortemente digitada, baseada em atributos, quando tanto a configuração quanto a injeção de dependência são necessárias.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-104">Such implementations wrapped in a [[TypeFilter]](xref:Microsoft.AspNetCore.Mvc.TypeFilterAttribute) attribute are a [popular](https://stackoverflow.com/a/41348219/608220) and supported way to achieve strongly-typed, attribute-based authorization when both configuration and dependency injection are required.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ce9d5-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ce9d5-105">Version introduced</span></span>

<span data-ttu-id="ce9d5-106">3.0</span><span class="sxs-lookup"><span data-stu-id="ce9d5-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ce9d5-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ce9d5-107">Old behavior</span></span>

<span data-ttu-id="ce9d5-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous>apareceu na coleção [AuthorizationFilterContext.Filters.](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A)</span><span class="sxs-lookup"><span data-stu-id="ce9d5-108"><xref:Microsoft.AspNetCore.Authorization.IAllowAnonymous> appeared in the [AuthorizationFilterContext.Filters](xref:Microsoft.AspNetCore.Mvc.Filters.FilterContext.Filters%2A) collection.</span></span> <span data-ttu-id="ce9d5-109">O teste para a presença da interface foi uma abordagem válida para substituir ou desativar o filtro em métodos individuais de controlador.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-109">Testing for the interface's presence was a valid approach to override or disable the filter on individual controller methods.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ce9d5-110">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ce9d5-110">New behavior</span></span>

<span data-ttu-id="ce9d5-111">`IAllowAnonymous`não aparece mais `AuthorizationFilterContext.Filters` na coleção.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-111">`IAllowAnonymous` no longer appears in the `AuthorizationFilterContext.Filters` collection.</span></span> <span data-ttu-id="ce9d5-112">`IAsyncAuthorizationFilter`implementações que dependem do comportamento antigo normalmente causam respostas intermitentes HTTP 401 Não Autorizadas ou HTTP 403 Proibidas.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-112">`IAsyncAuthorizationFilter` implementations that are dependent on the old behavior typically cause intermittent HTTP 401 Unauthorized or HTTP 403 Forbidden responses.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ce9d5-113">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="ce9d5-113">Reason for change</span></span>

<span data-ttu-id="ce9d5-114">Uma nova estratégia de roteamento de ponto final foi introduzida no ASP.NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ce9d5-114">A new endpoint routing strategy was introduced in ASP.NET Core 3.0.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ce9d5-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ce9d5-115">Recommended action</span></span>

<span data-ttu-id="ce9d5-116">Pesquise os metadados `IAllowAnonymous`do ponto final para .</span><span class="sxs-lookup"><span data-stu-id="ce9d5-116">Search the endpoint metadata for `IAllowAnonymous`.</span></span> <span data-ttu-id="ce9d5-117">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="ce9d5-117">For example:</span></span>

```csharp
var endpoint = context.HttpContext.GetEndpoint();
if (endpoint?.Metadata?.GetMetadata<IAllowAnonymous>() != null)
{
}
```

<span data-ttu-id="ce9d5-118">Um exemplo dessa técnica é visto [neste método HasAllowAnonymous](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span><span class="sxs-lookup"><span data-stu-id="ce9d5-118">An example of this technique is seen in [this HasAllowAnonymous method](https://github.com/dotnet/aspnetcore/blob/bd65275148abc9b07a3b59797a88d485341152bf/src/Mvc/Mvc.Core/src/Authorization/AuthorizeFilter.cs#L236).</span></span>

#### <a name="category"></a><span data-ttu-id="ce9d5-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="ce9d5-119">Category</span></span>

<span data-ttu-id="ce9d5-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce9d5-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ce9d5-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ce9d5-121">Affected APIs</span></span>

<span data-ttu-id="ce9d5-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ce9d5-122">None</span></span>

<!--

#### Affected APIs

Not detectable via API analysis

-->
