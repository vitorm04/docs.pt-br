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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b861b5c6c151c5d3aeec2810c7f2a228f22fdf6e
ms.lasthandoff: 03/13/2017

---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite
Avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite. Para reabilitar a avaliação da função, siga as etapas novamente ou reinicie a depuração.  
  
 No depurador do Visual Studio, uma expressão especifica uma chamada de procedimento, mas outra avaliação expirou.  
  
 Possíveis causas para uma chamada de procedimento para tempo limite incluem um loop infinito ou *loop infinito*. Para obter mais informações, consulte [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md).  
  
 É um caso especial de um loop infinito *recursão*. Para obter mais informações, consulte [procedimentos recursivos](../../../visual-basic/programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID do erro:** BC30957  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Se possível, determine qual foi a avaliação de função anterior e o que causou o tempo limite. Caso contrário, você pode encontrar esse erro novamente.  
  
2.  Siga as etapas novamente, o depurador ou encerrar e reiniciar a depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depurando no Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [Navegar pelo Código com o Depurador](https://docs.microsoft.com/visualstudio/debugger/navigating-through-code-with-the-debugger)
