---
title: Operador /= (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
caps.latest.revision: 23
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94448856072a949582e64577287134c4b975bfec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>Operador /= (Visual Basic)
Divide o valor de uma variável ou propriedade pelo valor de uma expressão e atribui o resultado de ponto flutuante para a variável ou propriedade.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Partes  
 `variableorproperty`  
 Necessário. Qualquer variável numérica ou propriedade.  
  
 `expression`  
 Necessário. Qualquer expressão numérica.  
  
## <a name="remarks"></a>Comentários  
 O elemento à esquerda do `/=` operador pode ser uma simples variável escalar, uma propriedade ou um elemento de uma matriz. A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 O `/=` operador primeiro divide o valor da variável ou propriedade (no lado esquerdo do operador) pelo valor da expressão (no lado direito do operador). O operador, em seguida, atribui o resultado dessa operação de ponto flutuante para a variável ou propriedade.  
  
 Essa instrução atribui um `Double` valor à variável ou propriedade à esquerda. Se `Option Strict` é `On`, `variableorproperty` deve ser um `Double`. Se `Option Strict` é `Off`, Visual Basic executará uma conversão implícita e atribui o valor resultante para `variableorproperty`, com um possível erro em tempo de execução. Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) e [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Sobrecarga  
 O [/ operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura. Sobrecarga de `/` operador afeta o comportamento do `/=` operador. Se seu código usa `/=` em uma classe ou estrutura que sobrecarrega `/`, certifique-se de compreender o comportamento redefinido. Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa o `/=` operador para dividir uma `Integer` variável por um segundo e atribuir a quociente à primeira variável.  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [/ Operador (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [\\= Operador](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [Operadores de Atribuição](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operadores Aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Listados por Funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Instruções](../../../visual-basic/programming-guide/language-features/statements.md)
