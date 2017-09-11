---
title: Operador OR (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Or
dev_langs:
- VB
helpviewer_keywords:
- Or operator
- operators [Visual Basic], bitwise
- inclusive Or operator
- bitwise operators, OR operator
- Or keyword
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison
- logical disjunction
- disjunction operator
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
caps.latest.revision: 12
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: 01d51f50dd785f168ed850e3f1763b300d9d2011
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="or-operator-visual-basic"></a><span data-ttu-id="b162f-102">Operador Or (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b162f-102">Or Operator (Visual Basic)</span></span>
<span data-ttu-id="b162f-103">Executa uma disjunção lógica em duas `Boolean` expressões ou uma disjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="b162f-103">Performs a logical disjunction on two `Boolean` expressions, or a bitwise disjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b162f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b162f-104">Syntax</span></span>  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="b162f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b162f-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="b162f-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b162f-106">Required.</span></span> <span data-ttu-id="b162f-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="b162f-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="b162f-108">Para `Boolean` comparação, `result` é a disjunção lógica de dois `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="b162f-108">For `Boolean` comparison, `result` is the inclusive logical disjunction of two `Boolean` values.</span></span> <span data-ttu-id="b162f-109">Para operações bit a bit, `result` é um valor numérico representando a disjução bit a bit de dois padrões numéricos de bits.</span><span class="sxs-lookup"><span data-stu-id="b162f-109">For bitwise operations, `result` is a numeric value representing the inclusive bitwise disjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="b162f-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b162f-110">Required.</span></span> <span data-ttu-id="b162f-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="b162f-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="b162f-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b162f-112">Required.</span></span> <span data-ttu-id="b162f-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="b162f-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b162f-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="b162f-114">Remarks</span></span>  
 <span data-ttu-id="b162f-115">Para `Boolean` comparação, `result` é `False` se e somente se ambos os `expression1` e `expression2` são avaliadas como `False`.</span><span class="sxs-lookup"><span data-stu-id="b162f-115">For `Boolean` comparison, `result` is `False` if and only if both `expression1` and `expression2` evaluate to `False`.</span></span> <span data-ttu-id="b162f-116">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="b162f-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="b162f-117">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="b162f-117">If `expression1` is</span></span>|<span data-ttu-id="b162f-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="b162f-118">And `expression2` is</span></span>|<span data-ttu-id="b162f-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="b162f-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="b162f-120">Em um `Boolean` comparação, o `Or` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="b162f-120">In a `Boolean` comparison, the `Or` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="b162f-121">O [operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) executa *Short-circuiting*, que significa que, se `expression1` é `True`, em seguida, `expression2` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="b162f-121">The [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) performs *short-circuiting*, which means that if `expression1` is `True`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="b162f-122">Para operações bit a bit, o `Or` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b162f-122">For bitwise operations, the `Or` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="b162f-123">Se bit no `expression1` é</span><span class="sxs-lookup"><span data-stu-id="b162f-123">If bit in `expression1` is</span></span>|<span data-ttu-id="b162f-124">E o bit na `expression2` é</span><span class="sxs-lookup"><span data-stu-id="b162f-124">And bit in `expression2` is</span></span>|<span data-ttu-id="b162f-125">O bit no `result` é</span><span class="sxs-lookup"><span data-stu-id="b162f-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="b162f-126">1</span><span class="sxs-lookup"><span data-stu-id="b162f-126">1</span></span>|<span data-ttu-id="b162f-127">1</span><span class="sxs-lookup"><span data-stu-id="b162f-127">1</span></span>|<span data-ttu-id="b162f-128">1</span><span class="sxs-lookup"><span data-stu-id="b162f-128">1</span></span>|  
|<span data-ttu-id="b162f-129">1</span><span class="sxs-lookup"><span data-stu-id="b162f-129">1</span></span>|<span data-ttu-id="b162f-130">0</span><span class="sxs-lookup"><span data-stu-id="b162f-130">0</span></span>|<span data-ttu-id="b162f-131">1</span><span class="sxs-lookup"><span data-stu-id="b162f-131">1</span></span>|  
|<span data-ttu-id="b162f-132">0</span><span class="sxs-lookup"><span data-stu-id="b162f-132">0</span></span>|<span data-ttu-id="b162f-133">1</span><span class="sxs-lookup"><span data-stu-id="b162f-133">1</span></span>|<span data-ttu-id="b162f-134">1</span><span class="sxs-lookup"><span data-stu-id="b162f-134">1</span></span>|  
|<span data-ttu-id="b162f-135">0</span><span class="sxs-lookup"><span data-stu-id="b162f-135">0</span></span>|<span data-ttu-id="b162f-136">0</span><span class="sxs-lookup"><span data-stu-id="b162f-136">0</span></span>|<span data-ttu-id="b162f-137">0</span><span class="sxs-lookup"><span data-stu-id="b162f-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="b162f-138">Como os operadores lógicos e bit a bit possuem uma precedência menor que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser colocadas entre parênteses para garantir execução precisa.</span><span class="sxs-lookup"><span data-stu-id="b162f-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="b162f-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="b162f-139">Data Types</span></span>  
 <span data-ttu-id="b162f-140">Se o operando consiste em uma `Boolean` expressão e uma expressão numérica, o Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="b162f-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="b162f-141">Para uma `Boolean` comparação, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b162f-141">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="b162f-142">Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="b162f-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="b162f-143">Consulte a tabela "Comparações relacionais e bit a bit" [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="b162f-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b162f-144">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="b162f-144">Overloading</span></span>  
 <span data-ttu-id="b162f-145">O `Or` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="b162f-145">The `Or` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b162f-146">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="b162f-146">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b162f-147">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b162f-147">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b162f-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b162f-148">Example</span></span>  
 <span data-ttu-id="b162f-149">O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="b162f-149">The following example uses the `Or` operator to perform an inclusive logical disjunction on two expressions.</span></span> <span data-ttu-id="b162f-150">O resultado é um `Boolean` valor que representa se uma das duas expressões são `True`.</span><span class="sxs-lookup"><span data-stu-id="b162f-150">The result is a `Boolean` value that represents whether either of the two expressions is `True`.</span></span>  
  
 <span data-ttu-id="b162f-151">[!code-vb[VbVbalrOperators&#35;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b162f-151">[!code-vb[VbVbalrOperators#35](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="b162f-152">O exemplo anterior produz resultados de `True`, `True`, e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b162f-152">The preceding example produces results of `True`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b162f-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b162f-153">Example</span></span>  
 <span data-ttu-id="b162f-154">O exemplo a seguir usa o `Or` operador para executar uma disjunção lógica inclusiva nos bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="b162f-154">The following example uses the `Or` operator to perform inclusive logical disjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="b162f-155">O bit no padrão resultante é definido se nenhum dos bits correspondentes nos dois operandos é definido como 1.</span><span class="sxs-lookup"><span data-stu-id="b162f-155">The bit in the result pattern is set if either of the corresponding bits in the operands is set to 1.</span></span>  
  
 <span data-ttu-id="b162f-156">[!code-vb[VbVbalrOperators&#36;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b162f-156">[!code-vb[VbVbalrOperators#36](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/or-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="b162f-157">O exemplo anterior produz resultados 10, 14 e 14, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b162f-157">The preceding example produces results of 10, 14, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b162f-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b162f-158">See Also</span></span>  
 <span data-ttu-id="b162f-159">[Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="b162f-159">[Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="b162f-160"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="b162f-160"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="b162f-161"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="b162f-161"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="b162f-162"> [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md) </span><span class="sxs-lookup"><span data-stu-id="b162f-162"> [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md) </span></span>  
<span data-ttu-id="b162f-163"> [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="b162f-163"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>

