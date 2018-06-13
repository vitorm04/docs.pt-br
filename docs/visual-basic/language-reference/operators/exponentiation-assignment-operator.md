---
title: Operador ^= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 571ef26eb188d9044ec8f6c8e6e4b490780f17a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603490"
---
# <a name="-operator-visual-basic"></a>Operador ^= (Visual Basic)
Gera o valor de uma variável ou propriedade à potência de uma expressão e atribui o resultado de volta para a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `^=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `^=` operador primeiro gera o valor da variável ou propriedade (no lado esquerdo do operador) para a potência do valor da expressão (no lado direito do operador). O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.  
  
 Visual Basic sempre executa exponenciação no [tipo de dados Double](../../../visual-basic/language-reference/data-types/double-data-type.md). Operandos de qualquer outro tipo são convertidos em `Double`, e o resultado é sempre `Double`.  
  
 O valor de `expression` pode ser fracionário, negativo, ou ambos.  
  
## <a name="overloading"></a>Sobrecarga  
 O [^ operador](../../../visual-basic/language-reference/operators/exponentiation-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `^` operador afeta o comportamento do `^=` operador. Se seu código usa `^=` em uma classe ou estrutura que sobrecarrega `^`, certifique-se de compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `^=` operador para aumentar o valor de um `Integer` variável à potência de uma segunda variável e atribui o resultado à primeira variável.  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador ^](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
