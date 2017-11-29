---
title: "&#39; #ElseIf &#39; deve ser precedido por uma correspondência &#39; #If &#39; ou &#39; #ElseIf &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30014
- bc30014
helpviewer_keywords: BC30014
ms.assetid: 5215585e-2efa-485a-9efe-9833a1cc83a0
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b3a4e809e1108fcd6e116538a1947057e9548ce
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="39elseif39-must-be-preceded-by-a-matching-39if39-or-39elseif39"></a>&#39; #ElseIf &#39; deve ser precedido por uma correspondência &#39; #If &#39; ou &#39; #ElseIf &#39;
`#ElseIf`é uma diretiva de compilação condicional. Um `#ElseIf` cláusula deve ser precedida por uma correspondência `#If` ou `#ElseIf` cláusula.  
  
 **ID do erro:** BC30014  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
1.  Verifique se precedidos `#If` ou `#ElseIf` não foi separado deste `#ElseIf` por um bloco de compilação condicional ou incorretamente localizado `#End If`.  
  
2.  Se o `#ElseIf` é precedido por um `#Else` diretiva, remova o `#Else` ou alterá-lo para um `#ElseIf`.  
  
3.  Se tudo estiver em ordem, adicione um `#If` diretiva para o início do bloco de compilação condicional.  
  
## <a name="see-also"></a>Consulte também  
 [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
