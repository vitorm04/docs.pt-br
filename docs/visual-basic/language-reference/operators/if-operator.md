---
title: Se o operador (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.IfOperator
- IfOperator
dev_langs:
- VB
helpviewer_keywords:
- ternary operators
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
caps.latest.revision: 19
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e27485785fadc2de50a4387daba7a86bb69433a4
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="if-operator-visual-basic"></a><span data-ttu-id="597cc-102">Operador If (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="597cc-102">If Operator (Visual Basic)</span></span>
<span data-ttu-id="597cc-103">Usos de curto-circuito avaliação para retornar um de dois valores condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="597cc-103">Uses short-circuit evaluation to conditionally return one of two values.</span></span> <span data-ttu-id="597cc-104">O `If` operador pode ser chamado com três argumentos ou com dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="597cc-104">The `If` operator can be called with three arguments or with two arguments.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597cc-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="597cc-105">Syntax</span></span>  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a><span data-ttu-id="597cc-106">Se o operador chamado com três argumentos</span><span class="sxs-lookup"><span data-stu-id="597cc-106">If Operator Called with Three Arguments</span></span>  
 <span data-ttu-id="597cc-107">Quando `If` é chamado usando três argumentos, o primeiro argumento deve ser avaliada como um valor que pode ser convertido como um `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="597cc-107">When `If` is called by using three arguments, the first argument must evaluate to a value that can be cast as a `Boolean`.</span></span> <span data-ttu-id="597cc-108">Que `Boolean` valor determinará qual dos outros dois argumentos é avaliado e retornado.</span><span class="sxs-lookup"><span data-stu-id="597cc-108">That `Boolean` value will determine which of the other two arguments is evaluated and returned.</span></span> <span data-ttu-id="597cc-109">A lista a seguir se aplica somente quando o `If` é chamado de operador usando três argumentos.</span><span class="sxs-lookup"><span data-stu-id="597cc-109">The following list applies only when the `If` operator is called by using three arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="597cc-110">Partes</span><span class="sxs-lookup"><span data-stu-id="597cc-110">Parts</span></span>  
  
|<span data-ttu-id="597cc-111">Termo</span><span class="sxs-lookup"><span data-stu-id="597cc-111">Term</span></span>|<span data-ttu-id="597cc-112">Definição</span><span class="sxs-lookup"><span data-stu-id="597cc-112">Definition</span></span>|  
|---|---|  
|`argument1`|<span data-ttu-id="597cc-113">Necessário.</span><span class="sxs-lookup"><span data-stu-id="597cc-113">Required.</span></span> <span data-ttu-id="597cc-114">`Boolean`.</span><span class="sxs-lookup"><span data-stu-id="597cc-114">`Boolean`.</span></span> <span data-ttu-id="597cc-115">Determina qual dos outros argumentos para avaliar e retornar.</span><span class="sxs-lookup"><span data-stu-id="597cc-115">Determines which of the other arguments to evaluate and return.</span></span>|  
|`argument2`|<span data-ttu-id="597cc-116">Necessário.</span><span class="sxs-lookup"><span data-stu-id="597cc-116">Required.</span></span> <span data-ttu-id="597cc-117">`Object`.</span><span class="sxs-lookup"><span data-stu-id="597cc-117">`Object`.</span></span> <span data-ttu-id="597cc-118">Avaliado e retornado se `argument1` é avaliada como `True`.</span><span class="sxs-lookup"><span data-stu-id="597cc-118">Evaluated and returned if `argument1` evaluates to `True`.</span></span>|  
|`argument3`|<span data-ttu-id="597cc-119">Necessário.</span><span class="sxs-lookup"><span data-stu-id="597cc-119">Required.</span></span> <span data-ttu-id="597cc-120">`Object`.</span><span class="sxs-lookup"><span data-stu-id="597cc-120">`Object`.</span></span> <span data-ttu-id="597cc-121">Avaliado e retornado se `argument1` é avaliada como `False` ou se `argument1` é um [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` variável que é avaliada como [nada](../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="597cc-121">Evaluated and returned if `argument1` evaluates to `False` or if `argument1` is a [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` variable that evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md).</span></span>|  
  
 <span data-ttu-id="597cc-122">Um `If` operador que é chamado com três argumentos funciona como um `IIf` função exceto que ele usa curto-circuito avaliação.</span><span class="sxs-lookup"><span data-stu-id="597cc-122">An `If` operator that is called with three arguments works like an `IIf` function except that it uses short-circuit evaluation.</span></span> <span data-ttu-id="597cc-123">Um `IIf` função sempre avalia todos os três argumentos, enquanto um `If` operador que possui três argumentos é avaliada somente dois deles.</span><span class="sxs-lookup"><span data-stu-id="597cc-123">An `IIf` function always evaluates all three of its arguments, whereas an `If` operator that has three arguments evaluates only two of them.</span></span> <span data-ttu-id="597cc-124">A primeira `If` argumento é avaliado e o resultado é convertido como um `Boolean` valor, `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="597cc-124">The first `If` argument is evaluated and the result is cast as a `Boolean` value, `True` or `False`.</span></span> <span data-ttu-id="597cc-125">Se o valor for `True`, `argument2` é avaliada e seu valor é retornado, mas `argument3` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="597cc-125">If the value is `True`, `argument2` is evaluated and its value is returned, but `argument3` is not evaluated.</span></span> <span data-ttu-id="597cc-126">Se o valor da `Boolean` expressão é `False`, `argument3` é avaliada e seu valor é retornado, mas `argument2` não será avaliado.</span><span class="sxs-lookup"><span data-stu-id="597cc-126">If the value of the `Boolean` expression is `False`, `argument3` is evaluated and its value is returned, but `argument2` is not evaluated.</span></span> <span data-ttu-id="597cc-127">Os exemplos a seguir ilustram o uso de `If` quando são usados três argumentos:</span><span class="sxs-lookup"><span data-stu-id="597cc-127">The following examples illustrate the use of `If` when three arguments are used:</span></span>  
  
 <span data-ttu-id="597cc-128">[!code-vb[VbVbalrOperators&#100;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="597cc-128">[!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="597cc-129">O exemplo a seguir ilustra o valor de avaliação de curto-circuito.</span><span class="sxs-lookup"><span data-stu-id="597cc-129">The following example illustrates the value of short-circuit evaluation.</span></span> <span data-ttu-id="597cc-130">O exemplo mostra duas tentativas de dividir variável `number` pela variável `divisor` exceto quando `divisor` é zero.</span><span class="sxs-lookup"><span data-stu-id="597cc-130">The example shows two attempts to divide variable `number` by variable `divisor` except when `divisor` is zero.</span></span> <span data-ttu-id="597cc-131">Nesse caso, um 0 deve ser retornado, e deve ser feita nenhuma tentativa de executar a divisão porque resultaria um erro de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="597cc-131">In that case, a 0 should be returned, and no attempt should be made to perform the division because a run-time error would result.</span></span> <span data-ttu-id="597cc-132">Porque o `If` avaliação de curto-circuito do uso de expressões, ele avalia o segundo ou terceiro argumento, dependendo do valor do primeiro argumento.</span><span class="sxs-lookup"><span data-stu-id="597cc-132">Because the `If` expression uses short-circuit evaluation, it evaluates either the second or the third argument, depending on the value of the first argument.</span></span> <span data-ttu-id="597cc-133">Se o primeiro argumento for true, o divisor não for zero e é seguro avaliar o segundo argumento e realizar a divisão.</span><span class="sxs-lookup"><span data-stu-id="597cc-133">If the first argument is true, the divisor is not zero and it is safe to evaluate the second argument and perform the division.</span></span> <span data-ttu-id="597cc-134">Se o primeiro argumento for false, somente o terceiro argumento é avaliado e 0 é retornado.</span><span class="sxs-lookup"><span data-stu-id="597cc-134">If the first argument is false, only the third argument is evaluated and a 0 is returned.</span></span> <span data-ttu-id="597cc-135">Portanto, quando o divisor for 0, nenhuma tentativa é feita para realizar a divisão e nenhum resultado de erro.</span><span class="sxs-lookup"><span data-stu-id="597cc-135">Therefore, when the divisor is 0, no attempt is made to perform the division and no error results.</span></span> <span data-ttu-id="597cc-136">No entanto, porque `IIf` não usa avaliação de curto-circuito, o segundo argumento é avaliado, mesmo quando o primeiro argumento é false.</span><span class="sxs-lookup"><span data-stu-id="597cc-136">However, because `IIf` does not use short-circuit evaluation, the second argument is evaluated even when the first argument is false.</span></span> <span data-ttu-id="597cc-137">Isso causará um erro de divisão por zero tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="597cc-137">This causes a run-time divide-by-zero error.</span></span>  
  
 <span data-ttu-id="597cc-138">[!code-vb[VbVbalrOperators&#101;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="597cc-138">[!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]</span></span>  
  
## <a name="if-operator-called-with-two-arguments"></a><span data-ttu-id="597cc-139">Se o operador chamado com dois argumentos</span><span class="sxs-lookup"><span data-stu-id="597cc-139">If Operator Called with Two Arguments</span></span>  
 <span data-ttu-id="597cc-140">O primeiro argumento para `If` pode ser omitido.</span><span class="sxs-lookup"><span data-stu-id="597cc-140">The first argument to `If` can be omitted.</span></span> <span data-ttu-id="597cc-141">Isso permite que o operador a ser chamado usando apenas dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="597cc-141">This enables the operator to be called by using only two arguments.</span></span> <span data-ttu-id="597cc-142">A lista a seguir se aplica somente quando o `If` operador é chamado com dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="597cc-142">The following list applies only when the `If` operator is called with two arguments.</span></span>  
  
## <a name="parts"></a><span data-ttu-id="597cc-143">Partes</span><span class="sxs-lookup"><span data-stu-id="597cc-143">Parts</span></span>  
  
|<span data-ttu-id="597cc-144">Termo</span><span class="sxs-lookup"><span data-stu-id="597cc-144">Term</span></span>|<span data-ttu-id="597cc-145">Definição</span><span class="sxs-lookup"><span data-stu-id="597cc-145">Definition</span></span>|  
|---|---|  
|`argument2`|<span data-ttu-id="597cc-146">Necessário.</span><span class="sxs-lookup"><span data-stu-id="597cc-146">Required.</span></span> <span data-ttu-id="597cc-147">`Object`.</span><span class="sxs-lookup"><span data-stu-id="597cc-147">`Object`.</span></span> <span data-ttu-id="597cc-148">Deve ser uma referência ou um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="597cc-148">Must be a reference or nullable type.</span></span> <span data-ttu-id="597cc-149">Avaliado e retornado quando ele for avaliado como algo diferente de `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="597cc-149">Evaluated and returned when it evaluates to anything other than `Nothing`.</span></span>|  
|`argument3`|<span data-ttu-id="597cc-150">Necessário.</span><span class="sxs-lookup"><span data-stu-id="597cc-150">Required.</span></span> <span data-ttu-id="597cc-151">`Object`.</span><span class="sxs-lookup"><span data-stu-id="597cc-151">`Object`.</span></span> <span data-ttu-id="597cc-152">Avaliado e retornado se `argument2` é avaliada como `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="597cc-152">Evaluated and returned if `argument2` evaluates to `Nothing`.</span></span>|  
  
 <span data-ttu-id="597cc-153">Quando o `Boolean` argumento for omitido, o primeiro argumento deve ser uma referência ou um tipo anulável.</span><span class="sxs-lookup"><span data-stu-id="597cc-153">When the `Boolean` argument is omitted, the first argument must be a reference or nullable type.</span></span> <span data-ttu-id="597cc-154">Se o primeiro argumento for avaliado como `Nothing`, o valor do segundo argumento é retornado.</span><span class="sxs-lookup"><span data-stu-id="597cc-154">If the first argument evaluates to `Nothing`, the value of the second argument is returned.</span></span> <span data-ttu-id="597cc-155">Em outros casos, o valor do primeiro argumento será retornado.</span><span class="sxs-lookup"><span data-stu-id="597cc-155">In all other cases, the value of the first argument is returned.</span></span> <span data-ttu-id="597cc-156">O exemplo a seguir ilustra como funciona essa avaliação.</span><span class="sxs-lookup"><span data-stu-id="597cc-156">The following example illustrates how this evaluation works.</span></span>  
  
 <span data-ttu-id="597cc-157">[!code-vb[VbVbalrOperators&#102;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="597cc-157">[!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597cc-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="597cc-158">See Also</span></span>  
 <span data-ttu-id="597cc-159"><xref:Microsoft.VisualBasic.Interaction.IIf%2A></xref:Microsoft.VisualBasic.Interaction.IIf%2A></span><span class="sxs-lookup"><span data-stu-id="597cc-159"><xref:Microsoft.VisualBasic.Interaction.IIf%2A></span></span>   
<span data-ttu-id="597cc-160"> [Tipos de valor anulável](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="597cc-160"> [Nullable Value Types](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="597cc-161"> [Nothing](../../../visual-basic/language-reference/nothing.md)</span><span class="sxs-lookup"><span data-stu-id="597cc-161"> [Nothing](../../../visual-basic/language-reference/nothing.md)</span></span>
