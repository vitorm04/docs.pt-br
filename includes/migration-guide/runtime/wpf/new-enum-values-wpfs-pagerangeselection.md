---
ms.openlocfilehash: bae6d7c0f8843211c721c68ce6f16000b35b4401
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619891"
---
### <a name="new-enum-values-in-wpfs-pagerangeselection"></a><span data-ttu-id="35ef0-101">Novos valores de enumeração em PageRangeSelection do WPF</span><span class="sxs-lookup"><span data-stu-id="35ef0-101">New enum values in WPF's PageRangeSelection</span></span>

#### <a name="details"></a><span data-ttu-id="35ef0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="35ef0-102">Details</span></span>

<span data-ttu-id="35ef0-103">Os dois novos membros (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> e <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) foram adicionados à enumeração <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="35ef0-103">Two new members (<xref:System.Windows.Controls.PageRangeSelection.CurrentPage?displayProperty=fullName> and <xref:System.Windows.Controls.PageRangeSelection.SelectedPages?displayProperty=fullName>) have been added to the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> enum.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="35ef0-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="35ef0-104">Suggestion</span></span>

<span data-ttu-id="35ef0-105">Na maioria das vezes, essas mudanças não afetarão o código do usuário.</span><span class="sxs-lookup"><span data-stu-id="35ef0-105">In most cases, these changes won't impact user code.</span></span> <span data-ttu-id="35ef0-106">O código que depende de um número específico de elementos existentes nas chamadas <xref:System.Enum.GetNames(System.Type)> ou <xref:System.Enum.GetValues(System.Type)> no tipo <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> deve ser modificado.</span><span class="sxs-lookup"><span data-stu-id="35ef0-106">Code that depends on a particular number of elements existing in <xref:System.Enum.GetNames(System.Type)> or <xref:System.Enum.GetValues(System.Type)> calls on the <xref:System.Windows.Controls.PageRangeSelection?displayProperty=fullName> type should be modified, though.</span></span>

| <span data-ttu-id="35ef0-107">Name</span><span class="sxs-lookup"><span data-stu-id="35ef0-107">Name</span></span>    | <span data-ttu-id="35ef0-108">Valor</span><span class="sxs-lookup"><span data-stu-id="35ef0-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="35ef0-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="35ef0-109">Scope</span></span>   |<span data-ttu-id="35ef0-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="35ef0-110">Edge</span></span>|
|<span data-ttu-id="35ef0-111">Versão</span><span class="sxs-lookup"><span data-stu-id="35ef0-111">Version</span></span>|<span data-ttu-id="35ef0-112">4.5</span><span class="sxs-lookup"><span data-stu-id="35ef0-112">4.5</span></span>|
|<span data-ttu-id="35ef0-113">Type</span><span class="sxs-lookup"><span data-stu-id="35ef0-113">Type</span></span>|<span data-ttu-id="35ef0-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="35ef0-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="35ef0-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="35ef0-115">Affected APIs</span></span>

-<xref:System.Windows.Controls.PageRangeSelection?displayProperty=nameWithType></li></ul>|
