---
title: Conversão de delegado reduzida
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: ffb242842553382ba26121333c38fc65eaa168a9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345225"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="575ef-102">Conversão de delegado reduzida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="575ef-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="575ef-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span><span class="sxs-lookup"><span data-stu-id="575ef-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="575ef-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span><span class="sxs-lookup"><span data-stu-id="575ef-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="575ef-105">Parameters and Return Type</span><span class="sxs-lookup"><span data-stu-id="575ef-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="575ef-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span><span class="sxs-lookup"><span data-stu-id="575ef-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="575ef-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span><span class="sxs-lookup"><span data-stu-id="575ef-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="575ef-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span><span class="sxs-lookup"><span data-stu-id="575ef-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="575ef-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span><span class="sxs-lookup"><span data-stu-id="575ef-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="575ef-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span><span class="sxs-lookup"><span data-stu-id="575ef-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="575ef-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span><span class="sxs-lookup"><span data-stu-id="575ef-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="575ef-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span><span class="sxs-lookup"><span data-stu-id="575ef-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="575ef-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span><span class="sxs-lookup"><span data-stu-id="575ef-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="575ef-114">Omitting Parameter Specifications</span><span class="sxs-lookup"><span data-stu-id="575ef-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="575ef-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span><span class="sxs-lookup"><span data-stu-id="575ef-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="575ef-116">Note that you cannot specify some parameters and omit others.</span><span class="sxs-lookup"><span data-stu-id="575ef-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="575ef-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span><span class="sxs-lookup"><span data-stu-id="575ef-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="575ef-118">The arguments to some event handlers are not used.</span><span class="sxs-lookup"><span data-stu-id="575ef-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="575ef-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span><span class="sxs-lookup"><span data-stu-id="575ef-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="575ef-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span><span class="sxs-lookup"><span data-stu-id="575ef-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="575ef-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="575ef-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="575ef-122">AddressOf Examples</span><span class="sxs-lookup"><span data-stu-id="575ef-122">AddressOf Examples</span></span>  
 <span data-ttu-id="575ef-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span><span class="sxs-lookup"><span data-stu-id="575ef-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="575ef-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="575ef-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="575ef-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span><span class="sxs-lookup"><span data-stu-id="575ef-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="575ef-126">The following example is valid only when `Option Strict` is set to `Off`.</span><span class="sxs-lookup"><span data-stu-id="575ef-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="575ef-127">Dropping Function Returns</span><span class="sxs-lookup"><span data-stu-id="575ef-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="575ef-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span><span class="sxs-lookup"><span data-stu-id="575ef-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="575ef-129">However, you cannot assign a `Sub` to a function delegate.</span><span class="sxs-lookup"><span data-stu-id="575ef-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="575ef-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span><span class="sxs-lookup"><span data-stu-id="575ef-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="575ef-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="575ef-131">See also</span></span>

- [<span data-ttu-id="575ef-132">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="575ef-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="575ef-133">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="575ef-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="575ef-134">Delegados</span><span class="sxs-lookup"><span data-stu-id="575ef-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="575ef-135">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="575ef-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="575ef-136">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="575ef-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="575ef-137">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="575ef-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
