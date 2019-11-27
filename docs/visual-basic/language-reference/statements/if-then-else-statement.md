---
title: Instrução If...Then...Else
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
ms.openlocfilehash: f505755caeb9cc3cfeeb1ba83b6de15f48314103
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351156"
---
# <a name="ifthenelse-statement-visual-basic"></a>Instrução If...Then... (Visual Basic)

Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.

## <a name="syntax"></a>Sintaxe

```vb
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

Este artigo inclui vários exemplos que ilustram usos da instrução `If`...`Then`...`Else`:

- [Exemplo de sintaxe multilinha](#multi-line)
- [Exemplo de sintaxe aninhada](#nested)
- [Exemplo de sintaxe de linha única](#single-line)

## <a name="parts"></a>Partes

`condition` \
Necessária. Expressão. Deve avaliar para `True` ou `False`ou para um tipo de dados que é implicitamente conversível para `Boolean`.

Se a expressão for uma variável `Boolean` [anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) que é avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md), a condição será tratada como se a expressão for `False`, e os blocos de `ElseIf` serão avaliados, se existirem, ou o bloco de `Else` será executado se existir.

`Then` \
Necessário na sintaxe de linha única; opcional na sintaxe de várias linhas.

`statements` \
Opcional. Uma ou mais instruções após `If`...`Then` que são executadas se `condition` for avaliada como `True`.

`elseifcondition` \
Necessário se `ElseIf` estiver presente. Expressão. Deve avaliar para `True` ou `False`ou para um tipo de dados que é implicitamente conversível para `Boolean`.

`elseifstatements` \
Opcional. Uma ou mais instruções após `ElseIf`...`Then` que são executadas se `elseifcondition` for avaliada como `True`.

`elsestatements` \
Opcional. Uma ou mais instruções que são executadas se nenhuma expressão `condition` ou `elseifcondition` anterior for avaliada como `True`.

`End If` \
Encerra a versão de várias linhas do `If`...`Then`...`Else` bloco.

## <a name="remarks"></a>Comentários

### <a name="multiline-syntax"></a>Sintaxe de várias linhas

Quando uma instrução `If`...`Then`...`Else` for encontrada, `condition` será testado. Se `condition` for `True`, as instruções a seguir `Then` serão executadas. Se `condition` for `False`, cada instrução `ElseIf` (se houver) será avaliada na ordem. Quando um `True` `elseifcondition` é encontrado, as instruções imediatamente após as `ElseIf` associadas são executadas. Se nenhum `elseifcondition` for avaliado como `True`ou se não houver instruções `ElseIf`, as instruções a seguir `Else` serão executadas. Depois de executar as instruções seguindo `Then`, `ElseIf`ou `Else`, a execução continua com a instrução a seguir `End If`.

As cláusulas `ElseIf` e `Else` são opcionais. Você pode ter tantas `ElseIf` cláusulas quanto desejar em uma instrução `If`...`Then`...`Else`, mas nenhuma cláusula `ElseIf` pode aparecer após uma cláusula `Else`. as instruções `If`...`Then`...`Else` podem ser aninhadas entre si.

Na sintaxe de várias linhas, a instrução de `If` deve ser a única instrução na primeira linha. As instruções `ElseIf`, `Else`e `End If` podem ser precedidas apenas por um rótulo de linha. O bloco `If`...`Then`...`Else` deve terminar com uma instrução `End If`.

> [!TIP]
> A [seleção... A instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) pode ser mais útil quando você avalia uma única expressão que tem vários valores possíveis.

### <a name="single-line-syntax"></a>Sintaxe de linha única

Você pode usar a sintaxe de linha única para uma única condição com o código a ser executado se for verdadeiro. No entanto, a sintaxe de várias linhas fornece mais estrutura e flexibilidade e é mais fácil de ler, manter e depurar.

O que segue a palavra-chave `Then` é examinado para determinar se uma instrução é uma `If`de linha única. Se algo diferente de um comentário for exibido após `Then` na mesma linha, a instrução será tratada como uma instrução de `If` de linha única. Se `Then` estiver ausente, ele deverá ser o início de uma `If`de várias linhas...`Then`...`Else`.

Na sintaxe de linha única, você pode ter várias instruções executadas como resultado de uma decisão de `If`...`Then`. Todas as instruções devem estar na mesma linha e separadas por dois-pontos.

## <a name="multiline-syntax-example"></a>Exemplo de sintaxe multilinha

<a name="multi-line"></a>

O exemplo a seguir ilustra o uso da sintaxe de várias linhas da instrução `If`...`Then`...`Else`.

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>Exemplo de sintaxe aninhada

<a name="nested"></a>

O exemplo a seguir contém instruções aninhadas `If`...`Then`...`Else`.

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
