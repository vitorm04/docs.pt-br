---
title: "&quot;ReDim&quot; só pode alterar a dimensão mais à direita | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 339a011b979f1f541c92a995cf46071264cce4bb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="e253e-102">'ReDim' só pode alterar a dimensão mais à direita</span><span class="sxs-lookup"><span data-stu-id="e253e-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="e253e-103">A `ReDim` instrução tentou usar o `Preserve` palavra-chave para alterar uma dimensão de uma matriz que não seja a última dimensão.</span><span class="sxs-lookup"><span data-stu-id="e253e-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="e253e-104">Ao usar `Preserve`, você pode redimensionar a última dimensão de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="e253e-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="e253e-105">Para todas as outras dimensões, você deve especificar o mesmo tamanho de matriz existente.</span><span class="sxs-lookup"><span data-stu-id="e253e-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e253e-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="e253e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="e253e-107">Remover o `Preserve` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e253e-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e253e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e253e-108">See Also</span></span>  
 <span data-ttu-id="e253e-109">[Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/en-us/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8) </span><span class="sxs-lookup"><span data-stu-id="e253e-109">[NOTINBUILD Overview of Arrays in Visual Basic](http://msdn.microsoft.com/en-us/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8) </span></span>  
<span data-ttu-id="e253e-110"> [NOTINBUILD matrizes multidimensionais no Visual Basic](http://msdn.microsoft.com/en-us/d92cad25-07e2-4d79-8ea4-ab269700f5de) </span><span class="sxs-lookup"><span data-stu-id="e253e-110"> [NOTINBUILD Multidimensional Arrays in Visual Basic](http://msdn.microsoft.com/en-us/d92cad25-07e2-4d79-8ea4-ab269700f5de) </span></span>  
<span data-ttu-id="e253e-111"> [Instrução reDim](../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e253e-111"> [ReDim Statement](../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="e253e-112"> [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="e253e-112"> [Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md) </span></span>  
<span data-ttu-id="e253e-113"> [Preservar - excluir](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)</span><span class="sxs-lookup"><span data-stu-id="e253e-113"> [Preserve - delete](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)</span></span>
