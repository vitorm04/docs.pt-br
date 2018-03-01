---
title: "&#39; ReDim &#39; só é possível alterar a dimensão mais à direita"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 752e0e54c48b3b348a477787e5e911f1b1777667
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="ff0e4-102">&#39; ReDim &#39; só é possível alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="ff0e4-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="ff0e4-103">Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é da última dimensão.</span><span class="sxs-lookup"><span data-stu-id="ff0e4-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="ff0e4-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="ff0e4-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="ff0e4-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="ff0e4-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ff0e4-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="ff0e4-106">To correct this error</span></span>  
  
-   <span data-ttu-id="ff0e4-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="ff0e4-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff0e4-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff0e4-108">See Also</span></span>  
 [<span data-ttu-id="ff0e4-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff0e4-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="ff0e4-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ff0e4-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="ff0e4-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="ff0e4-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="ff0e4-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="ff0e4-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="ff0e4-113">Preservar - excluir</span><span class="sxs-lookup"><span data-stu-id="ff0e4-113">Preserve - delete</span></span>](http://msdn.microsoft.com/library/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
