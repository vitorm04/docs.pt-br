---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282517"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="d869c-101">HTTP: alguns padrões de SameSite de cookie foram alterados para nenhum</span><span class="sxs-lookup"><span data-stu-id="d869c-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="d869c-102">`SameSite` é uma opção para cookies que podem ajudar a atenuar ataques CSRF (solicitação entre sites forjada).</span><span class="sxs-lookup"><span data-stu-id="d869c-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="d869c-103">Quando essa opção foi introduzida inicialmente, padrões inconsistentes foram usados em várias APIs de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d869c-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="d869c-104">A inconsistência levou a resultados confusos.</span><span class="sxs-lookup"><span data-stu-id="d869c-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="d869c-105">A partir do ASP.NET Core 3,0, esses padrões são mais alinhados.</span><span class="sxs-lookup"><span data-stu-id="d869c-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="d869c-106">Você deve aceitar esse recurso em uma base por componente.</span><span class="sxs-lookup"><span data-stu-id="d869c-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d869c-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d869c-107">Version introduced</span></span>

<span data-ttu-id="d869c-108">3,0</span><span class="sxs-lookup"><span data-stu-id="d869c-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d869c-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="d869c-109">Old behavior</span></span>

<span data-ttu-id="d869c-110">APIs ASP.NET Core semelhantes usavam valores padrão diferentes <xref:Microsoft.AspNetCore.Http.SameSiteMode> .</span><span class="sxs-lookup"><span data-stu-id="d869c-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="d869c-111">Um exemplo da inconsistência é visto em `HttpResponse.Cookies.Append(String, String)` e `HttpResponse.Cookies.Append(String, String, CookieOptions)` , que é padronizado para `SameSiteMode.None` e `SameSiteMode.Lax` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d869c-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d869c-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="d869c-112">New behavior</span></span>

<span data-ttu-id="d869c-113">Todas as APIs afetadas são padrão para `SameSiteMode.None` .</span><span class="sxs-lookup"><span data-stu-id="d869c-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d869c-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="d869c-114">Reason for change</span></span>

<span data-ttu-id="d869c-115">O valor padrão foi alterado para fazer `SameSite` um recurso de aceitação.</span><span class="sxs-lookup"><span data-stu-id="d869c-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d869c-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d869c-116">Recommended action</span></span>

<span data-ttu-id="d869c-117">Cada componente que emite cookies precisa decidir se `SameSite` é apropriado para seus cenários.</span><span class="sxs-lookup"><span data-stu-id="d869c-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="d869c-118">Examine o uso das APIs afetadas e reconfigure `SameSite` conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="d869c-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="d869c-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="d869c-119">Category</span></span>

<span data-ttu-id="d869c-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d869c-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d869c-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d869c-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
