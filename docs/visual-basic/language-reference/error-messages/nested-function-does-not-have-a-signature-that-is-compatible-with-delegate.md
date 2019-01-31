---
title: A função aninhada não tem uma assinatura que seja compatível com o delegado '<delegatename>'
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: ea6f230715520cb35809d57db76b300da326ec9a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283459"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="b6eeb-102">Função aninhada não tem uma assinatura que é compatível com o delegado '\<delegatename >'</span><span class="sxs-lookup"><span data-stu-id="b6eeb-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>
<span data-ttu-id="b6eeb-103">Uma expressão lambda recebeu a um delegado que tem uma assinatura incompatível.</span><span class="sxs-lookup"><span data-stu-id="b6eeb-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="b6eeb-104">Por exemplo, no código a seguir, delegar `Del` tem dois parâmetros inteiros.</span><span class="sxs-lookup"><span data-stu-id="b6eeb-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="b6eeb-105">O erro é gerado se uma expressão lambda com um argumento é declarada como tipo `Del`:</span><span class="sxs-lookup"><span data-stu-id="b6eeb-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="b6eeb-106">**ID do erro:** BC36532</span><span class="sxs-lookup"><span data-stu-id="b6eeb-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b6eeb-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="b6eeb-107">To correct this error</span></span>  
  
-   <span data-ttu-id="b6eeb-108">Ajuste a definição de delegado ou expressão lambda atribuído para que as assinaturas sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="b6eeb-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6eeb-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6eeb-109">See also</span></span>
- [<span data-ttu-id="b6eeb-110">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="b6eeb-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="b6eeb-111">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="b6eeb-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
