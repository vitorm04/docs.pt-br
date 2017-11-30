---
title: "Expressões boolianas (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 48071c6833f9841fa42311dda59d6959c0645ff4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-expressions-visual-basic"></a>Expressões boolianas (Visual Basic)
Um *expressão booleana* é uma expressão que é avaliada como um valor de [tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` ou `False`. `Boolean`expressões podem ter várias formas. A forma mais simples é a comparação direta do valor de um `Boolean` variável para um `Boolean` literal, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>Dois significados do operador =  
 Observe que a instrução de atribuição `newCustomer = True` pareça ser o mesmo que a expressão no exemplo anterior, mas ele executa uma função diferente e é usado de maneira diferente. No exemplo anterior, a expressão `newCustomer = True` representa um valor booliano e o `=` sinal é interpretado como um operador de comparação. Em uma instrução autônoma, o `=` sinal é interpretado como um operador de atribuição e atribui o valor à direita para a variável à esquerda. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Para obter mais informações, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) e [instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operadores de comparação  
 Operadores de comparação como `=`, `<`, `>`, `<>`, `<=`, e `>=` produzir expressões booleanas, comparando a expressão à esquerda do operador para a expressão à direita o operador e avaliar o resultado como `True` ou `False`. O exemplo a seguir ilustra essa situação.  
  
 `42 < 81`  
  
 Como 42 é menor que 81, a expressão booliana no exemplo anterior é avaliada como `True`. Para obter mais informações sobre esse tipo de expressão, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operadores de comparação combinados com operadores lógicos  
 Expressões de comparação podem ser combinadas usando operadores lógicos para produzir mais complexas expressões Boolianas. O exemplo a seguir demonstra o uso dos operadores de comparação em conjunto com um operador lógico.  
  
 `x > y And x < 1000`  
  
 No exemplo anterior, o valor da expressão geral depende dos valores das expressões de cada lado do `And` operador. Se as duas expressões são `True`, em seguida, avalia a expressão geral para `True`. Se qualquer expressão for `False`, em seguida, toda a expressão é avaliada como `False`.  
  
## <a name="short-circuiting-operators"></a>Operadores de curto-circuito  
 Os operadores lógicos `AndAlso` e `OrElse` apresentar comportamento conhecido como *curto-circuito*. Um operador de curto-circuito primeiro avalia o operando da esquerda. Se o operando da esquerda determina o valor de toda a expressão, a execução do programa continua sem avaliar a expressão da direita. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 No exemplo anterior, o operador avalia a expressão da esquerda, `45 < 12`. Porque a expressão da esquerda é avaliada como `False`, toda a expressão lógica deve ser avaliada como `False`. A execução do programa, portanto, ignora a execução de código dentro do `If` blocos sem avaliar a expressão da direita, `testFunction(3)`. Este exemplo não chama `testFunction()` porque a expressão da esquerda falsifica a expressão inteira.  
  
 Da mesma forma, se a expressão da esquerda em uma expressão lógica usando `OrElse` é avaliada como `True`, a execução continua para a próxima linha de código sem avaliar a expressão da direita, porque a expressão da esquerda já foi validado todo o expressão.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Comparação com operadores de não-curto-circuito  
 Por outro lado, ambos os lados do operador lógico são avaliados quando os operadores lógicos `And` e `Or` são usados. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 O exemplo chama anterior `testFunction()` mesmo que avalia a expressão da esquerda para `False`.  
  
## <a name="parenthetical-expressions"></a>Expressões entre parênteses  
 Você pode usar parênteses para controlar a ordem de avaliação de expressões Boolianas. Expressões entre parênteses, avalie primeiro. Vários níveis de aninhamento, precedência é concedida às expressões mais profundamente aninhadas. Dentro dos parênteses, avaliação procede de acordo com as regras de precedência de operador. Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operadores de Comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)  
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
