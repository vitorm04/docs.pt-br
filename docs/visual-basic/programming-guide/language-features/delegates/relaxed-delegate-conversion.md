---
title: "Conversão de delegado reduzida (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0cca3d09b538905714f627c9fa006187b8927383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="954b0-102">Conversão de delegado reduzida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="954b0-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="954b0-103">Conversão de delegado reduzida permite que você atribua sub-rotinas e funções a delegados ou manipuladores mesmo quando as assinaturas não são idênticas.</span><span class="sxs-lookup"><span data-stu-id="954b0-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="954b0-104">Portanto, ligação a delegados fica consistente com a associação já permitida para invocações de método.</span><span class="sxs-lookup"><span data-stu-id="954b0-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="954b0-105">Parâmetros e tipo de retorno</span><span class="sxs-lookup"><span data-stu-id="954b0-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="954b0-106">Em vez de correspondência exata de assinatura, a conversão reduzida requer que as seguintes condições ser atendidas quando `Option Strict` é definido como `On`:</span><span class="sxs-lookup"><span data-stu-id="954b0-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
-   <span data-ttu-id="954b0-107">Uma conversão de ampliação deve existir do tipo de dados de cada parâmetro delegado para o tipo de dados do parâmetro correspondente da função atribuída ou `Sub`.</span><span class="sxs-lookup"><span data-stu-id="954b0-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="954b0-108">No exemplo a seguir, o delegado `Del1` tem um parâmetro, um `Integer`.</span><span class="sxs-lookup"><span data-stu-id="954b0-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="954b0-109">Parâmetro `m` lambda atribuídas expressões devem ter um tipo de dados para o qual há uma conversão de ampliação de `Integer`, como `Long` ou `Double`.</span><span class="sxs-lookup"><span data-stu-id="954b0-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_2.vb)]  
  
     <span data-ttu-id="954b0-110">Conversões de restrição é permitido somente quando `Option Strict` é definido como `Off`.</span><span class="sxs-lookup"><span data-stu-id="954b0-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_3.vb)]  
  
-   <span data-ttu-id="954b0-111">Uma conversão de ampliação deve existir na direção oposta do tipo de retorno da função atribuída ou `Sub` para o tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="954b0-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="954b0-112">Nos exemplos a seguir, o corpo de cada expressão lambda atribuída deve ser avaliada como um tipo de dados que amplia a `Integer` porque o tipo de retorno de `del1` é `Integer`.</span><span class="sxs-lookup"><span data-stu-id="954b0-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_4.vb)]  
  
 <span data-ttu-id="954b0-113">Se `Option Strict` é definido como `Off`, a restrição de ampliação é removido em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="954b0-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_5.vb)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="954b0-114">Omitindo especificações de parâmetro</span><span class="sxs-lookup"><span data-stu-id="954b0-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="954b0-115">Delegados reduzidos também permitem que você omita completamente especificações de parâmetro no método atribuído:</span><span class="sxs-lookup"><span data-stu-id="954b0-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_6.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_7.vb)]  
  
 <span data-ttu-id="954b0-116">Observe que não é possível especificar alguns parâmetros e omitir outras pessoas.</span><span class="sxs-lookup"><span data-stu-id="954b0-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_8.vb)]  
  
 <span data-ttu-id="954b0-117">A capacidade para omitir os parâmetros é útil em uma situação como definir um manipulador de eventos, onde vários parâmetros complexos estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="954b0-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="954b0-118">Os argumentos para alguns manipuladores de eventos não são usados.</span><span class="sxs-lookup"><span data-stu-id="954b0-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="954b0-119">Em vez disso, o manipulador acessa diretamente o estado do controle no qual o evento é registrado e ignora os argumentos.</span><span class="sxs-lookup"><span data-stu-id="954b0-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="954b0-120">Delegados reduzidos permitem omitir os argumentos em tais declarações quando nenhum resultado ambiguidades.</span><span class="sxs-lookup"><span data-stu-id="954b0-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="954b0-121">No exemplo a seguir, o método totalmente especificado `OnClick` pode ser reescrita como `RelaxedOnClick`.</span><span class="sxs-lookup"><span data-stu-id="954b0-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="954b0-122">Exemplos de AddressOf</span><span class="sxs-lookup"><span data-stu-id="954b0-122">AddressOf Examples</span></span>  
 <span data-ttu-id="954b0-123">Expressões lambda são usadas nos exemplos anteriores para facilitar as relações de tipo ver.</span><span class="sxs-lookup"><span data-stu-id="954b0-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="954b0-124">No entanto, as mesmas reduções são permitidas para atribuições de delegado que usam `AddressOf`, `Handles`, ou `AddHandler`.</span><span class="sxs-lookup"><span data-stu-id="954b0-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="954b0-125">No exemplo a seguir, as funções `f1`, `f2`, `f3`, e `f4` podem ser atribuídos a `Del1`.</span><span class="sxs-lookup"><span data-stu-id="954b0-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_1.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_9.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_10.vb)]  
  
 <span data-ttu-id="954b0-126">O exemplo a seguir é válido somente quando `Option Strict` é definido como `Off`.</span><span class="sxs-lookup"><span data-stu-id="954b0-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_11.vb)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="954b0-127">Descartando função de retorno</span><span class="sxs-lookup"><span data-stu-id="954b0-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="954b0-128">Conversão de delegado reduzida permite que você atribua uma função para um `Sub` representante, ignorando efetivamente o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="954b0-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="954b0-129">No entanto, você não pode atribuir um `Sub` a um delegado de função.</span><span class="sxs-lookup"><span data-stu-id="954b0-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="954b0-130">No exemplo a seguir, o endereço de função `doubler` é atribuído a `Sub` delegar `Del3`.</span><span class="sxs-lookup"><span data-stu-id="954b0-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_12.vb)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](../../../../visual-basic/programming-guide/language-features/delegates/codesnippet/VisualBasic/relaxed-delegate-conversion_13.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="954b0-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="954b0-131">See Also</span></span>  
 [<span data-ttu-id="954b0-132">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="954b0-132">Lambda Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="954b0-133">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="954b0-133">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="954b0-134">Delegados</span><span class="sxs-lookup"><span data-stu-id="954b0-134">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)  
 [<span data-ttu-id="954b0-135">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="954b0-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)  
 [<span data-ttu-id="954b0-136">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="954b0-136">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="954b0-137">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="954b0-137">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
