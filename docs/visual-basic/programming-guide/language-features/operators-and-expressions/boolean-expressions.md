---
title: "Expressões Boolianas (Visual Basic) | Documentos do Microsoft"
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
- expressions [Visual Basic], Boolean
- expression evaluation, Boolean expressions
- operators [Visual Basic], short-circuiting
- Visual Basic code, operators
- short-circuit evaluation
- logical operators, short-circuiting
- operators [Visual Basic], Boolean
- Visual Basic code, expressions
ms.assetid: d3d90406-55c8-4404-8143-50fd7f0d0d1a
caps.latest.revision: 19
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
ms.openlocfilehash: 61f0e2910d7c0e157900a2c93cb025245f87881b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="boolean-expressions-visual-basic"></a><span data-ttu-id="2a7cc-102">Expressões boolianas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2a7cc-102">Boolean Expressions (Visual Basic)</span></span>
<span data-ttu-id="2a7cc-103">A *expressão booleana* é uma expressão que é avaliada como um valor de [tipo de dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-103">A *Boolean expression* is an expression that evaluates to a value of the [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md): `True` or `False`.</span></span> <span data-ttu-id="2a7cc-104">`Boolean`expressões podem ter diversos formatos.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-104">`Boolean` expressions can take several forms.</span></span> <span data-ttu-id="2a7cc-105">A mais simples é a comparação direta do valor de uma `Boolean` variável para um `Boolean` literal, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-105">The simplest is the direct comparison of the value of a `Boolean` variable to a `Boolean` literal, as shown in the following example.</span></span>  
  
 <span data-ttu-id="2a7cc-106">[!code-vb[VbVbalrOperators&#87;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a7cc-106">[!code-vb[VbVbalrOperators#87](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_1.vb)]</span></span>  
  
## <a name="two-meanings-of-the--operator"></a><span data-ttu-id="2a7cc-107">Dois significados do operador =</span><span class="sxs-lookup"><span data-stu-id="2a7cc-107">Two Meanings of the = Operator</span></span>  
 <span data-ttu-id="2a7cc-108">Observe que a instrução de atribuição `newCustomer = True` a mesma aparência a expressão no exemplo anterior, mas executa uma função diferente e é usado de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-108">Notice that the assignment statement `newCustomer = True` looks the same as the expression in the preceding example, but it performs a different function and is used differently.</span></span> <span data-ttu-id="2a7cc-109">No exemplo anterior, a expressão `newCustomer = True` representa um valor booleano e o `=` sinal é interpretado como um operador de comparação.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-109">In the preceding example, the expression `newCustomer = True` represents a Boolean value, and the `=` sign is interpreted as a comparison operator.</span></span> <span data-ttu-id="2a7cc-110">Em uma instrução autônoma, o `=` sinal é interpretado como um operador de atribuição e atribui o valor à direita para a variável à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-110">In a stand-alone statement, the `=` sign is interpreted as an assignment operator and assigns the value on the right to the variable on the left.</span></span> <span data-ttu-id="2a7cc-111">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-111">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="2a7cc-112">[!code-vb[88 VbVbalrOperators](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a7cc-112">[!code-vb[VbVbalrOperators#88](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_2.vb)]</span></span>  
  
 <span data-ttu-id="2a7cc-113">Para obter mais informações, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) e [instruções](../../../../visual-basic/language-reference/statements/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a7cc-113">For further information, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) and [Statements](../../../../visual-basic/language-reference/statements/index.md).</span></span>  
  
## <a name="comparison-operators"></a><span data-ttu-id="2a7cc-114">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="2a7cc-114">Comparison Operators</span></span>  
 <span data-ttu-id="2a7cc-115">Operadores de comparação como `=`, `<`, `>`, `<>`, `<=`, e `>=` produzir expressões Boolianas, comparando a expressão no lado esquerdo do operador para a expressão à direita do operador e avaliar o resultado como `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-115">Comparison operators such as `=`, `<`, `>`, `<>`, `<=`, and `>=` produce Boolean expressions by comparing the expression on the left side of the operator to the expression on the right side of the operator and evaluating the result as `True` or `False`.</span></span> <span data-ttu-id="2a7cc-116">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-116">The following example illustrates this.</span></span>  
  
 `42 < 81`  
  
 <span data-ttu-id="2a7cc-117">Como 42 é menor que 81, a expressão booliana no exemplo anterior é avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-117">Because 42 is less than 81, the Boolean expression in the preceding example evaluates to `True`.</span></span> <span data-ttu-id="2a7cc-118">Para obter mais informações sobre esse tipo de expressão, consulte [comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span><span class="sxs-lookup"><span data-stu-id="2a7cc-118">For more information on this kind of expression, see [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md).</span></span>  
  
### <a name="comparison-operators-combined-with-logical-operators"></a><span data-ttu-id="2a7cc-119">Operadores de comparação combinados com operadores lógicos</span><span class="sxs-lookup"><span data-stu-id="2a7cc-119">Comparison Operators Combined with Logical Operators</span></span>  
 <span data-ttu-id="2a7cc-120">Expressões de comparação podem ser combinadas usando operadores lógicos para produzir mais complexas expressões booleanas.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-120">Comparison expressions can be combined using logical operators to produce more complex Boolean expressions.</span></span> <span data-ttu-id="2a7cc-121">O exemplo a seguir demonstra o uso de operadores de comparação em conjunto com um operador lógico.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-121">The following example demonstrates the use of comparison operators in conjunction with a logical operator.</span></span>  
  
 `x > y And x < 1000`  
  
 <span data-ttu-id="2a7cc-122">No exemplo anterior, o valor da expressão geral depende dos valores das expressões de cada lado do `And` operador.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-122">In the preceding example, the value of the overall expression depends on the values of the expressions on each side of the `And` operator.</span></span> <span data-ttu-id="2a7cc-123">Se ambas as expressões forem `True`, em seguida, avalia a expressão geral para `True`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-123">If both expressions are `True`, then the overall expression evaluates to `True`.</span></span> <span data-ttu-id="2a7cc-124">Se qualquer expressão for `False`, em seguida, toda a expressão é avaliada como `False`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-124">If either expression is `False`, then the entire expression evaluates to `False`.</span></span>  
  
## <a name="short-circuiting-operators"></a><span data-ttu-id="2a7cc-125">Operadores de curto-circuito</span><span class="sxs-lookup"><span data-stu-id="2a7cc-125">Short-Circuiting Operators</span></span>  
 <span data-ttu-id="2a7cc-126">Os operadores lógicos `AndAlso` e `OrElse` apresentar comportamento conhecido como *Short-circuiting*.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-126">The logical operators `AndAlso` and `OrElse` exhibit behavior known as *short-circuiting*.</span></span> <span data-ttu-id="2a7cc-127">Um operador Short-circuiting primeiro avalia o operando esquerdo.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-127">A short-circuiting operator evaluates the left operand first.</span></span> <span data-ttu-id="2a7cc-128">Se o operando esquerdo determina o valor de toda a expressão, a execução do programa prossegue sem avaliar a expressão direita.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-128">If the left operand determines the value of the entire expression, then program execution proceeds without evaluating the right expression.</span></span> <span data-ttu-id="2a7cc-129">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-129">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="2a7cc-130">[!code-vb[VbVbalrOperators&#89;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a7cc-130">[!code-vb[VbVbalrOperators#89](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_3.vb)]</span></span>  
  
 <span data-ttu-id="2a7cc-131">No exemplo anterior, o operador avalia a expressão à esquerda, `45 < 12`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-131">In the preceding example, the operator evaluates the left expression, `45 < 12`.</span></span> <span data-ttu-id="2a7cc-132">Porque a expressão esquerda é avaliada como `False`, toda a expressão lógica deve ser avaliada como `False`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-132">Because the left expression evaluates to `False`, the entire logical expression must evaluate to `False`.</span></span> <span data-ttu-id="2a7cc-133">A execução do programa, portanto, ignora a execução do código dentro de `If` bloco sem avaliar a expressão direita, `testFunction(3)`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-133">Program execution thus skips execution of the code within the `If` block without evaluating the right expression, `testFunction(3)`.</span></span> <span data-ttu-id="2a7cc-134">Este exemplo não chama `testFunction()` porque a expressão esquerda falsifica a expressão inteira.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-134">This example does not call `testFunction()` because the left expression falsifies the entire expression.</span></span>  
  
 <span data-ttu-id="2a7cc-135">Da mesma forma, se a expressão esquerda em uma expressão lógica usando `OrElse` é avaliada como `True`, a execução continua para a próxima linha de código sem avaliar a expressão direita, porque a expressão esquerda já validou a expressão inteira.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-135">Similarly, if the left expression in a logical expression using `OrElse` evaluates to `True`, execution proceeds to the next line of code without evaluating the right expression, because the left expression has already validated the entire expression.</span></span>  
  
### <a name="comparison-with-non-short-circuiting-operators"></a><span data-ttu-id="2a7cc-136">Comparação com operadores não curto circuito</span><span class="sxs-lookup"><span data-stu-id="2a7cc-136">Comparison with Non-Short-Circuiting Operators</span></span>  
 <span data-ttu-id="2a7cc-137">Por outro lado, ambos os lados do operador lógico são avaliados quando os operadores lógicos `And` e `Or` são usados.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-137">By contrast, both sides of the logical operator are evaluated when the logical operators `And` and `Or` are used.</span></span> <span data-ttu-id="2a7cc-138">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-138">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="2a7cc-139">[!code-vb[VbVbalrOperators&#90;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="2a7cc-139">[!code-vb[VbVbalrOperators#90](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/boolean-expressions_4.vb)]</span></span>  
  
 <span data-ttu-id="2a7cc-140">O exemplo chama anterior `testFunction()` mesmo que avalia a expressão da esquerda para `False`.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-140">The preceding example calls `testFunction()` even though the left expression evaluates to `False`.</span></span>  
  
## <a name="parenthetical-expressions"></a><span data-ttu-id="2a7cc-141">Expressões entre parênteses</span><span class="sxs-lookup"><span data-stu-id="2a7cc-141">Parenthetical Expressions</span></span>  
 <span data-ttu-id="2a7cc-142">Você pode usar parênteses para controlar a ordem de avaliação de expressões booleanas.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-142">You can use parentheses to control the order of evaluation of Boolean expressions.</span></span> <span data-ttu-id="2a7cc-143">Expressões entre parênteses são avaliadas primeiro.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-143">Expressions enclosed by parentheses evaluate first.</span></span> <span data-ttu-id="2a7cc-144">Vários níveis de aninhamento, precedência é concedida às expressões mais profundamente aninhadas.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-144">For multiple levels of nesting, precedence is granted to the most deeply nested expressions.</span></span> <span data-ttu-id="2a7cc-145">Dentro dos parênteses, avaliação procede de acordo com as regras de precedência de operador.</span><span class="sxs-lookup"><span data-stu-id="2a7cc-145">Within parentheses, evaluation proceeds according to the rules of operator precedence.</span></span> <span data-ttu-id="2a7cc-146">Para obter mais informações, consulte [precedência de operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span><span class="sxs-lookup"><span data-stu-id="2a7cc-146">For more information, see [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a7cc-147">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2a7cc-147">See Also</span></span>  
 <span data-ttu-id="2a7cc-148">[Operadores lógicos e bit a bit no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2a7cc-148">[Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md) </span></span>  
<span data-ttu-id="2a7cc-149"> [Comparações de valor](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="2a7cc-149"> [Value Comparisons](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md) </span></span>  
<span data-ttu-id="2a7cc-150"> [Instruções](../../../../visual-basic/programming-guide/language-features/statements.md) </span><span class="sxs-lookup"><span data-stu-id="2a7cc-150"> [Statements](../../../../visual-basic/programming-guide/language-features/statements.md) </span></span>  
<span data-ttu-id="2a7cc-151"> [Operadores de comparação](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2a7cc-151"> [Comparison Operators](../../../../visual-basic/language-reference/operators/comparison-operators.md) </span></span>  
<span data-ttu-id="2a7cc-152"> [Combinação eficiente de operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md) </span><span class="sxs-lookup"><span data-stu-id="2a7cc-152"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md) </span></span>  
<span data-ttu-id="2a7cc-153"> [Precedência do operador no Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="2a7cc-153"> [Operator Precedence in Visual Basic](../../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="2a7cc-154"> [Tipo de Dados Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="2a7cc-154"> [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)</span></span>
