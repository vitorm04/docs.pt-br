---
title: "'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 142c142afe0d9be0ecd4d8a0340f0f1957b20470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162772"
---
# <a name="bc30014-elseif-must-be-preceded-by-a-matching-if-or-elseif"></a><span data-ttu-id="d1c31-102">BC30014: ' #ElseIf ' deve ser precedido por ' #If ' ou ' #ElseIf ' correspondente</span><span class="sxs-lookup"><span data-stu-id="d1c31-102">BC30014: '#ElseIf' must be preceded by a matching '#If' or '#ElseIf'</span></span>

<span data-ttu-id="d1c31-103">`#ElseIf` é uma diretiva de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="d1c31-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="d1c31-104">Uma `#ElseIf` cláusula deve ser precedida por uma `#If` cláusula or correspondente `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="d1c31-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>

 <span data-ttu-id="d1c31-105">**ID do erro:** BC30014</span><span class="sxs-lookup"><span data-stu-id="d1c31-105">**Error ID:** BC30014</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d1c31-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="d1c31-106">To correct this error</span></span>

1. <span data-ttu-id="d1c31-107">Verifique se um `#If` ou anterior `#ElseIf` não foi separado dele `#ElseIf` por um bloco de compilação condicional intermediário ou foi colocado incorretamente `#End If` .</span><span class="sxs-lookup"><span data-stu-id="d1c31-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>

2. <span data-ttu-id="d1c31-108">Se o `#ElseIf` for precedido por uma `#Else` diretiva, remova `#Else` ou altere-o para um `#ElseIf` .</span><span class="sxs-lookup"><span data-stu-id="d1c31-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>

3. <span data-ttu-id="d1c31-109">Se todo o resto estiver em ordem, adicione uma `#If` diretiva ao início do bloco de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="d1c31-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>

## <a name="see-also"></a><span data-ttu-id="d1c31-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="d1c31-110">See also</span></span>

- [<span data-ttu-id="d1c31-111">#If... Diretivas then... #Else</span><span class="sxs-lookup"><span data-stu-id="d1c31-111">#If...Then...#Else Directives</span></span>](../directives/if-then-else-directives.md)
