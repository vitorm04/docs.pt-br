---
title: '&quot;#ElseIf&quot; deve ser precedido por um &quot;#If&quot; ou &quot;#ElseIf&quot; correspondente | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
dev_langs:
- VB
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f9345fdb33b83048d3876305074d9a912a62d76d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a><span data-ttu-id="adf24-102">'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente</span><span class="sxs-lookup"><span data-stu-id="adf24-102">&#39;#ElseIf&#39; must be preceded by a matching &#39;#If&#39; or &#39;#ElseIf&#39;</span></span>
<span data-ttu-id="adf24-103">`#ElseIf`é uma diretiva de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="adf24-103">`#ElseIf` is a conditional compilation directive.</span></span> <span data-ttu-id="adf24-104">Um `#ElseIf` cláusula deve ser precedida por uma correspondência `#If` ou `#ElseIf` cláusula.</span><span class="sxs-lookup"><span data-stu-id="adf24-104">An `#ElseIf` clause must be preceded by a matching `#If` or `#ElseIf` clause.</span></span>  
  
 <span data-ttu-id="adf24-105">**ID do erro:** BC30014</span><span class="sxs-lookup"><span data-stu-id="adf24-105">**Error ID:** BC30014</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="adf24-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="adf24-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="adf24-107">Verifique se precedidos `#If` ou `#ElseIf` não foi separado disso `#ElseIf` por um bloco de compilação condicional ou incorretamente localizado `#End If`.</span><span class="sxs-lookup"><span data-stu-id="adf24-107">Check that a preceding `#If` or `#ElseIf` has not been separated from this `#ElseIf` by an intervening conditional compilation block or an incorrectly placed `#End If`.</span></span>  
  
2.  <span data-ttu-id="adf24-108">Se o `#ElseIf` é precedido por um `#Else` diretiva, remova o `#Else` ou alterá-lo para um `#ElseIf`.</span><span class="sxs-lookup"><span data-stu-id="adf24-108">If the `#ElseIf` is preceded by a `#Else` directive, either remove the `#Else` or change it to an `#ElseIf`.</span></span>  
  
3.  <span data-ttu-id="adf24-109">Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.</span><span class="sxs-lookup"><span data-stu-id="adf24-109">If everything else is in order, add an `#If` directive to the beginning of the conditional compilation block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf24-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="adf24-110">See Also</span></span>  
 [<span data-ttu-id="adf24-111">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="adf24-111">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
