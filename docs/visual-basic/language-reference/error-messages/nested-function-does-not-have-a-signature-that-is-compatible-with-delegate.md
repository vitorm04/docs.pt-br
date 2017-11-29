---
title: "Função aninhada não tem uma assinatura compatível com delegado &#39; &lt;delegatename&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a>Função aninhada não tem uma assinatura compatível com delegado &#39; &lt;delegatename&gt;&#39;
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
  
-   Ajuste a definição de delegado ou a expressão lambda atribuído para que as assinaturas sejam compatíveis.  
  
## <a name="see-also"></a>Consulte também  
 [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
