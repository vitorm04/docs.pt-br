---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282517"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="aee95-101">HTTP: alguns padrões de SameSite de cookie foram alterados para nenhum</span><span class="sxs-lookup"><span data-stu-id="aee95-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="aee95-102">`SameSite` é uma opção para cookies que podem ajudar a atenuar ataques de solicitação entre sites forjados (CSRF).</span><span class="sxs-lookup"><span data-stu-id="aee95-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="aee95-103">Quando essa opção foi introduzida inicialmente, padrões inconsistentes foram usados em várias APIs de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="aee95-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="aee95-104">A inconsistência levou a resultados confusos.</span><span class="sxs-lookup"><span data-stu-id="aee95-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="aee95-105">A partir do ASP.NET Core 3,0, esses padrões são mais alinhados.</span><span class="sxs-lookup"><span data-stu-id="aee95-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="aee95-106">Você deve aceitar esse recurso em uma base por componente.</span><span class="sxs-lookup"><span data-stu-id="aee95-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="aee95-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="aee95-107">Version introduced</span></span>

<span data-ttu-id="aee95-108">3.0</span><span class="sxs-lookup"><span data-stu-id="aee95-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="aee95-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="aee95-109">Old behavior</span></span>

<span data-ttu-id="aee95-110">APIs ASP.NET Core semelhantes usavam valores de <xref:Microsoft.AspNetCore.Http.SameSiteMode> padrão diferentes.</span><span class="sxs-lookup"><span data-stu-id="aee95-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="aee95-111">Um exemplo da inconsistência é visto em `HttpResponse.Cookies.Append(String, String)` e `HttpResponse.Cookies.Append(String, String, CookieOptions)`, que tem como padrão `SameSiteMode.None` e `SameSiteMode.Lax`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="aee95-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="aee95-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="aee95-112">New behavior</span></span>

<span data-ttu-id="aee95-113">Todas as APIs afetadas têm como padrão `SameSiteMode.None`.</span><span class="sxs-lookup"><span data-stu-id="aee95-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="aee95-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="aee95-114">Reason for change</span></span>

<span data-ttu-id="aee95-115">O valor padrão foi alterado para fazer `SameSite` um recurso de aceitação.</span><span class="sxs-lookup"><span data-stu-id="aee95-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="aee95-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="aee95-116">Recommended action</span></span>

<span data-ttu-id="aee95-117">Cada componente que emite cookies precisa decidir se `SameSite` é apropriado para seus cenários.</span><span class="sxs-lookup"><span data-stu-id="aee95-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="aee95-118">Examine o uso das APIs afetadas e reconfigure `SameSite` conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="aee95-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="aee95-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="aee95-119">Category</span></span>

<span data-ttu-id="aee95-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="aee95-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="aee95-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="aee95-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
