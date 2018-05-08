---
title: '&#39;#Region&#39; e &#39;#End região&#39; instruções não são válidas em lambdas de várias linhas do corpo de método'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: bf3843e0ec3009f3dc7d60e91c340a7f20543231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39;#Region&#39; e &#39;#End região&#39; instruções não são válidas dentro do método corpos/lambdas multilinha
O `#Region` bloco deve ser declarado em um nível de namespace, módulo ou classe. Uma região recolhível pode incluir um ou mais procedimentos, mas ele não pode começar ou terminar dentro de um procedimento.  
  
 **ID do erro:** BC32025  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Certifique-se de que o procedimento anterior é encerrado corretamente com um `End Function` ou `End Sub` instrução.  
  
2.  Certifique-se de que o `#Region` e `#End Region` diretivas estão no mesmo bloco de código.  
  
## <a name="see-also"></a>Consulte também  
 [Diretiva #Region](../../../visual-basic/language-reference/directives/region-directive.md)
