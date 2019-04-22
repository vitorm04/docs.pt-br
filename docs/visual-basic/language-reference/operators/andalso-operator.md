---
title: Operador AndAlso (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AndAlso
- AndAlso
helpviewer_keywords:
- short-circuiting
- AndAlso operator [Visual Basic]
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], conjunction
- short-circuit evaluation
ms.assetid: bbc15191-b374-495b-9b8f-7b8c2f4388eb
ms.openlocfilehash: 3876fd9c32d486b8ebecc9ee2428486a687a1624
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817117"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="c95c4-102">Operador AndAlso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c95c4-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="c95c4-103">Executa uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="c95c4-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c95c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c95c4-104">Syntax</span></span>  
  
```  
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="c95c4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="c95c4-105">Parts</span></span>  
  
|<span data-ttu-id="c95c4-106">Termo</span><span class="sxs-lookup"><span data-stu-id="c95c4-106">Term</span></span>|<span data-ttu-id="c95c4-107">Definição</span><span class="sxs-lookup"><span data-stu-id="c95c4-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="c95c4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c95c4-108">Required.</span></span> <span data-ttu-id="c95c4-109">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c95c4-109">Any `Boolean` expression.</span></span> <span data-ttu-id="c95c4-110">O resultado é o `Boolean` resultado da comparação das duas expressões.</span><span class="sxs-lookup"><span data-stu-id="c95c4-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="c95c4-111">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c95c4-111">Required.</span></span> <span data-ttu-id="c95c4-112">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c95c4-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="c95c4-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="c95c4-113">Required.</span></span> <span data-ttu-id="c95c4-114">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="c95c4-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c95c4-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="c95c4-115">Remarks</span></span>  
 <span data-ttu-id="c95c4-116">Uma operação lógica será considerada *Short-circuiting* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado de outra expressão.</span><span class="sxs-lookup"><span data-stu-id="c95c4-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="c95c4-117">Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não é possível alterar o resultado final.</span><span class="sxs-lookup"><span data-stu-id="c95c4-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="c95c4-118">Short-circuiting pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="c95c4-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="c95c4-119">Se ambas as expressões são avaliadas como `True`, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="c95c4-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="c95c4-120">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="c95c4-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="c95c4-121">Se `expression1` é</span><span class="sxs-lookup"><span data-stu-id="c95c4-121">If `expression1` is</span></span>|<span data-ttu-id="c95c4-122">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="c95c4-122">And `expression2` is</span></span>|<span data-ttu-id="c95c4-123">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="c95c4-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="c95c4-124">(não avaliado)</span><span class="sxs-lookup"><span data-stu-id="c95c4-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="c95c4-125">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="c95c4-125">Data Types</span></span>  
 <span data-ttu-id="c95c4-126">O `AndAlso` operador está definido apenas para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="c95c4-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="c95c4-127">Cada operando conforme necessário para o Visual Basic converte `Boolean` e executa a operação completamente em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c95c4-127">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="c95c4-128">Se você atribuir o resultado a um tipo numérico, Visual Basic converte-o de `Boolean` a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="c95c4-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="c95c4-129">Isso pode produzir um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="c95c4-129">This could produce unexpected behavior.</span></span> <span data-ttu-id="c95c4-130">Por exemplo, `5 AndAlso 12` resulta em `–1` quando convertido em `Integer`.</span><span class="sxs-lookup"><span data-stu-id="c95c4-130">For example, `5 AndAlso 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c95c4-131">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="c95c4-131">Overloading</span></span>  
 <span data-ttu-id="c95c4-132">O [operador And](../../../visual-basic/language-reference/operators/and-operator.md) e o [Operador IsFalse](../../../visual-basic/language-reference/operators/isfalse-operator.md) pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo que classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="c95c4-132">The [And Operator](../../../visual-basic/language-reference/operators/and-operator.md) and the [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c95c4-133">Sobrecarregando o `And` e `IsFalse` operadores afeta o comportamento do `AndAlso` operador.</span><span class="sxs-lookup"><span data-stu-id="c95c4-133">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="c95c4-134">Se seu código usa `AndAlso` em uma classe ou estrutura que sobrecarrega `And` e `IsFalse`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="c95c4-134">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="c95c4-135">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c95c4-135">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c95c4-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c95c4-136">Example</span></span>  
 <span data-ttu-id="c95c4-137">O exemplo a seguir usa o `AndAlso` operador para executar uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="c95c4-137">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="c95c4-138">O resultado é um `Boolean` valor que indica se todo o unidas a expressão é true.</span><span class="sxs-lookup"><span data-stu-id="c95c4-138">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="c95c4-139">Se a primeira expressão é `False`, a segunda não será avaliada.</span><span class="sxs-lookup"><span data-stu-id="c95c4-139">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="c95c4-140">O exemplo anterior produz resultados `True`, `False`, e `False`, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c95c4-140">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="c95c4-141">No cálculo da `secondCheck`, a segunda expressão é avaliada não porque a primeira já é `False`.</span><span class="sxs-lookup"><span data-stu-id="c95c4-141">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="c95c4-142">No entanto, a segunda expressão é avaliada no cálculo de `thirdCheck`.</span><span class="sxs-lookup"><span data-stu-id="c95c4-142">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c95c4-143">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c95c4-143">Example</span></span>  
 <span data-ttu-id="c95c4-144">A exemplo a seguir mostra um `Function` procedimento que procura por um determinado valor entre os elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c95c4-144">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="c95c4-145">Se a matriz está vazia ou se o comprimento da matriz foi excedido, o `While` instrução não testa o elemento da matriz com relação ao valor de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="c95c4-145">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="c95c4-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c95c4-146">See also</span></span>

- [<span data-ttu-id="c95c4-147">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c95c4-147">Logical/Bitwise Operators (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [<span data-ttu-id="c95c4-148">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c95c4-148">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="c95c4-149">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="c95c4-149">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="c95c4-150">Operador And</span><span class="sxs-lookup"><span data-stu-id="c95c4-150">And Operator</span></span>](../../../visual-basic/language-reference/operators/and-operator.md)
- [<span data-ttu-id="c95c4-151">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="c95c4-151">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="c95c4-152">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c95c4-152">Logical and Bitwise Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
