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
ms.openlocfilehash: bd6ebbf5f53a7cf187b5d8ce7630080d44d46df2
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591622"
---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="5f989-102">Operador And (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f989-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="5f989-103">Executa uma conjunção lógica em duas expressões `Boolean`, ou uma conjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="5f989-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f989-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f989-104">Syntax</span></span>  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="5f989-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5f989-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="5f989-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5f989-106">Required.</span></span> <span data-ttu-id="5f989-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f989-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="5f989-108">Para comparação booliana, `result` é a conjunção lógica de dois valores `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5f989-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="5f989-109">Para operações de bit-a-zero, `result` é um valor numérico que representa a conjunção de bits de dois padrões numéricos de bit.</span><span class="sxs-lookup"><span data-stu-id="5f989-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="5f989-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5f989-110">Required.</span></span> <span data-ttu-id="5f989-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f989-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="5f989-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5f989-112">Required.</span></span> <span data-ttu-id="5f989-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f989-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f989-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f989-114">Remarks</span></span>  
 <span data-ttu-id="5f989-115">Para comparação booliana, `result` será `True` se e somente se `expression1` e `expression2` forem avaliados como `True`.</span><span class="sxs-lookup"><span data-stu-id="5f989-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="5f989-116">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="5f989-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="5f989-117">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="5f989-117">If `expression1` is</span></span>|<span data-ttu-id="5f989-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="5f989-118">And `expression2` is</span></span>|<span data-ttu-id="5f989-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="5f989-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="5f989-120">Em uma comparação Booleana, o operador `And` sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="5f989-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="5f989-121">O [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) executa um *curto-circuito*, o que significa que, se `expression1` for `False`, `expression2` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="5f989-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="5f989-122">Quando aplicado a valores numéricos, o operador `And` executa uma comparação bit a bit de bits posicionados de forma idêntica em duas expressões numéricas e define o bit correspondente em `result` de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="5f989-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="5f989-123">Se o bit em `expression1` for</span><span class="sxs-lookup"><span data-stu-id="5f989-123">If bit in `expression1` is</span></span>|<span data-ttu-id="5f989-124">E o bit em `expression2` é</span><span class="sxs-lookup"><span data-stu-id="5f989-124">And bit in `expression2` is</span></span>|<span data-ttu-id="5f989-125">O bit em `result` é</span><span class="sxs-lookup"><span data-stu-id="5f989-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="5f989-126">1</span><span class="sxs-lookup"><span data-stu-id="5f989-126">1</span></span>|<span data-ttu-id="5f989-127">1</span><span class="sxs-lookup"><span data-stu-id="5f989-127">1</span></span>|<span data-ttu-id="5f989-128">1</span><span class="sxs-lookup"><span data-stu-id="5f989-128">1</span></span>|  
|<span data-ttu-id="5f989-129">1</span><span class="sxs-lookup"><span data-stu-id="5f989-129">1</span></span>|<span data-ttu-id="5f989-130">0</span><span class="sxs-lookup"><span data-stu-id="5f989-130">0</span></span>|<span data-ttu-id="5f989-131">0</span><span class="sxs-lookup"><span data-stu-id="5f989-131">0</span></span>|  
|<span data-ttu-id="5f989-132">0</span><span class="sxs-lookup"><span data-stu-id="5f989-132">0</span></span>|<span data-ttu-id="5f989-133">1</span><span class="sxs-lookup"><span data-stu-id="5f989-133">1</span></span>|<span data-ttu-id="5f989-134">0</span><span class="sxs-lookup"><span data-stu-id="5f989-134">0</span></span>|  
|<span data-ttu-id="5f989-135">0</span><span class="sxs-lookup"><span data-stu-id="5f989-135">0</span></span>|<span data-ttu-id="5f989-136">0</span><span class="sxs-lookup"><span data-stu-id="5f989-136">0</span></span>|<span data-ttu-id="5f989-137">0</span><span class="sxs-lookup"><span data-stu-id="5f989-137">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="5f989-138">Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem estar entre parênteses para garantir resultados precisos</span><span class="sxs-lookup"><span data-stu-id="5f989-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="5f989-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="5f989-139">Data Types</span></span>  
 <span data-ttu-id="5f989-140">Se os operandos contiverem uma expressão `Boolean` e uma expressão numérica, Visual Basic converterá a expressão `Boolean` em um valor numérico (– 1 para `True` e 0 para `False`) e executará uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="5f989-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="5f989-141">Para uma comparação booliana, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="5f989-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="5f989-142">Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="5f989-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="5f989-143">Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="5f989-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f989-144">O operador `And` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5f989-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5f989-145">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="5f989-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="5f989-146">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5f989-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f989-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f989-147">Example</span></span>  
 <span data-ttu-id="5f989-148">O exemplo a seguir usa o operador `And` para executar uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="5f989-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="5f989-149">O resultado é um valor `Boolean` que representa se ambas as expressões são `True`.</span><span class="sxs-lookup"><span data-stu-id="5f989-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 <span data-ttu-id="5f989-150">O exemplo anterior produz resultados de `True` e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5f989-150">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f989-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f989-151">Example</span></span>  
 <span data-ttu-id="5f989-152">O exemplo a seguir usa o operador `And` para executar uma conjunção lógica em bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="5f989-152">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="5f989-153">O bit no padrão de resultado será definido se os bits correspondentes nos operandos estiverem definidos como 1.</span><span class="sxs-lookup"><span data-stu-id="5f989-153">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 <span data-ttu-id="5f989-154">O exemplo anterior produz resultados de 8, 2 e 0, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5f989-154">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f989-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f989-155">See also</span></span>

- [<span data-ttu-id="5f989-156">Operadores lógicos/bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f989-156">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="5f989-157">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f989-157">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5f989-158">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="5f989-158">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5f989-159">Operador AndAlso</span><span class="sxs-lookup"><span data-stu-id="5f989-159">AndAlso Operator</span></span>](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [<span data-ttu-id="5f989-160">Operadores lógicos e de bits bit a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f989-160">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
