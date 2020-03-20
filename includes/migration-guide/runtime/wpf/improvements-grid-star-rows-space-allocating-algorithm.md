---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68237611"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="509ac-101">Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade</span><span class="sxs-lookup"><span data-stu-id="509ac-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="509ac-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="509ac-102">Details</span></span>|<span data-ttu-id="509ac-103">Correção de um bug no [algoritmo para alocar tamanhos](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="509ac-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="509ac-104">Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.</span><span class="sxs-lookup"><span data-stu-id="509ac-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="509ac-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="509ac-105">Suggestion</span></span>|<span data-ttu-id="509ac-106">Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="509ac-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="509ac-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="509ac-107">Scope</span></span>|<span data-ttu-id="509ac-108">Principal</span><span class="sxs-lookup"><span data-stu-id="509ac-108">Major</span></span>|
|<span data-ttu-id="509ac-109">Versão</span><span class="sxs-lookup"><span data-stu-id="509ac-109">Version</span></span>|<span data-ttu-id="509ac-110">4.8</span><span class="sxs-lookup"><span data-stu-id="509ac-110">4.8</span></span>|
|<span data-ttu-id="509ac-111">Type</span><span class="sxs-lookup"><span data-stu-id="509ac-111">Type</span></span>|<span data-ttu-id="509ac-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="509ac-112">Runtime</span></span>|
