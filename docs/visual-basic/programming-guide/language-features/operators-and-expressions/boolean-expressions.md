---
title: Expressões boolianas (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation [Visual Basic], Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators [Visual Basic], short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
ms.openlocfilehash: 065df7d6217dd6f817dee1d11dd0fd4a68b6323c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965534"
---
# <a name="boolean-expressions-visual-basic"></a>Expressões boolianas (Visual Basic)
Um *expressão booliana* é uma expressão que é avaliada como um valor de [tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` ou `False`. `Boolean` expressões podem ter diversos formatos. A mais simples é a comparação direta do valor de uma `Boolean` variável para um `Boolean` literal, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Dois significados do operador =  
 Observe que a instrução de atribuição `newCustomer = True` tem a mesma aparência da expressão no exemplo anterior, mas ele executa uma função diferente e é usado de maneira diferente. No exemplo anterior, a expressão `newCustomer = True` representa um valor booleano e o `=` sinal é interpretado como um operador de comparação. Em uma instrução autônoma, o `=` é interpretada como um operador de atribuição de entrada e atribui o valor à direita para a variável à esquerda. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Para obter mais informações, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) e [instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operadores de comparação  
 Operadores de comparação, como `=`, `<`, `>`, `<>`, `<=`, e `>=` produzir as expressões Boolianas, comparando a expressão no lado esquerdo do operador para a expressão no lado direito o operador e avaliar o resultado como `True` ou `False`. O exemplo a seguir ilustra essa situação.  
  
 `42 < 81`  
  
 Como 42 é menor que 81, a expressão booliana no exemplo anterior é avaliada como `True`. Para obter mais informações sobre esse tipo de expressão, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operadores de comparação, combinados com operadores lógicos  
 Expressões de comparação podem ser combinadas usando operadores lógicos para produzir as expressões Boolianas mais complexas. O exemplo a seguir demonstra o uso de operadores de comparação em conjunto com um operador lógico.  
  
 `x > y And x < 1000`  
  
 No exemplo anterior, o valor da expressão geral depende dos valores das expressões em cada lado do `And` operador. Se ambas as expressões forem `True`, em seguida, avalia a expressão geral `True`. Se qualquer expressão for `False`, toda a expressão é avaliada como `False`.  
  
## <a name="short-circuiting-operators"></a>Operadores de curto-circuito  
 Os operadores lógicos `AndAlso` e `OrElse` apresentam comportamento conhecido como *Short-circuiting*. Um operador de curto-circuito avaliará o operando esquerdo primeiro. Se o operando esquerdo determina o valor da expressão inteira, a execução do programa continua sem avaliar a expressão direita. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 No exemplo anterior, o operador avalia a expressão da esquerda, `45 < 12`. Porque a expressão da esquerda é avaliada como `False`, toda a expressão lógica deve ser avaliada como `False`. A execução do programa, portanto, ignora a execução do código dentro de `If` bloco sem avaliar a expressão da direita, `testFunction(3)`. Este exemplo não chama `testFunction()` porque a expressão esquerda falsifica a expressão inteira.  
  
 Da mesma forma, se a expressão da esquerda em uma expressão lógica usando `OrElse` for avaliada como `True`, a execução continua para a próxima linha de código sem avaliar a expressão da direita, porque a expressão esquerda já foi validado para todo o expressão.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Comparação com operadores-circuito curto  
 Por outro lado, ambos os lados do operador lógico são avaliados quando operadores lógicos `And` e `Or` são usados. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 O exemplo a anterior chama `testFunction()` mesmo que a expressão da esquerda é avaliada como `False`.  
  
## <a name="parenthetical-expressions"></a>Expressões entre parênteses  
 Você pode usar parênteses para controlar a ordem de avaliação de expressões Boolianas. Expressões entre parênteses, avalie primeiro. Para vários níveis de aninhamento, precedência é concedida às expressões mais profundamente aninhadas. Dentro dos parênteses, avaliação procede de acordo com as regras de precedência de operador. Para obter mais informações, consulte [precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também
- [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Operadores de Comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
