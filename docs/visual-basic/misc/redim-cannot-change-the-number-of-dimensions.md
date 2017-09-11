---
title: "&quot;ReDim&quot; não pode alterar o número de dimensões | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
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
ms.openlocfilehash: 0bab4ac157c1badfa31479f77d9303f7e89f3d7f
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39redim39-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="6a58d-102">'ReDim' não pode alterar o número de dimensões</span><span class="sxs-lookup"><span data-stu-id="6a58d-102">&#39;ReDim&#39; cannot change the number of dimensions</span></span>
<span data-ttu-id="6a58d-103">Uma operação tenta usar o `ReDim` instrução para alterar a classificação (número de dimensões) de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="6a58d-103">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="6a58d-104">`ReDim`pode alterar o tamanho de uma ou mais dimensões de um array que já foi formalmente declarado, mas ele não pode alterar o posto de um array.</span><span class="sxs-lookup"><span data-stu-id="6a58d-104">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6a58d-105">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="6a58d-105">To correct this error</span></span>  
  
-   <span data-ttu-id="6a58d-106">Certifique-se de que você pretende alterar o posto do array e não os tamanhos das suas dimensões e se possível, use `Dim` para declarar um novo array com o posto desejado.</span><span class="sxs-lookup"><span data-stu-id="6a58d-106">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a58d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a58d-107">See Also</span></span>  
 <span data-ttu-id="6a58d-108">[Visão geral NOTINBUILD de matrizes no Visual Basic](http://msdn.microsoft.com/en-us/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8) </span><span class="sxs-lookup"><span data-stu-id="6a58d-108">[NOTINBUILD Overview of Arrays in Visual Basic](http://msdn.microsoft.com/en-us/ca50e2f2-b4d2-4c57-9169-9abbcc3392d8) </span></span>  
<span data-ttu-id="6a58d-109"> [NOTINBUILD matrizes multidimensionais no Visual Basic](http://msdn.microsoft.com/en-us/d92cad25-07e2-4d79-8ea4-ab269700f5de) </span><span class="sxs-lookup"><span data-stu-id="6a58d-109"> [NOTINBUILD Multidimensional Arrays in Visual Basic](http://msdn.microsoft.com/en-us/d92cad25-07e2-4d79-8ea4-ab269700f5de) </span></span>  
<span data-ttu-id="6a58d-110"> [Instrução reDim](../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="6a58d-110"> [ReDim Statement](../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="6a58d-111"> [Instrução Dim](../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="6a58d-111"> [Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md)</span></span>
