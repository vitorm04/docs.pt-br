---
title: "&#39; ReDim &#39; só é possível alterar a dimensão mais à direita"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="1301a-102">&#39; ReDim &#39; só é possível alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="1301a-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="1301a-103">Um `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não é da última dimensão.</span><span class="sxs-lookup"><span data-stu-id="1301a-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="1301a-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="1301a-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="1301a-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="1301a-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1301a-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="1301a-106">To correct this error</span></span>  
  
-   <span data-ttu-id="1301a-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="1301a-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1301a-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1301a-108">See Also</span></span>  
 [<span data-ttu-id="1301a-109">Matrizes no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1301a-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="1301a-110">Dimensões de matriz no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1301a-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="1301a-111">Instrução ReDim</span><span class="sxs-lookup"><span data-stu-id="1301a-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="1301a-112">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="1301a-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="1301a-113">Preservar - excluir</span><span class="sxs-lookup"><span data-stu-id="1301a-113">Preserve - delete</span></span>](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
