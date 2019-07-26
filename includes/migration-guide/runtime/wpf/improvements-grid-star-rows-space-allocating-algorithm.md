---
ms.openlocfilehash: 8e0c934cd8c3cb8c08a526c7e145436db6ecf4a5
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68237611"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="815cb-101">Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade</span><span class="sxs-lookup"><span data-stu-id="815cb-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="815cb-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="815cb-102">Details</span></span>|<span data-ttu-id="815cb-103">Correção de um bug no [algoritmo para alocar tamanhos](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="815cb-103">Fixed a bug in the [algorithm for allocating sizes to](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="815cb-104">Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.</span><span class="sxs-lookup"><span data-stu-id="815cb-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="815cb-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="815cb-105">Suggestion</span></span>|<span data-ttu-id="815cb-106">Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="815cb-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="815cb-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="815cb-107">Scope</span></span>|<span data-ttu-id="815cb-108">Principal</span><span class="sxs-lookup"><span data-stu-id="815cb-108">Major</span></span>|
|<span data-ttu-id="815cb-109">Versão</span><span class="sxs-lookup"><span data-stu-id="815cb-109">Version</span></span>|<span data-ttu-id="815cb-110">4.8</span><span class="sxs-lookup"><span data-stu-id="815cb-110">4.8</span></span>|
|<span data-ttu-id="815cb-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="815cb-111">Type</span></span>|<span data-ttu-id="815cb-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="815cb-112">Runtime</span></span>|
