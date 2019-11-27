---
title: Operadores lógicos e bit a bit
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
ms.openlocfilehash: 55a246c0d56501a409ebbc7d0d0aa39ae9fa1770
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343601"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operadores lógicos e bit a bit no Visual Basic
Operadores lógicos comparam expressões `Boolean` e retornam um resultado de `Boolean`. Os operadores `And`, `Or`, `AndAlso`, `OrElse`e `Xor` são *binários* porque usam dois operandos, enquanto o operador de `Not` é *unário* porque usa um único operando. Alguns desses operadores também podem executar operações lógicas de bit a bit em valores integrais.  
  
## <a name="unary-logical-operator"></a>Operador lógico unário  
 O [operador NOT](../../../../visual-basic/language-reference/operators/not-operator.md) executa uma *negação* lógica em uma expressão `Boolean`. Ele gera o oposto lógico de seu operando. Se a expressão for avaliada como `True`, `Not` retornará `False`; se a expressão for avaliada como `False`, `Not` retornará `True`. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Operadores lógicos binários  
 O [operador and](../../../../visual-basic/language-reference/operators/and-operator.md) executa a *conjunção* lógica em duas expressões de `Boolean`. Se as duas expressões forem avaliadas como `True`, `And` retornará `True`. Se pelo menos uma das expressões for avaliada como `False`, `And` retornará `False`.  
  
 O [operador OR](../../../../visual-basic/language-reference/operators/or-operator.md) executa a *disjunção* lógica ou a *inclusão* em duas expressões de `Boolean`. Se uma das expressões for avaliada como `True`ou ambos forem avaliadas como `True`, `Or` retornará `True`. Se nenhuma expressão for avaliada como `True`, `Or` retornará `False`.  
  
 O [operador XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) executa a *exclusão* lógica em duas expressões de `Boolean`. Se exatamente uma expressão for avaliada como `True`, mas não em ambos, `Xor` retornará `True`. Se as duas expressões forem avaliadas como `True` ou ambas forem avaliadas como `False`, `Xor` retornará `False`.  
  
 O exemplo a seguir ilustra os operadores `And`, `Or`e `Xor`.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Operações lógicas de curto-circuito  
 O [Operador AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) é muito semelhante ao operador de `And`, pois ele também executa uma conjunção lógica em duas expressões de `Boolean`. A principal diferença entre os dois é que `AndAlso` exibe o comportamento *de curto-circuito* . Se a primeira expressão em uma expressão de `AndAlso` for avaliada como `False`, a segunda expressão não será avaliada porque não poderá alterar o resultado final e `AndAlso` retornará `False`.  
  
 Da mesma forma, o [Operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) executa uma disjunção lógica de curto-circuito em duas expressões de `Boolean`. Se a primeira expressão em uma expressão de `OrElse` for avaliada como `True`, a segunda expressão não será avaliada porque não poderá alterar o resultado final e `OrElse` retornará `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Compensações de curto-circuito  
 O curto-circuito pode melhorar o desempenho não avaliando uma expressão que não possa alterar o resultado da operação lógica. No entanto, se essa expressão executar ações adicionais, o circuito curto ignorará essas ações. Por exemplo, se a expressão incluir uma chamada para um procedimento `Function`, esse procedimento não será chamado se a expressão tiver um circuito curto e qualquer código adicional contido no `Function` não for executado. Portanto, a função pode ser executada apenas ocasionalmente e pode não ser testada corretamente. Ou a lógica do programa pode depender do código na `Function`.  
  
 O exemplo a seguir ilustra a diferença entre `And`, `Or`e suas contrapartes de curto-circuito.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 No exemplo anterior, observe que algum código importante dentro de `checkIfValid()` não é executado quando a chamada é de curto-circuito. A primeira instrução `If` chama `checkIfValid()` mesmo que `12 > 45` retorne `False`, porque o `And` não é de curto-circuito. A segunda instrução `If` não chama `checkIfValid()`, porque quando `12 > 45` retorna `False`, `AndAlso` short-circuits a segunda expressão. A terceira instrução de `If` chama `checkIfValid()` mesmo que `12 < 45` retorne `True`, porque `Or` não faz um circuito curto. A quarta `If` instrução não chama `checkIfValid()`, porque quando `12 < 45` retorna `True`, `OrElse` short-circuits a segunda expressão.  
  
## <a name="bitwise-operations"></a>Operações bits  
 As operações bit a bit avaliam dois valores integrais no formulário binário (base 2). Eles comparam os bits em posições correspondentes e, em seguida, atribuem valores com base na comparação. O exemplo a seguir ilustra o operador de `And`.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 O exemplo anterior define o valor de `x` como 1. Isso ocorre pelos seguintes motivos:  
  
- Os valores são tratados como binários:  
  
     3 em formato binário = 011  
  
     5 em formato binário = 101  
  
- O operador `And` compara as representações binárias, uma posição binária (bit) por vez. Se ambos os bits em uma determinada posição forem 1, um 1 será colocado nessa posição no resultado. Se um dos dois bits for 0, um 0 será colocado nessa posição no resultado. No exemplo anterior, isso funciona da seguinte maneira:  
  
     011 (3 em formato binário)  
  
     101 (5 em formato binário)  
  
     001 (o resultado, em formato binário)  
  
- O resultado é tratado como Decimal. O valor 001 é a representação binária de 1, portanto `x` = 1.  
  
 A operação de `Or` bits é semelhante, exceto pelo fato de que um 1 é atribuído ao bit de resultado se um ou ambos os bits comparados forem 1. `Xor` atribui um 1 ao bit de resultado se exatamente um dos bits comparados (não ambos) for 1. `Not` usa um único operando e inverte todos os bits, incluindo o bit de sinal e atribui esse valor ao resultado. Isso significa que, para números positivos assinados, `Not` sempre retorna um valor negativo e, para números negativos, `Not` sempre retorna um valor positivo ou zero.  
  
 O `AndAlso` e os operadores de `OrElse` não dão suporte a operações de bits.  
  
> [!NOTE]
> As operações de bit a bit podem ser executadas somente em tipos integrais. Os valores de ponto flutuante devem ser convertidos em tipos integrais antes que a operação bit-up possa continuar.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
