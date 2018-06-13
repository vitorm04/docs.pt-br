---
title: Expressões lambda não são válidas na primeira expressão de uma &#39;Select Case&#39; instrução
ms.date: 07/20/2015
f1_keywords:
- bc36635
- vbc36635
helpviewer_keywords:
- BC36635
ms.assetid: 74609979-9c03-4864-bbce-f588aa2e0917
ms.openlocfilehash: c492615850ec089fe35c1ae4eaba90a741e30f42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588915"
---
# <a name="lambda-expressions-are-not-valid-in-the-first-expression-of-a-39select-case39-statement"></a>Expressões lambda não são válidas na primeira expressão de uma &#39;Select Case&#39; instrução
Você não pode usar uma expressão lambda para a expressão de teste em um `Select Case` instrução. Definições de expressão lambda retornam funções e a expressão de teste de um `Select Case` instrução deve ser um tipo de dados elementares.  
  
 O código a seguir faz com que esse erro:  
  
```vb  
' Select Case (Function(arg) arg Is Nothing)  
    ' List of the cases.  
' End Select  
```  
  
 **ID do erro:** BC36635  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
-   Examine seu código para determinar se uma construção condicional diferente, como um `If...Then...Else` instrução, funcionaria para você.  
  
-   Você pode ter pretendido chamar a função, conforme mostrado no código a seguir:  
  
```vb  
Dim num? As Integer  
Select Case ((Function(arg? As Integer) arg Is Nothing)(num))  
    ' List of the cases  
End Select  
```  
  
## <a name="see-also"></a>Consulte também  
 [Expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [Instrução If...Then...Else](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
