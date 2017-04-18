---
title: "Função aninhada não tem uma assinatura compatível com delegado &quot;&lt;delegatename&gt;&quot; | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
dev_langs:
- VB
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 5
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6a399e3ae7266e4bfd5afef1eb2fe039166f3d91
ms.lasthandoff: 03/13/2017

---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Função aninhada não tem uma assinatura compatível com delegado '&lt;delegatename&gt;'
Uma expressão lambda foi atribuída a um delegado que tem uma assinatura incompatível. Por exemplo, no código a seguir, delegar `Del` tem dois parâmetros inteiros.  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 O erro é gerado se uma expressão lambda com um argumento é declarada como tipo `Del`:  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **ID do erro:** BC36532  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Ajuste a definição de representante ou o expressão lambda atribuído para que as assinaturas sejam compatíveis.  
  
## <a name="see-also"></a>Consulte também  
 [Conversão de delegado reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
