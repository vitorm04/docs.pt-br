---
title: Operador AndAlso
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
ms.openlocfilehash: 8b67897956a21d06d465cf206856354d2e3f9d68
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371928"
---
# <a name="andalso-operator-visual-basic"></a><span data-ttu-id="aa471-102">Operador AndAlso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa471-102">AndAlso Operator (Visual Basic)</span></span>
<span data-ttu-id="aa471-103">Executa uma conjunção lógica de curto-circuito em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="aa471-103">Performs short-circuiting logical conjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa471-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aa471-104">Syntax</span></span>  
  
```vb
result = expression1 AndAlso expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="aa471-105">Partes</span><span class="sxs-lookup"><span data-stu-id="aa471-105">Parts</span></span>  
  
|<span data-ttu-id="aa471-106">Termo</span><span class="sxs-lookup"><span data-stu-id="aa471-106">Term</span></span>|<span data-ttu-id="aa471-107">Definição</span><span class="sxs-lookup"><span data-stu-id="aa471-107">Definition</span></span>|  
|---|---|  
|`result`|<span data-ttu-id="aa471-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="aa471-108">Required.</span></span> <span data-ttu-id="aa471-109">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="aa471-109">Any `Boolean` expression.</span></span> <span data-ttu-id="aa471-110">O resultado é o `Boolean` resultado da comparação entre as duas expressões.</span><span class="sxs-lookup"><span data-stu-id="aa471-110">The result is the `Boolean` result of comparison of the two expressions.</span></span>|  
|`expression1`|<span data-ttu-id="aa471-111">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="aa471-111">Required.</span></span> <span data-ttu-id="aa471-112">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="aa471-112">Any `Boolean` expression.</span></span>|  
|`expression2`|<span data-ttu-id="aa471-113">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="aa471-113">Required.</span></span> <span data-ttu-id="aa471-114">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="aa471-114">Any `Boolean` expression.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa471-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="aa471-115">Remarks</span></span>  
 <span data-ttu-id="aa471-116">Uma operação lógica é chamada de *curto-circuito* se o código compilado puder ignorar a avaliação de uma expressão, dependendo do resultado de outra expressão.</span><span class="sxs-lookup"><span data-stu-id="aa471-116">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="aa471-117">Se o resultado da primeira expressão avaliada determinar o resultado final da operação, não será necessário avaliar a segunda expressão, pois ela não pode alterar o resultado final.</span><span class="sxs-lookup"><span data-stu-id="aa471-117">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="aa471-118">O curto circuito pode melhorar o desempenho se a expressão ignorada for complexa ou se envolver chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="aa471-118">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="aa471-119">Se as duas expressões forem avaliadas como `True` , `result` será `True` .</span><span class="sxs-lookup"><span data-stu-id="aa471-119">If both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="aa471-120">A tabela a seguir ilustra como o `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="aa471-120">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="aa471-121">Se `expression1` for </span><span class="sxs-lookup"><span data-stu-id="aa471-121">If `expression1` is</span></span>|<span data-ttu-id="aa471-122">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="aa471-122">And `expression2` is</span></span>|<span data-ttu-id="aa471-123">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="aa471-123">The value of `result` is</span></span>|  
|---|---|---|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|<span data-ttu-id="aa471-124">(não avaliado)</span><span class="sxs-lookup"><span data-stu-id="aa471-124">(not evaluated)</span></span>|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="aa471-125">Tipos de dados</span><span class="sxs-lookup"><span data-stu-id="aa471-125">Data Types</span></span>  
 <span data-ttu-id="aa471-126">O `AndAlso` operador é definido somente para o [tipo de dados booliano](../data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="aa471-126">The `AndAlso` operator is defined only for the [Boolean Data Type](../data-types/boolean-data-type.md).</span></span> <span data-ttu-id="aa471-127">Visual Basic converte cada operando conforme necessário `Boolean` antes de avaliar a expressão.</span><span class="sxs-lookup"><span data-stu-id="aa471-127">Visual Basic converts each operand as necessary to `Boolean` before evaluating the expression.</span></span> <span data-ttu-id="aa471-128">Se você atribuir o resultado a um tipo numérico, Visual Basic o converterá de `Boolean` para esse tipo, isso `False` se tornará `0` e `True` se tornará `-1` .</span><span class="sxs-lookup"><span data-stu-id="aa471-128">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type such that `False` becomes `0` and `True` becomes `-1`.</span></span>
<span data-ttu-id="aa471-129">Para obter mais informações, consulte [conversões de tipo booliano](../data-types/boolean-data-type.md#type-conversions).</span><span class="sxs-lookup"><span data-stu-id="aa471-129">For more information, see [Boolean Type Conversions](../data-types/boolean-data-type.md#type-conversions).</span></span>
  
## <a name="overloading"></a><span data-ttu-id="aa471-130">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="aa471-130">Overloading</span></span>  
 <span data-ttu-id="aa471-131">O [operador and](and-operator.md) e o [Operador IsFalse](isfalse-operator.md) podem ser *sobrecarregados*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="aa471-131">The [And Operator](and-operator.md) and the [IsFalse Operator](isfalse-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="aa471-132">Sobrecarregar os `And` operadores e `IsFalse` afeta o comportamento do `AndAlso` operador.</span><span class="sxs-lookup"><span data-stu-id="aa471-132">Overloading the `And` and `IsFalse` operators affects the behavior of the `AndAlso` operator.</span></span> <span data-ttu-id="aa471-133">Se o seu código usa `AndAlso` em uma classe ou estrutura que sobrecarrega `And` e, certifique-se de `IsFalse` entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="aa471-133">If your code uses `AndAlso` on a class or structure that overloads `And` and `IsFalse`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="aa471-134">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="aa471-134">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa471-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa471-135">Example</span></span>  
 <span data-ttu-id="aa471-136">O exemplo a seguir usa o `AndAlso` operador para executar uma conjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="aa471-136">The following example uses the `AndAlso` operator to perform a logical conjunction on two expressions.</span></span> <span data-ttu-id="aa471-137">O resultado é um `Boolean` valor que representa se a expressão conjunta inteira é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="aa471-137">The result is a `Boolean` value that represents whether the entire conjoined expression is true.</span></span> <span data-ttu-id="aa471-138">Se a primeira expressão for `False` , a segunda não será avaliada.</span><span class="sxs-lookup"><span data-stu-id="aa471-138">If the first expression is `False`, the second is not evaluated.</span></span>  
  
 [!code-vb[VbVbalrOperators#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#24)]  
  
 <span data-ttu-id="aa471-139">O exemplo anterior produz resultados de `True` , `False` , e `False` , respectivamente.</span><span class="sxs-lookup"><span data-stu-id="aa471-139">The preceding example produces results of `True`, `False`, and `False`, respectively.</span></span> <span data-ttu-id="aa471-140">No cálculo de `secondCheck` , a segunda expressão não é avaliada porque a primeira já é `False` .</span><span class="sxs-lookup"><span data-stu-id="aa471-140">In the calculation of `secondCheck`, the second expression is not evaluated because the first is already `False`.</span></span> <span data-ttu-id="aa471-141">No entanto, a segunda expressão é avaliada no cálculo de `thirdCheck` .</span><span class="sxs-lookup"><span data-stu-id="aa471-141">However, the second expression is evaluated in the calculation of `thirdCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa471-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa471-142">Example</span></span>  
 <span data-ttu-id="aa471-143">O exemplo a seguir mostra um `Function` procedimento que pesquisa um determinado valor entre os elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="aa471-143">The following example shows a `Function` procedure that searches for a given value among the elements of an array.</span></span> <span data-ttu-id="aa471-144">Se a matriz estiver vazia ou se o comprimento da matriz tiver sido excedido, a `While` instrução não testará o elemento de matriz em relação ao valor de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="aa471-144">If the array is empty, or if the array length has been exceeded, the `While` statement does not test the array element against the search value.</span></span>  
  
 [!code-vb[VbVbalrOperators#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#25)]  
  
## <a name="see-also"></a><span data-ttu-id="aa471-145">Confira também</span><span class="sxs-lookup"><span data-stu-id="aa471-145">See also</span></span>

- [<span data-ttu-id="aa471-146">Operadores lógicos/bit a bit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa471-146">Logical/Bitwise Operators (Visual Basic)</span></span>](logical-bitwise-operators.md)
- [<span data-ttu-id="aa471-147">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa471-147">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="aa471-148">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="aa471-148">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="aa471-149">Operador And</span><span class="sxs-lookup"><span data-stu-id="aa471-149">And Operator</span></span>](and-operator.md)
- [<span data-ttu-id="aa471-150">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="aa471-150">IsFalse Operator</span></span>](isfalse-operator.md)
- [<span data-ttu-id="aa471-151">Operadores lógicos e bit a bit no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa471-151">Logical and Bitwise Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
