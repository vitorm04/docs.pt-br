---
title: "' ReDim ' não pode alterar o número de dimensões"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: fb60c93f988ca40305f13cca07f55a70bd779081
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664393"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="9602c-102">' ReDim ' não pode alterar o número de dimensões</span><span class="sxs-lookup"><span data-stu-id="9602c-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="9602c-103">Uma operação tenta usar a `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9602c-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="9602c-104">`ReDim`pode alterar o tamanho de uma ou mais dimensões de uma matriz que já foi formalmente declarada, mas não pode alterar a classificação de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="9602c-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9602c-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9602c-105">To correct this error</span></span>  
  
- <span data-ttu-id="9602c-106">Certifique-se de que você pretende alterar a classificação da matriz e não os tamanhos de suas dimensões e, se possível `Dim` , use para declarar uma nova matriz com a classificação desejada.</span><span class="sxs-lookup"><span data-stu-id="9602c-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9602c-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9602c-107">See also</span></span>

- [<span data-ttu-id="9602c-108">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9602c-108">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="9602c-109">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9602c-109">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="9602c-110">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="9602c-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="9602c-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="9602c-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
