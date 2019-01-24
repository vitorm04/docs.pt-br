---
title: "'ReDim' não é possível alterar o número de dimensões"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 80546b427afdafaf6e9fcea493d58cf1019e79e9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54638451"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="7fbe2-102">'ReDim' não é possível alterar o número de dimensões</span><span class="sxs-lookup"><span data-stu-id="7fbe2-102">'ReDim' cannot change the number of dimensions</span></span>
<span data-ttu-id="7fbe2-103">Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="7fbe2-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="7fbe2-104">`ReDim` pode alterar o tamanho de uma ou mais dimensões de uma matriz que já foi formalmente declarado, mas ele não é possível alterar a classificação de matriz.</span><span class="sxs-lookup"><span data-stu-id="7fbe2-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7fbe2-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7fbe2-105">To correct this error</span></span>  
  
-   <span data-ttu-id="7fbe2-106">Certifique-se de que você pretende alterar a classificação da matriz e não os tamanhos das suas dimensões e, se possível, use `Dim` para declarar uma nova matriz com a classificação desejada.</span><span class="sxs-lookup"><span data-stu-id="7fbe2-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fbe2-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fbe2-107">See also</span></span>
- [<span data-ttu-id="7fbe2-108">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fbe2-108">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="7fbe2-109">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fbe2-109">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="7fbe2-110">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="7fbe2-110">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="7fbe2-111">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="7fbe2-111">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
