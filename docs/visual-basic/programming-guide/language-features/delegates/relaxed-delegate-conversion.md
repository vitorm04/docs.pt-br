---
title: "Conversão de delegado (Visual Basic) reduzida | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions, relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
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
ms.openlocfilehash: 016c808145f7faba26a288cd5075f10d7f5279d5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="a8769-102">Conversão de delegado reduzida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a8769-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="a8769-103">Conversão de delegado reduzida permite que você atribua sub-rotinas e funções a delegados ou manipuladores mesmo quando as assinaturas não são idênticas.</span><span class="sxs-lookup"><span data-stu-id="a8769-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="a8769-104">Portanto, a ligação a delegados fica consistente com a associação já permitida para invocações de método.</span><span class="sxs-lookup"><span data-stu-id="a8769-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="a8769-105">Parâmetros e tipo de retorno</span><span class="sxs-lookup"><span data-stu-id="a8769-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="a8769-106">Em vez de correspondência exata de assinatura, a conversão reduzida requer que as seguintes condições ser atendidas quando `Option Strict` é definido como `On`:</span><span class="sxs-lookup"><span data-stu-id="a8769-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="a8769-107">Uma conversão de ampliação deve existir do tipo de dados de cada parâmetro delegado para o tipo de dados do parâmetro correspondente da função atribuída ou `Sub`.</span><span class="sxs-lookup"><span data-stu-id="a8769-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="a8769-108">No exemplo a seguir, o delegado `Del1` tem um parâmetro, um `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a8769-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="a8769-109">Parâmetro `m` lambda atribuídas expressões devem ter um tipo de dados para o qual há uma conversão de ampliação de `Integer`, como `Long` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="a8769-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     <span data-ttu-id="a8769-110">[!code-vb[VbVbalrRelaxedDelegates n º&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-110">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
     <span data-ttu-id="a8769-111">[!code-vb[VbVbalrRelaxedDelegates n º&2;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-111">[!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]</span></span>  
  
     <span data-ttu-id="a8769-112">Conversões de restrição são permitidas somente quando `Option Strict` é definido como `Off`.</span><span class="sxs-lookup"><span data-stu-id="a8769-112">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     <span data-ttu-id="a8769-113">[!code-vb[VbVbalrRelaxedDelegates n º&8;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-113">[!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]</span></span>  
  
-   <span data-ttu-id="a8769-114">Uma conversão de ampliação deve existir na direção oposta do tipo de retorno da função atribuída ou `Sub` para o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="a8769-114">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="a8769-115">Nos exemplos a seguir, o corpo de cada expressão lambda atribuída deve ser avaliada como um tipo de dados que amplia a `Integer` porque o tipo de retorno de `del1` é `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a8769-115">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     <span data-ttu-id="a8769-116">[!code-vb[VbVbalrRelaxedDelegates n º&3;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-116">[!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]</span></span>  
  
 <span data-ttu-id="a8769-117">Se `Option Strict` é definido como `Off`, a restrição de ampliação será removida em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="a8769-117">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 <span data-ttu-id="a8769-118">[!code-vb[VbVbalrRelaxedDelegates n º&4;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-118">[!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]</span></span>  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="a8769-119">Omitindo especificações de parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8769-119">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="a8769-120">Delegados relaxados também permitem que você omita completamente especificações de parâmetro no método atribuído:</span><span class="sxs-lookup"><span data-stu-id="a8769-120">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 <span data-ttu-id="a8769-121">[!code-vb[VbVbalrRelaxedDelegates n º&5;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-121">[!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]</span></span>  
  
 <span data-ttu-id="a8769-122">[!code-vb[VbVbalrRelaxedDelegates n º&6;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-122">[!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]</span></span>  
  
 <span data-ttu-id="a8769-123">Observe que não é possível especificar alguns parâmetros e omitir outros.</span><span class="sxs-lookup"><span data-stu-id="a8769-123">Note that you cannot specify some parameters and omit others.</span></span>  
  
 <span data-ttu-id="a8769-124">[!code-vb[VbVbalrRelaxedDelegates&#15;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-124">[!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]</span></span>  
  
 <span data-ttu-id="a8769-125">A capacidade para omitir os parâmetros é útil em uma situação como definir um manipulador de eventos, onde vários parâmetros complexos estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="a8769-125">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="a8769-126">Os argumentos para alguns manipuladores de eventos não são usados.</span><span class="sxs-lookup"><span data-stu-id="a8769-126">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="a8769-127">Em vez disso, o manipulador acessa diretamente o estado do controle no qual o evento está registrado e ignora os argumentos.</span><span class="sxs-lookup"><span data-stu-id="a8769-127">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="a8769-128">Delegados relaxados permitem que você omita os argumentos em tais declarações quando não há ambiguidades nos resultados.</span><span class="sxs-lookup"><span data-stu-id="a8769-128">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="a8769-129">No exemplo a seguir, o método totalmente especificado `OnClick` pode ser reescrito como `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="a8769-129">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="a8769-130">Exemplos de AddressOf</span><span class="sxs-lookup"><span data-stu-id="a8769-130">AddressOf Examples</span></span>  
 <span data-ttu-id="a8769-131">Expressões lambda são usadas nos exemplos anteriores para facilitar ver os relacionamentos de tipo.</span><span class="sxs-lookup"><span data-stu-id="a8769-131">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="a8769-132">No entanto, as mesmas reduções são permitidas para atribuições de delegado que usam `AddressOf`, `Handles`, ou `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="a8769-132">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="a8769-133">No exemplo a seguir, as funções `f1`, `f2`, `f3`, e `f4` podem ser atribuídos a `Del1`.</span><span class="sxs-lookup"><span data-stu-id="a8769-133">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 <span data-ttu-id="a8769-134">[!code-vb[VbVbalrRelaxedDelegates n º&1;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-134">[!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]</span></span>  
  
 <span data-ttu-id="a8769-135">[!code-vb[VbVbalrRelaxedDelegates&#7;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-135">[!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]</span></span>  
  
 <span data-ttu-id="a8769-136">[!code-vb[VbVbalrRelaxedDelegates n º&9;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-136">[!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]</span></span>  
  
 <span data-ttu-id="a8769-137">O exemplo a seguir é válido somente quando `Option Strict` é definido como `Off`.</span><span class="sxs-lookup"><span data-stu-id="a8769-137">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 <span data-ttu-id="a8769-138">[!code-vb[VbVbalrRelaxedDelegates&#14;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-138">[!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]</span></span>  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="a8769-139">Descartando função de retorno</span><span class="sxs-lookup"><span data-stu-id="a8769-139">Dropping Function Returns</span></span>  
 <span data-ttu-id="a8769-140">Conversão de delegado reduzida permite atribuir uma função a um `Sub` representante, ignorando efetivamente o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="a8769-140">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="a8769-141">No entanto, você não pode atribuir um `Sub` a uma função delegada.</span><span class="sxs-lookup"><span data-stu-id="a8769-141">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="a8769-142">No exemplo a seguir, o endereço da função `doubler` é atribuído a `Sub` delegar `Del3`.</span><span class="sxs-lookup"><span data-stu-id="a8769-142">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 <span data-ttu-id="a8769-143">[!code-vb[VbVbalrRelaxedDelegates n º&10;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-143">[!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]</span></span>  
  
 <span data-ttu-id="a8769-144">[!code-vb[VbVbalrRelaxedDelegates n º&11;](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span><span class="sxs-lookup"><span data-stu-id="a8769-144">[!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8769-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8769-145">See Also</span></span>  
 <span data-ttu-id="a8769-146">[Expressões lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="a8769-146">[Lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="a8769-147"> [Conversões entre](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="a8769-147"> [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) </span></span>  
<span data-ttu-id="a8769-148"> [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="a8769-148"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="a8769-149"> [Como: passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a8769-149"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="a8769-150"> [Inferência de tipo local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="a8769-150"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="a8769-151"> [Instrução Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="a8769-151"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
