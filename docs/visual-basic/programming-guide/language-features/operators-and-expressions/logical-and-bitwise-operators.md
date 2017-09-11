---
title: "Operadores lógicos e bit a bit no Visual Basic | Documentos do Microsoft"
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
- operators [Visual Basic], logical
- AndAlso operator
- Not operator [Visual Basic], Boolean expressions
- Xor operator [Visual Basic], Boolean expressions
- And operator [Visual Basic], logical operators
- logical operators
- expressions [Visual Basic], Boolean
- Or operator, logical operators
- Visual Basic code, operators
- short-circuiting, logical operators
- logical operators, short-circuiting
- Visual Basic code, expressions
- logical operators, binary
- OrElse operator [Visual Basic]
- logical operators, unary
ms.assetid: ca474e13-567d-4b1d-a18b-301433705e57
caps.latest.revision: 22
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
ms.openlocfilehash: 851a9485e7c8310aba51bf32f4174903ef819466
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="logical-and-bitwise-operators-in-visual-basic"></a><span data-ttu-id="c2e38-102">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2e38-102">Logical and Bitwise Operators in Visual Basic</span></span>
<span data-ttu-id="c2e38-103">Operadores lógicos comparam `Boolean` expressões e retornar um `Boolean` resultado.</span><span class="sxs-lookup"><span data-stu-id="c2e38-103">Logical operators compare `Boolean` expressions and return a `Boolean` result.</span></span> <span data-ttu-id="c2e38-104">O `And`, `Or`, `AndAlso`, `OrElse`, e `Xor` operadores são *binário* porque eles usam dois operandos, enquanto o `Not` operador é *unário* porque ele usa um operando único.</span><span class="sxs-lookup"><span data-stu-id="c2e38-104">The `And`, `Or`, `AndAlso`, `OrElse`, and `Xor` operators are *binary* because they take two operands, while the `Not` operator is *unary* because it takes a single operand.</span></span> <span data-ttu-id="c2e38-105">Alguns desses operadores também podem executar operações de lógicas bit a bit em valores integral.</span><span class="sxs-lookup"><span data-stu-id="c2e38-105">Some of these operators can also perform bitwise logical operations on integral values.</span></span>  
  
## <a name="unary-logical-operator"></a><span data-ttu-id="c2e38-106">Operador lógico unário</span><span class="sxs-lookup"><span data-stu-id="c2e38-106">Unary Logical Operator</span></span>  
 <span data-ttu-id="c2e38-107">O [operador Not](../../../../visual-basic/language-reference/operators/not-operator.md) executa lógica *negação* em um `Boolean` expressão.</span><span class="sxs-lookup"><span data-stu-id="c2e38-107">The [Not Operator](../../../../visual-basic/language-reference/operators/not-operator.md) performs logical *negation* on a `Boolean` expression.</span></span> <span data-ttu-id="c2e38-108">Produz a lógica oposta do operando.</span><span class="sxs-lookup"><span data-stu-id="c2e38-108">It yields the logical opposite of its operand.</span></span> <span data-ttu-id="c2e38-109">Se a expressão for avaliada como `True`, em seguida, `Not` retorna `False`; se a expressão for avaliada como `False`, em seguida, `Not` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-109">If the expression evaluates to `True`, then `Not` returns `False`; if the expression evaluates to `False`, then `Not` returns `True`.</span></span> <span data-ttu-id="c2e38-110">O exemplo a seguir ilustra essa situação.</span><span class="sxs-lookup"><span data-stu-id="c2e38-110">The following example illustrates this.</span></span>  
  
 <span data-ttu-id="c2e38-111">[!code-vb[VbVbalrOperators&#77;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2e38-111">[!code-vb[VbVbalrOperators#77](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_1.vb)]</span></span>  
  
## <a name="binary-logical-operators"></a><span data-ttu-id="c2e38-112">Operadores lógicos binários</span><span class="sxs-lookup"><span data-stu-id="c2e38-112">Binary Logical Operators</span></span>  
 <span data-ttu-id="c2e38-113">O [operador e](../../../../visual-basic/language-reference/operators/and-operator.md) executa lógica *conjunto* em dois `Boolean` expressões.</span><span class="sxs-lookup"><span data-stu-id="c2e38-113">The [And Operator](../../../../visual-basic/language-reference/operators/and-operator.md) performs logical *conjunction* on two `Boolean` expressions.</span></span> <span data-ttu-id="c2e38-114">Se as duas expressões são `True`, em seguida, `And` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-114">If both expressions evaluate to `True`, then `And` returns `True`.</span></span> <span data-ttu-id="c2e38-115">Se pelo menos uma das expressões é avaliada como `False`, em seguida, `And` retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-115">If at least one of the expressions evaluates to `False`, then `And` returns `False`.</span></span>  
  
 <span data-ttu-id="c2e38-116">O [operador ou](../../../../visual-basic/language-reference/operators/or-operator.md) executa lógica *disjunção* ou *inclusão* em dois `Boolean` expressões.</span><span class="sxs-lookup"><span data-stu-id="c2e38-116">The [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) performs logical *disjunction* or *inclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="c2e38-117">Se qualquer expressão for avaliada como `True`, ou ambos são avaliadas como `True`, em seguida, `Or` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-117">If either expression evaluates to `True`, or both evaluate to `True`, then `Or` returns `True`.</span></span> <span data-ttu-id="c2e38-118">Se nenhuma expressão for avaliada como `True`, `Or` retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-118">If neither expression evaluates to `True`, `Or` returns `False`.</span></span>  
  
 <span data-ttu-id="c2e38-119">O [operador Xor](../../../../visual-basic/language-reference/operators/xor-operator.md) executa lógica *exclusão* em dois `Boolean` expressões.</span><span class="sxs-lookup"><span data-stu-id="c2e38-119">The [Xor Operator](../../../../visual-basic/language-reference/operators/xor-operator.md) performs logical *exclusion* on two `Boolean` expressions.</span></span> <span data-ttu-id="c2e38-120">Se exatamente uma expressão for avaliada como `True`, mas não ambos, `Xor` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-120">If exactly one expression evaluates to `True`, but not both, `Xor` returns `True`.</span></span> <span data-ttu-id="c2e38-121">Se as duas expressões são `True` ou ambos são avaliadas como `False`, `Xor` retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-121">If both expressions evaluate to `True` or both evaluate to `False`, `Xor` returns `False`.</span></span>  
  
 <span data-ttu-id="c2e38-122">O exemplo a seguir ilustra o `And`, `Or`, e `Xor` operadores.</span><span class="sxs-lookup"><span data-stu-id="c2e38-122">The following example illustrates the `And`, `Or`, and `Xor` operators.</span></span>  
  
 <span data-ttu-id="c2e38-123">[!code-vb[VbVbalrOperators&#78;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2e38-123">[!code-vb[VbVbalrOperators#78](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_2.vb)]</span></span>  
  
## <a name="short-circuiting-logical-operations"></a><span data-ttu-id="c2e38-124">Operações de lógicas do curto-circuito</span><span class="sxs-lookup"><span data-stu-id="c2e38-124">Short-Circuiting Logical Operations</span></span>  
 <span data-ttu-id="c2e38-125">O [operador AndAlso](../../../../visual-basic/language-reference/operators/andalso-operator.md) é muito semelhante do `And` operador, que também executa conjunção lógica em duas `Boolean` expressões.</span><span class="sxs-lookup"><span data-stu-id="c2e38-125">The [AndAlso Operator](../../../../visual-basic/language-reference/operators/andalso-operator.md) is very similar to the `And` operator, in that it also performs logical conjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="c2e38-126">A principal diferença entre os dois é que `AndAlso` exibe *Short-circuiting* comportamento.</span><span class="sxs-lookup"><span data-stu-id="c2e38-126">The key difference between the two is that `AndAlso` exhibits *short-circuiting* behavior.</span></span> <span data-ttu-id="c2e38-127">Se a primeira expressão em uma `AndAlso` expressão é avaliada como `False`, em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `AndAlso` retorna `False`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-127">If the first expression in an `AndAlso` expression evaluates to `False`, then the second expression is not evaluated because it cannot alter the final result, and `AndAlso` returns `False`.</span></span>  
  
 <span data-ttu-id="c2e38-128">Da mesma forma, o [operador OrElse](../../../../visual-basic/language-reference/operators/orelse-operator.md) executa a disjunção lógica de circuito em duas `Boolean` expressões.</span><span class="sxs-lookup"><span data-stu-id="c2e38-128">Similarly, the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md) performs short-circuiting logical disjunction on two `Boolean` expressions.</span></span> <span data-ttu-id="c2e38-129">Se a primeira expressão em uma `OrElse` expressão é avaliada como `True`, em seguida, a segunda expressão é avaliada não porque ele não é possível alterar o resultado final, e `OrElse` retorna `True`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-129">If the first expression in an `OrElse` expression evaluates to `True`, then the second expression is not evaluated because it cannot alter the final result, and `OrElse` returns `True`.</span></span>  
  
### <a name="short-circuiting-trade-offs"></a><span data-ttu-id="c2e38-130">Vantagens e desvantagens do curto-circuito</span><span class="sxs-lookup"><span data-stu-id="c2e38-130">Short-Circuiting Trade-Offs</span></span>  
 <span data-ttu-id="c2e38-131">Short-circuiting pode melhorar o desempenho por não avaliar uma expressão que não é possível alterar o resultado da operação lógica.</span><span class="sxs-lookup"><span data-stu-id="c2e38-131">Short-circuiting can improve performance by not evaluating an expression that cannot alter the result of the logical operation.</span></span> <span data-ttu-id="c2e38-132">No entanto, se essa expressão executa ações adicionais, Short-circuiting ignora essas ações.</span><span class="sxs-lookup"><span data-stu-id="c2e38-132">However, if that expression performs additional actions, short-circuiting skips those actions.</span></span> <span data-ttu-id="c2e38-133">Por exemplo, se a expressão incluir uma chamada para um `Function` procedimento, o procedimento não é chamado se a expressão for curto-circuitada, e qualquer código adicional contidas a `Function` não é executado.</span><span class="sxs-lookup"><span data-stu-id="c2e38-133">For example, if the expression includes a call to a `Function` procedure, that procedure is not called if the expression is short-circuited, and any additional code contained in the `Function` does not run.</span></span> <span data-ttu-id="c2e38-134">Portanto, a função pode ser executado apenas ocasionalmente e não pode ser testada corretamente.</span><span class="sxs-lookup"><span data-stu-id="c2e38-134">Therefore, the function might run only occasionally, and might not be tested correctly.</span></span> <span data-ttu-id="c2e38-135">Ou a lógica do programa pode depender do código de `Function`.</span><span class="sxs-lookup"><span data-stu-id="c2e38-135">Or the program logic might depend on the code in the `Function`.</span></span>  
  
 <span data-ttu-id="c2e38-136">O exemplo a seguir ilustra a diferença entre `And`, `Or`e suas contrapartes curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="c2e38-136">The following example illustrates the difference between `And`, `Or`, and their short-circuiting counterparts.</span></span>  
  
 <span data-ttu-id="c2e38-137">[!code-vb[VbVbalrOperators&#81;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2e38-137">[!code-vb[VbVbalrOperators#81](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_3.vb)]</span></span>  
  
 <span data-ttu-id="c2e38-138">[!code-vb[VbVbalrOperators&#80;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2e38-138">[!code-vb[VbVbalrOperators#80](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_4.vb)]</span></span>  
  
 <span data-ttu-id="c2e38-139">[!code-vb[VbVbalrOperators&#79;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2e38-139">[!code-vb[VbVbalrOperators#79](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/logical-and-bitwise-operators_5.vb)]</span></span>  
  
 <span data-ttu-id="c2e38-140">No exemplo anterior, observe que alguns códigos importantes dentro de `checkIfValid()` não é executado quando a chamada é curto-circuitada.</span><span class="sxs-lookup"><span data-stu-id="c2e38-140">In the preceding example, note that some important code inside `checkIfValid()` does not run when the call is short-circuited.</span></span> <span data-ttu-id="c2e38-141">A primeira `If` chamadas de instrução `checkIfValid()` , embora `12 > 45` retorna `False`, pois `And` não curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="c2e38-141">The first `If` statement calls `checkIfValid()` even though `12 > 45` returns `False`, because `And` does not short-circuit.</span></span> <span data-ttu-id="c2e38-142">A segunda `If` instrução não chama `checkIfValid()`, porque quando `12 > 45` retorna `False`, `AndAlso` reduz a segunda expressão.</span><span class="sxs-lookup"><span data-stu-id="c2e38-142">The second `If` statement does not call `checkIfValid()`, because when `12 > 45` returns `False`, `AndAlso` short-circuits the second expression.</span></span> <span data-ttu-id="c2e38-143">A terceira `If` chamadas de instrução `checkIfValid()` , embora `12 < 45` retorna `True`, pois `Or` não curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="c2e38-143">The third `If` statement calls `checkIfValid()` even though `12 < 45` returns `True`, because `Or` does not short-circuit.</span></span> <span data-ttu-id="c2e38-144">O quarto `If` instrução não chama `checkIfValid()`, porque quando `12 < 45` retorna `True`, `OrElse` reduz a segunda expressão.</span><span class="sxs-lookup"><span data-stu-id="c2e38-144">The fourth `If` statement does not call `checkIfValid()`, because when `12 < 45` returns `True`, `OrElse` short-circuits the second expression.</span></span>  
  
## <a name="bitwise-operations"></a><span data-ttu-id="c2e38-145">Operações bit a bit</span><span class="sxs-lookup"><span data-stu-id="c2e38-145">Bitwise Operations</span></span>  
 <span data-ttu-id="c2e38-146">Operações bit a bit avaliar dois valores integrais em formato binário (base 2).</span><span class="sxs-lookup"><span data-stu-id="c2e38-146">Bitwise operations evaluate two integral values in binary (base 2) form.</span></span> <span data-ttu-id="c2e38-147">Eles comparam os bits em posições correspondentes e, em seguida, atribuir valores com base na comparação.</span><span class="sxs-lookup"><span data-stu-id="c2e38-147">They compare the bits at corresponding positions and then assign values based on the comparison.</span></span> <span data-ttu-id="c2e38-148">O exemplo a seguir ilustra o `And` operador.</span><span class="sxs-lookup"><span data-stu-id="c2e38-148">The following example illustrates the `And` operator.</span></span>  
  
 <span data-ttu-id="c2e38-149">[!code-vb[VbVbalrConcepts n º&2;](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="c2e38-149">[!code-vb[VbVbalrConcepts#2](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/codesnippet/VisualBasic/logical-and-bitwise-operators_6.vb)]</span></span>  
  
 <span data-ttu-id="c2e38-150">O exemplo anterior define o valor de `x` como 1.</span><span class="sxs-lookup"><span data-stu-id="c2e38-150">The preceding example sets the value of `x` to 1.</span></span> <span data-ttu-id="c2e38-151">Isso acontece pelas seguintes razões:</span><span class="sxs-lookup"><span data-stu-id="c2e38-151">This happens for the following reasons:</span></span>  
  
-   <span data-ttu-id="c2e38-152">Os valores são tratados como binários:</span><span class="sxs-lookup"><span data-stu-id="c2e38-152">The values are treated as binary:</span></span>  
  
     <span data-ttu-id="c2e38-153">3 no formato binário = 011</span><span class="sxs-lookup"><span data-stu-id="c2e38-153">3 in binary form = 011</span></span>  
  
     <span data-ttu-id="c2e38-154">5 na forma binária = 101</span><span class="sxs-lookup"><span data-stu-id="c2e38-154">5 in binary form = 101</span></span>  
  
-   <span data-ttu-id="c2e38-155">O `And` operador compara as representações binárias, uma posição de binária (bits) por vez.</span><span class="sxs-lookup"><span data-stu-id="c2e38-155">The `And` operator compares the binary representations, one binary position (bit) at a time.</span></span> <span data-ttu-id="c2e38-156">Se os dois bits na posição especificada forem 1, 1 é colocado na posição no resultado.</span><span class="sxs-lookup"><span data-stu-id="c2e38-156">If both bits at a given position are 1, then a 1 is placed in that position in the result.</span></span> <span data-ttu-id="c2e38-157">Se um bit for 0, 0 é colocado na posição no resultado.</span><span class="sxs-lookup"><span data-stu-id="c2e38-157">If either bit is 0, then a 0 is placed in that position in the result.</span></span> <span data-ttu-id="c2e38-158">No exemplo anterior isso funciona da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c2e38-158">In the preceding example this works out as follows:</span></span>  
  
     <span data-ttu-id="c2e38-159">011 (3 em formato binário)</span><span class="sxs-lookup"><span data-stu-id="c2e38-159">011 (3 in binary form)</span></span>  
  
     <span data-ttu-id="c2e38-160">101 (5 em formato binário)</span><span class="sxs-lookup"><span data-stu-id="c2e38-160">101 (5 in binary form)</span></span>  
  
     <span data-ttu-id="c2e38-161">001 (o resultado, no formato binário)</span><span class="sxs-lookup"><span data-stu-id="c2e38-161">001 (The result, in binary form)</span></span>  
  
-   <span data-ttu-id="c2e38-162">O resultado é tratado como decimal.</span><span class="sxs-lookup"><span data-stu-id="c2e38-162">The result is treated as decimal.</span></span> <span data-ttu-id="c2e38-163">O valor 001 é a representação binária de 1, então `x` = 1.</span><span class="sxs-lookup"><span data-stu-id="c2e38-163">The value 001 is the binary representation of 1, so `x` = 1.</span></span>  
  
 <span data-ttu-id="c2e38-164">Bit a bit `Or` operação é semelhante, exceto que um 1 é atribuído para o bit de resultado se um ou ambos os bits comparados é 1.</span><span class="sxs-lookup"><span data-stu-id="c2e38-164">The bitwise `Or` operation is similar, except that a 1 is assigned to the result bit if either or both of the compared bits is 1.</span></span> <span data-ttu-id="c2e38-165">`Xor`atribui um 1 para o bit de resultado se exatamente um dos bits comparados (não ambos) é 1.</span><span class="sxs-lookup"><span data-stu-id="c2e38-165">`Xor` assigns a 1 to the result bit if exactly one of the compared bits (not both) is 1.</span></span> <span data-ttu-id="c2e38-166">`Not`leva um operando único e inverte todos os bits, incluindo o bit de sinal e atribui o valor para o resultado.</span><span class="sxs-lookup"><span data-stu-id="c2e38-166">`Not` takes a single operand and inverts all the bits, including the sign bit, and assigns that value to the result.</span></span> <span data-ttu-id="c2e38-167">Isso significa que para assinado números positivos, `Not` sempre retorna um valor negativo e para números negativos, `Not` sempre retorna um positivo ou valor zero.</span><span class="sxs-lookup"><span data-stu-id="c2e38-167">This means that for signed positive numbers, `Not` always returns a negative value, and for negative numbers, `Not` always returns a positive or zero value.</span></span>  
  
 <span data-ttu-id="c2e38-168">O `AndAlso` e `OrElse` operadores não oferecem suporte a operações bit a bit.</span><span class="sxs-lookup"><span data-stu-id="c2e38-168">The `AndAlso` and `OrElse` operators do not support bitwise operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2e38-169">Operações bit a bit podem ser executadas em apenas tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="c2e38-169">Bitwise operations can be performed on integral types only.</span></span> <span data-ttu-id="c2e38-170">Valores de ponto flutuante devem ser convertidos em tipos integrais antes de prosseguir com a operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="c2e38-170">Floating-point values must be converted to integral types before bitwise operation can proceed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2e38-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2e38-171">See Also</span></span>  
 <span data-ttu-id="c2e38-172">[Operadores lógicos/bit a bit (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="c2e38-172">[Logical/Bitwise Operators (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="c2e38-173"> [Expressões Boolianas](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="c2e38-173"> [Boolean Expressions](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md) </span></span>  
<span data-ttu-id="c2e38-174"> [Operadores aritméticos em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="c2e38-174"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="c2e38-175"> [Operadores de comparação em Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="c2e38-175"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="c2e38-176"> [Operadores de concatenação no Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span><span class="sxs-lookup"><span data-stu-id="c2e38-176"> [Concatenation Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md) </span></span>  
<span data-ttu-id="c2e38-177"> [Combinação Eficiente de Operadores](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span><span class="sxs-lookup"><span data-stu-id="c2e38-177"> [Efficient Combination of Operators](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/efficient-combination-of-operators.md)</span></span>
