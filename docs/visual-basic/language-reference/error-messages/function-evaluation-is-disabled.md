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
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite
Avaliação de função está desabilitada porque uma avaliação de função anterior expirou. Para reabilitar a avaliação da função, siga as etapas novamente ou reinicie a depuração.  
  
 No depurador do Visual Studio, uma expressão especifica uma chamada de procedimento, mas outra avaliação expirou.  
  
 Causas possíveis para uma chamada de procedimento para o tempo limite incluem um loop infinito ou *loop infinito*. Para obter mais informações, consulte [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 É um caso especial de um loop infinito *recursão*. Para obter mais informações, consulte [procedimentos recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID do erro:** BC30957  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se possível, determine qual foi a avaliação da função anterior e o que causou o tempo limite. Caso contrário, você pode encontrar esse erro novamente.  
  
2.  Etapa do depurador novamente, ou encerre e reinicie a depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](/visualstudio/debugger/debugging-in-visual-studio)  
 [Navegar pelo Código com o Depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger)
