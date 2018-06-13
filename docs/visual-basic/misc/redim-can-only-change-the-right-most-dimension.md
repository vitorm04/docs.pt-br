---
title: '&#39;ReDim&#39; só pode alterar a dimensão mais à direita'
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: efb98df13a7e3e378347b30b6fc00b90030ec194
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33641177"
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="5fa86-102">&#39;ReDim&#39; só pode alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="5fa86-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="5fa86-103">Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é da última dimensão.</span><span class="sxs-lookup"><span data-stu-id="5fa86-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="5fa86-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="5fa86-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="5fa86-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="5fa86-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5fa86-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5fa86-106">To correct this error</span></span>  
  
-   <span data-ttu-id="5fa86-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="5fa86-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fa86-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5fa86-108">See Also</span></span>  
 [<span data-ttu-id="5fa86-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fa86-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="5fa86-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fa86-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="5fa86-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="5fa86-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="5fa86-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="5fa86-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="5fa86-113">Preservar - excluir</span><span class="sxs-lookup"><span data-stu-id="5fa86-113">Preserve - delete</span></span>](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
