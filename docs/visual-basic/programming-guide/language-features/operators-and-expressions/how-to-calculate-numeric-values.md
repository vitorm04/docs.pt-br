---
title: "Como calcular valores numéricos (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations [Visual Basic], numeric expressions
- precedence [Visual Basic], of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65cd446b99018d029e8a18d69ed33d8b8ac28f8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Como calcular valores numéricos (Visual Basic)
Você pode calcular valores numéricos com o uso de expressões numéricas. Um *expressão numérica* é uma expressão que contém literais, constantes e variáveis que representam valores numéricos e operadores que atuam sobre esses valores.  
  
## <a name="calculating-numeric-values"></a>Calculando valores numéricos  
  
#### <a name="to-calculate-a-numeric-value"></a>Para calcular um valor numérico  
  
-   Combine um ou mais literais numéricos, constantes e variáveis em uma expressão numérica. O exemplo a seguir mostra algumas expressões numéricas válidos.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     As três primeiras linhas mostram um literal, uma constante e uma variável. Cada uma forma de uma expressão numérica válida por si só. A linha final exibe uma combinação de uma variável com dois literais.  
  
     Observe que uma expressão numérica não formam uma completa [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instrução por si só. Você deve usar a expressão como parte de uma instrução completa.  
  
#### <a name="to-store-a-numeric-value"></a>Para armazenar um valor numérico  
  
-   Você pode usar uma instrução de atribuição para atribuir o valor representado por uma expressão numérica a uma variável, como demonstrado no exemplo a seguir.  
  
     [!code-vb[VbVbalrOperators#82](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     No exemplo anterior, o valor da expressão no lado direito do operador igual (`=`) é atribuído à variável `j` no lado esquerdo do operador, portanto `j` é avaliada como 276.  
  
     Para obter mais informações, consulte [Instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Vários operadores  
 Se a expressão numérica contém mais de um operador, a ordem na qual eles são avaliados é determinada pelas regras de precedência de operador. Para substituir as regras de precedência de operador, você deve colocar expressões entre parênteses, como no exemplo acima; as expressões entre são avaliadas primeiro.  
  
#### <a name="to-override-normal-operator-precedence"></a>Para substituir a precedência do operador normal  
  
-   Use parênteses para incluir as operações que você deseja que seja executada primeiro. O exemplo a seguir mostra dois resultados diferentes com o mesmo operandos e operadores.  
  
     [!code-vb[VbVbalrOperators#83](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     No exemplo anterior, o cálculo de `j` executa o operador de adição (`+`) primeiro porque os parênteses que delimitam `(67 + i)` substituir prioridade normal e o valor atribuído à `j` é 276 (69 4 vezes). O cálculo de `k` executa os operadores na sua prioridade normal (`*` antes de `+`) e o valor atribuído à `k` é 270 (268 + 2).  
  
     Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também  
 [Operadores e Expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)  
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operadores Aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
