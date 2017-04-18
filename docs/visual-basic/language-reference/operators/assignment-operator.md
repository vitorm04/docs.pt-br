---
title: = Operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
dev_langs:
- VB
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
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
ms.openlocfilehash: 47b69a908f12ec36daf2848da6ee4b04895fd3a4
ms.lasthandoff: 03/13/2017

---
# <a name="-operator-visual-basic"></a>Operador = (Visual Basic)
Atribui um valor a uma variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
  
variableorproperty = value  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Qualquer variável gravável ou propriedade.  
  
 `value`  
 Qualquer literal, uma constante ou uma expressão.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do sinal de igual (`=`) pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). O `=` operador atribui o valor à sua direita à variável ou propriedade à sua esquerda.  
  
> [!NOTE]
>  O `=` também é usado como um operador de comparação. Para obter detalhes, consulte [operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O `=` operador pode ser sobrecarregado somente como um operador relacional, não como um operador de atribuição. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o operador de atribuição. O valor à direita é atribuído à variável à esquerda.  
  
 [!code-vb[VbVbalrOperators n º&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [< / Operador =](../../../visual-basic/language-reference/operators/and-assignment-operator.md)   
 [* O operador =](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)   
 [+ = Operador](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)   
 [-= Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)   
 [Operador / = (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)   
 [\\= Operador](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)   
 [^ = Operador](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)   
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Somente leitura](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)

