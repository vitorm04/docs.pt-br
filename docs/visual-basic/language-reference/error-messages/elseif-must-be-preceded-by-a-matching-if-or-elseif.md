---
title: "'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311052"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="02287-102">'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente</span><span class="sxs-lookup"><span data-stu-id="02287-102">'#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>
<span data-ttu-id="02287-103">`#ElseIf` é uma diretiva de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="02287-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="02287-104">Uma `#ElseIf` cláusula deve ser precedida por uma correspondência `#If` ou `#ElseIf` cláusula.</span><span class="sxs-lookup"><span data-stu-id="02287-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="02287-105">**ID do erro:** BC30014</span><span class="sxs-lookup"><span data-stu-id="02287-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="02287-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="02287-106">To correct this error</span></span>  
  
1. <span data-ttu-id="02287-107">Verifique se precedidos `#If` ou `#ElseIf` não foi separado deste `#ElseIf` por um bloco de compilação condicional ou incorretamente localizado `#End If`.</span><span class="sxs-lookup"><span data-stu-id="02287-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2. <span data-ttu-id="02287-108">Se o `#ElseIf` é precedida por um `#Else` diretiva, remova o `#Else` ou altere-o para um `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="02287-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3. <span data-ttu-id="02287-109">Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="02287-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02287-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="02287-110">See also</span></span>

- [<span data-ttu-id="02287-111">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="02287-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
