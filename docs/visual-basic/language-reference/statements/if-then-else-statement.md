---
title: "If... Then... Instrução Else (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
dev_langs:
- VB
helpviewer_keywords:
- ElseIf statement, If...Then...Else
- Then statement, If...Then...Else
- control flow, branching
- execution, conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement, If...Then...Else
- If statement
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching, conditional
- IIf function, and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
caps.latest.revision: 29
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 1b47777d42b142b266e4b80718386573cc2ed9ad
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="ifthenelse-statement-visual-basic"></a><span data-ttu-id="8474a-102">Instrução If...Then... (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8474a-102">If...Then...Else Statement (Visual Basic)</span></span>
<span data-ttu-id="8474a-103">Execute um grupo de instruções condicionalmente, dependendo do valor de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="8474a-103">Conditionally executes a group of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8474a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8474a-104">Syntax</span></span>  
  
```  
' Multiple-line syntax:  
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
  
## <a name="parts"></a><span data-ttu-id="8474a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8474a-105">Parts</span></span>  
 `condition`  
 <span data-ttu-id="8474a-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8474a-106">Required.</span></span> <span data-ttu-id="8474a-107">Expressão.</span><span class="sxs-lookup"><span data-stu-id="8474a-107">Expression.</span></span> <span data-ttu-id="8474a-108">Deve ser avaliada como `True` ou `False`, ou um tipo de dados que é implicitamente conversível para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8474a-108">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 <span data-ttu-id="8474a-109">Se a expressão for uma [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variável que é avaliada como [nada](../../../visual-basic/language-reference/nothing.md), a condição é tratada como se a expressão não `True`e o `Else` bloco é executado.</span><span class="sxs-lookup"><span data-stu-id="8474a-109">If the expression is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the condition is treated as if the expression is not `True`, and the `Else` block is executed.</span></span>  
  
 `Then`  
 <span data-ttu-id="8474a-110">Obrigatório na sintaxe de linha única; opcional na sintaxe de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="8474a-110">Required in the single-line syntax; optional in the multiple-line syntax.</span></span>  
  
 `statements`  
 <span data-ttu-id="8474a-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8474a-111">Optional.</span></span> <span data-ttu-id="8474a-112">Uma ou mais instruções após `If`... `Then` que são executadas se `condition` é avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="8474a-112">One or more statements following `If`...`Then` that are executed if `condition` evaluates to `True`.</span></span>  
  
 `elseifcondition`  
 <span data-ttu-id="8474a-113">Necessário se `ElseIf` está presente.</span><span class="sxs-lookup"><span data-stu-id="8474a-113">Required if `ElseIf` is present.</span></span> <span data-ttu-id="8474a-114">Expressão.</span><span class="sxs-lookup"><span data-stu-id="8474a-114">Expression.</span></span> <span data-ttu-id="8474a-115">Deve ser avaliada como `True` ou `False`, ou um tipo de dados que é implicitamente conversível para `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8474a-115">Must evaluate to `True` or `False`, or to a data type that is implicitly convertible to `Boolean`.</span></span>  
  
 `elseifstatements`  
 <span data-ttu-id="8474a-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8474a-116">Optional.</span></span> <span data-ttu-id="8474a-117">Uma ou mais instruções após `ElseIf`... `Then` que são executadas se `elseifcondition` é avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="8474a-117">One or more statements following `ElseIf`...`Then` that are executed if `elseifcondition` evaluates to `True`.</span></span>  
  
 `elsestatements`  
 <span data-ttu-id="8474a-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8474a-118">Optional.</span></span> <span data-ttu-id="8474a-119">Uma ou mais instruções que são executadas se anterior não `condition` ou `elseifcondition` expressão é avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="8474a-119">One or more statements that are executed if no previous `condition` or `elseifcondition` expression evaluates to `True`.</span></span>  
  
 `End If`  
 <span data-ttu-id="8474a-120">Encerra o `If`... `Then`... `Else` bloco.</span><span class="sxs-lookup"><span data-stu-id="8474a-120">Terminates the `If`...`Then`...`Else` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8474a-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="8474a-121">Remarks</span></span>  
  
## <a name="multiple-line-syntax"></a><span data-ttu-id="8474a-122">Sintaxe de várias linhas</span><span class="sxs-lookup"><span data-stu-id="8474a-122">Multiple-Line Syntax</span></span>  
 <span data-ttu-id="8474a-123">Quando um `If`... `Then`... `Else` instrução for encontrada, `condition` é testada.</span><span class="sxs-lookup"><span data-stu-id="8474a-123">When an `If`...`Then`...`Else` statement is encountered, `condition` is tested.</span></span> <span data-ttu-id="8474a-124">Se `condition` é `True`, as instruções a seguir `Then` são executados.</span><span class="sxs-lookup"><span data-stu-id="8474a-124">If `condition` is `True`, the statements following `Then` are executed.</span></span> <span data-ttu-id="8474a-125">Se `condition` é `False`, cada `ElseIf` instrução (se houver alguma) é avaliada na ordem.</span><span class="sxs-lookup"><span data-stu-id="8474a-125">If `condition` is `False`, each `ElseIf` statement (if there are any) is evaluated in order.</span></span> <span data-ttu-id="8474a-126">Quando um `True``elseifcondition` for encontrada, as declarações seguindo imediatamente associado `ElseIf` são executados.</span><span class="sxs-lookup"><span data-stu-id="8474a-126">When a `True``elseifcondition` is found, the statements immediately following the associated `ElseIf` are executed.</span></span> <span data-ttu-id="8474a-127">Se nenhum `elseifcondition` é avaliada como `True`, ou se não houver nenhum `ElseIf` instruções, as instruções a seguir `Else` são executados.</span><span class="sxs-lookup"><span data-stu-id="8474a-127">If no `elseifcondition` evaluates to `True`, or if there are no `ElseIf` statements, the statements following `Else` are executed.</span></span> <span data-ttu-id="8474a-128">Depois de executar as seguintes instruções `Then`, `ElseIf`, ou `Else`, a execução continua com o seguinte instrução `End If`.</span><span class="sxs-lookup"><span data-stu-id="8474a-128">After executing the statements following `Then`, `ElseIf`, or `Else`, execution continues with the statement following `End If`.</span></span>  
  
 <span data-ttu-id="8474a-129">O `ElseIf` e `Else` cláusulas são opcionais.</span><span class="sxs-lookup"><span data-stu-id="8474a-129">The `ElseIf` and `Else` clauses are both optional.</span></span> <span data-ttu-id="8474a-130">Você pode ter tantas `ElseIf` cláusulas como você deseja em um `If`... `Then`... `Else` instrução, mas não `ElseIf` cláusula pode aparecer após uma `Else` cláusula.</span><span class="sxs-lookup"><span data-stu-id="8474a-130">You can have as many `ElseIf` clauses as you want in an `If`...`Then`...`Else` statement, but no `ElseIf` clause can appear after an `Else` clause.</span></span> <span data-ttu-id="8474a-131">`If`... `Then`... `Else` instruções podem ser aninhadas dentro do outro.</span><span class="sxs-lookup"><span data-stu-id="8474a-131">`If`...`Then`...`Else` statements can be nested within each other.</span></span>  
  
 <span data-ttu-id="8474a-132">A sintaxe de várias linhas, o `If` instrução deve ser a única declaração na primeira linha.</span><span class="sxs-lookup"><span data-stu-id="8474a-132">In the multiple-line syntax, the `If` statement must be the only statement on the first line.</span></span> <span data-ttu-id="8474a-133">O `ElseIf`, `Else`, e `End If` instruções podem ser precedidas apenas de um rótulo de linha.</span><span class="sxs-lookup"><span data-stu-id="8474a-133">The `ElseIf`, `Else`, and `End If` statements can be preceded only by a line label.</span></span> <span data-ttu-id="8474a-134">The `If`... `Then`... `Else` bloco deve terminar com um `End If` instrução.</span><span class="sxs-lookup"><span data-stu-id="8474a-134">The `If`...`Then`...`Else` block must end with an `End If` statement.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="8474a-135">O [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) pode ser mais útil quando você avalia uma única expressão que possui vários valores possíveis.</span><span class="sxs-lookup"><span data-stu-id="8474a-135">The [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) might be more useful when you evaluate a single expression that has several possible values.</span></span>  
  
## <a name="single-line-syntax"></a><span data-ttu-id="8474a-136">Sintaxe de linha única</span><span class="sxs-lookup"><span data-stu-id="8474a-136">Single-Line Syntax</span></span>  
 <span data-ttu-id="8474a-137">Você pode usar a sintaxe de linha única para testes curtos, simples.</span><span class="sxs-lookup"><span data-stu-id="8474a-137">You can use the single-line syntax for short, simple tests.</span></span> <span data-ttu-id="8474a-138">No entanto, a sintaxe de linhas múltiplas fornece mais estrutura e flexibilidade e é geralmente mais fácil de ler, manter e depurar.</span><span class="sxs-lookup"><span data-stu-id="8474a-138">However, the multiple-line syntax provides more structure and flexibility and is usually easier to read, maintain, and debug.</span></span>  
  
 <span data-ttu-id="8474a-139">O que segue o `Then` palavra-chave é examinada para determinar se uma instrução é uma única linha `If`.</span><span class="sxs-lookup"><span data-stu-id="8474a-139">What follows the `Then` keyword is examined to determine whether a statement is a single-line `If`.</span></span> <span data-ttu-id="8474a-140">Se nada aparece exceto um comentário após `Then` na mesma linha, a declaração é tratada como uma única linha `If` instrução.</span><span class="sxs-lookup"><span data-stu-id="8474a-140">If anything other than a comment appears after `Then` on the same line, the statement is treated as a single-line `If` statement.</span></span> <span data-ttu-id="8474a-141">Se `Then` estiver ausente, ele deve ser o início de uma linha de vários `If`... `Then`... `Else`.</span><span class="sxs-lookup"><span data-stu-id="8474a-141">If `Then` is absent, it must be the start of a multiple-line `If`...`Then`...`Else`.</span></span>  
  
 <span data-ttu-id="8474a-142">A sintaxe de linha única, você pode ter várias declarações executadas como o resultado de uma `If`... `Then` decisão.</span><span class="sxs-lookup"><span data-stu-id="8474a-142">In the single-line syntax, you can have multiple statements executed as the result of an `If`...`Then` decision.</span></span> <span data-ttu-id="8474a-143">Todas as instruções devem estar na mesma linha e ser separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="8474a-143">All statements must be on the same line and be separated by colons.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8474a-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8474a-144">Example</span></span>  
 <span data-ttu-id="8474a-145">O exemplo a seguir ilustra o uso da sintaxe de várias linhas de `If`... `Then`... `Else` instrução.</span><span class="sxs-lookup"><span data-stu-id="8474a-145">The following example illustrates the use of the multiple-line syntax of the `If`...`Then`...`Else` statement.</span></span>  
  
 <span data-ttu-id="8474a-146">[!code-vb[VbVbalrStatements&#101;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8474a-146">[!code-vb[VbVbalrStatements#101](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8474a-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8474a-147">Example</span></span>  
 <span data-ttu-id="8474a-148">O exemplo a seguir contém aninhadas `If`... `Then`... `Else` instruções.</span><span class="sxs-lookup"><span data-stu-id="8474a-148">The following example contains nested `If`...`Then`...`Else` statements.</span></span>  
  
 <span data-ttu-id="8474a-149">[!code-vb[VbVbalrStatements&#102;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8474a-149">[!code-vb[VbVbalrStatements#102](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8474a-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8474a-150">Example</span></span>  
 <span data-ttu-id="8474a-151">O exemplo a seguir ilustra o uso da sintaxe de linha única.</span><span class="sxs-lookup"><span data-stu-id="8474a-151">The following example illustrates the use of the single-line syntax.</span></span>  
  
 <span data-ttu-id="8474a-152">[!code-vb[VbVbalrStatements&#103;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="8474a-152">[!code-vb[VbVbalrStatements#103](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/if-then-else-statement_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8474a-153">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8474a-153">See Also</span></span>  
 <span data-ttu-id="8474a-154"><xref:Microsoft.VisualBasic.Interaction.Choose%2A></xref:Microsoft.VisualBasic.Interaction.Choose%2A></span><span class="sxs-lookup"><span data-stu-id="8474a-154"><xref:Microsoft.VisualBasic.Interaction.Choose%2A></span></span>   
 <span data-ttu-id="8474a-155"><xref:Microsoft.VisualBasic.Interaction.Switch%2A></xref:Microsoft.VisualBasic.Interaction.Switch%2A></span><span class="sxs-lookup"><span data-stu-id="8474a-155"><xref:Microsoft.VisualBasic.Interaction.Switch%2A></span></span>   
<span data-ttu-id="8474a-156"> [#If... Then... #Else diretivas](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span><span class="sxs-lookup"><span data-stu-id="8474a-156"> [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) </span></span>  
<span data-ttu-id="8474a-157"> [Selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8474a-157"> [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) </span></span>  
<span data-ttu-id="8474a-158"> [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="8474a-158"> [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="8474a-159"> [Estruturas de decisão](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span><span class="sxs-lookup"><span data-stu-id="8474a-159"> [Decision Structures](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md) </span></span>  
<span data-ttu-id="8474a-160"> [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="8474a-160"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span></span>  
<span data-ttu-id="8474a-161"> [Operador If](../../../visual-basic/language-reference/operators/if-operator.md)</span><span class="sxs-lookup"><span data-stu-id="8474a-161"> [If Operator](../../../visual-basic/language-reference/operators/if-operator.md)</span></span>
