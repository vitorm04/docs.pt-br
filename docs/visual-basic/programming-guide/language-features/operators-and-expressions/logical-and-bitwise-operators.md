---
title: Operadores lógicos e bit a bit no Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- short-circuiting
- Boolean expressions
- logical operators [Visual Basic], Boolean expressions
- operators [Visual Basic], logical
- AndAlso operator [Visual Basic]
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators [Visual Basic]
- expressions [Visual Basic], Boolean
- Or operator [Visual Basic], logical operators
- Visual Basic code, operators
- short-circuiting [Visual Basic], logical operators
- logical operators [Visual Basic], short-circuiting
- Visual Basic code, expressions
- logical operators [Visual Basic], binary
- OrElse operator [Visual Basic]
- logical operators [Visual Basic], unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
ms.openlocfilehash: ac47b6d7fa4861d18646a23f442caccc4062852f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58819301"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operadores lógicos e bit a bit no Visual Basic
Operadores lógicos comparam `Boolean` expressões e retornam um `Boolean` resultado. O `And`, `Or`, `AndAlso`, `OrElse`, e `Xor` operadores são *binário* porque elas usam dois operandos, enquanto o `Not` operador é *unário* porque ele usa um operando único. Alguns desses operadores também podem executar operações de lógicas bit a bit em valores integrais.  
  
## <a name="unary-logical-operator"></a>Operador lógico unário  
 O [não o operador](../../../../visual-basic/language-reference/operators/not-operator.md) executa a lógica *negação* em um `Boolean` expressão. Ele gera a lógica oposta de seu operando. Se a expressão for avaliada como `True`, em seguida, `Not` retorna `False`; se a expressão for avaliada como `False`, em seguida, `Not` retorna `True`. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Operadores lógicos binários  
 O [operador And](../../../../visual-basic/language-reference/operators/and-operator.md) executa a lógica *junto* em dois `Boolean` expressões. Se ambas as expressões são avaliadas como `True`, em seguida, `And` retorna `True`. Se pelo menos uma das expressões for avaliada como `False`, em seguida, `And` retorna `False`.  
  
 O [ou operador](../../../../visual-basic/language-reference/operators/or-operator.md) executa a lógica *disjunção* ou *inclusão* em dois `Boolean` expressões. Se qualquer expressão for avaliada como `True`, ou ambos são avaliadas como `True`, em seguida, `Or` retorna `True`. Se nenhuma expressão for avaliada como `True`, `Or` retorna `False`.  
  
 O [operador Xor](../../../../visual-basic/language-reference/operators/xor-operator.md) executa a lógica *exclusão* em dois `Boolean` expressões. Se exatamente uma expressão for avaliada como `True`, mas não ambos `Xor` retorna `True`. Se ambas as expressões são avaliadas como `True` ou ambos são avaliadas como `False`, `Xor` retorna `False`.  
  
 O exemplo a seguir ilustra a `And`, `Or`, e `Xor` operadores.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Operações lógicas de curto-circuito  
 O [operador AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) é muito semelhante ao `And` operador, em que ele também executa a conjunção lógica em duas `Boolean` expressões. A principal diferença entre os dois é que `AndAlso` apresenta *Short-circuiting* comportamento. Se a primeira expressão em uma `AndAlso` expressão é avaliada como `False`, em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `AndAlso` retorna `False`.  
  
 Da mesma forma, o [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) executa a disjunção lógica de circuito em dois `Boolean` expressões. Se a primeira expressão em uma `OrElse` expressão é avaliada como `True`, em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `OrElse` retorna `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Vantagens e desvantagens de curto-circuito  
 Short-circuiting pode melhorar o desempenho, não avaliar uma expressão que não é possível alterar o resultado da operação lógica. No entanto, se essa expressão executa ações adicionais, Short-circuiting ignora essas ações. Por exemplo, se a expressão inclui uma chamada para um `Function` procedimento, o procedimento não é chamado se a expressão é curto-circuitada, e qualquer código adicional contido no `Function` não é executado. Portanto, a função pode ser executado apenas ocasionalmente e não pode ser testada corretamente. Ou a lógica do programa pode depender do código a `Function`.  
  
 O exemplo a seguir ilustra a diferença entre `And`, `Or`e suas contrapartes de curto-circuito.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 No exemplo anterior, observe que alguns códigos importantes dentro `checkIfValid()` não é executado quando a chamada é curto-circuitada. A primeira `If` declaração chama `checkIfValid()` Embora `12 > 45` retorna `False`, pois `And` não curto-circuito. A segunda `If` instrução não chamará `checkIfValid()`, porque quando `12 > 45` retorna `False`, `AndAlso` causam curto-circuito a segunda expressão. O terceiro `If` declaração chama `checkIfValid()` Embora `12 < 45` retorna `True`, pois `Or` não curto-circuito. O quarto `If` instrução não chamará `checkIfValid()`, porque quando `12 < 45` retorna `True`, `OrElse` causam curto-circuito a segunda expressão.  
  
## <a name="bitwise-operations"></a>Operações bit a bit  
 Operações bit a bit avaliar dois valores inteiros em formato binário (base 2). Eles comparam os bits nas posições correspondentes e, em seguida, atribuir valores com base na comparação. O exemplo a seguir ilustra o `And` operador.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 O exemplo anterior define o valor de `x` como 1. Isso acontece pelos seguintes motivos:  
  
-   Os valores são tratados como binários:  
  
     3 em formato binário = 011  
  
     5 em formato binário = 101  
  
-   O `And` operador compara as representações binárias, uma posição binária (bits) por vez. Se ambos os bits em uma posição especificada forem 1, 1 é colocado naquela posição no resultado. Se qualquer bit for 0, 0 é colocado na posição no resultado. No exemplo anterior isso funciona da seguinte maneira:  
  
     011 (3 em formato binário)  
  
     101 (5 em formato binário)  
  
     001 (o resultado, no formato binário)  
  
-   O resultado será tratado como decimal. O valor 001 é a representação binária de 1, portanto, `x` = 1.  
  
 O bit a bit `Or` operação é semelhante, exceto que um 1 é atribuído para o bit de resultado, se um ou ambos os bits comparados é 1. `Xor` atribui um 1 para o bit de resultado se exatamente um dos bits comparados (não ambos) for 1. `Not` receba um operando único e inverte todos os bits, incluindo o bit de sinal e atribui o valor para o resultado. Isso significa que, para assinado números positivos e negativos `Not` sempre retorna um valor negativo e para números negativos, `Not` sempre retorna um alarme ou valor zero.  
  
 O `AndAlso` e `OrElse` operadores não dão suporte a operações bit a bit.  
  
> [!NOTE]
>  Operações bit a bit podem ser executadas em tipos integrais somente. Valores de ponto flutuante devem ser convertidos em tipos integrais antes de prosseguir com a operação bit a bit.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bit a bit (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
