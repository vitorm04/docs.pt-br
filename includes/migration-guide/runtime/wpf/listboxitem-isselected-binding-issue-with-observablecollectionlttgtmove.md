---
ms.openlocfilehash: f4ff938b2d0e9ead481fdf239aed8a6b918a99b0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619888"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="2ed64-101">Problema de associação de ListBoxItem IsSelected com ObservableCollection&lt;T&gt;.Move</span><span class="sxs-lookup"><span data-stu-id="2ed64-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="2ed64-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="2ed64-102">Details</span></span>

<span data-ttu-id="2ed64-103">Chamar <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> em uma coleção associada a um <xref:System.Windows.Controls.ListBox?displayProperty=fullName> com itens selecionados pode gerar comportamento imprevisível em seleções ou cancelamentos de seleção futuros de itens <xref:System.Windows.Controls.ListBox?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="2ed64-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2ed64-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="2ed64-104">Suggestion</span></span>

<span data-ttu-id="2ed64-105">Chamar <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> e <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> em vez de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> é uma solução alternativa para esse problema.</span><span class="sxs-lookup"><span data-stu-id="2ed64-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="2ed64-106">Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2ed64-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="2ed64-107">Name</span><span class="sxs-lookup"><span data-stu-id="2ed64-107">Name</span></span>    | <span data-ttu-id="2ed64-108">Valor</span><span class="sxs-lookup"><span data-stu-id="2ed64-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2ed64-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="2ed64-109">Scope</span></span>   |<span data-ttu-id="2ed64-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="2ed64-110">Minor</span></span>|
|<span data-ttu-id="2ed64-111">Versão</span><span class="sxs-lookup"><span data-stu-id="2ed64-111">Version</span></span>|<span data-ttu-id="2ed64-112">4.5</span><span class="sxs-lookup"><span data-stu-id="2ed64-112">4.5</span></span>|
|<span data-ttu-id="2ed64-113">Type</span><span class="sxs-lookup"><span data-stu-id="2ed64-113">Type</span></span>|<span data-ttu-id="2ed64-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="2ed64-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2ed64-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="2ed64-115">Affected APIs</span></span>

-<xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType></li><li><xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType></li></ul>|
