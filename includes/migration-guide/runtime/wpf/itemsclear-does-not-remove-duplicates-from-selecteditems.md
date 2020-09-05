---
ms.openlocfilehash: 25ce391f917bd270d4d9a75f608e4a8ec763d15c
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497920"
---
### <a name="itemsclear-does-not-remove-duplicates-from-selecteditems"></a><span data-ttu-id="17b12-101">Items.Clear não remove duplicatas de SelectedItems</span><span class="sxs-lookup"><span data-stu-id="17b12-101">Items.Clear does not remove duplicates from SelectedItems</span></span>

#### <a name="details"></a><span data-ttu-id="17b12-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="17b12-102">Details</span></span>

<span data-ttu-id="17b12-103">Suponha que um Seletor (com seleção múltipla habilitada) tenha duplicatas em sua coleção <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> – o mesmo item é exibido mais de uma vez.</span><span class="sxs-lookup"><span data-stu-id="17b12-103">Suppose a Selector (with multiple selection enabled) has duplicates in its <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> collection - the same item appears more than once.</span></span>  <span data-ttu-id="17b12-104">A remoção desses itens da fonte de dados (por exemplo, chamando Items.Clear) falha ao removê-los de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; somente a primeira instância é removida.</span><span class="sxs-lookup"><span data-stu-id="17b12-104">Removing those items from the data source (e.g. by calling Items.Clear) fails to remove them from <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName>; only the first instance is removed.</span></span> <span data-ttu-id="17b12-105">Além disso, o uso subsequente de <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (por exemplo, SelectedItems.Clear()) pode encontrar problemas, como <xref:System.ArgumentException?displayProperty=fullName>, pois <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contém itens que não estão mais na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="17b12-105">Furthermore, subsequent use of <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> (e.g. SelectedItems.Clear()) can encounter problems such as <xref:System.ArgumentException?displayProperty=fullName>, because <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=fullName> contains items that are no longer in the data source.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="17b12-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="17b12-106">Suggestion</span></span>

<span data-ttu-id="17b12-107">Atualize se possível para o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="17b12-107">Upgrade if possible to .NET Framework 4.6.2.</span></span>

| <span data-ttu-id="17b12-108">Nome</span><span class="sxs-lookup"><span data-stu-id="17b12-108">Name</span></span>    | <span data-ttu-id="17b12-109">Valor</span><span class="sxs-lookup"><span data-stu-id="17b12-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="17b12-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="17b12-110">Scope</span></span>   |<span data-ttu-id="17b12-111">Secundária</span><span class="sxs-lookup"><span data-stu-id="17b12-111">Minor</span></span>|
|<span data-ttu-id="17b12-112">Versão</span><span class="sxs-lookup"><span data-stu-id="17b12-112">Version</span></span>|<span data-ttu-id="17b12-113">4.5</span><span class="sxs-lookup"><span data-stu-id="17b12-113">4.5</span></span>|
|<span data-ttu-id="17b12-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="17b12-114">Type</span></span>|<span data-ttu-id="17b12-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="17b12-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="17b12-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="17b12-116">Affected APIs</span></span>

- <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems?displayProperty=nameWithType>

<!--

#### Affected APIs

- `P:System.Windows.Controls.Primitives.MultiSelector.SelectedItems`

-->
