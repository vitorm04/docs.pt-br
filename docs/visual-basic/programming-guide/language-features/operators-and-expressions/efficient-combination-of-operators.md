---
title: "Combinação eficiente de operadores (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b0f1d637bc1757515cf271a8c70d62effab0843
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-combination-of-operators-visual-basic"></a>Combinação eficiente de operadores (Visual Basic)
Expressões complexas podem conter muitos operadores diferentes. O exemplo a seguir ilustra essa situação.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Criar expressões complexas, como mostrado no exemplo anterior requer uma compreensão completa das regras de precedência de operador. Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Expressões entre parênteses  
 Geralmente, você deseja operações continuem em uma ordem diferente daquela que determinado pela precedência do operador. Considere o exemplo a seguir.  
  
 `x = z * y + 4`  
  
 Multiplica o exemplo anterior `z` por `y`, em seguida, adiciona o resultado para `4`. Porém, se você deseja adicionar `y` e `4` antes de multiplicar o resultado pelo `z`, você pode substituir a precedência do operador normal usando parênteses. Colocando uma expressão entre parênteses, você deve forçar essa expressão seja avaliada primeiro, independentemente de precedência do operador. Para forçar o exemplo anterior para fazer a adição primeiro, você poderia reescrever como no exemplo a seguir.  
  
 `x = z * (y + 4)`  
  
 O exemplo anterior adiciona `y` e `4`, em seguida, multiplica essa soma pelo `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Expressões entre parênteses aninhadas  
 Você pode aninhar expressões em vários níveis de parênteses para substituir a precedência ainda mais. As expressões mais profundamente aninhadas entre parênteses são avaliadas primeiro, seguida da próxima mais profundamente aninhada, de e assim por diante para menos profundamente aninhadas e, finalmente, as expressões fora parênteses. O exemplo a seguir ilustra essa situação.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 No exemplo anterior, `z + 2` é avaliado primeiro, depois em seguida outras expressões entre parênteses. Exponenciação, que normalmente tem precedência maior do que a adição ou multiplicação, é avaliada pela última neste exemplo porque outras expressões são colocados entre parênteses.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)  
 [Comparações de Valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Como calcular valores numéricos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)  
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
