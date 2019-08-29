---
title: Instrução If...Then... (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: e0b365afaa8cf7dff130cf01d2937be629e5f7a8
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106524"
---
# <a name="ifthenelse-statement-visual-basic"></a>Instrução If...Then... (Visual Basic)

Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.

## <a name="syntax"></a>Sintaxe

```
' Multiline syntax:
If condition [ Then ]
    [ statements ]
[ ElseIf elseifcondition [ Then ]
    [ elseifstatements ] ]
[ Else
    [ elsestatements ] ]
End If

' Single-line syntax:
If condition Then [ statements ] [ Else [ elsestatements ] ]
```

## <a name="quick-links-to-example-code"></a>Links rápidos para código de exemplo

Este artigo inclui vários exemplos que ilustram o `If`uso do... `Then`... `Else` instrução:

- [Exemplo de sintaxe multilinha](#multi-line)
- [Exemplo de sintaxe aninhada](#nested)
- [Exemplo de sintaxe de linha única](#single-line)

## <a name="parts"></a>Partes

`condition` \
Necessário. Expressão. Deve avaliar para `True` ou `False`, ou para um tipo de dados que é implicitamente conversível para `Boolean`.

Se a expressão for uma variável [anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` que é avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md), a condição será tratada como se a expressão `False` for e `Else` o bloco será executado.

`Then` \
Necessário na sintaxe de linha única; opcional na sintaxe de várias linhas.

`statements` \
Opcional. Uma ou mais instruções a `If`seguir... que são executadas se `condition` o for avaliado `True`como. `Then`

`elseifcondition` \
Obrigatório se `ElseIf` estiver presente. Expressão. Deve avaliar para `True` ou `False`, ou para um tipo de dados que é implicitamente conversível para `Boolean`.

`elseifstatements` \
Opcional. Uma ou mais instruções a `ElseIf`seguir... que são executadas se `elseifcondition` o for avaliado `True`como. `Then`

`elsestatements` \
Opcional. Uma ou mais instruções que são executadas se nenhuma expressão `condition` anterior `elseifcondition` ou for avaliada `True`como.

`End If` \
Finaliza a versão de várias linhas `If`de... `Then`... `Else` bloquear.

## <a name="remarks"></a>Comentários

### <a name="multiline-syntax"></a>Sintaxe de várias linhas

Quando um `If`... `Then`... foi encontrada uma instrução `condition` , é testada. `Else` Se `condition` `Then` for `True`, as instruções a seguir serão executadas. Se `condition` for `False`, cada`ElseIf` instrução (se houver) será avaliada na ordem. Quando um `True` `elseifcondition` é encontrado, as instruções imediatamente após as associadas `ElseIf` são executadas. Se não `elseifcondition` for avaliada `True`como, `ElseIf` ou se não houver instruções, as instruções a `Else` seguir serão executadas. Depois de executar as instruções `Then`a `ElseIf`seguir, `Else`ou, a execução continuará com `End If`a instrução a seguir.

As `ElseIf` cláusulas e `Else` são ambas opcionais. Você pode ter quantas `ElseIf` cláusulas desejar em um `If`... `Then`... instrução, mas nenhuma `ElseIf` cláusula pode aparecer após uma `Else` cláusula. `Else` `If`... `Then`... `Else` as instruções podem ser aninhadas entre si.

Na sintaxe de várias linhas, `If` a instrução deve ser a única instrução na primeira linha. As `ElseIf`instruções `Else`, e`End If` podem ser precedidas apenas por um rótulo de linha. A `If`... `Then`... o bloco deve terminar com `End If` uma instrução. `Else`

> [!TIP]
> A [seleção... A instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) pode ser mais útil quando você avalia uma única expressão que tem vários valores possíveis.

### <a name="single-line-syntax"></a>Sintaxe de linha única

Você pode usar a sintaxe de linha única para uma única condição com o código a ser executado se for verdadeiro. No entanto, a sintaxe de várias linhas fornece mais estrutura e flexibilidade e é mais fácil de ler, manter e depurar.

O que segue `Then` a palavra-chave é examinado para determinar se uma instrução é `If`de linha única. Se algo diferente de um comentário aparecer depois `Then` da mesma linha, a instrução será tratada como uma instrução de linha `If` única. Se `Then` estiver ausente, deverá ser o início de uma linha `If`múltipla... `Then`... `Else`.

Na sintaxe de linha única, você pode ter várias instruções executadas como o resultado de um `If`... `Then` decisão. Todas as instruções devem estar na mesma linha e separadas por dois-pontos.

## <a name="multiline-syntax-example"></a>Exemplo de sintaxe multilinha

<a name="multi-line"></a>

O exemplo a seguir ilustra o uso da sintaxe de várias linhas `If`do... `Then`... `Else` instrução.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Exemplo de sintaxe aninhada

<a name="nested"></a>

O exemplo a seguir contém `If`aninhado... `Then`... `Else` instruções.

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>Exemplo de sintaxe de linha única

<a name="single-line"></a>O exemplo a seguir ilustra o uso da sintaxe de linha única.

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [Diretivas #If...Then...#Else](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Instrução Select...Case](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Estruturas de Controle Aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [Estruturas de Decisão](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Operadores lógicos e de bits bit a Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)
