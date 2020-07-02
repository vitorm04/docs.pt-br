---
ms.openlocfilehash: 75f176133697056bab9349ba1d18d7a0e1aa7da2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619762"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="06b9b-101">Items.Clear não remove duplicatas de SelectedItems</span><span class="sxs-lookup"><span data-stu-id="06b9b-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="06b9b-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="06b9b-102">Details</span></span>

<span data-ttu-id="06b9b-103">Suponha que um Seletor (com seleção múltipla habilitada) tenha duplicatas em sua coleção <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> – o mesmo item é exibido mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="06b9b-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="06b9b-104">A remoção desses itens da fonte de dados (por exemplo, chamando Items.Clear) falha ao removê-los de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; somente a primeira instância é removida.</span><span class="sxs-lookup"><span data-stu-id="06b9b-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="06b9b-105">Além disso, o uso subsequente de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (por exemplo, SelectedItems.Clear()) pode encontrar problemas, como <xref:System.ArgumentException?displayProperty=fullName>, pois <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contém itens que não estão mais na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="06b9b-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="06b9b-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="06b9b-106">Suggestion</span></span>

<span data-ttu-id="06b9b-107">Atualize se possível para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="06b9b-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="06b9b-108">Name</span><span class="sxs-lookup"><span data-stu-id="06b9b-108">Name</span></span>    | <span data-ttu-id="06b9b-109">Valor</span><span class="sxs-lookup"><span data-stu-id="06b9b-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="06b9b-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="06b9b-110">Scope</span></span>   |<span data-ttu-id="06b9b-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="06b9b-111">Minor</span></span>|
|<span data-ttu-id="06b9b-112">Versão</span><span class="sxs-lookup"><span data-stu-id="06b9b-112">Version</span></span>|<span data-ttu-id="06b9b-113">4.5</span><span class="sxs-lookup"><span data-stu-id="06b9b-113">4.5</span></span>|
|<span data-ttu-id="06b9b-114">Type</span><span class="sxs-lookup"><span data-stu-id="06b9b-114">Type</span></span>|<span data-ttu-id="06b9b-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="06b9b-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06b9b-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="06b9b-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType></li></ul>|
