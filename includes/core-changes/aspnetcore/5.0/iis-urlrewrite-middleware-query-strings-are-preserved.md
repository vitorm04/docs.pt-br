---
ms.openlocfilehash: 29908ed916690e67db3cc5d72ebe1b1c6aea45c6
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325212"
---
### <a name="iis-urlrewrite-middleware-query-strings-are-preserved"></a><span data-ttu-id="2ced4-101">IIS: cadeias de consulta de middleware UrlRewrite são preservadas</span><span class="sxs-lookup"><span data-stu-id="2ced4-101">IIS: UrlRewrite middleware query strings are preserved</span></span>

<span data-ttu-id="2ced4-102">Um defeito de middleware UrlRewrite do IIS impediu que a cadeia de caracteres de consulta fosse preservada nas regras de regravação.</span><span class="sxs-lookup"><span data-stu-id="2ced4-102">An IIS UrlRewrite middleware defect prevented the query string from being preserved in rewrite rules.</span></span> <span data-ttu-id="2ced4-103">Esse defeito foi corrigido para manter a consistência com o comportamento do módulo UrlRewrite do IIS.</span><span class="sxs-lookup"><span data-stu-id="2ced4-103">That defect has been fixed to maintain consistency with the IIS UrlRewrite Module's behavior.</span></span>

<span data-ttu-id="2ced4-104">Para obter uma discussão, veja Issue [dotnet/aspnetcore # 22972](https://github.com/dotnet/aspnetcore/issues/22972).</span><span class="sxs-lookup"><span data-stu-id="2ced4-104">For discussion, see issue [dotnet/aspnetcore#22972](https://github.com/dotnet/aspnetcore/issues/22972).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2ced4-105">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="2ced4-105">Version introduced</span></span>

<span data-ttu-id="2ced4-106">ASP.NET Core 5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="2ced4-106">ASP.NET Core 5.0 Preview 7</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2ced4-107">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="2ced4-107">Old behavior</span></span>

<span data-ttu-id="2ced4-108">Considere a seguinte regra de reescrita:</span><span class="sxs-lookup"><span data-stu-id="2ced4-108">Consider the following rewrite rule:</span></span>

```xml
<rule name="MyRule" stopProcessing="true">
  <match url="^about" />
  <action type="Redirect" url="/contact" redirectType="Temporary" appendQueryString="true" />
</rule>
```

<span data-ttu-id="2ced4-109">A regra anterior não acrescenta a cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="2ced4-109">The preceding rule doesn't append the query string.</span></span> <span data-ttu-id="2ced4-110">Um URI como `/about?id=1` redireciona para `/contact` em vez de `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="2ced4-110">A URI like `/about?id=1` redirects to `/contact` instead of `/contact?id=1`.</span></span> <span data-ttu-id="2ced4-111">O `appendQueryString` atributo `true` também usa como padrão.</span><span class="sxs-lookup"><span data-stu-id="2ced4-111">The `appendQueryString` attribute defaults to `true` as well.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2ced4-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="2ced4-112">New behavior</span></span>

<span data-ttu-id="2ced4-113">A cadeia de caracteres de consulta é preservada.</span><span class="sxs-lookup"><span data-stu-id="2ced4-113">The query string is preserved.</span></span> <span data-ttu-id="2ced4-114">O URI do exemplo no [comportamento antigo](#old-behavior) seria `/contact?id=1` .</span><span class="sxs-lookup"><span data-stu-id="2ced4-114">The URI from the example in [Old behavior](#old-behavior) would be `/contact?id=1`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2ced4-115">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="2ced4-115">Reason for change</span></span>

<span data-ttu-id="2ced4-116">O comportamento antigo não correspondia ao comportamento do módulo UrlRewrite do IIS.</span><span class="sxs-lookup"><span data-stu-id="2ced4-116">The old behavior didn't match the IIS UrlRewrite Module's behavior.</span></span> <span data-ttu-id="2ced4-117">Para dar suporte à portabilidade entre o middleware e o módulo, o objetivo é manter comportamentos consistentes.</span><span class="sxs-lookup"><span data-stu-id="2ced4-117">To support porting between the middleware and module, the goal is to maintain consistent behaviors.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2ced4-118">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="2ced4-118">Recommended action</span></span>

<span data-ttu-id="2ced4-119">Se o comportamento de remover a cadeia de caracteres de consulta for preferencial, defina o `action` elemento como `appendQueryString="false"` .</span><span class="sxs-lookup"><span data-stu-id="2ced4-119">If the behavior of removing the query string is preferred, set the `action` element to `appendQueryString="false"`.</span></span>

#### <a name="category"></a><span data-ttu-id="2ced4-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="2ced4-120">Category</span></span>

<span data-ttu-id="2ced4-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2ced4-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ced4-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2ced4-122">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Rewrite.IISUrlRewriteOptionsExtensions.AddIISUrlRewrite`

-->
