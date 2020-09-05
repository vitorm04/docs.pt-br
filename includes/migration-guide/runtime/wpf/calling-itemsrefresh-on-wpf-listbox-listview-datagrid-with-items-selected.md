---
ms.openlocfilehash: 972601874d80d82ebae8b79779acfed82e5570cb
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496900"
---
### <a name="calling-itemsrefresh-on-a-wpf-listbox-listview-or-datagrid-with-items-selected-can-cause-duplicate-items-to-appear-in-the-element"></a><span data-ttu-id="06878-101">Chamar Items.Refresh em uma ListBox, ListView ou DataGrid do WPF com itens selecionados pode exibir itens duplicados no elemento</span><span class="sxs-lookup"><span data-stu-id="06878-101">Calling Items.Refresh on a WPF ListBox, ListView, or DataGrid with items selected can cause duplicate items to appear in the element</span></span>

#### <a name="details"></a><span data-ttu-id="06878-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="06878-102">Details</span></span>

<span data-ttu-id="06878-103">No .NET Framework 4.5, chamar ListBox.Items.Refresh do código enquanto itens estiverem selecionados em uma <xref:System.Windows.Controls.ListBox?displayProperty=fullName> pode fazer com que os itens selecionados sejam duplicados na lista.</span><span class="sxs-lookup"><span data-stu-id="06878-103">In the .NET Framework 4.5, calling ListBox.Items.Refresh from code while items are selected in a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> can cause the selected items to be duplicated in the list.</span></span> <span data-ttu-id="06878-104">Ocorre um problema semelhante com <xref:System.Windows.Controls.ListView?displayProperty=fullName> e <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="06878-104">A similar issue occurs with <xref:System.Windows.Controls.ListView?displayProperty=fullName> and <xref:System.Windows.Controls.DataGrid?displayProperty=fullName>.</span></span> <span data-ttu-id="06878-105">Isso foi corrigido no .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="06878-105">This is fixed in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="06878-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="06878-106">Suggestion</span></span>

<span data-ttu-id="06878-107">Esse problema pode ser contornado de forma programática cancelando a seleção dos itens antes de chamar <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> e selecionando-os novamente após a conclusão da chamada.</span><span class="sxs-lookup"><span data-stu-id="06878-107">This issue may be worked around by programmatically unselecting items before <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=fullName> is called and then re-selecting them after the call is completed.</span></span> <span data-ttu-id="06878-108">Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06878-108">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="06878-109">Nome</span><span class="sxs-lookup"><span data-stu-id="06878-109">Name</span></span>    | <span data-ttu-id="06878-110">Valor</span><span class="sxs-lookup"><span data-stu-id="06878-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="06878-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="06878-111">Scope</span></span>   |<span data-ttu-id="06878-112">Secundária</span><span class="sxs-lookup"><span data-stu-id="06878-112">Minor</span></span>|
|<span data-ttu-id="06878-113">Versão</span><span class="sxs-lookup"><span data-stu-id="06878-113">Version</span></span>|<span data-ttu-id="06878-114">4.5</span><span class="sxs-lookup"><span data-stu-id="06878-114">4.5</span></span>|
|<span data-ttu-id="06878-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="06878-115">Type</span></span>|<span data-ttu-id="06878-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="06878-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="06878-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="06878-117">Affected APIs</span></span>

- <xref:System.Windows.Data.CollectionView.Refresh?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Data.CollectionView.Refresh`

-->
