---
title: "'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente"
ms.date: 07/20/2015
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
ms.openlocfilehash: 4832fb80cfbe42c7a1303e0de69f36784711c05a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311052"
---
# <a name="elseif-must-be-preceded-by-a-matching-if-or-elseif"></a>'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente
`#ElseIf` é uma diretiva de compilação condicional. Uma `#ElseIf` cláusula deve ser precedida por uma correspondência `#If` ou `#ElseIf` cláusula.  
  
 **ID do erro:** BC30014  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1. Verifique se precedidos `#If` ou `#ElseIf` não foi separado deste `#ElseIf` por um bloco de compilação condicional ou incorretamente localizado `#End If`.  
  
2. Se o `#ElseIf` é precedida por um `#Else` diretiva, remova o `#Else` ou altere-o para um `#ElseIf`.  
  
3. Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.  
  
## <a name="see-also"></a>Consulte também

- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
