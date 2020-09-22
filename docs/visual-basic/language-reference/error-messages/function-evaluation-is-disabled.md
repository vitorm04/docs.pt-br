---
title: A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite
ms.date: 07/20/2015
f1_keywords:
- bc30957
- vbc30957
helpviewer_keywords:
- BC30957
ms.assetid: 561e593a-f50a-4b72-a708-4cab60ec7b28
ms.openlocfilehash: 9bdc12e3dc57b440ed9f304201b8ec401db37871
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874071"
---
# <a name="function-evaluation-is-disabled-because-a-previous-function-evaluation-timed-out"></a>A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite

A avaliação de função está desabilitada porque uma avaliação de função anterior atingiu o tempo limite. Para reabilitar a avaliação da função, execute novamente ou reinicie a depuração.  
  
 No depurador do Visual Studio, uma expressão especifica uma chamada de procedimento, mas outra avaliação atingiu o tempo limite.  
  
 As possíveis causas de uma chamada de procedimento para o tempo limite incluem um loop infinito ou um *loop infinito*. Para obter mais informações, consulte [para... Próxima instrução](../statements/for-next-statement.md).  
  
 Um caso especial de um loop infinito é a *recursão*. Para obter mais informações, consulte [procedimentos recursivos](../../programming-guide/language-features/procedures/recursive-procedures.md).  
  
 **ID do erro:** BC30957  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Se possível, determine qual foi a avaliação da função anterior e o que causou o tempo limite. Caso contrário, você pode encontrar esse erro novamente.  
  
2. Siga as etapas do depurador novamente ou encerre e reinicie a depuração.  
  
## <a name="see-also"></a>Confira também

- [Depurando no Visual Studio](/visualstudio/debugger/debugger-feature-tour)
- [Navegar pelo Código com o Depurador](/visualstudio/debugger/navigating-through-code-with-the-debugger)
