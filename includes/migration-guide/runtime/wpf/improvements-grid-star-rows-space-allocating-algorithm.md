---
ms.openlocfilehash: 770e303ab261b97efb49a3e0865a015d8de33247
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802643"
---
### <a name="improvements-to-grid-star-rows-space-allocating-algorithm"></a><span data-ttu-id="7c82f-101">Melhorias no algoritmo de alocação de espaço de linhas de estrela da grade</span><span class="sxs-lookup"><span data-stu-id="7c82f-101">Improvements to Grid star-rows space allocating algorithm</span></span>

|   |   |
|---|---|
|<span data-ttu-id="7c82f-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="7c82f-102">Details</span></span>|<span data-ttu-id="7c82f-103">Correção de um bug no [algoritmo para alocar tamanhos a ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) em um <xref:System.Windows.Controls.Grid> introduzido no .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="7c82f-103">Fixed a bug in the [algorithm for allocating sizes to ](https://github.com/Microsoft/dotnet/blob/master/Documentation/compatibility/wpf-grid-allocation-of-space-to-star-columns.md)) in a <xref:System.Windows.Controls.Grid> introduced in .NET Framework 4.7.</span></span>  <span data-ttu-id="7c82f-104">Em alguns casos, como uma grade com <code>Height=&quot;Auto&quot;</code> contendo linhas vazias, as linhas foram organizadas na posição incorreta, possivelmente fora da grade.</span><span class="sxs-lookup"><span data-stu-id="7c82f-104">In some cases, such as a Grid with <code>Height=&quot;Auto&quot;</code> containing empty rows, rows were arranged at the wrong position, possibly outside the Grid altogether.</span></span>|
|<span data-ttu-id="7c82f-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="7c82f-105">Suggestion</span></span>|<span data-ttu-id="7c82f-106">Para que o aplicativo se beneficie dessas alterações, ele deve ser executado no .NET Framework 4.8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="7c82f-106">In order for the application to benefit from these changes, it must run on the .NET Framework 4.8 or later.</span></span>|
|<span data-ttu-id="7c82f-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="7c82f-107">Scope</span></span>|<span data-ttu-id="7c82f-108">Principal</span><span class="sxs-lookup"><span data-stu-id="7c82f-108">Major</span></span>|
|<span data-ttu-id="7c82f-109">Versão</span><span class="sxs-lookup"><span data-stu-id="7c82f-109">Version</span></span>|<span data-ttu-id="7c82f-110">4.8</span><span class="sxs-lookup"><span data-stu-id="7c82f-110">4.8</span></span>|
|<span data-ttu-id="7c82f-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="7c82f-111">Type</span></span>|<span data-ttu-id="7c82f-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="7c82f-112">Runtime</span></span>|

