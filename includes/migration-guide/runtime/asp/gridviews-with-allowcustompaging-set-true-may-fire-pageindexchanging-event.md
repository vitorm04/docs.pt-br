---
ms.openlocfilehash: 4d210eeedd2f228017634d29f11554deb6ed8079
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497621"
---
### <a name="gridviews-with-allowcustompaging-set-to-true-may-fire-the-pageindexchanging-event-when-leaving-the-final-page-of-the-view"></a><span data-ttu-id="843a5-101">GridViews com AllowCustomPaging definido como verdadeiro pode acionar o evento PageIndexChanging ao deixar a página final do modo de exibição</span><span class="sxs-lookup"><span data-stu-id="843a5-101">GridViews with AllowCustomPaging set to true may fire the PageIndexChanging event when leaving the final page of the view</span></span>

#### <a name="details"></a><span data-ttu-id="843a5-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="843a5-102">Details</span></span>

<span data-ttu-id="843a5-103">Um bug no .NET Framework 4.5 faz com que <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName>, às vezes, não seja acionado para <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s com <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName> habilitado.</span><span class="sxs-lookup"><span data-stu-id="843a5-103">A bug in the .NET Framework 4.5 causes <xref:System.Web.UI.WebControls.GridView.PageIndexChanging?displayProperty=fullName> to sometimes not fire for <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName>s that have enabled <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=fullName>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="843a5-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="843a5-104">Suggestion</span></span>

<span data-ttu-id="843a5-105">Esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="843a5-105">This issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span> <span data-ttu-id="843a5-106">Como solução alternativa, o aplicativo pode fazer um BindGrid explícito em qualquer <code>Page_Load</code> que respeite essas condições (o <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> está na última página e Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> é diferente de <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span><span class="sxs-lookup"><span data-stu-id="843a5-106">As a work-around, the app can do an explicit BindGrid on any <code>Page_Load</code> that would hit these conditions (the <xref:System.Web.UI.WebControls.GridView?displayProperty=fullName> is on the last page and Last<xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName> is different from <xref:System.Web.UI.WebControls.GridView.PageSize?displayProperty=fullName>).</span></span> <span data-ttu-id="843a5-107">Como alternativa, o aplicativo pode ser modificado para permitir a paginação (em vez da paginação personalizada), uma vez que esse cenário não demonstra o problema.</span><span class="sxs-lookup"><span data-stu-id="843a5-107">Alternatively, the app can be modified to allow paging (instead of custom paging), as that scenario does not demonstrate the problem.</span></span>

| <span data-ttu-id="843a5-108">Nome</span><span class="sxs-lookup"><span data-stu-id="843a5-108">Name</span></span>    | <span data-ttu-id="843a5-109">Valor</span><span class="sxs-lookup"><span data-stu-id="843a5-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="843a5-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="843a5-110">Scope</span></span>   |<span data-ttu-id="843a5-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="843a5-111">Minor</span></span>|
|<span data-ttu-id="843a5-112">Versão</span><span class="sxs-lookup"><span data-stu-id="843a5-112">Version</span></span>|<span data-ttu-id="843a5-113">4.5</span><span class="sxs-lookup"><span data-stu-id="843a5-113">4.5</span></span>|
|<span data-ttu-id="843a5-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="843a5-114">Type</span></span>|<span data-ttu-id="843a5-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="843a5-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="843a5-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="843a5-116">Affected APIs</span></span>

- <xref:System.Web.UI.WebControls.GridView.AllowCustomPaging?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Web.UI.WebControls.GridView.AllowCustomPaging`

-->
