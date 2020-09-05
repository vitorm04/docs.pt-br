---
ms.openlocfilehash: 31ada197db36be192317e32a37a353d375d9cc65
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496506"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="78e1c-101">Rolar em uma TreeView ou ListBox agrupada no WPF em um VirtualizingStackPanel pode causar travamento</span><span class="sxs-lookup"><span data-stu-id="78e1c-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="78e1c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="78e1c-102">Details</span></span>

<span data-ttu-id="78e1c-103">No .NET Framework v4.5, rolar em uma <xref:System.Windows.Controls.TreeView?displayProperty=fullName> do WPF em um painel de pilha virtualizado poderá causar travamentos se houver margens no visor (entre os itens na <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, por exemplo, ou em um elemento ItemsPresenter).</span><span class="sxs-lookup"><span data-stu-id="78e1c-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="78e1c-104">Além disso, em alguns casos, itens de tamanhos diferentes no modo de exibição podem causar instabilidade, mesmo se não houver margens.</span><span class="sxs-lookup"><span data-stu-id="78e1c-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="78e1c-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="78e1c-105">Suggestion</span></span>

<span data-ttu-id="78e1c-106">Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="78e1c-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="78e1c-107">Como alternativa, as margens poderão ser removidas das coleções de exibições (como <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) em painéis de pilha virtualizados se todos os itens contidos forem do mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="78e1c-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="78e1c-108">Nome</span><span class="sxs-lookup"><span data-stu-id="78e1c-108">Name</span></span>    | <span data-ttu-id="78e1c-109">Valor</span><span class="sxs-lookup"><span data-stu-id="78e1c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="78e1c-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="78e1c-110">Scope</span></span>   |<span data-ttu-id="78e1c-111">Principal</span><span class="sxs-lookup"><span data-stu-id="78e1c-111">Major</span></span>|
|<span data-ttu-id="78e1c-112">Versão</span><span class="sxs-lookup"><span data-stu-id="78e1c-112">Version</span></span>|<span data-ttu-id="78e1c-113">4.5</span><span class="sxs-lookup"><span data-stu-id="78e1c-113">4.5</span></span>|
|<span data-ttu-id="78e1c-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="78e1c-114">Type</span></span>|<span data-ttu-id="78e1c-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="78e1c-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="78e1c-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="78e1c-116">Affected APIs</span></span>

- <xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)`

-->
