---
title: Comparações de valor
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], comparing values
- Visual Basic code, operators
- Visual Basic code, expressions
- comparison operators [Visual Basic], comparing expressions
- numeric expressions
- operators [Visual Basic], comparison
- expressions [Visual Basic], comparing
ms.assetid: 60da0c76-9458-4afc-97e9-44a7939c064c
ms.openlocfilehash: f766eaaada486a0f70838bafb754d25070ff4174
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346281"
---
# <a name="value-comparisons-visual-basic"></a>Comparações de valor (Visual Basic)
Operadores de comparação podem ser usados para construir expressões que comparam os valores de variáveis numéricas. Essas expressões retornam um valor `Boolean` com base em se a comparação é verdadeira ou falsa. Exemplos de tal expressão são os seguintes.  
  
 `45 > 26`  
  
 `26 > 45`  
  
 A primeira expressão é avaliada como `True`, pois 45 é maior que 26. O segundo exemplo é avaliado como `False`, porque 26 não é maior que 45.  
  
 Você também pode comparar expressões numéricas dessa maneira. As expressões que você compara podem ser expressões complexas, como no exemplo a seguir.  
  
 `x / 45 * (y +17) >= System.Math.Sqrt(z) / (p - (x * 16))`  
  
 A expressão complexa anterior inclui literais, variáveis e chamadas de função. As expressões em ambos os lados do operador de comparação são avaliadas e os valores resultantes são comparados usando o operador de comparação de `>=`. Se o valor da expressão no lado esquerdo for maior ou igual ao valor da expressão à direita, a expressão inteira será avaliada como `True`; caso contrário, ele será avaliado como `False`.  
  
 As expressões que comparam valores são mais comumente usadas em `If...Then` construções, como no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#84](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#84)]  
  
 O sinal de `=` é um operador de comparação, bem como um operador de atribuição. Quando usado como um operador de comparação, ele avalia se o valor à esquerda é igual ao valor à direita, conforme mostrado no exemplo a seguir.  
  
 [!code-vb[VbVbalrOperators#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#85)]  
  
 Você também pode usar uma expressão de comparação em qualquer lugar que um valor `Boolean` seja necessário, como em uma instrução `If`, `While`, `Loop`ou `ElseIf` ou ao atribuir ou ao passar um valor para uma variável `Boolean`. No exemplo a seguir, o valor retornado pela expressão de comparação é atribuído a uma variável `Boolean`.  
  
 [!code-vb[VbVbalrOperators#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#86)]  
  
## <a name="see-also"></a>Consulte também

- [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operadores e Expressões](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Como calcular valores numéricos](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md)
