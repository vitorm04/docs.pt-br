---
title: Operador OrElse (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- OrElse
- vb.OrElse
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
ms.openlocfilehash: 02be78c8f2b7529f1fb0e46e9fe610a3c66b0652
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67860136"
---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="0f2f7-102">Operador OrElse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f2f7-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="0f2f7-103">Executa uma disjunção lógica inclusiva em duas expressões de curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f2f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f2f7-104">Syntax</span></span>  
  
```vb
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="0f2f7-105">Partes</span><span class="sxs-lookup"><span data-stu-id="0f2f7-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0f2f7-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-106">Required.</span></span> <span data-ttu-id="0f2f7-107">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0f2f7-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="0f2f7-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-108">Required.</span></span> <span data-ttu-id="0f2f7-109">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0f2f7-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0f2f7-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-110">Required.</span></span> <span data-ttu-id="0f2f7-111">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="0f2f7-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f2f7-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f2f7-112">Remarks</span></span>  
 <span data-ttu-id="0f2f7-113">Uma operação lógica será considerada *Short-circuiting* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado de outra expressão.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="0f2f7-114">Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não é possível alterar o resultado final.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="0f2f7-115">Short-circuiting pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="0f2f7-116">Se uma ou ambas as expressões são avaliadas como `True`, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="0f2f7-117">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="0f2f7-118">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="0f2f7-118">If `expression1` is</span></span>|<span data-ttu-id="0f2f7-119">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="0f2f7-119">And `expression2` is</span></span>|<span data-ttu-id="0f2f7-120">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="0f2f7-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="0f2f7-121">(não avaliado)</span><span class="sxs-lookup"><span data-stu-id="0f2f7-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="0f2f7-122">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="0f2f7-122">Data Types</span></span>  
 <span data-ttu-id="0f2f7-123">O `OrElse` operador está definido apenas para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="0f2f7-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="0f2f7-124">Visual Basic converte cada operando conforme necessário para `Boolean` antes de avaliar a expressão.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-124">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="0f2f7-125">Se você atribuir o resultado a um tipo numérico, Visual Basic converte-o de `Boolean` a esse tipo, de modo que `False` se torna `0` e `True` se torna `-1`.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="0f2f7-126">Para obter mais informações, consulte [conversões de tipo booliano](../data-types/boolean-data-type.md#type-conversions)</span><span class="sxs-lookup"><span data-stu-id="0f2f7-126">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions)</span></span>
  
## <a name="overloading"></a><span data-ttu-id="0f2f7-127">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="0f2f7-127">Overloading</span></span>  
 <span data-ttu-id="0f2f7-128">O [ou operador](../../../visual-basic/language-reference/operators/or-operator.md) e o [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-128">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0f2f7-129">Sobrecarregando o `Or` e `IsTrue` operadores afeta o comportamento do `OrElse` operador.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-129">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="0f2f7-130">Se seu código usa `OrElse` em uma classe ou estrutura que sobrecarrega `Or` e `IsTrue`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-130">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="0f2f7-131">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0f2f7-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f2f7-132">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f2f7-132">Example</span></span>  
 <span data-ttu-id="0f2f7-133">O exemplo a seguir usa o `OrElse` operador para executar uma disjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-133">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="0f2f7-134">O resultado é um `Boolean` valor que representa se uma das duas expressões são true.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-134">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="0f2f7-135">Se a primeira expressão é `True`, a segunda não será avaliada.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-135">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#37)]  
  
 <span data-ttu-id="0f2f7-136">O exemplo anterior produz resultados `True`, `True`, e `False` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-136">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="0f2f7-137">No cálculo da `firstCheck`, a segunda expressão é avaliada não porque a primeira já é `True`.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-137">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="0f2f7-138">No entanto, a segunda expressão é avaliada no cálculo de `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-138">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f2f7-139">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f2f7-139">Example</span></span>  
 <span data-ttu-id="0f2f7-140">A exemplo a seguir mostra um `If`... `Then` instrução que contém duas chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-140">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="0f2f7-141">Se a primeira chamada retorna `True`, o segundo procedimento não é chamado.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-141">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="0f2f7-142">Isso pode produzir resultados inesperados se o segundo procedimento executa tarefas importantes que sempre devem ser executadas quando essa seção do código é executado.</span><span class="sxs-lookup"><span data-stu-id="0f2f7-142">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 [!code-vb[VbVbalrOperators#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#38)]  
  
## <a name="see-also"></a><span data-ttu-id="0f2f7-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f2f7-143">See also</span></span>

- [<span data-ttu-id="0f2f7-144">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f2f7-144">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="0f2f7-145">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f2f7-145">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0f2f7-146">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="0f2f7-146">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0f2f7-147">Operador Or</span><span class="sxs-lookup"><span data-stu-id="0f2f7-147">Or Operator</span></span>](../../../visual-basic/language-reference/operators/or-operator.md)
- [<span data-ttu-id="0f2f7-148">Operador IsTrue</span><span class="sxs-lookup"><span data-stu-id="0f2f7-148">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="0f2f7-149">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f2f7-149">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
