---
ms.openlocfilehash: 3b329bf5ba2af4d3ab9c3e203e99daba8ca0d0c0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619764"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="8bd83-101">GridViews com AllowCustomPaging definido como verdadeiro pode acionar o evento PageIndexChanging ao deixar a página final do modo de exibição</span><span class="sxs-lookup"><span data-stu-id="8bd83-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="8bd83-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="8bd83-102">Details</span></span>

<span data-ttu-id="8bd83-103">Um bug no .NET Framework 4.5 faz com que <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName>, às vezes, não seja acionado para <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s com <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> habilitado.</span><span class="sxs-lookup"><span data-stu-id="8bd83-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8bd83-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="8bd83-104">Suggestion</span></span>

<span data-ttu-id="8bd83-105">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8bd83-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="8bd83-106">Como solução alternativa, o aplicativo pode fazer um BindGrid explícito em qualquer <code>Page_Load</code> que respeite essas condições (o <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> está na última página e Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> é diferente de <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="8bd83-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="8bd83-107">Como alternativa, o aplicativo pode ser modificado para permitir a paginação (em vez da paginação personalizada), uma vez que esse cenário não demonstra o problema.</span><span class="sxs-lookup"><span data-stu-id="8bd83-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="8bd83-108">Name</span><span class="sxs-lookup"><span data-stu-id="8bd83-108">Name</span></span>    | <span data-ttu-id="8bd83-109">Valor</span><span class="sxs-lookup"><span data-stu-id="8bd83-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8bd83-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="8bd83-110">Scope</span></span>   |<span data-ttu-id="8bd83-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="8bd83-111">Minor</span></span>|
|<span data-ttu-id="8bd83-112">Versão</span><span class="sxs-lookup"><span data-stu-id="8bd83-112">Version</span></span>|<span data-ttu-id="8bd83-113">4.5</span><span class="sxs-lookup"><span data-stu-id="8bd83-113">4.5</span></span>|
|<span data-ttu-id="8bd83-114">Type</span><span class="sxs-lookup"><span data-stu-id="8bd83-114">Type</span></span>|<span data-ttu-id="8bd83-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="8bd83-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8bd83-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8bd83-116">Affected APIs</span></span>

-<xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType></li></ul>|
