---
title: '&gt;&gt;= Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= Operador (Visual Basic)
Executa um deslocamento aritmético para a direita no valor de uma variável ou propriedade e atribui o resultado de volta para a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Variável ou propriedade de um tipo integral (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, ou `ULong`).  
  
 `amount`  
 Necessário. Expressão numérica de um tipo de dados que amplia a `Integer`.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `>>=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `>>=` operador primeiro executa um deslocamento aritmético para a direita no valor da variável ou propriedade. O operador, em seguida, atribui o resultado da operação para a variável ou propriedade.  
  
 Deslocamentos aritméticos não são circulares, que significa que os bits deslocados uma extremidade do resultado não são reintroduzidos na outra extremidade. Em um deslocamento aritmético à direita, os bits deslocados além da posição de bit mais à direita são descartados e o bit mais à esquerda é propagado para as posições de bits vagas à esquerda. Isso significa que se `variableorproperty` tem um valor negativo, as posições vazias são definidas como um. Se `variableorproperty` for positivo, ou se seu tipo de dados é um tipo não assinado, as posições vazias são definidas como zero.  
  
## <a name="overloading"></a>Sobrecarga  
 O [>> operador](../../../visual-basic/language-reference/operators/right-shift-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `>>` operador afeta o comportamento do `>>=` operador. Se seu código usa `>>=` em uma classe ou estrutura que sobrecarrega `>>`, certifique-se de compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `>>=` operador para deslocar o padrão de bits de um `Integer` variável diretamente pela quantidade especificada e atribui o resultado à variável.  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Operador >>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operadores Bit Shift](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
