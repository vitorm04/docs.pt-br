---
title: Operador OrElse (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- OrElse
- vb.OrElse
dev_langs:
- VB
helpviewer_keywords:
- short-circuiting
- operators [Visual Basic], short-circuiting
- operators [Visual Basic], disjunction
- short-circuit evaluation
- OrElse operator [Visual Basic]
ms.assetid: 253803d8-05b0-47d7-b213-abd222847779
caps.latest.revision: 15
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
ms.openlocfilehash: 53956b1b159a16a18543e2fa09de90d1eb73543f
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="orelse-operator-visual-basic"></a><span data-ttu-id="50121-102">Operador OrElse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="50121-102">OrElse Operator (Visual Basic)</span></span>
<span data-ttu-id="50121-103">Executa a disjunção lógica em duas expressões do curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="50121-103">Performs short-circuiting inclusive logical disjunction on two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50121-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="50121-104">Syntax</span></span>  
  
```  
result = expression1 OrElse expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="50121-105">Partes</span><span class="sxs-lookup"><span data-stu-id="50121-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="50121-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="50121-106">Required.</span></span> <span data-ttu-id="50121-107">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="50121-107">Any `Boolean` expression.</span></span>  
  
 `expression1`  
 <span data-ttu-id="50121-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="50121-108">Required.</span></span> <span data-ttu-id="50121-109">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="50121-109">Any `Boolean` expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="50121-110">Necessário.</span><span class="sxs-lookup"><span data-stu-id="50121-110">Required.</span></span> <span data-ttu-id="50121-111">Qualquer expressão de `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="50121-111">Any `Boolean` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50121-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="50121-112">Remarks</span></span>  
 <span data-ttu-id="50121-113">Uma operação lógica será considerada *Short-circuiting* se o código compilado pode ignorar a avaliação de uma expressão, dependendo do resultado da outra expressão.</span><span class="sxs-lookup"><span data-stu-id="50121-113">A logical operation is said to be *short-circuiting* if the compiled code can bypass the evaluation of one expression depending on the result of another expression.</span></span> <span data-ttu-id="50121-114">Se o resultado da primeira expressão avaliada determina o resultado final da operação, não é necessário para avaliar a segunda expressão, porque ele não pode alterar o resultado final.</span><span class="sxs-lookup"><span data-stu-id="50121-114">If the result of the first expression evaluated determines the final result of the operation, there is no need to evaluate the second expression, because it cannot change the final result.</span></span> <span data-ttu-id="50121-115">Short-circuiting pode melhorar o desempenho se a expressão ignorada é complexa, ou se ela envolve chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="50121-115">Short-circuiting can improve performance if the bypassed expression is complex, or if it involves procedure calls.</span></span>  
  
 <span data-ttu-id="50121-116">Se uma ou ambas as expressões forem avaliados como `True`, `result` é `True`.</span><span class="sxs-lookup"><span data-stu-id="50121-116">If either or both expressions evaluate to `True`, `result` is `True`.</span></span> <span data-ttu-id="50121-117">A tabela a seguir ilustra como `result` é determinado.</span><span class="sxs-lookup"><span data-stu-id="50121-117">The following table illustrates how `result` is determined.</span></span>  
  
|<span data-ttu-id="50121-118">If `expression1` is</span><span class="sxs-lookup"><span data-stu-id="50121-118">If `expression1` is</span></span>|<span data-ttu-id="50121-119">E `expression2` é</span><span class="sxs-lookup"><span data-stu-id="50121-119">And `expression2` is</span></span>|<span data-ttu-id="50121-120">O valor de `result` é</span><span class="sxs-lookup"><span data-stu-id="50121-120">The value of `result` is</span></span>|  
|-------------------------|--------------------------|------------------------------|  
|`True`|<span data-ttu-id="50121-121">(não avaliado)</span><span class="sxs-lookup"><span data-stu-id="50121-121">(not evaluated)</span></span>|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
## <a name="data-types"></a><span data-ttu-id="50121-122">Tipos de Dados</span><span class="sxs-lookup"><span data-stu-id="50121-122">Data Types</span></span>  
 <span data-ttu-id="50121-123">O `OrElse` operador é definido somente para o [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="50121-123">The `OrElse` operator is defined only for the [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md).</span></span> <span data-ttu-id="50121-124">Visual Basic converte cada operando conforme necessário para `Boolean` e executa a operação completamente em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="50121-124">Visual Basic converts each operand as necessary to `Boolean` and performs the operation entirely in `Boolean`.</span></span> <span data-ttu-id="50121-125">Se você atribuir o resultado a um tipo numérico, Visual Basic converte do `Boolean` para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="50121-125">If you assign the result to a numeric type, Visual Basic converts it from `Boolean` to that type.</span></span> <span data-ttu-id="50121-126">Isso pode produzir um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="50121-126">This could produce unexpected behavior.</span></span> <span data-ttu-id="50121-127">Por exemplo, `5 OrElse 12` resulta em `–1` quando convertido em `Integer`.</span><span class="sxs-lookup"><span data-stu-id="50121-127">For example, `5 OrElse 12` results in `–1` when converted to `Integer`.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="50121-128">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="50121-128">Overloading</span></span>  
 <span data-ttu-id="50121-129">O [operador ou](../../../visual-basic/language-reference/operators/or-operator.md) e [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) podem ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="50121-129">The [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) and the [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) can be *overloaded*, which means that a class or structure can redefine their behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="50121-130">Sobrecarga de `Or` e `IsTrue` operadores afeta o comportamento do `OrElse` operador.</span><span class="sxs-lookup"><span data-stu-id="50121-130">Overloading the `Or` and `IsTrue` operators affects the behavior of the `OrElse` operator.</span></span> <span data-ttu-id="50121-131">Se seu código usa `OrElse` em uma classe ou estrutura que sobrecarrega `Or` e `IsTrue`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="50121-131">If your code uses `OrElse` on a class or structure that overloads `Or` and `IsTrue`, be sure you understand their redefined behavior.</span></span> <span data-ttu-id="50121-132">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="50121-132">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50121-133">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50121-133">Example</span></span>  
 <span data-ttu-id="50121-134">O exemplo a seguir usa o `OrElse` operador para executar uma disjunção lógica em duas expressões.</span><span class="sxs-lookup"><span data-stu-id="50121-134">The following example uses the `OrElse` operator to perform logical disjunction on two expressions.</span></span> <span data-ttu-id="50121-135">O resultado é um `Boolean` valor que representa se uma das duas expressões são verdadeiras.</span><span class="sxs-lookup"><span data-stu-id="50121-135">The result is a `Boolean` value that represents whether either of the two expressions is true.</span></span> <span data-ttu-id="50121-136">Se a primeira expressão for `True`, a segunda não será avaliada.</span><span class="sxs-lookup"><span data-stu-id="50121-136">If the first expression is `True`, the second is not evaluated.</span></span>  
  
 <span data-ttu-id="50121-137">[!code-vb[VbVbalrOperators&#37;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="50121-137">[!code-vb[VbVbalrOperators#37](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="50121-138">O exemplo anterior produz resultados de `True`, `True`, e `False` respectivamente.</span><span class="sxs-lookup"><span data-stu-id="50121-138">The preceding example produces results of `True`, `True`, and `False` respectively.</span></span> <span data-ttu-id="50121-139">No cálculo de `firstCheck`, a segunda expressão é avaliada não porque a primeira já é `True`.</span><span class="sxs-lookup"><span data-stu-id="50121-139">In the calculation of `firstCheck`, the second expression is not evaluated because the first is already `True`.</span></span> <span data-ttu-id="50121-140">No entanto, a segunda expressão é avaliada no cálculo de `secondCheck`.</span><span class="sxs-lookup"><span data-stu-id="50121-140">However, the second expression is evaluated in the calculation of `secondCheck`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50121-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50121-141">Example</span></span>  
 <span data-ttu-id="50121-142">A exemplo a seguir mostra um `If`... `Then` instrução contendo duas chamadas de procedimento.</span><span class="sxs-lookup"><span data-stu-id="50121-142">The following example shows an `If`...`Then` statement containing two procedure calls.</span></span> <span data-ttu-id="50121-143">Se a primeira chamada retornar `True`, o segundo procedimento não é chamado.</span><span class="sxs-lookup"><span data-stu-id="50121-143">If the first call returns `True`, the second procedure is not called.</span></span> <span data-ttu-id="50121-144">Isso pode produzir resultados inesperados se o segundo procedimento executa tarefas importantes que sempre devem ser executadas quando esta seção do código é executado.</span><span class="sxs-lookup"><span data-stu-id="50121-144">This could produce unexpected results if the second procedure performs important tasks that should always be performed when this section of the code runs.</span></span>  
  
 <span data-ttu-id="50121-145">[!code-vb[VbVbalrOperators&38;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="50121-145">[!code-vb[VbVbalrOperators#38](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/orelse-operator_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50121-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50121-146">See Also</span></span>  
 <span data-ttu-id="50121-147">[Operadores lógicos/bit a bit (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span><span class="sxs-lookup"><span data-stu-id="50121-147">[Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md) </span></span>  
<span data-ttu-id="50121-148"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="50121-148"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="50121-149"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="50121-149"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="50121-150"> [Operador or](../../../visual-basic/language-reference/operators/or-operator.md) </span><span class="sxs-lookup"><span data-stu-id="50121-150"> [Or Operator](../../../visual-basic/language-reference/operators/or-operator.md) </span></span>  
<span data-ttu-id="50121-151"> [Operador IsTrue](../../../visual-basic/language-reference/operators/istrue-operator.md) </span><span class="sxs-lookup"><span data-stu-id="50121-151"> [IsTrue Operator](../../../visual-basic/language-reference/operators/istrue-operator.md) </span></span>  
<span data-ttu-id="50121-152"> [Operadores lógicos e bit a bit no Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="50121-152"> [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>

