---
title: Operador Xor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Xor
helpviewer_keywords:
- exclusive OR operator [Visual Basic]
- logical exclusion
- operators [Visual Basic], exclusive or
- exclusion operator [Visual Basic]
- operators [Visual Basic], bitwise
- bitwise operators [Visual Basic], XOR operator
- Xor operator [Visual Basic]
- Xor keyword [Visual Basic]
- bitwise comparison [Visual Basic]
ms.assetid: 036000a9-3934-4e7f-a9d0-a816de3d84a6
ms.openlocfilehash: 34d317da5d85127e371c2df7229e0f0873972f50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604790"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="60b85-102">Operador Xor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60b85-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="60b85-103">Executa uma exclusão lógica em duas `Boolean` expressões ou uma exclusão bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="60b85-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60b85-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="60b85-104">Syntax</span></span>  
  
```  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="60b85-105">Partes</span><span class="sxs-lookup"><span data-stu-id="60b85-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="60b85-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="60b85-106">Required.</span></span> <span data-ttu-id="60b85-107">Qualquer `Boolean` ou variável numérica.</span><span class="sxs-lookup"><span data-stu-id="60b85-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="60b85-108">Para comparação Boolean, `result` é a exclusão lógica (disjunção lógica exclusiva) de dois `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="60b85-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="60b85-109">Para operações bit a bit, `result` é um valor numérico que representa a exclusão bit a bit (disjunção bit a bit exclusiva) dos dois padrões numéricos de bits.</span><span class="sxs-lookup"><span data-stu-id="60b85-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="60b85-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="60b85-110">Required.</span></span> <span data-ttu-id="60b85-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="60b85-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="60b85-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="60b85-112">Required.</span></span> <span data-ttu-id="60b85-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="60b85-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60b85-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="60b85-114">Remarks</span></span>  
 <span data-ttu-id="60b85-115">Para comparação Boolean, `result` é `True` se e somente se exatamente um `expression1` e `expression2` é avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="60b85-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="60b85-116">Ou seja, se e somente se `expression1` e `expression2` avaliar como oposto `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="60b85-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="60b85-117">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="60b85-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="60b85-118">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="60b85-118">If `expression1` is</span></span>|<span data-ttu-id="60b85-119">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="60b85-119">And `expression2` is</span></span>|<span data-ttu-id="60b85-120">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="60b85-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="60b85-121">Em uma comparação booliana, o `Xor` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="60b85-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="60b85-122">Não há nenhum equivalente de curto-circuito para `Xor`, porque o resultado sempre depende dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="60b85-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="60b85-123">Para *curto-circuito* operadores lógicos, consulte [operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) e [operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="60b85-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="60b85-124">Para operações bit a bit, o `Xor` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="60b85-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="60b85-125">Se bit no `expression1` é</span><span class="sxs-lookup"><span data-stu-id="60b85-125">If bit in `expression1` is</span></span>|<span data-ttu-id="60b85-126">E o bit na `expression2` é</span><span class="sxs-lookup"><span data-stu-id="60b85-126">And bit in `expression2` is</span></span>|<span data-ttu-id="60b85-127">O bit `result` é</span><span class="sxs-lookup"><span data-stu-id="60b85-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="60b85-128">1</span><span class="sxs-lookup"><span data-stu-id="60b85-128">1</span></span>|<span data-ttu-id="60b85-129">1</span><span class="sxs-lookup"><span data-stu-id="60b85-129">1</span></span>|<span data-ttu-id="60b85-130">0</span><span class="sxs-lookup"><span data-stu-id="60b85-130">0</span></span>|  
|<span data-ttu-id="60b85-131">1</span><span class="sxs-lookup"><span data-stu-id="60b85-131">1</span></span>|<span data-ttu-id="60b85-132">0</span><span class="sxs-lookup"><span data-stu-id="60b85-132">0</span></span>|<span data-ttu-id="60b85-133">1</span><span class="sxs-lookup"><span data-stu-id="60b85-133">1</span></span>|  
|<span data-ttu-id="60b85-134">0</span><span class="sxs-lookup"><span data-stu-id="60b85-134">0</span></span>|<span data-ttu-id="60b85-135">1</span><span class="sxs-lookup"><span data-stu-id="60b85-135">1</span></span>|<span data-ttu-id="60b85-136">1</span><span class="sxs-lookup"><span data-stu-id="60b85-136">1</span></span>|  
|<span data-ttu-id="60b85-137">0</span><span class="sxs-lookup"><span data-stu-id="60b85-137">0</span></span>|<span data-ttu-id="60b85-138">0</span><span class="sxs-lookup"><span data-stu-id="60b85-138">0</span></span>|<span data-ttu-id="60b85-139">0</span><span class="sxs-lookup"><span data-stu-id="60b85-139">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="60b85-140">Como os operadores lógicos e bit a bit possuem uma precedência inferior que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser entre parênteses para garantir execução precisa.</span><span class="sxs-lookup"><span data-stu-id="60b85-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="60b85-141">Por exemplo, 5 `Xor` 3 é 6.</span><span class="sxs-lookup"><span data-stu-id="60b85-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="60b85-142">Para ver por que isso assim, converta 5 e 3 em suas representações binárias, 101 e 011.</span><span class="sxs-lookup"><span data-stu-id="60b85-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="60b85-143">Em seguida, use a tabela anterior para determinar que 101 Xor 011 é 110, que é a representação binária do número decimal 6.</span><span class="sxs-lookup"><span data-stu-id="60b85-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="60b85-144">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="60b85-144">Data Types</span></span>  
 <span data-ttu-id="60b85-145">Se os operandos consistem em uma `Boolean` expressão e uma expressão numérica, Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="60b85-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="60b85-146">Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="60b85-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="60b85-147">Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="60b85-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="60b85-148">Consulte a tabela "Comparações relacionais e bit a bit" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="60b85-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="60b85-149">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="60b85-149">Overloading</span></span>  
 <span data-ttu-id="60b85-150">O `Xor` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="60b85-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="60b85-151">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="60b85-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="60b85-152">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="60b85-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b85-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60b85-153">Example</span></span>  
 <span data-ttu-id="60b85-154">O exemplo a seguir usa o `Xor` operador para executar exclusão lógica (disjunção lógica exclusiva) em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="60b85-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="60b85-155">O resultado é um `Boolean` valor que representa se exatamente uma das expressões é `True`.</span><span class="sxs-lookup"><span data-stu-id="60b85-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_1.vb)]  
  
 <span data-ttu-id="60b85-156">O exemplo anterior produz resultados `False`, `True`, e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="60b85-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60b85-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="60b85-157">Example</span></span>  
 <span data-ttu-id="60b85-158">O exemplo a seguir usa o `Xor` operador para executar exclusão lógica (disjunção lógica exclusiva) nos bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="60b85-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="60b85-159">O bit no padrão resultante é definido se exatamente um dos bits correspondentes nos dois operandos é definido como 1.</span><span class="sxs-lookup"><span data-stu-id="60b85-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xor-operator_2.vb)]  
  
 <span data-ttu-id="60b85-160">O exemplo anterior produz resultados 2, 12 e 14, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="60b85-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60b85-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="60b85-161">See Also</span></span>  
 [<span data-ttu-id="60b85-162">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60b85-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="60b85-163">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60b85-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="60b85-164">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="60b85-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="60b85-165">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60b85-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
