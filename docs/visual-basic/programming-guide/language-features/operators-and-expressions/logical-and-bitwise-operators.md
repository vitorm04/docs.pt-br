---
title: "Operadores lógicos e bit a bit no Visual Basic | Documentos do Microsoft"
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
- operators [Visual Basic], logical
- AndAlso operator
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators
- expressions [Visual Basic], Boolean
- Or operator, logical operators
- Visual Basic code, operators
- short-circuiting, logical operators
- logical operators, short-circuiting
- Visual Basic code, expressions
- logical operators, binary
- OrElse operator [Visual Basic]
- logical operators, unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: 22
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
ms.openlocfilehash: 0d2b4827e416b633ac00167dd200d66b3c798858
ms.lasthandoff: 03/13/2017

---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operadores lógicos e bit a bit no Visual Basic
Operadores lógicos comparam `Boolean` expressões e retornar um `Boolean` resultado. O `And`, `Or`, `AndAlso`, `OrElse`, e `Xor` operadores são *binário* porque eles usam dois operandos, enquanto o `Not` operador é *unário* porque ele usa um operando único. Alguns desses operadores também podem executar operações de lógicas bit a bit em valores integral.  
  
## <a name="unary-logical-operator"></a>Operador lógico unário  
 O [operador Not](../../../../visual-basic/language-reference/operators/not-operator.md) executa lógica *negação* em um `Boolean` expressão. Produz a lógica oposta do operando. Se a expressão for avaliada como `True`, em seguida, `Not` retorna `False`; se a expressão for avaliada como `False`, em seguida, `Not` retorna `True`. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators&#77;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]  
  
## <a name="binary-logical-operators"></a>Operadores lógicos binários  
 O [operador e](../../../../visual-basic/language-reference/operators/and-operator.md) executa lógica *conjunto* em dois `Boolean` expressões. Se as duas expressões são `True`, em seguida, `And` retorna `True`. Se pelo menos uma das expressões é avaliada como `False`, em seguida, `And` retorna `False`.  
  
 O [operador ou](../../../../visual-basic/language-reference/operators/or-operator.md) executa lógica *disjunção* ou *inclusão* em dois `Boolean` expressões. Se qualquer expressão for avaliada como `True`, ou ambos são avaliadas como `True`, em seguida, `Or` retorna `True`. Se nenhuma expressão for avaliada como `True`, `Or` retorna `False`.  
  
 O [operador Xor](../../../../visual-basic/language-reference/operators/xor-operator.md) executa lógica *exclusão* em dois `Boolean` expressões. Se exatamente uma expressão for avaliada como `True`, mas não ambos, `Xor` retorna `True`. Se as duas expressões são `True` ou ambos são avaliadas como `False`, `Xor` retorna `False`.  
  
 O exemplo a seguir ilustra o `And`, `Or`, e `Xor` operadores.  
  
 [!code-vb[VbVbalrOperators&#78;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]  
  
## <a name="short-circuiting-logical-operations"></a>Operações de lógicas do curto-circuito  
 O [operador AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) é muito semelhante do `And` operador, que também executa conjunção lógica em duas `Boolean` expressões. A principal diferença entre os dois é que `AndAlso` exibe *Short-circuiting* comportamento. Se a primeira expressão em uma `AndAlso` expressão é avaliada como `False`, em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `AndAlso` retorna `False`.  
  
 Da mesma forma, o [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) executa a disjunção lógica de circuito em duas `Boolean` expressões. Se a primeira expressão em uma `OrElse` expressão é avaliada como `True`, em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `OrElse` retorna `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Vantagens e desvantagens do curto-circuito  
 Short-circuiting pode melhorar o desempenho por não avaliar uma expressão que não é possível alterar o resultado da operação lógica. No entanto, se essa expressão executa ações adicionais, Short-circuiting ignora essas ações. Por exemplo, se a expressão incluir uma chamada para um `Function` procedimento, o procedimento não é chamado se a expressão for curto-circuitada, e qualquer código adicional contidas a `Function` não é executado. Portanto, a função pode ser executado apenas ocasionalmente e não pode ser testada corretamente. Ou a lógica do programa pode depender do código de `Function`.  
  
 O exemplo a seguir ilustra a diferença entre `And`, `Or`e suas contrapartes curto-circuito.  
  
 [!code-vb[VbVbalrOperators&#81;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]  
  
 [!code-vb[VbVbalrOperators&#80;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]  
  
 [!code-vb[VbVbalrOperators&#79;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]  
  
 No exemplo anterior, observe que alguns códigos importantes dentro de `checkIfValid()` não é executado quando a chamada é curto-circuitada. A primeira `If` chamadas de instrução `checkIfValid()` , embora `12 > 45` retorna `False`, pois `And` não curto-circuito. A segunda `If` instrução não chama `checkIfValid()`, porque quando `12 > 45` retorna `False`, `AndAlso` reduz a segunda expressão. A terceira `If` chamadas de instrução `checkIfValid()` , embora `12 < 45` retorna `True`, pois `Or` não curto-circuito. O quarto `If` instrução não chama `checkIfValid()`, porque quando `12 < 45` retorna `True`, `OrElse` reduz a segunda expressão.  
  
## <a name="bitwise-operations"></a>Operações bit a bit  
 Operações bit a bit avaliar dois valores integrais em formato binário (base 2). Eles comparam os bits em posições correspondentes e, em seguida, atribuir valores com base na comparação. O exemplo a seguir ilustra o `And` operador.  
  
 [!code-vb[VbVbalrConcepts n º&2;](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]  
  
 O exemplo anterior define o valor de `x` como 1. Isso acontece pelas seguintes razões:  
  
-   Os valores são tratados como binários:  
  
     3 no formato binário = 011  
  
     5 na forma binária = 101  
  
-   O `And` operador compara as representações binárias, uma posição de binária (bits) por vez. Se os dois bits na posição especificada forem 1, 1 é colocado na posição no resultado. Se um bit for 0, 0 é colocado na posição no resultado. No exemplo anterior isso funciona da seguinte maneira:  
  
     011 (3 em formato binário)  
  
     101 (5 em formato binário)  
  
     001 (o resultado, no formato binário)  
  
-   O resultado é tratado como decimal. O valor 001 é a representação binária de 1, então `x` = 1.  
  
 Bit a bit `Or` operação é semelhante, exceto que um 1 é atribuído para o bit de resultado se um ou ambos os bits comparados é 1. `Xor`atribui um 1 para o bit de resultado se exatamente um dos bits comparados (não ambos) é 1. `Not`leva um operando único e inverte todos os bits, incluindo o bit de sinal e atribui o valor para o resultado. Isso significa que para assinado números positivos, `Not` sempre retorna um valor negativo e para números negativos, `Not` sempre retorna um positivo ou valor zero.  
  
 O `AndAlso` e `OrElse` operadores não oferecem suporte a operações bit a bit.  
  
> [!NOTE]
>  Operações bit a bit podem ser executadas em apenas tipos integrais. Valores de ponto flutuante devem ser convertidos em tipos integrais antes de prosseguir com a operação bit a bit.  
  
## <a name="see-also"></a>Consulte também  
 [Operadores lógicos/bit a bit (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)   
 [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)   
 [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)   
 [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
