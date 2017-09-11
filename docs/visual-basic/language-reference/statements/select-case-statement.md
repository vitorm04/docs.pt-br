---
title: Selecione... Case Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Select
- vb.Case
dev_langs:
- VB
helpviewer_keywords:
- Select statement
- Case statement
- Select...Case statements
- conditional statements, Select Case
- control flow, branching
- Else keyword [Visual Basic], in Select...Case statements
- execution, conditional
- To keyword, in Select...Case statements
- Select Case statement, Select...Case
- Select statement, Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching, conditional
- Case Else statement, Select...Case
- End keyword, Select Case statements
- Case statement, Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
caps.latest.revision: 15
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
ms.openlocfilehash: 4759e7db2a72c7acc3a4a5fa6922db4295f450d4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="selectcase-statement-visual-basic"></a><span data-ttu-id="3fc16-102">Instrução Select...Case (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3fc16-102">Select...Case Statement (Visual Basic)</span></span>
<span data-ttu-id="3fc16-103">Executa um dos vários grupos de instruções, dependendo do valor de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="3fc16-103">Runs one of several groups of statements, depending on the value of an expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fc16-104">Syntax</span></span>  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a><span data-ttu-id="3fc16-105">Partes</span><span class="sxs-lookup"><span data-stu-id="3fc16-105">Parts</span></span>  
  
|<span data-ttu-id="3fc16-106">Termo</span><span class="sxs-lookup"><span data-stu-id="3fc16-106">Term</span></span>|<span data-ttu-id="3fc16-107">Definição</span><span class="sxs-lookup"><span data-stu-id="3fc16-107">Definition</span></span>|  
|---|---|  
|`testexpression`|<span data-ttu-id="3fc16-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="3fc16-108">Required.</span></span> <span data-ttu-id="3fc16-109">Expressão.</span><span class="sxs-lookup"><span data-stu-id="3fc16-109">Expression.</span></span> <span data-ttu-id="3fc16-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span><span class="sxs-lookup"><span data-stu-id="3fc16-110">Must evaluate to one of the elementary data types (`Boolean`, `Byte`, `Char`, `Date`, `Double`, `Decimal`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, and `UShort`).</span></span>|  
|`expressionlist`|<span data-ttu-id="3fc16-111">Necessário em um `Case` instrução.</span><span class="sxs-lookup"><span data-stu-id="3fc16-111">Required in a `Case` statement.</span></span> <span data-ttu-id="3fc16-112">Lista de cláusulas de expressões que representam valores correspondentes para `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-112">List of expression clauses representing match values for `testexpression`.</span></span> <span data-ttu-id="3fc16-113">Várias cláusulas expressão são separadas por vírgulas.</span><span class="sxs-lookup"><span data-stu-id="3fc16-113">Multiple expression clauses are separated by commas.</span></span> <span data-ttu-id="3fc16-114">Cada cláusula pode ter uma das seguintes formas:</span><span class="sxs-lookup"><span data-stu-id="3fc16-114">Each clause can take one of the following forms:</span></span><br /><br /><span data-ttu-id="3fc16-115"> -   *Expression1* `To` *expression2*</span><span class="sxs-lookup"><span data-stu-id="3fc16-115"> -   *expression1* `To` *expression2*</span></span><br /><span data-ttu-id="3fc16-116">-[ `Is` ] *comparisonoperator* *expressão*</span><span class="sxs-lookup"><span data-stu-id="3fc16-116">-   [ `Is` ] *comparisonoperator* *expression*</span></span><br /><span data-ttu-id="3fc16-117">-   *expressão*</span><span class="sxs-lookup"><span data-stu-id="3fc16-117">-   *expression*</span></span><br /><br /> <span data-ttu-id="3fc16-118">Use o `To` valores de palavra-chave para especificar os limites de um intervalo de correspondência para `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-118">Use the `To` keyword to specify the boundaries of a range of match values for `testexpression`.</span></span> <span data-ttu-id="3fc16-119">O valor de `expression1` deve ser menor ou igual ao valor de `expression2`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-119">The value of `expression1` must be less than or equal to the value of `expression2`.</span></span><br /><br /> <span data-ttu-id="3fc16-120">Use o `Is` palavra-chave com um operador de comparação (`=`, `<>`, `<`, `<=`, `>`, ou `>=`) para especificar uma restrição em valores de correspondência `testexpression`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-120">Use the `Is` keyword with a comparison operator (`=`, `<>`, `<`, `<=`, `>`, or `>=`) to specify a restriction on the match values for `testexpression`.</span></span> <span data-ttu-id="3fc16-121">Se o `Is` palavra-chave não for fornecido, ele é automaticamente inserido antes *comparisonoperator*.</span><span class="sxs-lookup"><span data-stu-id="3fc16-121">If the `Is` keyword is not supplied, it is automatically inserted before *comparisonoperator*.</span></span><br /><br /> <span data-ttu-id="3fc16-122">O formulário especificando somente `expression` é tratado como um caso especial do `Is` formulário onde *comparisonoperator* é o sinal de igual (`=`).</span><span class="sxs-lookup"><span data-stu-id="3fc16-122">The form specifying only `expression` is treated as a special case of the `Is` form where *comparisonoperator* is the equal sign (`=`).</span></span> <span data-ttu-id="3fc16-123">Este formulário é avaliado como `testexpression`  =  `expression`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-123">This form is evaluated as `testexpression` = `expression`.</span></span><br /><br /> <span data-ttu-id="3fc16-124">As expressões em `expressionlist` podem ser de qualquer tipo de dados, contanto que sejam implicitamente conversíveis para o tipo de `testexpression` e apropriado `comparisonoperator` é válido para os dois tipos que ele está sendo usado.</span><span class="sxs-lookup"><span data-stu-id="3fc16-124">The expressions in `expressionlist` can be of any data type, provided they are implicitly convertible to the type of `testexpression` and the appropriate `comparisonoperator` is valid for the two types it is being used with.</span></span>|  
|`statements`|<span data-ttu-id="3fc16-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3fc16-125">Optional.</span></span> <span data-ttu-id="3fc16-126">Uma ou mais instruções após `Case` que executam se `testexpression` coincide com qualquer cláusula na `expressionlist`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-126">One or more statements following `Case` that run if `testexpression` matches any clause in `expressionlist`.</span></span>|  
|`elsestatements`|<span data-ttu-id="3fc16-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="3fc16-127">Optional.</span></span> <span data-ttu-id="3fc16-128">Uma ou mais instruções após `Case Else` que executam se `testexpression` não coincide com nenhuma cláusula no `expressionlist` de qualquer o `Case` instruções.</span><span class="sxs-lookup"><span data-stu-id="3fc16-128">One or more statements following `Case Else` that run if `testexpression` does not match any clause in the `expressionlist` of any of the `Case` statements.</span></span>|  
|`End Select`|<span data-ttu-id="3fc16-129">Finaliza a definição de `Select`... `Case` construção.</span><span class="sxs-lookup"><span data-stu-id="3fc16-129">Terminates the definition of the `Select`...`Case` construction.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fc16-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="3fc16-130">Remarks</span></span>  
 <span data-ttu-id="3fc16-131">Se `testexpression` corresponde a qualquer `Case` `expressionlist` cláusula, as instruções a seguir que `Case` instrução executam até o próximo `Case`, `Case Else`, ou `End Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="3fc16-131">If `testexpression` matches any `Case` `expressionlist` clause, the statements following that `Case` statement run up to the next `Case`, `Case Else`, or `End Select` statement.</span></span> <span data-ttu-id="3fc16-132">Controle passa para a instrução depois `End Select`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-132">Control then passes to the statement following `End Select`.</span></span> <span data-ttu-id="3fc16-133">Se `testexpression` corresponde a um `expressionlist` cláusula em mais de um `Case` cláusula, somente as instruções depois da primeira correspondência são executadas.</span><span class="sxs-lookup"><span data-stu-id="3fc16-133">If `testexpression` matches an `expressionlist` clause in more than one `Case` clause, only the statements following the first match run.</span></span>  
  
 <span data-ttu-id="3fc16-134">O `Case Else` instrução é usada para introduzir o `elsestatements` para executar se nenhuma correspondência for encontrada entre o `testexpression` e uma `expressionlist` cláusula em qualquer dos outros `Case` instruções.</span><span class="sxs-lookup"><span data-stu-id="3fc16-134">The `Case Else` statement is used to introduce the `elsestatements` to run if no match is found between the `testexpression` and an `expressionlist` clause in any of the other `Case` statements.</span></span> <span data-ttu-id="3fc16-135">Embora não seja necessário, é uma boa ideia ter um `Case Else` instrução em seu `Select Case` construção para manipular imprevisto `testexpression` valores.</span><span class="sxs-lookup"><span data-stu-id="3fc16-135">Although not required, it is a good idea to have a `Case Else` statement in your `Select Case` construction to handle unforeseen `testexpression` values.</span></span> <span data-ttu-id="3fc16-136">Se nenhum `Case` `expressionlist` corresponde a cláusula `testexpression` e não há nenhum `Case Else` instrução, o controle passa para a instrução depois `End Select`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-136">If no `Case` `expressionlist` clause matches `testexpression` and there is no `Case Else` statement, control passes to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="3fc16-137">Você pode usar várias expressões ou intervalos em cada `Case` cláusula.</span><span class="sxs-lookup"><span data-stu-id="3fc16-137">You can use multiple expressions or ranges in each `Case` clause.</span></span> <span data-ttu-id="3fc16-138">Por exemplo, a linha a seguir é válida.</span><span class="sxs-lookup"><span data-stu-id="3fc16-138">For example, the following line is valid.</span></span>  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  <span data-ttu-id="3fc16-139">O `Is` palavra-chave usada no `Case` e `Case Else` instruções não é igual a [operador Is](../../../visual-basic/language-reference/operators/is-operator.md), que é usado para comparação de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="3fc16-139">The `Is` keyword used in the `Case` and `Case Else` statements is not the same as the [Is Operator](../../../visual-basic/language-reference/operators/is-operator.md), which is used for object reference comparison.</span></span>  
  
 <span data-ttu-id="3fc16-140">Você pode especificar intervalos e várias expressões para cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fc16-140">You can specify ranges and multiple expressions for character strings.</span></span> <span data-ttu-id="3fc16-141">No exemplo a seguir, `Case` corresponde a qualquer cadeia de caracteres que é exatamente igual a "apples", tem um valor entre "nuts" e "sopa" em ordem alfabética ou contém o mesmo valor que o valor atual de `testItem`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-141">In the following example, `Case` matches any string that is exactly equal to "apples", has a value between "nuts" and "soup" in alphabetical order, or contains the exact same value as the current value of `testItem`.</span></span>  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 <span data-ttu-id="3fc16-142">A configuração de `Option Compare` pode afetar as comparações de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="3fc16-142">The setting of `Option Compare` can affect string comparisons.</span></span> <span data-ttu-id="3fc16-143">Em `Option Compare Text`, as cadeias de caracteres "Maçãs" e "maçãs" comparam como iguais, mas em `Option Compare Binary`, não.</span><span class="sxs-lookup"><span data-stu-id="3fc16-143">Under `Option Compare Text`, the strings "Apples" and "apples" compare as equal, but under `Option Compare Binary`, they do not.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3fc16-144">A `Case` instrução com várias cláusulas pode apresentar comportamento conhecido como *Short-circuiting*.</span><span class="sxs-lookup"><span data-stu-id="3fc16-144">A `Case` statement with multiple clauses can exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="3fc16-145">Visual Basic avalia as cláusulas da esquerda para a direita e se uma produz uma correspondência com `testexpression`, as cláusulas restantes não são avaliadas.</span><span class="sxs-lookup"><span data-stu-id="3fc16-145">Visual Basic evaluates the clauses from left to right, and if one produces a match with `testexpression`, the remaining clauses are not evaluated.</span></span> <span data-ttu-id="3fc16-146">Short-circuiting pode melhorar o desempenho, mas ele pode produzir resultados inesperados se você estiver esperando que cada expressão no `expressionlist` a ser avaliada.</span><span class="sxs-lookup"><span data-stu-id="3fc16-146">Short-circuiting can improve performance, but it can produce unexpected results if you are expecting every expression in `expressionlist` to be evaluated.</span></span> <span data-ttu-id="3fc16-147">Para obter mais informações sobre Short-circuiting, consulte [expressões booleanas](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="3fc16-147">For more information on short-circuiting, see [Boolean Expressions](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md).</span></span>  
  
 <span data-ttu-id="3fc16-148">Se o código dentro de um `Case` ou `Case Else` bloco de instrução não precisa mais executar nenhuma das instruções no bloco, ele pode sair do bloco usando a `Exit Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="3fc16-148">If the code within a `Case` or `Case Else` statement block does not need to run any more of the statements in the block, it can exit the block by using the `Exit Select` statement.</span></span> <span data-ttu-id="3fc16-149">Isso transfere o controle imediatamente para a instrução depois `End Select`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-149">This transfers control immediately to the statement following `End Select`.</span></span>  
  
 <span data-ttu-id="3fc16-150">`Select Case`construções podem ser aninhadas.</span><span class="sxs-lookup"><span data-stu-id="3fc16-150">`Select Case` constructions can be nested.</span></span> <span data-ttu-id="3fc16-151">Cada `Select Case` construção deve ter uma correspondência `End Select` instrução e deve estar completamente contida em um único `Case` ou `Case Else` bloco de instrução de externo `Select Case` construção dentro da qual está aninhada.</span><span class="sxs-lookup"><span data-stu-id="3fc16-151">Each nested `Select Case` construction must have a matching `End Select` statement and must be completely contained within a single `Case` or `Case Else` statement block of the outer `Select Case` construction within which it is nested.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3fc16-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3fc16-152">Example</span></span>  
 <span data-ttu-id="3fc16-153">O exemplo a seguir usa uma `Select Case` construção para gravar uma linha correspondente ao valor da variável `number`.</span><span class="sxs-lookup"><span data-stu-id="3fc16-153">The following example uses a `Select Case` construction to write a line corresponding to the value of the variable `number`.</span></span> <span data-ttu-id="3fc16-154">A segunda `Case` declaração contém o valor que corresponde ao valor atual de `number`, portanto, a instrução que grava "entre 6 e 8, inclusive" é executada.</span><span class="sxs-lookup"><span data-stu-id="3fc16-154">The second `Case` statement contains the value that matches the current value of `number`, so the statement that writes "Between 6 and 8, inclusive" runs.</span></span>  
  
 <span data-ttu-id="3fc16-155">[!code-vb[VbVbalrStatements&#54;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="3fc16-155">[!code-vb[VbVbalrStatements#54](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/select-case-statement_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc16-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fc16-156">See Also</span></span>  
 <span data-ttu-id="3fc16-157"><xref:Microsoft.VisualBasic.Interaction.Choose%2A></xref:Microsoft.VisualBasic.Interaction.Choose%2A></span><span class="sxs-lookup"><span data-stu-id="3fc16-157"><xref:Microsoft.VisualBasic.Interaction.Choose%2A></span></span>   
<span data-ttu-id="3fc16-158"> [Instrução End](../../../visual-basic/language-reference/statements/end-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3fc16-158"> [End Statement](../../../visual-basic/language-reference/statements/end-statement.md) </span></span>  
<span data-ttu-id="3fc16-159"> [If... Then... Instrução else](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3fc16-159"> [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md) </span></span>  
<span data-ttu-id="3fc16-160"> [Instrução Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span><span class="sxs-lookup"><span data-stu-id="3fc16-160"> [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md) </span></span>  
<span data-ttu-id="3fc16-161"> [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md)</span><span class="sxs-lookup"><span data-stu-id="3fc16-161"> [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)</span></span>
