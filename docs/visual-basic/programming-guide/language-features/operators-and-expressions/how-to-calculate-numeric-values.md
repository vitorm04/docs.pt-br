---
title: "Como: calcular valores numéricos (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- operator precedence
- operators [Visual Basic]
- expressions [Visual Basic], numeric
- calculations, numeric expressions
- precedence, of operators
- Visual Basic code, operators
- Visual Basic code, expressions
- numeric expressions
ms.assetid: ba6bf43d-bd96-49b8-b1de-4a7797551372
caps.latest.revision: 13
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: d844e2af3892d897125e21d3fd7047a8b295d10a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Como calcular valores numéricos (Visual Basic)
Você pode calcular valores numéricos com o uso de expressões numéricas. A *expressão numérica* é uma expressão que contém variáveis que representam valores numéricos, literais e constantes e operadores que atuam sobre esses valores.  
  
## <a name="calculating-numeric-values"></a>Calculando valores numéricos  
  
#### <a name="to-calculate-a-numeric-value"></a>Para calcular um valor numérico  
  
-   Combine um ou mais literais numéricos, constantes e variáveis em uma expressão numérica. O exemplo a seguir mostra algumas expressões numéricas válidas.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     As três primeiras linhas mostram um literal, uma constante e uma variável. Cada um deles faz uma expressão numérica válida por si só. A linha final mostra uma combinação de uma variável com dois literais.  
  
     Observe que uma expressão numérica não formam uma completa [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instrução por si só. Você deve usar a expressão como parte de uma instrução completa.  
  
#### <a name="to-store-a-numeric-value"></a>Para armazenar um valor numérico  
  
-   Você pode usar uma instrução de atribuição para atribuir o valor representado por uma expressão numérica a uma variável, como demonstra o exemplo a seguir.  
  
     [!code-vb[VbVbalrOperators&#82;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_1.vb)]  
  
     No exemplo anterior, o valor da expressão no lado direito do operador igual (`=`) é atribuído à variável `j` no lado esquerdo do operador, portanto `j` avalia 276.  
  
     Para obter mais informações, consulte [instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Vários operadores  
 Se a expressão numérica contiver mais de um operador, a ordem na qual eles são avaliados é determinada pelas regras de precedência de operador. Para substituir as regras de precedência de operador, você colocar expressões entre parênteses, como no exemplo acima; as expressões incluídas são avaliadas primeiro.  
  
#### <a name="to-override-normal-operator-precedence"></a>Para substituir a precedência do operador normal  
  
-   Use parênteses para delimitar as operações a serem executadas primeiro. O exemplo a seguir mostra dois resultados diferentes com o mesmo operandos e operadores.  
  
     [!code-vb[VbVbalrOperators&#83;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-calculate-numeric-values_2.vb)]  
  
     No exemplo anterior, o cálculo de `j` executa o operador de adição (`+`) primeiro porque os parênteses `(67 + i)` substituir a precedência normal e o valor atribuído a `j` é 276 (69 4 vezes). O cálculo de `k` executa os operadores na sua prioridade normal (`*` antes de `+`) e o valor atribuído a `k` é 270 (268 mais 2).  
  
     Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também  
 [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Instruções](../../../../visual-basic/language-reference/statements/index.md)   
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Operadores aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)   
 [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
