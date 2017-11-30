---
title: "Instrução Select...Case (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a7527763a05ec32af88c6ba66ef717d839c33154
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="bfebc-102">Instrução Select...Case (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bfebc-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="bfebc-103">Executa um dos vários grupos de instruções, dependendo do valor de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="bfebc-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfebc-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bfebc-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="bfebc-105">Partes</span><span class="sxs-lookup"><span data-stu-id="bfebc-105">Parts</span></span>  
  
|<span data-ttu-id="bfebc-106">Termo</span><span class="sxs-lookup"><span data-stu-id="bfebc-106">Term</span></span>|<span data-ttu-id="bfebc-107">Definição</span><span class="sxs-lookup"><span data-stu-id="bfebc-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="bfebc-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="bfebc-108">Required.</span></span> <span data-ttu-id="bfebc-109">Expressão.</span><span class="sxs-lookup"><span data-stu-id="bfebc-109">Expression.</span></span> <span data-ttu-id="bfebc-110">Deve ser avaliada como um dos tipos de dados elementares (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, e `UShort`).</span><span class="sxs-lookup"><span data-stu-id="bfebc-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="bfebc-111">Necessário em um `Case` instrução.</span><span class="sxs-lookup"><span data-stu-id="bfebc-111">Required in a `Case` statement.</span></span> <span data-ttu-id="bfebc-112">Lista de cláusulas de expressões que representam valores correspondentes para `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="bfebc-113">Várias cláusulas de expressão são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="bfebc-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="bfebc-114">Cada cláusula pode ter uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="bfebc-114">Each clause can take one of the following forms:</span></span><br /><br /> <span data-ttu-id="bfebc-115">-   *Expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="bfebc-115">-   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="bfebc-116">-[ `Is` ] *comparisonoperator* *expressão*</span><span class="sxs-lookup"><span data-stu-id="bfebc-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="bfebc-117">-   *expressão*</span><span class="sxs-lookup"><span data-stu-id="bfebc-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="bfebc-118">Use o `To` valores de palavra-chave para especificar os limites de um intervalo de correspondência para `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="bfebc-119">O valor de `expression1` deve ser menor ou igual ao valor de `expression2`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="bfebc-120">Use o `Is` palavra-chave com um operador de comparação (`=`, `<>`, `<`, `<=`, `>`, ou `>=`) para especificar uma restrição em valores de correspondência `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="bfebc-121">Se o `Is` palavra-chave não for fornecido, ele é automaticamente inserido antes *comparisonoperator*.</span><span class="sxs-lookup"><span data-stu-id="bfebc-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="bfebc-122">O formulário especificando somente `expression` é tratado como um caso especial do `Is` formulário onde *comparisonoperator* é o sinal de igual (`=`).</span><span class="sxs-lookup"><span data-stu-id="bfebc-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="bfebc-123">Este formulário é avaliado como `testexpression`  =  `expression`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="bfebc-124">As expressões em `expressionlist` podem ser de qualquer tipo de dados, contanto que sejam implicitamente conversíveis para o tipo de `testexpression` e apropriada `comparisonoperator` é válida para os dois tipos que ele está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="bfebc-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="bfebc-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bfebc-125">Optional.</span></span> <span data-ttu-id="bfebc-126">Um ou mais instruções após `Case` que executam se `testexpression` coincide com qualquer cláusula na `expressionlist`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="bfebc-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bfebc-127">Optional.</span></span> <span data-ttu-id="bfebc-128">Um ou mais instruções após `Case Else` que executam se `testexpression` não coincide com nenhuma cláusula no `expressionlist` de qualquer um do `Case` instruções.</span><span class="sxs-lookup"><span data-stu-id="bfebc-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="bfebc-129">Finaliza a definição do `Select`... `Case` construção.</span><span class="sxs-lookup"><span data-stu-id="bfebc-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfebc-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfebc-130">Remarks</span></span>  
 <span data-ttu-id="bfebc-131">Se `testexpression` corresponde a qualquer `Case` `expressionlist` cláusula, as instruções a seguir que `Case` instrução executam até o próximo `Case`, `Case Else`, ou `End Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="bfebc-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="bfebc-132">Controle, em seguida, passa para a instrução após `End Select`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="bfebc-133">Se `testexpression` corresponde a um `expressionlist` cláusula em mais de um `Case` cláusula, somente as instruções depois da primeira correspondência são executadas.</span><span class="sxs-lookup"><span data-stu-id="bfebc-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="bfebc-134">O `Case Else` instrução é usada para apresentar o `elsestatements` para executar se nenhuma correspondência for encontrada entre o `testexpression` e um `expressionlist` cláusula em qualquer dos outros `Case` instruções.</span><span class="sxs-lookup"><span data-stu-id="bfebc-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="bfebc-135">Embora não seja necessário, é recomendável ter um `Case Else` instrução em seu `Select Case` construção para tratar imprevistos `testexpression` valores.</span><span class="sxs-lookup"><span data-stu-id="bfebc-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="bfebc-136">Se nenhum `Case` `expressionlist` corresponde a cláusula `testexpression` e não há nenhum `Case Else` instrução, o controle passa para a instrução após `End Select`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="bfebc-137">Você pode usar várias expressões ou intervalos em cada `Case` cláusula.</span><span class="sxs-lookup"><span data-stu-id="bfebc-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="bfebc-138">Por exemplo, a linha a seguir é válida.</span><span class="sxs-lookup"><span data-stu-id="bfebc-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  <span data-ttu-id="bfebc-139">O `Is` palavra-chave usada no `Case` e `Case Else` instruções não é igual a [operador Is](../../../visual-basic/language-reference/operators/is-operator.md), que é usada para comparação de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="bfebc-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="bfebc-140">Você pode especificar várias expressões para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bfebc-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="bfebc-141">No exemplo a seguir, `Case` corresponde a qualquer cadeia de caracteres que é exatamente igual a "maçãs", tem um valor entre "nuts" e "sopa" em ordem alfabética ou contém o mesmo valor que o valor atual de `testItem`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="bfebc-142">A configuração de `Option Compare` pode afetar as comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="bfebc-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="bfebc-143">Em `Option Compare Text`, as cadeias de caracteres "Maçãs" e "maçãs" comparam como iguais, mas em `Option Compare Binary`, eles não são.</span><span class="sxs-lookup"><span data-stu-id="bfebc-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfebc-144">Um `Case` instrução com várias cláusulas pode apresentar comportamento conhecido como *curto-circuito*.</span><span class="sxs-lookup"><span data-stu-id="bfebc-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="bfebc-145">Visual Basic avalia as cláusulas da esquerda para a direita e se uma produz uma correspondência com `testexpression`, as cláusulas restantes não são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="bfebc-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="bfebc-146">Curto-circuito pode melhorar o desempenho, mas ele pode produzir resultados inesperados se você está esperando que cada expressão no `expressionlist` a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="bfebc-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="bfebc-147">Para obter mais informações sobre curto-circuito, consulte [expressões Boolianas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="bfebc-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="bfebc-148">Se o código dentro de um `Case` ou `Case Else` bloco de instrução não precisa mais executar nenhuma das instruções no bloco, ele pode sair do bloco usando o `Exit Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="bfebc-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="bfebc-149">Isso transfere controle imediatamente para a instrução após `End Select`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="bfebc-150">`Select Case`construções podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="bfebc-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="bfebc-151">Cada `Select Case` construção deve ter uma correspondência `End Select` instrução e deve estar totalmente contido dentro de um único `Case` ou `Case Else` bloco de instrução de externa `Select Case` construção dentro da qual ele está aninhado.</span><span class="sxs-lookup"><span data-stu-id="bfebc-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfebc-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfebc-152">Example</span></span>  
 <span data-ttu-id="bfebc-153">O exemplo a seguir usa uma `Select Case` construção para gravar uma linha correspondente ao valor da variável `number`.</span><span class="sxs-lookup"><span data-stu-id="bfebc-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="bfebc-154">A segunda `Case` declaração contém o valor que corresponde ao valor atual da `number`, portanto, a instrução que grava "entre 6 e 8, inclusive" é executada.</span><span class="sxs-lookup"><span data-stu-id="bfebc-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 [!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="bfebc-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfebc-155">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Interaction.Choose%2A>  
 [<span data-ttu-id="bfebc-156">Instrução End</span><span class="sxs-lookup"><span data-stu-id="bfebc-156">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="bfebc-157">Instrução If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="bfebc-157">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="bfebc-158">Instrução Option Compare</span><span class="sxs-lookup"><span data-stu-id="bfebc-158">Option Compare Statement</span></span>](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [<span data-ttu-id="bfebc-159">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="bfebc-159">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
