---
title: '&amp;= Operator'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350259"
---
# <a name="amp-operator-visual-basic"></a>&amp;= Operator (Visual Basic)
Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.  
  
## <a name="syntax"></a>Sintaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Any `String` variable or property.  
  
 `expression`  
 Necessário. Qualquer expressão de `String` .  
  
## <a name="remarks"></a>Comentários  
 The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array. The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.  
  
## <a name="overloading"></a>Sobrecarga  
 The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. Overloading the `&` operator affects the behavior of the `&=` operator. If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior. For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Consulte também

- [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
