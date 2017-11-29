---
title: Operador ^= (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
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
