---
title: Função aninhada não tem uma assinatura que é compatível com o delegado &#39; &lt;delegatename&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: abfda4ee6064ec9ea54b8a3c383d10f8263a1458
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506401"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="7041a-102">Função aninhada não tem uma assinatura que é compatível com o delegado &#39; &lt;delegatename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="7041a-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="7041a-103">Uma expressão lambda recebeu a um delegado que tem uma assinatura incompatível.</span><span class="sxs-lookup"><span data-stu-id="7041a-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="7041a-104">Por exemplo, no código a seguir, delegar `Del` tem dois parâmetros inteiros.</span><span class="sxs-lookup"><span data-stu-id="7041a-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="7041a-105">O erro é gerado se uma expressão lambda com um argumento é declarada como tipo `Del`:</span><span class="sxs-lookup"><span data-stu-id="7041a-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="7041a-106">**ID do erro:** BC36532</span><span class="sxs-lookup"><span data-stu-id="7041a-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7041a-107">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="7041a-107">To correct this error</span></span>  
  
-   <span data-ttu-id="7041a-108">Ajuste a definição de delegado ou expressão lambda atribuído para que as assinaturas sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="7041a-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7041a-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7041a-109">See also</span></span>
- [<span data-ttu-id="7041a-110">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="7041a-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="7041a-111">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="7041a-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
