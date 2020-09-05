---
ms.openlocfilehash: 196b6a13d32c7767b858d6d68ca775eb49324805
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496889"
---
### <a name="listboxitem-isselected-binding-issue-with-observablecollectionlttgtmove"></a><span data-ttu-id="1f643-101">Problema de associação de ListBoxItem IsSelected com ObservableCollection&lt;T&gt;.Move</span><span class="sxs-lookup"><span data-stu-id="1f643-101">ListBoxItem IsSelected binding issue with ObservableCollection&lt;T&gt;.Move</span></span>

#### <a name="details"></a><span data-ttu-id="1f643-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1f643-102">Details</span></span>

<span data-ttu-id="1f643-103">Chamar <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> ou <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> em uma coleção associada a um <xref:System.Windows.Controls.ListBox?displayProperty=fullName> com itens selecionados pode gerar comportamento imprevisível em seleções ou cancelamentos de seleção futuros de itens <xref:System.Windows.Controls.ListBox?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1f643-103">Calling <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> or <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)> on a collection bound to a <xref:System.Windows.Controls.ListBox?displayProperty=fullName> with items selected can lead to erratic behavior with future selection or unselection of <xref:System.Windows.Controls.ListBox?displayProperty=fullName> items.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1f643-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1f643-104">Suggestion</span></span>

<span data-ttu-id="1f643-105">Chamar <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> e <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> em vez de <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> é uma solução alternativa para esse problema.</span><span class="sxs-lookup"><span data-stu-id="1f643-105">Calling <xref:System.Collections.ObjectModel.Collection%601.Remove(%600)?displayProperty=fullName> and <xref:System.Collections.ObjectModel.Collection%601.Insert(System.Int32,%600)?displayProperty=fullName> instead of <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)> will work around this issue.</span></span> <span data-ttu-id="1f643-106">Como alternativa, esse problema foi corrigido no .NET Framework 4.6 e pode ser resolvido com o upgrade para essa versão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1f643-106">Alternatively, this issue has been fixed in the .NET Framework 4.6 and may be addressed by upgrading to that version of the .NET Framework.</span></span>

| <span data-ttu-id="1f643-107">Nome</span><span class="sxs-lookup"><span data-stu-id="1f643-107">Name</span></span>    | <span data-ttu-id="1f643-108">Valor</span><span class="sxs-lookup"><span data-stu-id="1f643-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1f643-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="1f643-109">Scope</span></span>   |<span data-ttu-id="1f643-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="1f643-110">Minor</span></span>|
|<span data-ttu-id="1f643-111">Versão</span><span class="sxs-lookup"><span data-stu-id="1f643-111">Version</span></span>|<span data-ttu-id="1f643-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1f643-112">4.5</span></span>|
|<span data-ttu-id="1f643-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="1f643-113">Type</span></span>|<span data-ttu-id="1f643-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="1f643-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1f643-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1f643-115">Affected APIs</span></span>

- <xref:System.Collections.ObjectModel.ObservableCollection%601.Move(System.Int32,System.Int32)?displayProperty=nameWithType>
- <xref:System.Collections.ObjectModel.ObservableCollection%601.MoveItem(System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

#### Affected APIs

- ``M:System.Collections.ObjectModel.ObservableCollection`1.Move(System.Int32,System.Int32)``
- ``M:System.Collections.ObjectModel.ObservableCollection`1.MoveItem(System.Int32,System.Int32)``

-->
