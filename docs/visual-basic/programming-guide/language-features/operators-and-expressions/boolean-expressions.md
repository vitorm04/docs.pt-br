---
title: "Expressões Boolianas (Visual Basic) | Documentos do Microsoft"
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
- short-circuiting
- Boolean expressions
- logical operators, Boolean expressions
- expressions [Visual Basic], Boolean
- expression evaluation, Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators, short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 5e94a8d6235613290cd67e0043b501d30dbca21f
ms.lasthandoff: 03/13/2017

---
# <a name="boolean-expressions-visual-basic"></a>Expressões boolianas (Visual Basic)
A *expressão booleana* é uma expressão que é avaliada como um valor de [tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` ou `False`. `Boolean`expressões podem ter diversos formatos. A mais simples é a comparação direta do valor de uma `Boolean` variável para um `Boolean` literal, como mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#87;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]  
  
## <a name="two-meanings-of-the--operator"></a>Dois significados do operador =  
 Observe que a instrução de atribuição `newCustomer = True` a mesma aparência a expressão no exemplo anterior, mas executa uma função diferente e é usado de maneira diferente. No exemplo anterior, a expressão `newCustomer = True` representa um valor booleano e o `=` sinal é interpretado como um operador de comparação. Em uma instrução autônoma, o `=` sinal é interpretado como um operador de atribuição e atribui o valor à direita para a variável à esquerda. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[88 VbVbalrOperators](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]  
  
 Para obter mais informações, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) e [instruções](../../../../visual-basic/language-reference/statements/index.md).  
  
## <a name="comparison-operators"></a>Operadores de comparação  
 Operadores de comparação como `=`, `<`, `>`, `<>`, `<=`, e `>=` produzir expressões Boolianas, comparando a expressão no lado esquerdo do operador para a expressão à direita do operador e avaliar o resultado como `True` ou `False`. O exemplo a seguir ilustra essa situação.  
  
 `42 < 81`  
  
 Como 42 é menor que 81, a expressão booliana no exemplo anterior é avaliada como `True`. Para obter mais informações sobre esse tipo de expressão, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).  
  
### <a name="comparison-operators-combined-with-logical-operators"></a>Operadores de comparação combinados com operadores lógicos  
 Expressões de comparação podem ser combinadas usando operadores lógicos para produzir mais complexas expressões booleanas. O exemplo a seguir demonstra o uso de operadores de comparação em conjunto com um operador lógico.  
  
 `x > y And x < 1000`  
  
 No exemplo anterior, o valor da expressão geral depende dos valores das expressões de cada lado do `And` operador. Se ambas as expressões forem `True`, em seguida, avalia a expressão geral para `True`. Se qualquer expressão for `False`, em seguida, toda a expressão é avaliada como `False`.  
  
## <a name="short-circuiting-operators"></a>Operadores de curto-circuito  
 Os operadores lógicos `AndAlso` e `OrElse` apresentar comportamento conhecido como *Short-circuiting*. Um operador Short-circuiting primeiro avalia o operando esquerdo. Se o operando esquerdo determina o valor de toda a expressão, a execução do programa prossegue sem avaliar a expressão direita. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators&#89;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]  
  
 No exemplo anterior, o operador avalia a expressão à esquerda, `45 < 12`. Porque a expressão esquerda é avaliada como `False`, toda a expressão lógica deve ser avaliada como `False`. A execução do programa, portanto, ignora a execução do código dentro de `If` bloco sem avaliar a expressão direita, `testFunction(3)`. Este exemplo não chama `testFunction()` porque a expressão esquerda falsifica a expressão inteira.  
  
 Da mesma forma, se a expressão esquerda em uma expressão lógica usando `OrElse` é avaliada como `True`, a execução continua para a próxima linha de código sem avaliar a expressão direita, porque a expressão esquerda já validou a expressão inteira.  
  
### <a name="comparison-with-non-short-circuiting-operators"></a>Comparação com operadores não curto circuito  
 Por outro lado, ambos os lados do operador lógico são avaliados quando os operadores lógicos `And` e `Or` são usados. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators&#90;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]  
  
 O exemplo chama anterior `testFunction()` mesmo que avalia a expressão da esquerda para `False`.  
  
## <a name="parenthetical-expressions"></a>Expressões entre parênteses  
 Você pode usar parênteses para controlar a ordem de avaliação de expressões booleanas. Expressões entre parênteses são avaliadas primeiro. Vários níveis de aninhamento, precedência é concedida às expressões mais profundamente aninhadas. Dentro dos parênteses, avaliação procede de acordo com as regras de precedência de operador. Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md)   
 [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Combinação eficiente de operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)   
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)   
 [Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)
