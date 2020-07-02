---
ms.openlocfilehash: 1be68c2968d0eaa9024007bcf37abf9e44c36f1c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621924"
---
### <a name="scrolling-a-wpf-treeview-or-grouped-listbox-in-a-virtualizingstackpanel-can-cause-a-hang"></a><span data-ttu-id="ed01e-101">Rolar em uma TreeView ou ListBox agrupada no WPF em um VirtualizingStackPanel pode causar travamento</span><span class="sxs-lookup"><span data-stu-id="ed01e-101">Scrolling a WPF TreeView or grouped ListBox in a VirtualizingStackPanel can cause a hang</span></span>

#### <a name="details"></a><span data-ttu-id="ed01e-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ed01e-102">Details</span></span>

<span data-ttu-id="ed01e-103">No .NET Framework v4.5, rolar em uma <xref:System.Windows.Controls.TreeView?displayProperty=fullName> do WPF em um painel de pilha virtualizado poderá causar travamentos se houver margens no visor (entre os itens na <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, por exemplo, ou em um elemento ItemsPresenter).</span><span class="sxs-lookup"><span data-stu-id="ed01e-103">In the .NET Framework v4.5, scrolling a WPF <xref:System.Windows.Controls.TreeView?displayProperty=fullName> in a virtualized stack panel can cause hangs if there are margins in the viewport (between the items in the <xref:System.Windows.Controls.TreeView?displayProperty=fullName>, for example, or on an ItemsPresenter element).</span></span> <span data-ttu-id="ed01e-104">Além disso, em alguns casos, itens de tamanhos diferentes no modo de exibição podem causar instabilidade, mesmo se não houver margens.</span><span class="sxs-lookup"><span data-stu-id="ed01e-104">Additionally, in some cases, different sized items in the view can cause instability even if there are no margins.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ed01e-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ed01e-105">Suggestion</span></span>

<span data-ttu-id="ed01e-106">Esse bug pode ser evitado com a o upgrade para o .NET Framework 4.5.1.</span><span class="sxs-lookup"><span data-stu-id="ed01e-106">This bug can be avoided by upgrading to .NET Framework 4.5.1.</span></span> <span data-ttu-id="ed01e-107">Como alternativa, as margens poderão ser removidas das coleções de exibições (como <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) em painéis de pilha virtualizados se todos os itens contidos forem do mesmo tamanho.</span><span class="sxs-lookup"><span data-stu-id="ed01e-107">Alternatively, margins can be removed from view collections (like <xref:System.Windows.Controls.TreeView?displayProperty=fullName>s) within virtualized stack panels if all contained items are the same size.</span></span>

| <span data-ttu-id="ed01e-108">Name</span><span class="sxs-lookup"><span data-stu-id="ed01e-108">Name</span></span>    | <span data-ttu-id="ed01e-109">Valor</span><span class="sxs-lookup"><span data-stu-id="ed01e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ed01e-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="ed01e-110">Scope</span></span>   |<span data-ttu-id="ed01e-111">Principal</span><span class="sxs-lookup"><span data-stu-id="ed01e-111">Major</span></span>|
|<span data-ttu-id="ed01e-112">Versão</span><span class="sxs-lookup"><span data-stu-id="ed01e-112">Version</span></span>|<span data-ttu-id="ed01e-113">4.5</span><span class="sxs-lookup"><span data-stu-id="ed01e-113">4.5</span></span>|
|<span data-ttu-id="ed01e-114">Type</span><span class="sxs-lookup"><span data-stu-id="ed01e-114">Type</span></span>|<span data-ttu-id="ed01e-115">Runtime</span><span class="sxs-lookup"><span data-stu-id="ed01e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ed01e-116">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ed01e-116">Affected APIs</span></span>

-<xref:System.Windows.Controls.VirtualizingStackPanel.SetIsVirtualizing(System.Windows.DependencyObject,System.Boolean)?displayProperty=nameWithType></li></ul>|
