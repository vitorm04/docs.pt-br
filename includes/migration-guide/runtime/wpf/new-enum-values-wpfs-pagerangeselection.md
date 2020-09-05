---
ms.openlocfilehash: 61749f59f9379a6d18bb013b2612a07cb7822b3a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496270"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="1a8aa-101">Novos valores de enumeração em PageRangeSelection do WPF</span><span class="sxs-lookup"><span data-stu-id="1a8aa-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="1a8aa-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="1a8aa-102">Details</span></span>

<span data-ttu-id="1a8aa-103">Os dois novos membros (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> e <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) foram adicionados à enumeração <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="1a8aa-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1a8aa-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="1a8aa-104">Suggestion</span></span>

<span data-ttu-id="1a8aa-105">Na maioria das vezes, essas mudanças não afetarão o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="1a8aa-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="1a8aa-106">O código que depende de um número específico de elementos existentes nas chamadas <xref:System.Enum.GetNames(System.Type)> ou <xref:System.Enum.GetValues(System.Type)> no tipo <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> deve ser modificado.</span><span class="sxs-lookup"><span data-stu-id="1a8aa-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="1a8aa-107">Nome</span><span class="sxs-lookup"><span data-stu-id="1a8aa-107">Name</span></span>    | <span data-ttu-id="1a8aa-108">Valor</span><span class="sxs-lookup"><span data-stu-id="1a8aa-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1a8aa-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="1a8aa-109">Scope</span></span>   |<span data-ttu-id="1a8aa-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="1a8aa-110">Edge</span></span>|
|<span data-ttu-id="1a8aa-111">Versão</span><span class="sxs-lookup"><span data-stu-id="1a8aa-111">Version</span></span>|<span data-ttu-id="1a8aa-112">4.5</span><span class="sxs-lookup"><span data-stu-id="1a8aa-112">4.5</span></span>|
|<span data-ttu-id="1a8aa-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="1a8aa-113">Type</span></span>|<span data-ttu-id="1a8aa-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="1a8aa-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="1a8aa-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1a8aa-115">Affected APIs</span></span>

- <xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Windows.Controls.PageRangeSelection`

-->
