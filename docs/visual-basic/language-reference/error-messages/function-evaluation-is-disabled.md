---
title: A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 6231d48f3f90d8e436dc80bf4670886c1d030387
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="865fa-102">A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite</span><span class="sxs-lookup"><span data-stu-id="865fa-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="865fa-103">Avaliação de função está desabilitada porque uma avaliação de função anterior expirou. Para reabilitar a avaliação da função, siga as etapas novamente ou reinicie a depuração.</span><span class="sxs-lookup"><span data-stu-id="865fa-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="865fa-104">No depurador do Visual Studio, uma expressão especifica uma chamada de procedimento, mas outra avaliação expirou.</span><span class="sxs-lookup"><span data-stu-id="865fa-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="865fa-105">Causas possíveis para uma chamada de procedimento para o tempo limite incluem um loop infinito ou *loop infinito*.</span><span class="sxs-lookup"><span data-stu-id="865fa-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="865fa-106">Para obter mais informações, consulte [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="865fa-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="865fa-107">É um caso especial de um loop infinito *recursão*.</span><span class="sxs-lookup"><span data-stu-id="865fa-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="865fa-108">Para obter mais informações, consulte [procedimentos recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="865fa-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="865fa-109">**ID do erro:** BC30957</span><span class="sxs-lookup"><span data-stu-id="865fa-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="865fa-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="865fa-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="865fa-111">Se possível, determine qual foi a avaliação da função anterior e o que causou o tempo limite. Caso contrário, você pode encontrar esse erro novamente.</span><span class="sxs-lookup"><span data-stu-id="865fa-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="865fa-112">Etapa do depurador novamente, ou encerre e reinicie a depuração.</span><span class="sxs-lookup"><span data-stu-id="865fa-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="865fa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="865fa-113">See Also</span></span>  
 [<span data-ttu-id="865fa-114">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="865fa-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="865fa-115">Navegar pelo Código com o Depurador</span><span class="sxs-lookup"><span data-stu-id="865fa-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
