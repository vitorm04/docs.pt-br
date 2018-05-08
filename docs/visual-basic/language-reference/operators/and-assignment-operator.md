---
title: '&amp;= Operador (Visual Basic)'
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
ms.openlocfilehash: c3db2d4095600f32af92d1a4ce1f806a3f032af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-visual-basic"></a>&amp;= Operador (Visual Basic)
Concatena uma `String` expressão para uma `String` variável ou propriedade e atribui o resultado à variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer `String` variável ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão de `String` .  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `&=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md). O `&=` operador concatena o `String` expressão à direita para o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.  
  
## <a name="overloading"></a>Sobrecarga  
 O [& operador](../../../visual-basic/language-reference/operators/concatenation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `&` operador afeta o comportamento do `&=` operador. Se seu código usa `&=` em uma classe ou estrutura que sobrecarrega `&`, certifique-se de compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `&=` operador para concatenar duas `String` variáveis e atribui o resultado à primeira variável.  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador &](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [Operador +=](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operadores de Concatenação](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
