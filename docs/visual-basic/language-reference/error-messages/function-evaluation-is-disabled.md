---
title: "A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords: BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05067e730486b443b7a508adb499f34c060d5093
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
