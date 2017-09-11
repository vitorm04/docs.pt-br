---
title: "Função aninhada não tem uma assinatura compatível com delegado &quot;&lt;delegatename&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
dev_langs:
- VB
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 5
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
ms.openlocfilehash: fa6736f0e9e31d4ec36abb92e2f1ee1771238039
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="c8d4b-102">Função aninhada não tem uma assinatura compatível com delegado '&lt;delegatename&gt;'</span><span class="sxs-lookup"><span data-stu-id="c8d4b-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="c8d4b-103">Uma expressão lambda foi atribuída a um delegado que tem uma assinatura incompatível.</span><span class="sxs-lookup"><span data-stu-id="c8d4b-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="c8d4b-104">Por exemplo, no código a seguir, delegar `Del` tem dois parâmetros inteiros.</span><span class="sxs-lookup"><span data-stu-id="c8d4b-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="c8d4b-105">O erro é gerado se uma expressão lambda com um argumento é declarada como tipo `Del`:</span><span class="sxs-lookup"><span data-stu-id="c8d4b-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="c8d4b-106">**ID do erro:** BC36532</span><span class="sxs-lookup"><span data-stu-id="c8d4b-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c8d4b-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="c8d4b-107">To correct this error</span></span>  
  
-   <span data-ttu-id="c8d4b-108">Ajuste a definição de representante ou o expressão lambda atribuído para que as assinaturas sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="c8d4b-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8d4b-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c8d4b-109">See Also</span></span>  
 <span data-ttu-id="c8d4b-110">[Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span><span class="sxs-lookup"><span data-stu-id="c8d4b-110">[Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md) </span></span>  
<span data-ttu-id="c8d4b-111"> [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)</span><span class="sxs-lookup"><span data-stu-id="c8d4b-111"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)</span></span>
