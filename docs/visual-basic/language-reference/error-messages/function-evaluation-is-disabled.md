---
title: A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="efef7-102">A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite</span><span class="sxs-lookup"><span data-stu-id="efef7-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="efef7-103">Avaliação de função está desabilitada porque uma avaliação de função anterior expirou. Para reabilitar a avaliação da função, siga as etapas novamente ou reinicie a depuração.</span><span class="sxs-lookup"><span data-stu-id="efef7-103">Function evaluation is disabled because a previous function evaluation timed out. To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="efef7-104">No depurador do Visual Studio, uma expressão especifica uma chamada de procedimento, mas outra avaliação expirou.</span><span class="sxs-lookup"><span data-stu-id="efef7-104">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="efef7-105">Causas possíveis para uma chamada de procedimento para o tempo limite incluem um loop infinito ou *loop infinito*.</span><span class="sxs-lookup"><span data-stu-id="efef7-105">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="efef7-106">Para obter mais informações, consulte [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="efef7-106">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="efef7-107">É um caso especial de um loop infinito *recursão*.</span><span class="sxs-lookup"><span data-stu-id="efef7-107">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="efef7-108">Para obter mais informações, consulte [procedimentos recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="efef7-108">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="efef7-109">**ID do erro:** BC30957</span><span class="sxs-lookup"><span data-stu-id="efef7-109">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="efef7-110">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="efef7-110">To correct this error</span></span>  
  
1.  <span data-ttu-id="efef7-111">Se possível, determine qual foi a avaliação da função anterior e o que causou o tempo limite. Caso contrário, você pode encontrar esse erro novamente.</span><span class="sxs-lookup"><span data-stu-id="efef7-111">If possible, determine what the previous function evaluation was and what caused it to time out. Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="efef7-112">Etapa do depurador novamente, ou encerre e reinicie a depuração.</span><span class="sxs-lookup"><span data-stu-id="efef7-112">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efef7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="efef7-113">See Also</span></span>  
 [<span data-ttu-id="efef7-114">Depurando no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="efef7-114">Debugging in Visual Studio</span></span>](/visualstudio/debugger/debugging-in-visual-studio)  
 [<span data-ttu-id="efef7-115">Navegar pelo Código com o Depurador</span><span class="sxs-lookup"><span data-stu-id="efef7-115">Navigating through Code with the Debugger</span></span>](/visualstudio/debugger/navigating-through-code-with-the-debugger)
