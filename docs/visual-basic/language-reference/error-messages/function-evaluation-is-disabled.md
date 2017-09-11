---
title: "Avaliação de função está desabilitada porque uma avaliação de função anterior expirou | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
dev_langs:
- VB
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: 7
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
ms.openlocfilehash: 127f89f4c7ddaf794f58707d8925731a511f3740
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a><span data-ttu-id="5e0c9-102">A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite</span><span class="sxs-lookup"><span data-stu-id="5e0c9-102">Function evaluation is disabled because a previous function evaluation timed out</span></span>
<span data-ttu-id="5e0c9-103">Avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-103">Function evaluation is disabled because a previous function evaluation timed out.</span></span> <span data-ttu-id="5e0c9-104">Para reabilitar a avaliação da função, siga as etapas novamente ou reinicie a depuração.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-104">To re-enable function evaluation, step again or restart debugging.</span></span>  
  
 <span data-ttu-id="5e0c9-105">No depurador do Visual Studio, uma expressão especifica uma chamada de procedimento, mas outra avaliação expirou.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-105">In the Visual Studio debugger, an expression specifies a procedure call, but another evaluation has timed out.</span></span>  
  
 <span data-ttu-id="5e0c9-106">Possíveis causas para uma chamada de procedimento para tempo limite incluem um loop infinito ou *loop infinito*.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-106">Possible causes for a procedure call to time out include an infinite loop or *endless loop*.</span></span> <span data-ttu-id="5e0c9-107">Para obter mais informações, consulte [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e0c9-107">For more information, see [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md).</span></span>  
  
 <span data-ttu-id="5e0c9-108">É um caso especial de um loop infinito *recursão*.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-108">A special case of an infinite loop is *recursion*.</span></span> <span data-ttu-id="5e0c9-109">Para obter mais informações, consulte [procedimentos recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5e0c9-109">For more information, see [Recursive Procedures](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).</span></span>  
  
 <span data-ttu-id="5e0c9-110">**ID do erro:** BC30957</span><span class="sxs-lookup"><span data-stu-id="5e0c9-110">**Error ID:** BC30957</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5e0c9-111">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="5e0c9-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="5e0c9-112">Se possível, determine qual foi a avaliação de função anterior e o que causou o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-112">If possible, determine what the previous function evaluation was and what caused it to time out.</span></span> <span data-ttu-id="5e0c9-113">Caso contrário, você pode encontrar esse erro novamente.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-113">Otherwise, you might encounter this error again.</span></span>  
  
2.  <span data-ttu-id="5e0c9-114">Siga as etapas novamente, o depurador ou encerrar e reiniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="5e0c9-114">Either step the debugger again, or terminate and restart debugging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e0c9-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e0c9-115">See Also</span></span>  
 <span data-ttu-id="5e0c9-116">[Depurando no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="5e0c9-116">[Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="5e0c9-117"> [Navegar pelo Código com o Depurador](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)</span><span class="sxs-lookup"><span data-stu-id="5e0c9-117"> [Navigating through Code with the Debugger](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)</span></span>
