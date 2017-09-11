---
title: Operador and (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.And
dev_langs:
- VB
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator
- And operator [Visual Basic]
- bitwise operators, AND operator
- operators [Visual Basic], conjunction
- bitwise comparison
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
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
ms.openlocfilehash: 11e37d1dcd7ae7af619c12758b4c53431a2e46fc
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="and-operator-visual-basic"></a><span data-ttu-id="8ce96-102">Operador And (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8ce96-102">And Operator (Visual Basic)</span></span>
<span data-ttu-id="8ce96-103">Executa uma conjunção lógica em duas `Boolean` expressões ou uma conjunção bit a bit em duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="8ce96-103">Performs a logical conjunction on two `Boolean` expressions, or a bitwise conjunction on two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ce96-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8ce96-104">Syntax</span></span>  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="8ce96-105">Partes</span><span class="sxs-lookup"><span data-stu-id="8ce96-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="8ce96-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8ce96-106">Required.</span></span> <span data-ttu-id="8ce96-107">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="8ce96-107">Any `Boolean` or numeric expression.</span></span> <span data-ttu-id="8ce96-108">Para comparação Boolean, `result` é a conjunção lógica de dois `Boolean` valores.</span><span class="sxs-lookup"><span data-stu-id="8ce96-108">For Boolean comparison, `result` is the logical conjunction of two `Boolean` values.</span></span> <span data-ttu-id="8ce96-109">Para operações bit a bit, `result` é um valor numérico que representa a conjunção bit a bit de dois padrões numéricos de bits.</span><span class="sxs-lookup"><span data-stu-id="8ce96-109">For bitwise operations, `result` is a numeric value representing the bitwise conjunction of two numeric bit patterns.</span></span>  
  
 `expression1`  
 <span data-ttu-id="8ce96-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8ce96-110">Required.</span></span> <span data-ttu-id="8ce96-111">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="8ce96-111">Any `Boolean` or numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="8ce96-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="8ce96-112">Required.</span></span> <span data-ttu-id="8ce96-113">Qualquer `Boolean` ou expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="8ce96-113">Any `Boolean` or numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ce96-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="8ce96-114">Remarks</span></span>  
 <span data-ttu-id="8ce96-115">Para comparação Boolean, `result` é `True` se e somente se ambos os `expression1` e `expression2` são avaliadas como `True`.</span><span class="sxs-lookup"><span data-stu-id="8ce96-115">For Boolean comparison, `result` is `True` if and only if both `expression1` and `expression2` evaluate to `True`.</span></span> <span data-ttu-id="8ce96-116">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="8ce96-116">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="8ce96-117">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="8ce96-117">If `expression1` is</span></span>|<span data-ttu-id="8ce96-118">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="8ce96-118">And `expression2` is</span></span>|<span data-ttu-id="8ce96-119">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="8ce96-119">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
>  <span data-ttu-id="8ce96-120">Em uma comparação Booleana, o `And` operador sempre avalia as duas expressões, que podem incluir chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="8ce96-120">In a Boolean comparison, the `And` operator always evaluates both expressions, which could include making procedure calls.</span></span> <span data-ttu-id="8ce96-121">O [operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) executa *Short-circuiting*, que significa que, se `expression1` é `False`, em seguida, `expression2` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="8ce96-121">The [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) performs *short-circuiting*, which means that if `expression1` is `False`, then `expression2` is not evaluated.</span></span>  
  
 <span data-ttu-id="8ce96-122">Quando aplicado a valores numéricos, o `And` operador executa uma comparação bit a bit de bits posicionados identicamente em duas expressões numéricas e configura o bit no correspondente `result` acordo com a tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="8ce96-122">When applied to numeric values, the `And` operator performs a bitwise comparison of identically positioned bits in two numeric expressions and sets the corresponding bit in `result` according to the following table.</span></span>  
  
|<span data-ttu-id="8ce96-123">Se bit no `expression1` é</span><span class="sxs-lookup"><span data-stu-id="8ce96-123">If bit in `expression1` is</span></span>|<span data-ttu-id="8ce96-124">E o bit na `expression2` é</span><span class="sxs-lookup"><span data-stu-id="8ce96-124">And bit in `expression2` is</span></span>|<span data-ttu-id="8ce96-125">O bit no `result` é</span><span class="sxs-lookup"><span data-stu-id="8ce96-125">The bit in `result` is</span></span>|  
|--------------------------------|---------------------------------|----------------------------|  
|<span data-ttu-id="8ce96-126">1</span><span class="sxs-lookup"><span data-stu-id="8ce96-126">1</span></span>|<span data-ttu-id="8ce96-127">1</span><span class="sxs-lookup"><span data-stu-id="8ce96-127">1</span></span>|<span data-ttu-id="8ce96-128">1</span><span class="sxs-lookup"><span data-stu-id="8ce96-128">1</span></span>|  
|<span data-ttu-id="8ce96-129">1</span><span class="sxs-lookup"><span data-stu-id="8ce96-129">1</span></span>|<span data-ttu-id="8ce96-130">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-130">0</span></span>|<span data-ttu-id="8ce96-131">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-131">0</span></span>|  
|<span data-ttu-id="8ce96-132">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-132">0</span></span>|<span data-ttu-id="8ce96-133">1</span><span class="sxs-lookup"><span data-stu-id="8ce96-133">1</span></span>|<span data-ttu-id="8ce96-134">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-134">0</span></span>|  
|<span data-ttu-id="8ce96-135">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-135">0</span></span>|<span data-ttu-id="8ce96-136">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-136">0</span></span>|<span data-ttu-id="8ce96-137">0</span><span class="sxs-lookup"><span data-stu-id="8ce96-137">0</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="8ce96-138">Como os operadores lógicos e bit a bit possuem uma precedência menor que outros operadores aritméticos e relacionais, quaisquer operações bit a bit devem ser colocadas entre parênteses para garantir resultados precisos.</span><span class="sxs-lookup"><span data-stu-id="8ce96-138">Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate results.</span></span>  
  
## <a name="data-types"></a><span data-ttu-id="8ce96-139">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="8ce96-139">Data Types</span></span>  
 <span data-ttu-id="8ce96-140">Se o operando consiste em uma `Boolean` expressão e uma expressão numérica, o Visual Basic converte o `Boolean` expressão para um valor numérico (-1 para `True` e 0 para `False`) e executa uma operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="8ce96-140">If the operands consist of one `Boolean` expression and one numeric expression, Visual Basic converts the `Boolean` expression to a numeric value (–1 for `True` and 0 for `False`) and performs a bitwise operation.</span></span>  
  
 <span data-ttu-id="8ce96-141">Para comparação Booleana, o tipo de dados do resultado é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="8ce96-141">For a Boolean comparison, the data type of the result is `Boolean`.</span></span> <span data-ttu-id="8ce96-142">Para obter uma comparação bit a bit, o tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="8ce96-142">For a bitwise comparison, the result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="8ce96-143">Consulte a tabela "Comparações relacionais e bit a bit" [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="8ce96-143">See the "Relational and Bitwise Comparisons" table in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ce96-144">O `And` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="8ce96-144">The `And` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8ce96-145">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="8ce96-145">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8ce96-146">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8ce96-146">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ce96-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ce96-147">Example</span></span>  
 <span data-ttu-id="8ce96-148">O exemplo a seguir usa o `And` operador para executar uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="8ce96-148">The following example uses the `And` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="8ce96-149">O resultado é um `Boolean` valor que indica se as duas expressões são `True`.</span><span class="sxs-lookup"><span data-stu-id="8ce96-149">The result is a `Boolean` value that represents whether both of the expressions are `True`.</span></span>  
  
 <span data-ttu-id="8ce96-150">[!code-vb[VbVbalrOperators&#22;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ce96-150">[!code-vb[VbVbalrOperators#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="8ce96-151">O exemplo anterior produz resultados de `True` e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8ce96-151">The preceding example produces results of `True` and `False`, respectively.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ce96-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8ce96-152">Example</span></span>  
 <span data-ttu-id="8ce96-153">O exemplo a seguir usa o `And` operador para executar uma conjunção lógica nos bits individuais de duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="8ce96-153">The following example uses the `And` operator to perform logical conjunction on the individual bits of two numeric expressions.</span></span> <span data-ttu-id="8ce96-154">O bit no padrão resultante é definir se os bits correspondentes nos dois operandos são definidos como 1.</span><span class="sxs-lookup"><span data-stu-id="8ce96-154">The bit in the result pattern is set if the corresponding bits in the operands are both set to 1.</span></span>  
  
 <span data-ttu-id="8ce96-155">[!code-vb[VbVbalrOperators&#23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="8ce96-155">[!code-vb[VbVbalrOperators#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-operator_2.vb)]</span></span>  
  
 <span data-ttu-id="8ce96-156">O exemplo anterior produz resultados 8, 2 e 0, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8ce96-156">The preceding example produces results of 8, 2, and 0, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ce96-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8ce96-157">See Also</span></span>  
 <span data-ttu-id="8ce96-158">[Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="8ce96-158">[Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="8ce96-159"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="8ce96-159"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="8ce96-160"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="8ce96-160"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="8ce96-161"> [Operador AndAlso](../../../visual-basic/language-reference/operators/andalso-operator.md) </span><span class="sxs-lookup"><span data-stu-id="8ce96-161"> [AndAlso Operator](../../../visual-basic/language-reference/operators/andalso-operator.md) </span></span>  
<span data-ttu-id="8ce96-162"> [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="8ce96-162"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>

