---
title: Operador And (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
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
ms.openlocfilehash: 7e25f25677fa684427bdaf00cea73916ffbad655
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818612"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="9bb5c-102">Operador And (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bb5c-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="9bb5c-103">Executa uma conjunção lógica em duas `Boolean` expressões ou uma conjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bb5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bb5c-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="9bb5c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="9bb5c-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="9bb5c-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-106">Required.</span></span> <span data-ttu-id="9bb5c-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="9bb5c-108">Para comparação de booliana `result` é a conjunção lógica de duas `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="9bb5c-109">Para operações bit a bit, `result` é um valor numérico que representa a conjunção bit a bit de dois padrões numéricos de bits.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="9bb5c-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-110">Required.</span></span> <span data-ttu-id="9bb5c-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="9bb5c-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-112">Required.</span></span> <span data-ttu-id="9bb5c-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bb5c-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bb5c-114">Remarks</span></span>  
 <span data-ttu-id="9bb5c-115">Para comparação Boolean, `result` está `True` se e somente se os dois `expression1` e `expression2` são avaliadas como `True`.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="9bb5c-116">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="9bb5c-117">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="9bb5c-117">If `expression1` is</span></span>|<span data-ttu-id="9bb5c-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="9bb5c-118">And `expression2` is</span></span>|<span data-ttu-id="9bb5c-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="9bb5c-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="9bb5c-120">Em uma comparação Booleana, o `And` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="9bb5c-121">O [operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) executa *Short-circuiting*, que significa que, se `expression1` é `False`, em seguida, `expression2` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="9bb5c-122">Quando aplicado a valores numéricos, o `And` operador executa uma comparação bit a bit dos bits posicionados de forma idêntica em duas expressões numéricas e define o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="9bb5c-123">Se bit no `expression1` é</span><span class="sxs-lookup"><span data-stu-id="9bb5c-123">If bit in `expression1` is</span></span>|<span data-ttu-id="9bb5c-124">E o bit no `expression2` é</span><span class="sxs-lookup"><span data-stu-id="9bb5c-124">And bit in `expression2` is</span></span>|<span data-ttu-id="9bb5c-125">O bit no `result` é</span><span class="sxs-lookup"><span data-stu-id="9bb5c-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="9bb5c-126">1</span><span class="sxs-lookup"><span data-stu-id="9bb5c-126">1</span></span>|<span data-ttu-id="9bb5c-127">1</span><span class="sxs-lookup"><span data-stu-id="9bb5c-127">1</span></span>|<span data-ttu-id="9bb5c-128">1</span><span class="sxs-lookup"><span data-stu-id="9bb5c-128">1</span></span>|  
|<span data-ttu-id="9bb5c-129">1</span><span class="sxs-lookup"><span data-stu-id="9bb5c-129">1</span></span>|<span data-ttu-id="9bb5c-130">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-130">0</span></span>|<span data-ttu-id="9bb5c-131">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-131">0</span></span>|  
|<span data-ttu-id="9bb5c-132">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-132">0</span></span>|<span data-ttu-id="9bb5c-133">1</span><span class="sxs-lookup"><span data-stu-id="9bb5c-133">1</span></span>|<span data-ttu-id="9bb5c-134">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-134">0</span></span>|  
|<span data-ttu-id="9bb5c-135">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-135">0</span></span>|<span data-ttu-id="9bb5c-136">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-136">0</span></span>|<span data-ttu-id="9bb5c-137">0</span><span class="sxs-lookup"><span data-stu-id="9bb5c-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="9bb5c-138">Como os operadores lógicos e bit a bit tem uma precedência inferior outros operadores aritméticos e relacionais, todas as operações bit a bit devem ser colocadas entre parênteses para garantir resultados precisos.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="9bb5c-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="9bb5c-139">Data Types</span></span>  
 <span data-ttu-id="9bb5c-140">Se os operandos consistem em uma `Boolean` expressão e uma expressão numérica, Visual Basic converte as `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="9bb5c-141">Para obter uma comparação Booleana, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="9bb5c-142">Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="9bb5c-143">Consulte a tabela "Comparações relacionais e bit a bit" na [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="9bb5c-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bb5c-144">O `And` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="9bb5c-145">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="9bb5c-146">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="9bb5c-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bb5c-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bb5c-147">Example</span></span>  
 <span data-ttu-id="9bb5c-148">O exemplo a seguir usa o `And` operador para executar uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="9bb5c-149">O resultado é um `Boolean` valor que indica se as duas expressões são `True`.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="9bb5c-150">O exemplo anterior produz resultados `True` e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bb5c-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bb5c-151">Example</span></span>  
 <span data-ttu-id="9bb5c-152">O exemplo a seguir usa o `And` operador para realizar a conjunção lógica em bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="9bb5c-153">O bit no padrão resultante será definido se os bits correspondentes nos dois operandos são definidas como 1.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="9bb5c-154">O exemplo anterior produz resultados 8, 2 e 0, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9bb5c-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb5c-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bb5c-155">See also</span></span>

- [<span data-ttu-id="9bb5c-156">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9bb5c-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="9bb5c-157">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bb5c-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="9bb5c-158">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="9bb5c-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="9bb5c-159">Operador AndAlso</span><span class="sxs-lookup"><span data-stu-id="9bb5c-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="9bb5c-160">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9bb5c-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
