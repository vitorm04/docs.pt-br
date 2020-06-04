---
title: "'ReDim' só pode alterar a dimensão mais à direita"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 8e42e0df7b97fb96f468ce37dd4cfc52fad8c596
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84358290"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="27ced-102">'ReDim' só pode alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="27ced-102">'ReDim' can only change the right-most dimension</span></span>
<span data-ttu-id="27ced-103">Uma `ReDim` instrução tentou usar a `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é a última dimensão.</span><span class="sxs-lookup"><span data-stu-id="27ced-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="27ced-104">Ao usar `Preserve` o, você pode redimensionar apenas a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="27ced-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="27ced-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de para a matriz existente.</span><span class="sxs-lookup"><span data-stu-id="27ced-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="27ced-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="27ced-106">To correct this error</span></span>  
  
- <span data-ttu-id="27ced-107">Remova a `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="27ced-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ced-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="27ced-108">See also</span></span>

- [<span data-ttu-id="27ced-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27ced-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="27ced-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27ced-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="27ced-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="27ced-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="27ced-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="27ced-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
