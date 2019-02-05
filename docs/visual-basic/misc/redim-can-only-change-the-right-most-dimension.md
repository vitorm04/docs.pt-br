---
title: "'ReDim' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: d20d0374cd5183b6216d1c6e5b138256cf0a4f17
ms.sourcegitcommit: facefcacd7ae2e5645e463bc841df213c505ffd4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55738949"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="807d8-102">'ReDim' só pode alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="807d8-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="807d8-103">Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão.</span><span class="sxs-lookup"><span data-stu-id="807d8-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="807d8-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="807d8-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="807d8-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="807d8-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="807d8-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="807d8-106">To correct this error</span></span>  
  
-   <span data-ttu-id="807d8-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="807d8-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="807d8-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="807d8-108">See also</span></span>
- [<span data-ttu-id="807d8-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="807d8-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="807d8-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="807d8-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="807d8-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="807d8-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="807d8-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="807d8-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
