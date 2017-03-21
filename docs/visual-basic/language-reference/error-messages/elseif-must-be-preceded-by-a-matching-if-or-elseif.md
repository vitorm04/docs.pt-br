---
title: '&quot;#ElseIf&quot; deve ser precedido por um &quot;#If&quot; ou &quot;#ElseIf&quot; correspondente | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
dev_langs:
- VB
helpviewer_keywords:
- BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: 9
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
ms.openlocfilehash: dcaca3b1e79f26b2a80cedf1d23ec4a918511e10
ms.lasthandoff: 03/13/2017

---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>'#ElseIf' deve ser precedido por um '#If' ou '#ElseIf' correspondente
`#ElseIf`é uma diretiva de compilação condicional. Um `#ElseIf` cláusula deve ser precedida por uma correspondência `#If` ou `#ElseIf` cláusula.  
  
 **ID do erro:** BC30014  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se precedidos `#If` ou `#ElseIf` não foi separado disso `#ElseIf` por um bloco de compilação condicional ou incorretamente localizado `#End If`.  
  
2.  Se o `#ElseIf` é precedido por um `#Else` diretiva, remova o `#Else` ou alterá-lo para um `#ElseIf`.  
  
3.  Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.  
  
## <a name="see-also"></a>Consulte também  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
