---
title: "Valor comparações (Visual Basic) | Documentos do Microsoft"
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
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators, comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
caps.latest.revision: 9
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
ms.openlocfilehash: d26e1ff0210278538d6f854af019629e68429019
ms.lasthandoff: 03/13/2017

---
# <a name="value-comparisons-visual-basic"></a>Comparações de valor (Visual Basic)
Operadores de comparação podem ser usados para construir expressões que comparam valores de variáveis numéricas. Essas expressões retornam um `Boolean` valor com base em se a comparação é true ou false. Estes são exemplos de uma expressão.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 A primeira expressão é avaliada como `True`, porque 45 é maior que 26. O segundo exemplo avalia `False`, porque 26 não é maior do que 45.  
  
 Você também pode comparar expressões numéricas dessa maneira. Expressões que você compara podem estar expressões complexas, como no exemplo a seguir.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 A expressão complexa anterior inclui literais, variáveis e chamadas de função. As expressões em ambos os lados do operador de comparação são avaliadas, e os valores resultantes são então comparados usando o `>=` operador de comparação. Se o valor da expressão no lado esquerdo for maior que ou igual ao valor da expressão no lado direito, toda a expressão é avaliada como `True`; caso contrário, ele será avaliado como `False`.  
  
 Expressões que comparam valores são mais comumente usadas em `If...Then` construções, como no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#84;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_1.vb)]  
  
 O `=` sinal é um operador de comparação, bem como um operador de atribuição. Quando usado como um operador de comparação, ele avalia se o valor à esquerda é igual ao valor à direita, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators&#85;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_2.vb)]  
  
 Você também pode usar uma expressão de comparação em qualquer lugar uma `Boolean` valor é necessário, como em uma `If`, `While`, `Loop`, ou `ElseIf` instrução, ou quando atribuir ou passar um valor para um `Boolean` variável. No exemplo a seguir, o valor retornado pela expressão de comparação é atribuído a um `Boolean` variável.  
  
 [!code-vb[VbVbalrOperators&#86;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/value-comparisons_3.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operadores e expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Como: calcular valores numéricos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)   
 [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
