---
title: Operador Or (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4c9429eb2bdeb86bfa73786433231fdc22a230d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="5cc1a-102">Operador Or (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc1a-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="5cc1a-103">Executa uma disjunção lógica em duas `Boolean` expressões ou uma disjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5cc1a-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="5cc1a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5cc1a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="5cc1a-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-106">Required.</span></span> <span data-ttu-id="5cc1a-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="5cc1a-108">Para `Boolean` comparação, `result` é a disjunção lógica inclusiva de dois `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="5cc1a-109">Para operações bit a bit, `result` é um valor numérico que representa a disjunção bit a bit de dois padrões numéricos de bits.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="5cc1a-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-110">Required.</span></span> <span data-ttu-id="5cc1a-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="5cc1a-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-112">Required.</span></span> <span data-ttu-id="5cc1a-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5cc1a-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="5cc1a-114">Remarks</span></span>  
 <span data-ttu-id="5cc1a-115">Para `Boolean` comparação, `result` é `False` se e somente se ambos os `expression1` e `expression2` são avaliadas como `False`.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="5cc1a-116">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="5cc1a-117">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="5cc1a-117">If `expression1` is</span></span>|<span data-ttu-id="5cc1a-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="5cc1a-118">And `expression2` is</span></span>|<span data-ttu-id="5cc1a-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="5cc1a-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="5cc1a-120">Em um `Boolean` comparação, o `Or` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="5cc1a-121">O [operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) executa *curto-circuito*, que significa que, se `expression1` é `True`, em seguida, `expression2` não será avaliada.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="5cc1a-122">Para operações bit a bit, o `Or` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="5cc1a-123">Se bit no `expression1` é</span><span class="sxs-lookup"><span data-stu-id="5cc1a-123">If bit in `expression1` is</span></span>|<span data-ttu-id="5cc1a-124">E o bit na `expression2` é</span><span class="sxs-lookup"><span data-stu-id="5cc1a-124">And bit in `expression2` is</span></span>|<span data-ttu-id="5cc1a-125">O bit `result` é</span><span class="sxs-lookup"><span data-stu-id="5cc1a-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="5cc1a-126">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-126">1</span></span>|<span data-ttu-id="5cc1a-127">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-127">1</span></span>|<span data-ttu-id="5cc1a-128">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-128">1</span></span>|  
|<span data-ttu-id="5cc1a-129">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-129">1</span></span>|<span data-ttu-id="5cc1a-130">0</span><span class="sxs-lookup"><span data-stu-id="5cc1a-130">0</span></span>|<span data-ttu-id="5cc1a-131">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-131">1</span></span>|  
|<span data-ttu-id="5cc1a-132">0</span><span class="sxs-lookup"><span data-stu-id="5cc1a-132">0</span></span>|<span data-ttu-id="5cc1a-133">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-133">1</span></span>|<span data-ttu-id="5cc1a-134">1</span><span class="sxs-lookup"><span data-stu-id="5cc1a-134">1</span></span>|  
|<span data-ttu-id="5cc1a-135">0</span><span class="sxs-lookup"><span data-stu-id="5cc1a-135">0</span></span>|<span data-ttu-id="5cc1a-136">0</span><span class="sxs-lookup"><span data-stu-id="5cc1a-136">0</span></span>|<span data-ttu-id="5cc1a-137">0</span><span class="sxs-lookup"><span data-stu-id="5cc1a-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="5cc1a-138">Como os operadores lógicos e bit a bit possuem uma precedência inferior que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser entre parênteses para garantir execução precisa.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="5cc1a-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="5cc1a-139">Data Types</span></span>  
 <span data-ttu-id="5cc1a-140">Se os operandos consistem em uma `Boolean` expressão e uma expressão numérica, Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="5cc1a-141">Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="5cc1a-142">Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="5cc1a-143">Consulte a tabela "Comparações relacionais e bit a bit" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="5cc1a-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="5cc1a-144">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="5cc1a-144">Overloading</span></span>  
 <span data-ttu-id="5cc1a-145">O `Or` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5cc1a-146">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5cc1a-147">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5cc1a-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc1a-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5cc1a-148">Example</span></span>  
 <span data-ttu-id="5cc1a-149">O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="5cc1a-150">O resultado é um `Boolean` valor que representa se uma das duas expressões são `True`.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]  
  
 <span data-ttu-id="5cc1a-151">O exemplo anterior produz resultados de `True`, `True`, e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-151">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cc1a-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5cc1a-152">Example</span></span>  
 <span data-ttu-id="5cc1a-153">O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica inclusiva nos bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-153">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="5cc1a-154">O bit no padrão resultante é definido se os bits correspondentes nos dois operandos é definida como 1.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-154">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]  
  
 <span data-ttu-id="5cc1a-155">O exemplo anterior produz resultados 10, 14 e 14, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5cc1a-155">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc1a-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5cc1a-156">See Also</span></span>  
 [<span data-ttu-id="5cc1a-157">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5cc1a-157">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="5cc1a-158">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cc1a-158">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="5cc1a-159">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="5cc1a-159">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="5cc1a-160">Operador OrElse</span><span class="sxs-lookup"><span data-stu-id="5cc1a-160">OrElse Operator</span></span>](../../../visual-basic/language-reference/operators/orelse-operator.md)  
 [<span data-ttu-id="5cc1a-161">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5cc1a-161">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
