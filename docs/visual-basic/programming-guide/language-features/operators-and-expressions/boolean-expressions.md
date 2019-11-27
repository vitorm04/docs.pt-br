---
title: Expressões boolianas
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
ms.openlocfilehash: 1000ec6e4b35d0cb2c6232b50f9a9551cb0dfdcd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350805"
---
# <a name="boolean-expressions-visual-basic"></a>Expressões boolianas (Visual Basic)
Uma *expressão booliana* é uma expressão que é avaliada como um valor do [tipo de dados booliano](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` ou `False`. `Boolean` expressões podem ter várias formas. A maneira mais simples é a comparação direta do valor de uma variável `Boolean` para um literal `Boolean`, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#87](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#87)]  
  
## <a name="two-meanings-of-the--operator"></a>Dois significados do operador =  
 Observe que a instrução de atribuição `newCustomer = True` tem a mesma aparência da expressão no exemplo anterior, mas executa uma função diferente e é usada de forma diferente. No exemplo anterior, a expressão `newCustomer = True` representa um valor booliano e o sinal de `=` é interpretado como um operador de comparação. Em uma instrução autônoma, o sinal de `=` é interpretado como um operador de atribuição e atribui o valor à direita para a variável à esquerda. O exemplo a seguir mostra isso.  
  
 [!code-vb[VbVbalrOperators#88](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#88)]  
  
 Para obter mais informações, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) e [instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operadores de comparação  
 Operadores de comparação como `=`, `<`, `>`, `<>`, `<=`e `>=` produzem expressões booleanas comparando a expressão no lado esquerdo do operador com a expressão no lado direito do operador e avaliando o resultado como `True` ou `False`. O exemplo a seguir mostra isso.  
  
 `42 < 81`  
  
 Como 42 é menor que 81, a expressão booliana no exemplo anterior é avaliada como `True`. Para obter mais informações sobre esse tipo de expressão, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operadores de comparação combinados com operadores lógicos  
 Expressões de comparação podem ser combinadas usando operadores lógicos para produzir expressões booleanas mais complexas. O exemplo a seguir demonstra o uso de operadores de comparação em conjunto com um operador lógico.  
  
 `x > y And x < 1000`  
  
 No exemplo anterior, o valor da expressão geral depende dos valores das expressões em cada lado do operador de `And`. Se ambas as expressões forem `True`, a expressão geral será avaliada como `True`. Se uma das expressões for `False`, a expressão inteira será avaliada como `False`.  
  
## <a name="short-circuiting-operators"></a>Operadores de curto-circuito  
 Os operadores lógicos `AndAlso` e `OrElse` apresentam o comportamento conhecido como *curto-circuito*. Um operador de curto-circuito avalia o operando à esquerda primeiro. Se o operando esquerdo determinar o valor da expressão inteira, a execução do programa continuará sem avaliar a expressão correta. O exemplo a seguir mostra isso.  
  
 [!code-vb[VbVbalrOperators#89](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#89)]  
  
 No exemplo anterior, o operador avalia a expressão à esquerda, `45 < 12`. Como a expressão à esquerda é avaliada como `False`, a expressão lógica inteira deve ser avaliada como `False`. A execução do programa, portanto, ignora a execução do código dentro do bloco de `If` sem avaliar a expressão Right, `testFunction(3)`. Este exemplo não chama `testFunction()` porque a expressão Left falsifica a expressão inteira.  
  
 Da mesma forma, se a expressão esquerda em uma expressão lógica usando `OrElse` for avaliada como `True`, a execução prosseguirá para a próxima linha de código sem avaliar a expressão direita, porque a expressão à esquerda já validou a expressão inteira.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Comparação com operadores de circuito não curto  
 Por outro lado, ambos os lados do operador lógico são avaliados quando os operadores lógicos `And` e `Or` são usados. O exemplo a seguir mostra isso.  
  
 [!code-vb[VbVbalrOperators#90](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#90)]  
  
 O exemplo anterior chama `testFunction()` embora a expressão à esquerda seja avaliada como `False`.  
  
## <a name="parenthetical-expressions"></a>Expressões entre parênteses  
 Você pode usar parênteses para controlar a ordem de avaliação de expressões booleanas. As expressões delimitadas por parênteses são avaliadas primeiro. Para vários níveis de aninhamento, a precedência é concedida às expressões aninhadas mais profundamente. Entre parênteses, a avaliação prossegue de acordo com as regras de precedência de operador. Para obter mais informações, consulte [precedência de operador em Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos e de bits bit a Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md)
- [Operadores de Comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
- [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
