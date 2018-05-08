---
title: '&#39;#ElseIf&#39; deve ser precedido por uma correspondência &#39;#If&#39; ou &#39;#ElseIf&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: ef904173b1791309f6c2722bd959cabdad1d71da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39;#ElseIf&#39; deve ser precedido por uma correspondência &#39;#If&#39; ou &#39;#ElseIf&#39;
`#ElseIf` é uma diretiva de compilação condicional. Um `#ElseIf` cláusula deve ser precedida por uma correspondência `#If` ou `#ElseIf` cláusula.  
  
 **ID do erro:** BC30014  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se precedidos `#If` ou `#ElseIf` não foi separado deste `#ElseIf` por um bloco de compilação condicional ou incorretamente localizado `#End If`.  
  
2.  Se o `#ElseIf` é precedido por um `#Else` diretiva, remova o `#Else` ou alterá-lo para um `#ElseIf`.  
  
3.  Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.  
  
## <a name="see-also"></a>Consulte também  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
