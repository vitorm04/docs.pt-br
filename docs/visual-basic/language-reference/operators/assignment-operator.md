---
title: Operador = (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591835"
---
# <a name="-operator-visual-basic"></a>Operador = (Visual Basic)
Atribui um valor a uma variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Qualquer variável gravável ou qualquer propriedade.  
  
 `value`  
 Qualquer literal, constante ou expressão.  
  
## <a name="remarks"></a>Comentários  
 O elemento no lado esquerdo do sinal de igual (`=`) pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz. A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). O operador `=` atribui o valor à sua direita à variável ou à propriedade à esquerda.  
  
> [!NOTE]
> O operador `=` também é usado como um operador de comparação. Para obter detalhes, consulte [operadores de comparação](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O operador `=` só pode ser sobrecarregado como um operador de comparação relacional, não como um operador de atribuição. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o operador de atribuição. O valor à direita é atribuído à variável à esquerda.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Consulte também

- [Operador &=](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operador *=](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [Operador/= (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [Operador \\ =](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operador ^=](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
- [Operadores de Comparação](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Inferência de Tipo de Variável Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
