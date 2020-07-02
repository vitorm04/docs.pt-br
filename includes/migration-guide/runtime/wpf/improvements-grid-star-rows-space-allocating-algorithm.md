---
ms.openlocfilehash: 62702de022656e45466a45f4150e518226a3fecc
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621913"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="cc3fe-101">Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade</span><span class="sxs-lookup"><span data-stu-id="cc3fe-101">Improvements to Grid star-rows space allocating algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="cc3fe-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="cc3fe-102">Details</span></span>

<span data-ttu-id="cc3fe-103">Correção de um bug no [algoritmo para alocar tamanhos](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="cc3fe-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="cc3fe-104">Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.</span><span class="sxs-lookup"><span data-stu-id="cc3fe-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="cc3fe-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="cc3fe-105">Suggestion</span></span>

<span data-ttu-id="cc3fe-106">Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="cc3fe-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>

| <span data-ttu-id="cc3fe-107">Name</span><span class="sxs-lookup"><span data-stu-id="cc3fe-107">Name</span></span>    | <span data-ttu-id="cc3fe-108">Valor</span><span class="sxs-lookup"><span data-stu-id="cc3fe-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="cc3fe-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="cc3fe-109">Scope</span></span>   |<span data-ttu-id="cc3fe-110">Principal</span><span class="sxs-lookup"><span data-stu-id="cc3fe-110">Major</span></span>|
|<span data-ttu-id="cc3fe-111">Versão</span><span class="sxs-lookup"><span data-stu-id="cc3fe-111">Version</span></span>|<span data-ttu-id="cc3fe-112">4.8</span><span class="sxs-lookup"><span data-stu-id="cc3fe-112">4.8</span></span>|
|<span data-ttu-id="cc3fe-113">Type</span><span class="sxs-lookup"><span data-stu-id="cc3fe-113">Type</span></span>|<span data-ttu-id="cc3fe-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="cc3fe-114">Runtime</span></span>|
