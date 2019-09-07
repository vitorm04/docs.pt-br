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
ms.openlocfilehash: db81a1c41809b563d5f9d0777c3feb064c5e540b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400707"
---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="04372-102">Instrução If...Then... (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="04372-102">If...Then...Else Statement (Visual Basic)</span></span>

<span data-ttu-id="04372-103">Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="04372-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="04372-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="04372-104">Syntax</span></span>

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

## <a name="quick-links-to-example-code"></a><span data-ttu-id="04372-105">Links rápidos para código de exemplo</span><span class="sxs-lookup"><span data-stu-id="04372-105">Quick links to example code</span></span>

<span data-ttu-id="04372-106">Este artigo inclui vários exemplos que ilustram o `If`uso do... `Then`... `Else` instrução:</span><span class="sxs-lookup"><span data-stu-id="04372-106">This article includes several examples that illustrate uses of the `If`...`Then`...`Else` statement:</span></span>

- [<span data-ttu-id="04372-107">Exemplo de sintaxe multilinha</span><span class="sxs-lookup"><span data-stu-id="04372-107">Multiline syntax example</span></span>](#multi-line)
- [<span data-ttu-id="04372-108">Exemplo de sintaxe aninhada</span><span class="sxs-lookup"><span data-stu-id="04372-108">Nested syntax example</span></span>](#nested)
- [<span data-ttu-id="04372-109">Exemplo de sintaxe de linha única</span><span class="sxs-lookup"><span data-stu-id="04372-109">Single-line syntax example</span></span>](#single-line)

## <a name="parts"></a><span data-ttu-id="04372-110">Partes</span><span class="sxs-lookup"><span data-stu-id="04372-110">Parts</span></span>

`condition` \
<span data-ttu-id="04372-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="04372-111">Required.</span></span> <span data-ttu-id="04372-112">Expressão.</span><span class="sxs-lookup"><span data-stu-id="04372-112">Expression.</span></span> <span data-ttu-id="04372-113">Deve avaliar para `True` ou `False`, ou para um tipo de dados que é implicitamente conversível para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="04372-113">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

<span data-ttu-id="04372-114">Se a expressão for uma variável [anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` que é avaliada [como Nothing](../../../visual-basic/language-reference/nothing.md), a condição será tratada como se `False`fosse, e os `ElseIf` blocos serão avaliados, se existirem, ou `Else` o bloco será executado se existir.</span><span class="sxs-lookup"><span data-stu-id="04372-114">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is `False`, and the `ElseIf` blocks are evaluated if they exist, or the `Else` block is executed if it exists.</span></span>

`Then` \
<span data-ttu-id="04372-115">Necessário na sintaxe de linha única; opcional na sintaxe de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="04372-115">Required in the single-line syntax; optional in the multiline syntax.</span></span>

`statements` \
<span data-ttu-id="04372-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="04372-116">Optional.</span></span> <span data-ttu-id="04372-117">Uma ou mais instruções a `If`seguir... que são executadas se `condition` o for avaliado `True`como. `Then`</span><span class="sxs-lookup"><span data-stu-id="04372-117">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>

`elseifcondition` \
<span data-ttu-id="04372-118">Obrigatório se `ElseIf` estiver presente.</span><span class="sxs-lookup"><span data-stu-id="04372-118">Required if `ElseIf` is present.</span></span> <span data-ttu-id="04372-119">Expressão.</span><span class="sxs-lookup"><span data-stu-id="04372-119">Expression.</span></span> <span data-ttu-id="04372-120">Deve avaliar para `True` ou `False`, ou para um tipo de dados que é implicitamente conversível para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="04372-120">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>

`elseifstatements` \
<span data-ttu-id="04372-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="04372-121">Optional.</span></span> <span data-ttu-id="04372-122">Uma ou mais instruções a `ElseIf`seguir... que são executadas se `elseifcondition` o for avaliado `True`como. `Then`</span><span class="sxs-lookup"><span data-stu-id="04372-122">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>

`elsestatements` \
<span data-ttu-id="04372-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="04372-123">Optional.</span></span> <span data-ttu-id="04372-124">Uma ou mais instruções que são executadas se nenhuma expressão `condition` anterior `elseifcondition` ou for avaliada `True`como.</span><span class="sxs-lookup"><span data-stu-id="04372-124">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>

`End If` \
<span data-ttu-id="04372-125">Finaliza a versão de várias linhas `If`de... `Then`... `Else` bloquear.</span><span class="sxs-lookup"><span data-stu-id="04372-125">Terminates the multiline version of `If`...`Then`...`Else` block.</span></span>

## <a name="remarks"></a><span data-ttu-id="04372-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="04372-126">Remarks</span></span>

### <a name="multiline-syntax"></a><span data-ttu-id="04372-127">Sintaxe de várias linhas</span><span class="sxs-lookup"><span data-stu-id="04372-127">Multiline syntax</span></span>

<span data-ttu-id="04372-128">Quando um `If`... `Then`... foi encontrada uma instrução `condition` , é testada. `Else`</span><span class="sxs-lookup"><span data-stu-id="04372-128">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="04372-129">Se `condition` `Then` for `True`, as instruções a seguir serão executadas.</span><span class="sxs-lookup"><span data-stu-id="04372-129">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="04372-130">Se `condition` for `False`, cada`ElseIf` instrução (se houver) será avaliada na ordem.</span><span class="sxs-lookup"><span data-stu-id="04372-130">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="04372-131">Quando um `True` `elseifcondition` é encontrado, as instruções imediatamente após as associadas `ElseIf` são executadas.</span><span class="sxs-lookup"><span data-stu-id="04372-131">When a `True` `elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="04372-132">Se não `elseifcondition` for avaliada `True`como, `ElseIf` ou se não houver instruções, as instruções a `Else` seguir serão executadas.</span><span class="sxs-lookup"><span data-stu-id="04372-132">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="04372-133">Depois de executar as instruções `Then`a `ElseIf`seguir, `Else`ou, a execução continuará com `End If`a instrução a seguir.</span><span class="sxs-lookup"><span data-stu-id="04372-133">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>

<span data-ttu-id="04372-134">As `ElseIf` cláusulas e `Else` são ambas opcionais.</span><span class="sxs-lookup"><span data-stu-id="04372-134">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="04372-135">Você pode ter quantas `ElseIf` cláusulas desejar em um `If`... `Then`... instrução, mas nenhuma `ElseIf` cláusula pode aparecer após uma `Else` cláusula. `Else`</span><span class="sxs-lookup"><span data-stu-id="04372-135">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="04372-136">`If`... `Then`... `Else` as instruções podem ser aninhadas entre si.</span><span class="sxs-lookup"><span data-stu-id="04372-136">`If`...`Then`...`Else` statements can be nested within each other.</span></span>

<span data-ttu-id="04372-137">Na sintaxe de várias linhas, `If` a instrução deve ser a única instrução na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="04372-137">In the multiline syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="04372-138">As `ElseIf`instruções `Else`, e`End If` podem ser precedidas apenas por um rótulo de linha.</span><span class="sxs-lookup"><span data-stu-id="04372-138">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="04372-139">A `If`... `Then`... o bloco deve terminar com `End If` uma instrução. `Else`</span><span class="sxs-lookup"><span data-stu-id="04372-139">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>

> [!TIP]
> <span data-ttu-id="04372-140">A [seleção... A instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) pode ser mais útil quando você avalia uma única expressão que tem vários valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="04372-140">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>

### <a name="single-line-syntax"></a><span data-ttu-id="04372-141">Sintaxe de linha única</span><span class="sxs-lookup"><span data-stu-id="04372-141">Single-Line syntax</span></span>

<span data-ttu-id="04372-142">Você pode usar a sintaxe de linha única para uma única condição com o código a ser executado se for verdadeiro.</span><span class="sxs-lookup"><span data-stu-id="04372-142">You can use the single-line syntax for a single condition with code to execute if it's true.</span></span> <span data-ttu-id="04372-143">No entanto, a sintaxe de várias linhas fornece mais estrutura e flexibilidade e é mais fácil de ler, manter e depurar.</span><span class="sxs-lookup"><span data-stu-id="04372-143">However, the multiple-line syntax provides more structure and flexibility and is easier to read, maintain, and debug.</span></span>

<span data-ttu-id="04372-144">O que segue `Then` a palavra-chave é examinado para determinar se uma instrução é `If`de linha única.</span><span class="sxs-lookup"><span data-stu-id="04372-144">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="04372-145">Se algo diferente de um comentário aparecer depois `Then` da mesma linha, a instrução será tratada como uma instrução de linha `If` única.</span><span class="sxs-lookup"><span data-stu-id="04372-145">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="04372-146">Se `Then` estiver ausente, deverá ser o início de uma linha `If`múltipla... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="04372-146">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>

<span data-ttu-id="04372-147">Na sintaxe de linha única, você pode ter várias instruções executadas como o resultado de um `If`... `Then` decisão.</span><span class="sxs-lookup"><span data-stu-id="04372-147">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="04372-148">Todas as instruções devem estar na mesma linha e separadas por dois-pontos.</span><span class="sxs-lookup"><span data-stu-id="04372-148">All statements must be on the same line and be separated by colons.</span></span>

## <a name="multiline-syntax-example"></a><span data-ttu-id="04372-149">Exemplo de sintaxe multilinha</span><span class="sxs-lookup"><span data-stu-id="04372-149">Multiline syntax example</span></span>

<a name="multi-line"></a>

<span data-ttu-id="04372-150">O exemplo a seguir ilustra o uso da sintaxe de várias linhas `If`do... `Then`... `Else` instrução.</span><span class="sxs-lookup"><span data-stu-id="04372-150">The following example illustrates the use of the multiline syntax of the `If`...`Then`...`Else` statement.</span></span>

[!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a><span data-ttu-id="04372-151">Exemplo de sintaxe aninhada</span><span class="sxs-lookup"><span data-stu-id="04372-151">Nested syntax example</span></span>

<a name="nested"></a>

<span data-ttu-id="04372-152">O exemplo a seguir contém `If`aninhado... `Then`... `Else` instruções.</span><span class="sxs-lookup"><span data-stu-id="04372-152">The following example contains nested `If`...`Then`...`Else` statements.</span></span>

[!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a><span data-ttu-id="04372-153">Exemplo de sintaxe de linha única</span><span class="sxs-lookup"><span data-stu-id="04372-153">Single-Line syntax example</span></span>

<a name="single-line"></a><span data-ttu-id="04372-154">O exemplo a seguir ilustra o uso da sintaxe de linha única.</span><span class="sxs-lookup"><span data-stu-id="04372-154">The following example illustrates the use of the single-line syntax.</span></span>

[!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]

## <a name="see-also"></a><span data-ttu-id="04372-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="04372-155">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [<span data-ttu-id="04372-156">Diretivas #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="04372-156">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="04372-157">Instrução Select...Case</span><span class="sxs-lookup"><span data-stu-id="04372-157">Select...Case Statement</span></span>](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [<span data-ttu-id="04372-158">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="04372-158">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="04372-159">Estruturas de Decisão</span><span class="sxs-lookup"><span data-stu-id="04372-159">Decision Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="04372-160">Operadores lógicos e de bits bit a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="04372-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [<span data-ttu-id="04372-161">Operador If</span><span class="sxs-lookup"><span data-stu-id="04372-161">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
