---
title: "'ReDim' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 86d639e70e85b19a91f89fa4e0cab330af07dccf
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2019
ms.locfileid: "58028825"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="5534e-102">'ReDim' só pode alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="5534e-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="5534e-103">Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão.</span><span class="sxs-lookup"><span data-stu-id="5534e-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="5534e-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="5534e-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="5534e-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="5534e-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5534e-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5534e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5534e-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5534e-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5534e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5534e-108">See also</span></span>

- [<span data-ttu-id="5534e-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5534e-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="5534e-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5534e-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="5534e-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="5534e-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)
- [<span data-ttu-id="5534e-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="5534e-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)
