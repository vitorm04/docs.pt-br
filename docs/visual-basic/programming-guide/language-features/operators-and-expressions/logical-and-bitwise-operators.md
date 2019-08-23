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
ms.openlocfilehash: 40076b2ad6606b4c565bcd39dbeea9e55da47211
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963312"
---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a>Operadores lógicos e bit a bit no Visual Basic
Os operadores lógicos `Boolean` comparam `Boolean` expressões e retornam um resultado. Os `And`operadores `Or` `Not` ,, ,e`OrElse` são binários porque usam dois operandos, enquanto o operador é unário porque usa um único operando. `Xor` `AndAlso` Alguns desses operadores também podem executar operações lógicas de bit a bit em valores integrais.  
  
## <a name="unary-logical-operator"></a>Operador lógico unário  
 O [operador NOT](../../../../visual-basic/language-reference/operators/not-operator.md) executa uma *negação* lógica em `Boolean` uma expressão. Ele gera o oposto lógico de seu operando. Se a expressão for avaliada `True`como `Not` , retornará `False`; `Not` se a expressão for avaliada `False`como, retorna `True`. O exemplo a seguir ilustra essa situação.  
  
 [!code-vb[VbVbalrOperators#77](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#77)]  
  
## <a name="binary-logical-operators"></a>Operadores lógicos binários  
 O [operador and](../../../../visual-basic/language-reference/operators/and-operator.md) executa uma *conjunção* lógica `Boolean` em duas expressões. Se as duas expressões avaliarem `True`como `And` , `True`retornarão. Se pelo menos uma das expressões for avaliada como `False` `And` , retorna `False`.  
  
 O [operador OR](../../../../visual-basic/language-reference/operators/or-operator.md) executa a *disjunção* lógica ou a inclusão `Boolean` em duas expressões. Se qualquer expressão for avaliada `True`como, ou se for `True`avaliada `Or` como `True`, retorna. Se nenhuma expressão for avaliada `True`como `Or` , `False`retorna.  
  
 O [operador XOR](../../../../visual-basic/language-reference/operators/xor-operator.md) executa a *exclusão* lógica em `Boolean` duas expressões. Se exatamente uma expressão for avaliada `True`como, mas não ambos `Xor` , `True`retornará. Se ambas as expressões forem `True` avaliadas como ou `False`ambas forem `False`avaliadas como, `Xor` retorna.  
  
 O exemplo a seguir ilustra `And`os `Or`operadores, `Xor` e.  
  
 [!code-vb[VbVbalrOperators#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#78)]  
  
## <a name="short-circuiting-logical-operations"></a>Operações lógicas de curto-circuito  
 O [Operador AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) é muito semelhante ao operador `And` , pois ele também executa uma conjunção lógica em duas `Boolean` expressões. A principal diferença entre os dois é que `AndAlso` o exibe o comportamento *de curto-circuito* . Se a primeira expressão em uma `AndAlso` expressão for avaliada `False`como, a segunda expressão não será avaliada porque não pode alterar o resultado final e `AndAlso` retorna `False`.  
  
 Da mesma forma, o [Operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) executa uma disjunção lógica de curto- `Boolean` circuito em duas expressões. Se a primeira expressão em uma `OrElse` expressão for avaliada `True`como, a segunda expressão não será avaliada porque não pode alterar o resultado final e `OrElse` retorna `True`.  
  
### <a name="short-circuiting-trade-offs"></a>Compensações de curto-circuito  
 O curto-circuito pode melhorar o desempenho não avaliando uma expressão que não possa alterar o resultado da operação lógica. No entanto, se essa expressão executar ações adicionais, o circuito curto ignorará essas ações. Por exemplo, se a expressão incluir uma chamada para um `Function` procedimento, esse procedimento não será chamado se a expressão tiver um circuito curto e qualquer código adicional contido `Function` no não for executado. Portanto, a função pode ser executada apenas ocasionalmente e pode não ser testada corretamente. Ou a lógica do programa pode depender do código no `Function`.  
  
 O exemplo a seguir ilustra a diferença `And`entre `Or`, e suas contrapartes de curto-circuito.  
  
 [!code-vb[VbVbalrOperators#81](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#81)]  
  
 [!code-vb[VbVbalrOperators#80](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#80)]  
  
 [!code-vb[VbVbalrOperators#79](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#79)]  
  
 No exemplo anterior, observe que algum código importante dentro `checkIfValid()` não é executado quando a chamada é de curto-circuito. A primeira `If` instrução chama `checkIfValid()` , apesar `12 > 45` de `False`Returns, porque `And` não é um circuito curto. A segunda `If` instrução não chama `checkIfValid()`, porque quando `12 > 45` retorna, `False` `AndAlso` a segunda expressão é retornada por circuitos curtos. A terceira `If` instrução chama `checkIfValid()` , embora `12 < 45` retorne `True`, `Or` porque o não é um circuito curto. A quarta `If` instrução não chama `checkIfValid()`, porque, quando `12 < 45` retorna `True`, `OrElse` a segunda expressão é retornada por circuitos curtos.  
  
## <a name="bitwise-operations"></a>Operações bits  
 As operações bit a bit avaliam dois valores integrais no formulário binário (base 2). Eles comparam os bits em posições correspondentes e, em seguida, atribuem valores com base na comparação. O exemplo a seguir ilustra `And` o operador.  
  
 [!code-vb[VbVbalrConcepts#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConcepts/VB/Class1.vb#2)]  
  
 O exemplo anterior define o valor de `x` como 1. Isso ocorre pelos seguintes motivos:  
  
- Os valores são tratados como binários:  
  
     3 em formato binário = 011  
  
     5 em formato binário = 101  
  
- O `And` operador compara as representações binárias, uma posição binária (bit) por vez. Se ambos os bits em uma determinada posição forem 1, um 1 será colocado nessa posição no resultado. Se um dos dois bits for 0, um 0 será colocado nessa posição no resultado. No exemplo anterior, isso funciona da seguinte maneira:  
  
     011 (3 em formato binário)  
  
     101 (5 em formato binário)  
  
     001 (o resultado, em formato binário)  
  
- O resultado é tratado como Decimal. O valor 001 é a representação binária de 1, portanto `x` = 1.  
  
 `Or` Essa operação é semelhante, exceto pelo fato de que um 1 é atribuído ao bit de resultado se um ou ambos os bits comparados forem 1. `Xor`atribui um 1 ao bit de resultado se exatamente um dos bits comparados (não ambos) for 1. `Not`usa um único operando e inverte todos os bits, incluindo o bit de sinal e atribui esse valor ao resultado. Isso significa que, para números positivos assinados, `Not` sempre retorna um valor negativo e para números negativos, `Not` sempre retorna um valor positivo ou zero.  
  
 Os `AndAlso` operadores `OrElse` e não dão suporte a operações bit a bit.  
  
> [!NOTE]
> As operações de bit a bit podem ser executadas somente em tipos integrais. Os valores de ponto flutuante devem ser convertidos em tipos integrais antes que a operação bit-up possa continuar.  
  
## <a name="see-also"></a>Consulte também

- [Operadores lógicos/bits (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Operadores aritméticos no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operadores de comparação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)
