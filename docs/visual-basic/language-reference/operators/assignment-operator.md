---
title: Operador = (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>Operador = (Visual Basic)
Atribui um valor a uma variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Qualquer variável gravável ou qualquer propriedade.  
  
 `value`  
 Qualquer literal, uma constante ou uma expressão.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do sinal de igual (`=`) pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). O `=` operador atribui o valor à sua direita à variável ou propriedade à sua esquerda.  
  
> [!NOTE]
>  O `=` operador também é usado como um operador de comparação. Para obter detalhes, consulte [operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `=` operador pode ser sobrecarregado somente como um operador de comparação relacional, e não como um operador de atribuição. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o operador de atribuição. O valor à direita é atribuído à variável à esquerda.  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador &=](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Operador *=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= Operador](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [Operador ^=](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operadores de Comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
