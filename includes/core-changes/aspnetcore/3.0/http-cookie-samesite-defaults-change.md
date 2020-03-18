---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282517"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="73e30-101">HTTP: Alguns padrões do Cookie SameSite alterados para Nenhum</span><span class="sxs-lookup"><span data-stu-id="73e30-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="73e30-102">`SameSite`é uma opção para cookies que podem ajudar a mitigar alguns ataques de CSRF (Cross-Site Request Forgery).</span><span class="sxs-lookup"><span data-stu-id="73e30-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="73e30-103">Quando essa opção foi introduzida inicialmente, padrões inconsistentes foram usados em várias APIs ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="73e30-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="73e30-104">A inconsistência levou a resultados confusos.</span><span class="sxs-lookup"><span data-stu-id="73e30-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="73e30-105">A partir de ASP.NET Core 3.0, esses padrões estão melhor alinhados.</span><span class="sxs-lookup"><span data-stu-id="73e30-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="73e30-106">Você deve optar por esse recurso por componente.</span><span class="sxs-lookup"><span data-stu-id="73e30-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73e30-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="73e30-107">Version introduced</span></span>

<span data-ttu-id="73e30-108">3.0</span><span class="sxs-lookup"><span data-stu-id="73e30-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="73e30-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="73e30-109">Old behavior</span></span>

<span data-ttu-id="73e30-110">As APIs de ASP.NET <xref:Microsoft.AspNetCore.Http.SameSiteMode> semelhantes usavam diferentes valores padrão.</span><span class="sxs-lookup"><span data-stu-id="73e30-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="73e30-111">Um exemplo da inconsistência é `HttpResponse.Cookies.Append(String, String)` `HttpResponse.Cookies.Append(String, String, CookieOptions)`visto em e `SameSiteMode.None` `SameSiteMode.Lax`, que padrão para e , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="73e30-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="73e30-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="73e30-112">New behavior</span></span>

<span data-ttu-id="73e30-113">Todas as APIs `SameSiteMode.None`afetadas padrão para .</span><span class="sxs-lookup"><span data-stu-id="73e30-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="73e30-114">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="73e30-114">Reason for change</span></span>

<span data-ttu-id="73e30-115">O valor padrão foi `SameSite` alterado para fazer um recurso de opt-in.</span><span class="sxs-lookup"><span data-stu-id="73e30-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73e30-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="73e30-116">Recommended action</span></span>

<span data-ttu-id="73e30-117">Cada componente que emite `SameSite` cookies precisa decidir se é apropriado para seus cenários.</span><span class="sxs-lookup"><span data-stu-id="73e30-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="73e30-118">Revise o uso das APIs `SameSite` afetadas e reconfigure conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="73e30-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="73e30-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="73e30-119">Category</span></span>

<span data-ttu-id="73e30-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="73e30-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73e30-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="73e30-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
