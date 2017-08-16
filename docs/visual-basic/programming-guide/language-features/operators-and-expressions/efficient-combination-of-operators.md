---
title: "Combinação eficiente de operadores (Visual Basic) | Documentos do Microsoft"
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
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses, complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: 12
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
ms.openlocfilehash: 259330f3c3923786aae1b8a3cea89dd68601c7c9
ms.lasthandoff: 03/13/2017

---
# <a name="efficient-combination-of-operators-visual-basic"></a>Combinação eficiente de operadores (Visual Basic)
Expressões complexas podem conter muitos operadores diferentes. O exemplo a seguir ilustra essa situação.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Criar expressões complexas, como no exemplo anterior requer uma compreensão completa das regras de precedência de operador. Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## <a name="parenthetical-expressions"></a>Expressões entre parênteses  
 Com frequência você deseja operações em uma ordem diferente daquela determinada pela precedência de operador. Considere o exemplo a seguir.  
  
 `x = z * y + 4`  
  
 Multiplica o exemplo anterior `z` por `y`, em seguida, adiciona o resultado para `4`. Mas se você quiser adicionar `y` e `4` antes de multiplicar o resultado por `z`, você pode substituir a precedência do operador normal usando parênteses. Colocando uma expressão entre parênteses, você forçar essa expressão seja avaliada primeiro, independentemente de precedência de operador. Para forçar o exemplo anterior para fazer a adição primeiro, você poderia reescrever como no exemplo a seguir.  
  
 `x = z * (y + 4)`  
  
 O exemplo anterior adiciona `y` e `4`, em seguida, multiplica essa soma pelo `z`.  
  
### <a name="nested-parenthetical-expressions"></a>Expressões entre parênteses aninhadas  
 Você pode aninhar expressões em vários níveis de parênteses para substituir a precedência ainda mais. As expressões mais profundamente aninhadas em parênteses são avaliadas primeiro, seguido pelo próximo aninhado mais profundamente, e assim por diante para menos profundamente aninhados e, finalmente, as expressões fora parênteses. O exemplo a seguir ilustra essa situação.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 No exemplo anterior, `z + 2` é avaliado primeiro e, em seguida, outras expressões entre parênteses. Expoente, que normalmente tem precedência maior do que a adição ou multiplicação, é avaliada por último neste exemplo porque outras expressões estão entre parênteses.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Operadores lógicos/bit a bit (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Como: calcular valores numéricos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
