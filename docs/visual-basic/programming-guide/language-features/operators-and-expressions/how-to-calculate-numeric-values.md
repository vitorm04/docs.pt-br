---
title: 'Como: Calcular valores numéricos (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 3e367a10a3e703241c7417d3ea17068018becb5a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649726"
---
# <a name="how-to-calculate-numeric-values-visual-basic"></a>Como: Calcular valores numéricos (Visual Basic)
Você pode calcular valores numéricos com o uso de expressões numéricas. Um *expressão numérica* é uma expressão que contém os literais, constantes e variáveis que representam valores numéricos e operadores que atuam nesses valores.  
  
## <a name="calculating-numeric-values"></a>Calculando valores numéricos  
  
#### <a name="to-calculate-a-numeric-value"></a>Para calcular um valor numérico  
  
- Combine um ou mais literais numéricos, constantes e variáveis em uma expressão numérica. O exemplo a seguir mostra algumas expressões de numéricos válidos.  
  
     `93.217`  
  
     `System.Math.PI`  
  
     `counter`  
  
     `4 * (67 + i)`  
  
     As três primeiras linhas mostram um literal, uma constante e uma variável. Cada uma forma de uma expressão numérica válida por si só. A linha final mostra uma combinação de uma variável com dois literais.  
  
     Observe que uma expressão numérica não formam uma instrução completa do Visual Basic, por si só. Você deve usar a expressão como parte de uma instrução completa.  
  
#### <a name="to-store-a-numeric-value"></a>Para armazenar um valor numérico  
  
- Você pode usar uma instrução de atribuição para atribuir o valor representado por uma expressão numérica a uma variável, como demonstra o exemplo a seguir.  
  
     [!code-vb[VbVbalrOperators#82](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#82)]  
  
     No exemplo anterior, o valor da expressão no lado direito do operador de igual (`=`) é atribuído à variável `j` no lado esquerdo do operador, portanto, `j` é avaliada como 276.  
  
     Para obter mais informações, consulte [Instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="multiple-operators"></a>Vários operadores  
 Se a expressão numérica contiver mais de um operador, a ordem na qual eles são avaliados é determinada pelas regras de precedência do operador. Para substituir as regras de precedência de operador, você deve colocar expressões entre parênteses, como no exemplo acima; as expressões entre são avaliadas primeiro.  
  
#### <a name="to-override-normal-operator-precedence"></a>Para substituir a precedência do operador normal  
  
- Use parênteses para delimitar as operações que devem ser executadas pela primeira vez. O exemplo a seguir mostra dois resultados diferentes com o mesmo operandos e operadores.  
  
     [!code-vb[VbVbalrOperators#83](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#83)]  
  
     No exemplo anterior, o cálculo da `j` executa o operador de adição (`+`) primeiro porque os parênteses que delimitam `(67 + i)` substituir a precedência normal e o valor atribuído a `j` é 276 (4 vezes 69). O cálculo da `k` executa os operadores na respectiva precedência normal (`*` antes de `+`) e o valor atribuído a `k` é 270 (268 mais 2).  
  
     Para obter mais informações, consulte [precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também

- [Operadores e Expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instruções](../../../../visual-basic/language-reference/statements/index.md)
- [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operadores Aritméticos](../../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
