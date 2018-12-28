---
title: "'ReDim' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 5b4f054c5d1dfad52ce19e1a9f9d246945866703
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767382"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="b9a6f-102">'ReDim' só pode alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="b9a6f-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="b9a6f-103">Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="b9a6f-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="b9a6f-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b9a6f-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b9a6f-106">To correct this error</span></span>  
  
-   <span data-ttu-id="b9a6f-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b9a6f-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9a6f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9a6f-108">See Also</span></span>  
 [<span data-ttu-id="b9a6f-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9a6f-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="b9a6f-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9a6f-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="b9a6f-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="b9a6f-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="b9a6f-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="b9a6f-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="b9a6f-113">Preservar - excluir</span><span class="sxs-lookup"><span data-stu-id="b9a6f-113">Preserve - delete</span></span>](https://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
