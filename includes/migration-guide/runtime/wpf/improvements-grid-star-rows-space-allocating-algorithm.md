---
ms.openlocfilehash: 415eb1960c20fb662469e126560d6f366309eb0d
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496378"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="07f6f-101">Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade</span><span class="sxs-lookup"><span data-stu-id="07f6f-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="07f6f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="07f6f-102">Details</span></span>

<span data-ttu-id="07f6f-103">Correção de um bug no [algoritmo para alocar tamanhos](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="07f6f-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="07f6f-104">Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.</span><span class="sxs-lookup"><span data-stu-id="07f6f-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="07f6f-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="07f6f-105">Suggestion</span></span>

<span data-ttu-id="07f6f-106">Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="07f6f-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="07f6f-107">Nome</span><span class="sxs-lookup"><span data-stu-id="07f6f-107">Name</span></span>    | <span data-ttu-id="07f6f-108">Valor</span><span class="sxs-lookup"><span data-stu-id="07f6f-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="07f6f-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="07f6f-109">Scope</span></span>   |<span data-ttu-id="07f6f-110">Principal</span><span class="sxs-lookup"><span data-stu-id="07f6f-110">Major</span></span>|
|<span data-ttu-id="07f6f-111">Versão</span><span class="sxs-lookup"><span data-stu-id="07f6f-111">Version</span></span>|<span data-ttu-id="07f6f-112">4.8</span><span class="sxs-lookup"><span data-stu-id="07f6f-112">4.8</span></span>|
|<span data-ttu-id="07f6f-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="07f6f-113">Type</span></span>|<span data-ttu-id="07f6f-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="07f6f-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="07f6f-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="07f6f-115">Affected APIs</span></span>

<span data-ttu-id="07f6f-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="07f6f-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
