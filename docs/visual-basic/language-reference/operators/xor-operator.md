---
title: Operador Xor
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
ms.openlocfilehash: c5c7ec87bc173f724f8c670395bc3b0458444df6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74335398"
---
# <a name="xor-operator-visual-basic"></a><span data-ttu-id="39bbb-102">Operador Xor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39bbb-102">Xor Operator (Visual Basic)</span></span>
<span data-ttu-id="39bbb-103">Executa uma exclusão lógica em duas expressões de `Boolean`, ou uma exclusão de bits em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="39bbb-103">Performs a logical exclusion on two `Boolean` expressions, or a bitwise exclusion on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39bbb-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39bbb-104">Syntax</span></span>  
  
```vb  
result = expression1 Xor expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="39bbb-105">Partes</span><span class="sxs-lookup"><span data-stu-id="39bbb-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="39bbb-106">Necessária.</span><span class="sxs-lookup"><span data-stu-id="39bbb-106">Required.</span></span> <span data-ttu-id="39bbb-107">Qualquer `Boolean` ou variável numérica.</span><span class="sxs-lookup"><span data-stu-id="39bbb-107">Any `Boolean` or numeric variable.</span></span> <span data-ttu-id="39bbb-108">Para comparação de booliano, `result` é a exclusão lógica (disjunção lógica exclusiva) de dois valores de `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="39bbb-108">For Boolean comparison, `result` is the logical exclusion (exclusive logical disjunction) of two `Boolean` values.</span></span> <span data-ttu-id="39bbb-109">Para operações de bit-a-bit, `result` é um valor numérico que representa a exclusão de bits bit (disjunção de bits exclusiva) de dois padrões de bit numérico.</span><span class="sxs-lookup"><span data-stu-id="39bbb-109">For bitwise operations, `result` is a numeric value that represents the bitwise exclusion (exclusive bitwise disjunction) of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="39bbb-110">Necessária.</span><span class="sxs-lookup"><span data-stu-id="39bbb-110">Required.</span></span> <span data-ttu-id="39bbb-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="39bbb-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="39bbb-112">Necessária.</span><span class="sxs-lookup"><span data-stu-id="39bbb-112">Required.</span></span> <span data-ttu-id="39bbb-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="39bbb-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39bbb-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="39bbb-114">Remarks</span></span>  
 <span data-ttu-id="39bbb-115">Para comparação booliana, `result` será `True` se e somente se uma das `expression1` e `expression2` for avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="39bbb-115">For Boolean comparison, `result` is `True` if and only if exactly one of `expression1` and `expression2` evaluates to `True`.</span></span> <span data-ttu-id="39bbb-116">Ou seja, somente se `expression1` e `expression2` forem avaliadas como valores `Boolean` opostos.</span><span class="sxs-lookup"><span data-stu-id="39bbb-116">That is, if and only if `expression1` and `expression2` evaluate to opposite `Boolean` values.</span></span> <span data-ttu-id="39bbb-117">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="39bbb-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="39bbb-118">Se `expression1` for</span><span class="sxs-lookup"><span data-stu-id="39bbb-118">If `expression1` is</span></span>|<span data-ttu-id="39bbb-119">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="39bbb-119">And `expression2` is</span></span>|<span data-ttu-id="39bbb-120">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="39bbb-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`False`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> <span data-ttu-id="39bbb-121">Em uma comparação Booleana, o operador `Xor` sempre avalia as duas expressões, o que pode incluir fazer chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="39bbb-121">In a Boolean comparison, the `Xor` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="39bbb-122">Não há uma contraparte de curto-circuito para `Xor`, porque o resultado sempre depende dos dois operandos.</span><span class="sxs-lookup"><span data-stu-id="39bbb-122">There is no short-circuiting counterpart to `Xor`, because the result always depends on both operands.</span></span> <span data-ttu-id="39bbb-123">Para operadores lógicos de *curto-circuito* , consulte o operador [AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) e o [Operador OrElse](../../../visual-basic/language-reference/operators/orelse-operator.md).</span><span class="sxs-lookup"><span data-stu-id="39bbb-123">For *short-circuiting* logical operators, see [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) and [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
 <span data-ttu-id="39bbb-124">No caso de operações de bit-numérico, o operador de `Xor` executa uma comparação bit a bit de bits posicionados de forma idêntica em duas expressões numéricas e define o bit correspondente em `result` de acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="39bbb-124">For bitwise operations, the `Xor` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="39bbb-125">Se o bit no `expression1` for</span><span class="sxs-lookup"><span data-stu-id="39bbb-125">If bit in `expression1` is</span></span>|<span data-ttu-id="39bbb-126">E o bit no `expression2` é</span><span class="sxs-lookup"><span data-stu-id="39bbb-126">And bit in `expression2` is</span></span>|<span data-ttu-id="39bbb-127">O bit no `result` é</span><span class="sxs-lookup"><span data-stu-id="39bbb-127">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="39bbb-128">1</span><span class="sxs-lookup"><span data-stu-id="39bbb-128">1</span></span>|<span data-ttu-id="39bbb-129">1</span><span class="sxs-lookup"><span data-stu-id="39bbb-129">1</span></span>|<span data-ttu-id="39bbb-130">0</span><span class="sxs-lookup"><span data-stu-id="39bbb-130">0</span></span>|  
|<span data-ttu-id="39bbb-131">1</span><span class="sxs-lookup"><span data-stu-id="39bbb-131">1</span></span>|<span data-ttu-id="39bbb-132">0</span><span class="sxs-lookup"><span data-stu-id="39bbb-132">0</span></span>|<span data-ttu-id="39bbb-133">1</span><span class="sxs-lookup"><span data-stu-id="39bbb-133">1</span></span>|  
|<span data-ttu-id="39bbb-134">0</span><span class="sxs-lookup"><span data-stu-id="39bbb-134">0</span></span>|<span data-ttu-id="39bbb-135">1</span><span class="sxs-lookup"><span data-stu-id="39bbb-135">1</span></span>|<span data-ttu-id="39bbb-136">1</span><span class="sxs-lookup"><span data-stu-id="39bbb-136">1</span></span>|  
|<span data-ttu-id="39bbb-137">0</span><span class="sxs-lookup"><span data-stu-id="39bbb-137">0</span></span>|<span data-ttu-id="39bbb-138">0</span><span class="sxs-lookup"><span data-stu-id="39bbb-138">0</span></span>|<span data-ttu-id="39bbb-139">0</span><span class="sxs-lookup"><span data-stu-id="39bbb-139">0</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="39bbb-140">Uma vez que os operadores lógicos e bit-a-or têm uma precedência mais baixa do que outros operadores aritméticos e relacionais, todas as operações de bit-nte devem ser colocadas entre parênteses para garantir a execução</span><span class="sxs-lookup"><span data-stu-id="39bbb-140">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.</span></span>  
  
 <span data-ttu-id="39bbb-141">Por exemplo, 5 `Xor` 3 é 6.</span><span class="sxs-lookup"><span data-stu-id="39bbb-141">For example, 5 `Xor` 3 is 6.</span></span> <span data-ttu-id="39bbb-142">Para ver por que isso é feito, converta 5 e 3 em suas representações binárias, 101 e 011.</span><span class="sxs-lookup"><span data-stu-id="39bbb-142">To see why this is so, convert 5 and 3 to their binary representations, 101 and 011.</span></span> <span data-ttu-id="39bbb-143">Em seguida, use a tabela anterior para determinar que 101 XOR 011 é 110, que é a representação binária do número decimal 6.</span><span class="sxs-lookup"><span data-stu-id="39bbb-143">Then use the previous table to determine that 101 Xor 011 is 110, which is the binary representation of the decimal number 6.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="39bbb-144">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="39bbb-144">Data Types</span></span>  
 <span data-ttu-id="39bbb-145">Se os operandos contiverem uma expressão de `Boolean` e uma expressão numérica, Visual Basic converterá a expressão de `Boolean` em um valor numérico (– 1 para `True` e 0 para `False`) e executará uma operação de bits</span><span class="sxs-lookup"><span data-stu-id="39bbb-145">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="39bbb-146">Para uma comparação de `Boolean`, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="39bbb-146">For a `Boolean` comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="39bbb-147">Para uma comparação de bits, o tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="39bbb-147">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="39bbb-148">Consulte a tabela "comparações relacionais e de bits-bit" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="39bbb-148">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="39bbb-149">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="39bbb-149">Overloading</span></span>  
 <span data-ttu-id="39bbb-150">O operador `Xor` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="39bbb-150">The `Xor` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="39bbb-151">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="39bbb-151">If your code uses this operator on such a class or structure, make sure you understand its redefined behavior.</span></span> <span data-ttu-id="39bbb-152">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="39bbb-152">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="39bbb-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39bbb-153">Example</span></span>  
 <span data-ttu-id="39bbb-154">O exemplo a seguir usa o operador `Xor` para executar a exclusão lógica (disjunção lógica exclusiva) em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="39bbb-154">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on two expressions.</span></span> <span data-ttu-id="39bbb-155">O resultado é um valor `Boolean` que representa se exatamente uma das expressões é `True`.</span><span class="sxs-lookup"><span data-stu-id="39bbb-155">The result is a `Boolean` value that represents whether exactly one of the expressions is `True`.</span></span>  
  
 [!code-vb[VbVbalrOperators#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#40)]  
  
 <span data-ttu-id="39bbb-156">O exemplo anterior produz resultados de `False`, `True`e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="39bbb-156">The previous example produces results of `False`, `True`, and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39bbb-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39bbb-157">Example</span></span>  
 <span data-ttu-id="39bbb-158">O exemplo a seguir usa o operador `Xor` para executar a exclusão lógica (disjunção lógica exclusiva) em bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="39bbb-158">The following example uses the `Xor` operator to perform logical exclusion (exclusive logical disjunction) on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="39bbb-159">O bit no padrão de resultado será definido se exatamente um dos bits correspondentes nos operandos for definido como 1.</span><span class="sxs-lookup"><span data-stu-id="39bbb-159">The bit in the result pattern is set if exactly one of the corresponding bits in the operands is set to 1.</span></span>  
  
 [!code-vb[VbVbalrOperators#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#41)]  
  
 <span data-ttu-id="39bbb-160">O exemplo anterior produz resultados de 2, 12 e 14, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="39bbb-160">The previous example produces results of 2, 12, and 14, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39bbb-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39bbb-161">See also</span></span>

- [<span data-ttu-id="39bbb-162">Operadores lógicos/bits (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="39bbb-162">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="39bbb-163">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39bbb-163">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="39bbb-164">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="39bbb-164">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="39bbb-165">Operadores lógicos e de bits bit a Visual Basic</span><span class="sxs-lookup"><span data-stu-id="39bbb-165">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
