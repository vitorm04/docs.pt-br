---
ms.openlocfilehash: d23d7821e19b9d7f2db13a6bfdf868a8414cf721
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497672"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a><span data-ttu-id="68cb6-101">Rolagem de itens em uma lista simples de itens com diferentes alturas em pixels</span><span class="sxs-lookup"><span data-stu-id="68cb6-101">Item-scrolling a flat list with items of different pixel-height</span></span>

#### <a name="details"></a><span data-ttu-id="68cb6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="68cb6-102">Details</span></span>

<span data-ttu-id="68cb6-103">Quando um <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> exibe uma coleção usando virtualização (<code>IsVirtualizing=true</code>) e rolagem de itens (<code>ScrollUnit=Item</code>) e quando o controle rola para exibir um item cuja altura em pixels é diferente de seus vizinhos, o <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> itera em todos os itens na coleção.</span><span class="sxs-lookup"><span data-stu-id="68cb6-103">When an <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> displays a collection using virtualization (<code>IsVirtualizing=true</code>) and item- scrolling (<code>ScrollUnit=Item</code>), and when the control scrolls to display an item whose height in pixels differs from its neighbors, the <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=fullName> iterates over all items in the collection.</span></span> <span data-ttu-id="68cb6-104">A interface do usuário não está respondendo durante essa iteração; se a coleção for grande, isso poderá ser percebido como uma parada.</span><span class="sxs-lookup"><span data-stu-id="68cb6-104">The UI is unresponsive during this iteration; if the collection is large, this can be perceived as a hang.</span></span> <span data-ttu-id="68cb6-105">A iteração ocorre em outras circunstâncias, mesmo nas versões anteriores do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="68cb6-105">The iteration occurs in other circumstances, even in previous .NET Framework releases.</span></span> <span data-ttu-id="68cb6-106">Por exemplo, isso ocorre na rolagem de pixels (<code>ScrollUnit=Pixel</code>) ao encontrar um item com uma altura de pixels diferente e na rolagem de itens de dados hierárquicos (como em um <xref:System.Windows.Controls.TreeView?displayProperty=fullName> ou um <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> com o agrupamento habilitado) ao encontrar um item com um número de itens descendentes diferentes de seus vizinhos. Para o caso em que há rolagem de itens e diferentes alturas em pixels, a iteração foi introduzida no .NET Framework 4.6.1 para corrigir bugs no layout de dados hierárquicos.</span><span class="sxs-lookup"><span data-stu-id="68cb6-106">For example, it occurs when pixel-scrolling (<code>ScrollUnit=Pixel</code>) upon encountering an item with different pixel height, and when item-scrolling hierarchical data (such as a <xref:System.Windows.Controls.TreeView?displayProperty=fullName> or an <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> with grouping enabled) upon encountering an item with a different number of descendant items than its neighbors.For the case of item-scrolling and different pixel height, the iteration was introduced in .NET Framework 4.6.1 to fix bugs in the layout of hierarchical data.</span></span>  <span data-ttu-id="68cb6-107">Ela não será necessária se os dados forem simples (sem hierarquia) e, nesse caso, ela não ocorre no .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="68cb6-107">It is not needed if the data is flat (no hierarchy), and .NET Framework 4.6.2 does not do it in that case.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="68cb6-108">Sugestão</span><span class="sxs-lookup"><span data-stu-id="68cb6-108">Suggestion</span></span>

<span data-ttu-id="68cb6-109">Se a iteração ocorrer no .NET Framework 4.6.1, mas não nas versões anteriores, ou seja, se o <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> for uma lista plana de rolagem de item com itens de alturas em pixels diferentes, haverá duas soluções:</span><span class="sxs-lookup"><span data-stu-id="68cb6-109">If the iteration occurs in .NET Framework 4.6.1 but not in earlier releases - that is, if the <xref:System.Windows.Controls.ItemsControl?displayProperty=fullName> is item- scrolling a flat list with items of different pixel height - there are two remedies:</span></span><ol><li><span data-ttu-id="68cb6-110">Instalar o .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="68cb6-110">Install .NET Framework 4.6.2.</span></span></li><li><span data-ttu-id="68cb6-111">Instalar o hotfix HR 1605 para o .NET Framework 4.6.1.</span><span class="sxs-lookup"><span data-stu-id="68cb6-111">Install hotfix HR 1605 for .NET Framework 4.6.1.</span></span></li></ol>

| <span data-ttu-id="68cb6-112">Nome</span><span class="sxs-lookup"><span data-stu-id="68cb6-112">Name</span></span>    | <span data-ttu-id="68cb6-113">Valor</span><span class="sxs-lookup"><span data-stu-id="68cb6-113">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="68cb6-114">Escopo</span><span class="sxs-lookup"><span data-stu-id="68cb6-114">Scope</span></span>   |<span data-ttu-id="68cb6-115">Secundária</span><span class="sxs-lookup"><span data-stu-id="68cb6-115">Minor</span></span>|
|<span data-ttu-id="68cb6-116">Versão</span><span class="sxs-lookup"><span data-stu-id="68cb6-116">Version</span></span>|<span data-ttu-id="68cb6-117">4.6.1</span><span class="sxs-lookup"><span data-stu-id="68cb6-117">4.6.1</span></span>|
|<span data-ttu-id="68cb6-118">Tipo</span><span class="sxs-lookup"><span data-stu-id="68cb6-118">Type</span></span>|<span data-ttu-id="68cb6-119">Runtime</span><span class="sxs-lookup"><span data-stu-id="68cb6-119">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="68cb6-120">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="68cb6-120">Affected APIs</span></span>

- <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.VirtualizingStackPanel`

-->
