---
title: A função aninhada não tem uma assinatura que seja compatível com o delegado '<delegatename>'
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 912962e2ab39c4811294ccc225814b230100e12a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592010"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a><span data-ttu-id="7c8e7-102">Função aninhada não tem uma assinatura que é compatível com o delegado '\<delegatename >'</span><span class="sxs-lookup"><span data-stu-id="7c8e7-102">Nested function does not have a signature that is compatible with delegate '\<delegatename>'</span></span>
<span data-ttu-id="7c8e7-103">Uma expressão lambda recebeu a um delegado que tem uma assinatura incompatível.</span><span class="sxs-lookup"><span data-stu-id="7c8e7-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="7c8e7-104">Por exemplo, no código a seguir, delegar `Del` tem dois parâmetros inteiros.</span><span class="sxs-lookup"><span data-stu-id="7c8e7-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="7c8e7-105">O erro é gerado se uma expressão lambda com um argumento é declarada como tipo `Del`:</span><span class="sxs-lookup"><span data-stu-id="7c8e7-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="7c8e7-106">**ID do erro:** BC36532</span><span class="sxs-lookup"><span data-stu-id="7c8e7-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7c8e7-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7c8e7-107">To correct this error</span></span>  
  
- <span data-ttu-id="7c8e7-108">Ajuste a definição de delegado ou expressão lambda atribuído para que as assinaturas sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="7c8e7-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c8e7-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c8e7-109">See also</span></span>

- [<span data-ttu-id="7c8e7-110">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="7c8e7-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="7c8e7-111">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="7c8e7-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
