---
title: "Combina&#231;&#227;o eficiente de operadores (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "expressões [Visual Basic], complexo"
  - "expressões [Visual Basic], operadores"
  - "expressões [Visual Basic], parênteses"
  - "expressões numéricas"
  - "operadores [Visual Basic], associatividade"
  - "operadores [Visual Basic], expressões complexas"
  - "operadores [Visual Basic], precedência"
  - "parênteses, expressões complexas"
  - "código do Visual Basic, expressões"
  - "código do Visual Basic, operadores"
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Combina&#231;&#227;o eficiente de operadores (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Expressões complexas podem conter muitos operadores diferentes.  O exemplo a seguir ilustra isto:  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 A criação de expressões complexas, como no exemplo anterior requer uma compreensão completa das regras de precedência do operador.  Para obter mais informações, consulte [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).  
  
## Expressões entre parênteses  
 Freqüência em que as operações para continuar em uma ordem diferente daquela que determinadas pela precedência do operador.  Considere o exemplo a seguir:  
  
 `x = z * y + 4`  
  
 O exemplo anterior multiplica `z` por `y`, em seguida, adiciona o resultado para `4`.  Mas se você quiser adicionar `y` e `4` antes de multiplicar o resultado por `z`, você pode substituir a precedência do operador normal usando parênteses.  Colocando uma expressão entre parênteses, você pode forçar dessa expressão a ser avaliada em primeiro lugar, independentemente da precedência de operadores.  Para forçar o exemplo anterior para fazer a inclusão pela primeira vez, você poderia reescrevê\-lo como no exemplo a seguir.  
  
 `x = z * (y + 4)`  
  
 O exemplo anterior adiciona `y` e `4`, em seguida, multiplica essa soma pelo `z`.  
  
### Expressões entre parênteses aninhadas  
 Você pode aninhar as expressões em vários níveis de parênteses para substituir a precedência ainda mais.  As expressões mais profundamente aninhadas entre parênteses são avaliadas primeiro, seguido pelo próximo mais profundamente aninhado, de e assim por diante para menos profundamente aninhados e, finalmente, as expressões fora de parênteses.  O exemplo a seguir ilustra isto:  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 No exemplo anterior, `z + 2` é avaliado primeiro, depois em seguida outras expressões entre parênteses.  Exponenciação, que normalmente tem precedência maior do que a adição ou multiplicação, seja avaliada por último neste exemplo porque outras expressões são colocados entre parênteses.  
  
## Consulte também  
 [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)   
 [Operadores lógicos\/bit a bit](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Expressões boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Como calcular valores numéricos](../Topic/How%20to:%20Calculate%20Numeric%20Values%20\(Visual%20Basic\).md)   
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)