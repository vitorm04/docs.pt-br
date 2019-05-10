---
title: A função aninhada não tem uma assinatura que seja compatível com o delegado '<delegatename>'
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 912962e2ab39c4811294ccc225814b230100e12a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64592010"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>Função aninhada não tem uma assinatura que é compatível com o delegado '\<delegatename >'
Uma expressão lambda recebeu a um delegado que tem uma assinatura incompatível. Por exemplo, no código a seguir, delegar `Del` tem dois parâmetros inteiros.  
  
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
  
- Ajuste a definição de delegado ou expressão lambda atribuído para que as assinaturas sejam compatíveis.  
  
## <a name="see-also"></a>Consulte também

- [Conversão de Delegado Reduzida](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
