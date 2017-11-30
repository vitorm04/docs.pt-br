---
title: Operador And (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e1f9df11152f88ef0db24a794026d6f5888a2e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="e3250-102">Operador And (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3250-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="e3250-103">Executa uma conjunção lógica em duas `Boolean` expressões ou uma conjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="e3250-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3250-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e3250-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="e3250-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e3250-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="e3250-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e3250-106">Required.</span></span> <span data-ttu-id="e3250-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="e3250-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="e3250-108">Para comparação Boolean, `result` é a conjunção lógica de dois `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="e3250-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="e3250-109">Para operações bit a bit, `result` é um valor numérico que representa a conjunção bit a bit de dois padrões numéricos de bits.</span><span class="sxs-lookup"><span data-stu-id="e3250-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="e3250-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e3250-110">Required.</span></span> <span data-ttu-id="e3250-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="e3250-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="e3250-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e3250-112">Required.</span></span> <span data-ttu-id="e3250-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="e3250-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e3250-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="e3250-114">Remarks</span></span>  
 <span data-ttu-id="e3250-115">Para comparação Boolean, `result` é `True` se e somente se ambos os `expression1` e `expression2` são avaliadas como `True`.</span><span class="sxs-lookup"><span data-stu-id="e3250-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="e3250-116">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="e3250-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="e3250-117">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="e3250-117">If `expression1` is</span></span>|<span data-ttu-id="e3250-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="e3250-118">And `expression2` is</span></span>|<span data-ttu-id="e3250-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="e3250-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="e3250-120">Em uma comparação booliana, o `And` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="e3250-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="e3250-121">O [operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) executa *curto-circuito*, que significa que, se `expression1` é `False`, em seguida, `expression2` não será avaliada.</span><span class="sxs-lookup"><span data-stu-id="e3250-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="e3250-122">Quando aplicado a valores numéricos, o `And` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="e3250-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="e3250-123">Se bit no `expression1` é</span><span class="sxs-lookup"><span data-stu-id="e3250-123">If bit in `expression1` is</span></span>|<span data-ttu-id="e3250-124">E o bit na `expression2` é</span><span class="sxs-lookup"><span data-stu-id="e3250-124">And bit in `expression2` is</span></span>|<span data-ttu-id="e3250-125">O bit `result` é</span><span class="sxs-lookup"><span data-stu-id="e3250-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="e3250-126">1</span><span class="sxs-lookup"><span data-stu-id="e3250-126">1</span></span>|<span data-ttu-id="e3250-127">1</span><span class="sxs-lookup"><span data-stu-id="e3250-127">1</span></span>|<span data-ttu-id="e3250-128">1</span><span class="sxs-lookup"><span data-stu-id="e3250-128">1</span></span>|  
|<span data-ttu-id="e3250-129">1</span><span class="sxs-lookup"><span data-stu-id="e3250-129">1</span></span>|<span data-ttu-id="e3250-130">0</span><span class="sxs-lookup"><span data-stu-id="e3250-130">0</span></span>|<span data-ttu-id="e3250-131">0</span><span class="sxs-lookup"><span data-stu-id="e3250-131">0</span></span>|  
|<span data-ttu-id="e3250-132">0</span><span class="sxs-lookup"><span data-stu-id="e3250-132">0</span></span>|<span data-ttu-id="e3250-133">1</span><span class="sxs-lookup"><span data-stu-id="e3250-133">1</span></span>|<span data-ttu-id="e3250-134">0</span><span class="sxs-lookup"><span data-stu-id="e3250-134">0</span></span>|  
|<span data-ttu-id="e3250-135">0</span><span class="sxs-lookup"><span data-stu-id="e3250-135">0</span></span>|<span data-ttu-id="e3250-136">0</span><span class="sxs-lookup"><span data-stu-id="e3250-136">0</span></span>|<span data-ttu-id="e3250-137">0</span><span class="sxs-lookup"><span data-stu-id="e3250-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="e3250-138">Como os operadores lógicos e bit a bit possuem uma precedência inferior que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser incluídas entre parênteses para garantir resultados precisos.</span><span class="sxs-lookup"><span data-stu-id="e3250-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="e3250-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="e3250-139">Data Types</span></span>  
 <span data-ttu-id="e3250-140">Se os operandos consistem em uma `Boolean` expressão e uma expressão numérica, Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="e3250-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="e3250-141">Para obter uma comparação booliana, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e3250-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="e3250-142">Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="e3250-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="e3250-143">Consulte a tabela "Comparações relacionais e bit a bit" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="e3250-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3250-144">O `And` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e3250-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="e3250-145">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que compreender o comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="e3250-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="e3250-146">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e3250-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3250-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3250-147">Example</span></span>  
 <span data-ttu-id="e3250-148">O exemplo a seguir usa o `And` operador para executar uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="e3250-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="e3250-149">O resultado é um `Boolean` valor que indica se as duas expressões são `True`.</span><span class="sxs-lookup"><span data-stu-id="e3250-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]  
  
 <span data-ttu-id="e3250-150">O exemplo anterior produz resultados de `True` e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e3250-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3250-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e3250-151">Example</span></span>  
 <span data-ttu-id="e3250-152">O exemplo a seguir usa o `And` operador para executar uma conjunção lógica nos bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="e3250-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="e3250-153">O bit no padrão resultante é definido se os bits correspondentes nos dois operandos são definidas como 1.</span><span class="sxs-lookup"><span data-stu-id="e3250-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]  
  
 <span data-ttu-id="e3250-154">O exemplo anterior produz resultados 8, 2 e 0, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="e3250-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3250-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e3250-155">See Also</span></span>  
 [<span data-ttu-id="e3250-156">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3250-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)  
 [<span data-ttu-id="e3250-157">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3250-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="e3250-158">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="e3250-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="e3250-159">Operador AndAlso</span><span class="sxs-lookup"><span data-stu-id="e3250-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)  
 [<span data-ttu-id="e3250-160">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3250-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
