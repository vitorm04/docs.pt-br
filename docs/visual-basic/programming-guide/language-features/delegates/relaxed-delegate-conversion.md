---
title: Conversão de delegado reduzida
ms.date: 07/20/2015
helpviewer_keywords:
- relaxed delegate conversion [Visual Basic]
- delegates [Visual Basic], relaxed conversion
- conversions [Visual Basic], relaxed delegate
ms.assetid: 64f371d0-5416-4f65-b23b-adcbf556e81c
ms.openlocfilehash: a581ffae77c496908d2e4e38df53491a54ae2ab8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410664"
---
# <a name="relaxed-delegate-conversion-visual-basic"></a><span data-ttu-id="4f17c-102">Conversão de delegado reduzida (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4f17c-102">Relaxed Delegate Conversion (Visual Basic)</span></span>
<span data-ttu-id="4f17c-103">A conversão de delegado reduzida permite que você atribua sub-rotinas e funções a delegados ou manipuladores, mesmo quando suas assinaturas não forem idênticas.</span><span class="sxs-lookup"><span data-stu-id="4f17c-103">Relaxed delegate conversion enables you to assign subs and functions to delegates or handlers even when their signatures are not identical.</span></span> <span data-ttu-id="4f17c-104">Portanto, a associação a delegados se torna consistente com a associação já permitida para invocações de método.</span><span class="sxs-lookup"><span data-stu-id="4f17c-104">Therefore, binding to delegates becomes consistent with the binding already allowed for method invocations.</span></span>  
  
## <a name="parameters-and-return-type"></a><span data-ttu-id="4f17c-105">Parâmetros e tipo de retorno</span><span class="sxs-lookup"><span data-stu-id="4f17c-105">Parameters and Return Type</span></span>  
 <span data-ttu-id="4f17c-106">Em vez de uma correspondência exata de assinatura, a conversão reduzida exige que as seguintes condições sejam atendidas quando `Option Strict` é definido como `On` :</span><span class="sxs-lookup"><span data-stu-id="4f17c-106">In place of exact signature match, relaxed conversion requires that the following conditions be met when `Option Strict` is set to `On`:</span></span>  
  
- <span data-ttu-id="4f17c-107">Uma conversão de ampliação deve existir do tipo de dados de cada parâmetro delegado para o tipo de dados do parâmetro correspondente da função atribuída ou `Sub` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-107">A widening conversion must exist from the data type of each delegate parameter to the data type of the corresponding parameter of the assigned function or `Sub`.</span></span> <span data-ttu-id="4f17c-108">No exemplo a seguir, o delegado `Del1` tem um parâmetro, um `Integer` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-108">In the following example, the delegate `Del1` has one parameter, an `Integer`.</span></span> <span data-ttu-id="4f17c-109">`m`O parâmetro nas expressões lambda atribuídas deve ter um tipo de dados para o qual há uma conversão de ampliação de `Integer` , como `Long` ou `Double` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-109">Parameter `m` in the assigned lambda expressions must have a data type for which there is a widening conversion from `Integer`, such as `Long` or `Double`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
     [!code-vb[VbVbalrRelaxedDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#2)]  
  
     <span data-ttu-id="4f17c-110">Conversões redutoras são permitidas somente quando `Option Strict` é definido como `Off` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-110">Narrowing conversions are permitted only when `Option Strict` is set to `Off`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#8)]  
  
- <span data-ttu-id="4f17c-111">Uma conversão de ampliação deve existir na direção oposta do tipo de retorno da função atribuída ou `Sub` ao tipo de retorno do delegado.</span><span class="sxs-lookup"><span data-stu-id="4f17c-111">A widening conversion must exist in the opposite direction from the return type of the assigned function or `Sub` to the return type of the delegate.</span></span> <span data-ttu-id="4f17c-112">Nos exemplos a seguir, o corpo de cada expressão lambda atribuída deve ser avaliado como um tipo de dados que se expande como `Integer` o tipo de retorno de `del1` é `Integer` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-112">In the following examples, the body of each assigned lambda expression must evaluate to a data type that widens to `Integer` because the return type of `del1` is `Integer`.</span></span>  
  
     [!code-vb[VbVbalrRelaxedDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#3)]  
  
 <span data-ttu-id="4f17c-113">Se `Option Strict` é definido como `Off` , a restrição de ampliação é removida em ambas as direções.</span><span class="sxs-lookup"><span data-stu-id="4f17c-113">If `Option Strict` is set to `Off`, the widening restriction is removed in both directions.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#4)]  
  
## <a name="omitting-parameter-specifications"></a><span data-ttu-id="4f17c-114">Omitindo especificações de parâmetro</span><span class="sxs-lookup"><span data-stu-id="4f17c-114">Omitting Parameter Specifications</span></span>  
 <span data-ttu-id="4f17c-115">Delegados relaxados também permitem que você omita completamente as especificações de parâmetro no método atribuído:</span><span class="sxs-lookup"><span data-stu-id="4f17c-115">Relaxed delegates also allow you to completely omit parameter specifications in the assigned method:</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#5)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#6)]  
  
 <span data-ttu-id="4f17c-116">Observe que você não pode especificar alguns parâmetros e omitir outros.</span><span class="sxs-lookup"><span data-stu-id="4f17c-116">Note that you cannot specify some parameters and omit others.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#15)]  
  
 <span data-ttu-id="4f17c-117">A capacidade de omitir parâmetros é útil em uma situação como definir um manipulador de eventos, em que vários parâmetros complexos estão envolvidos.</span><span class="sxs-lookup"><span data-stu-id="4f17c-117">The ability to omit parameters is helpful in a situation such as defining an event handler, where several complex parameters are involved.</span></span> <span data-ttu-id="4f17c-118">Os argumentos para alguns manipuladores de eventos não são usados.</span><span class="sxs-lookup"><span data-stu-id="4f17c-118">The arguments to some event handlers are not used.</span></span> <span data-ttu-id="4f17c-119">Em vez disso, o manipulador acessa diretamente o estado do controle no qual o evento está registrado e ignora os argumentos.</span><span class="sxs-lookup"><span data-stu-id="4f17c-119">Instead, the handler directly accesses the state of the control on which the event is registered, and ignores the arguments.</span></span> <span data-ttu-id="4f17c-120">Delegados reduzidos permitem omitir os argumentos em tais declarações quando nenhuma ambiguidade resulta.</span><span class="sxs-lookup"><span data-stu-id="4f17c-120">Relaxed delegates allow you to omit the arguments in such declarations when no ambiguities result.</span></span> <span data-ttu-id="4f17c-121">No exemplo a seguir, o método totalmente especificado `OnClick` pode ser reescrito como `RelaxedOnClick` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-121">In the following example, the fully specified method `OnClick` can be rewritten as `RelaxedOnClick`.</span></span>  
  
```vb  
Sub OnClick(ByVal sender As Object, ByVal e As EventArgs) Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
  
Sub RelaxedOnClick() Handles b.Click  
    MessageBox.Show("Hello World from" + b.Text)  
End Sub  
```  
  
## <a name="addressof-examples"></a><span data-ttu-id="4f17c-122">Exemplos de AddressOf</span><span class="sxs-lookup"><span data-stu-id="4f17c-122">AddressOf Examples</span></span>  
 <span data-ttu-id="4f17c-123">As expressões lambda são usadas nos exemplos anteriores para facilitar a visualização das relações de tipo.</span><span class="sxs-lookup"><span data-stu-id="4f17c-123">Lambda expressions are used in the previous examples to make the type relationships easy to see.</span></span> <span data-ttu-id="4f17c-124">No entanto, as mesmas reduções são permitidas para atribuições de delegado que usam `AddressOf` , `Handles` ou `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-124">However, the same relaxations are permitted for delegate assignments that use `AddressOf`, `Handles`, or `AddHandler`.</span></span>  
  
 <span data-ttu-id="4f17c-125">No exemplo a seguir, `f1` as funções,, `f2` `f3` e `f4` podem ser atribuídas a `Del1` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-125">In the following example, functions `f1`, `f2`, `f3`, and `f4` can all be assigned to `Del1`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#7)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#9)]  
  
 <span data-ttu-id="4f17c-126">O exemplo a seguir é válido somente quando `Option Strict` é definido como `Off` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-126">The following example is valid only when `Option Strict` is set to `Off`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module2.vb#14)]  
  
## <a name="dropping-function-returns"></a><span data-ttu-id="4f17c-127">Descartando retornos de função</span><span class="sxs-lookup"><span data-stu-id="4f17c-127">Dropping Function Returns</span></span>  
 <span data-ttu-id="4f17c-128">A conversão de delegado reduzida permite que você atribua uma função a um `Sub` delegado, ignorando efetivamente o valor de retorno da função.</span><span class="sxs-lookup"><span data-stu-id="4f17c-128">Relaxed delegate conversion enables you to assign a function to a `Sub` delegate, effectively ignoring the return value of the function.</span></span> <span data-ttu-id="4f17c-129">No entanto, você não pode atribuir um `Sub` a um delegado de função.</span><span class="sxs-lookup"><span data-stu-id="4f17c-129">However, you cannot assign a `Sub` to a function delegate.</span></span> <span data-ttu-id="4f17c-130">No exemplo a seguir, o endereço da função `doubler` é atribuído ao `Sub` delegado `Del3` .</span><span class="sxs-lookup"><span data-stu-id="4f17c-130">In the following example, the address of function `doubler` is assigned to `Sub` delegate `Del3`.</span></span>  
  
 [!code-vb[VbVbalrRelaxedDelegates#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#10)]  
  
 [!code-vb[VbVbalrRelaxedDelegates#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrRelaxedDelegates/VB/Module1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="4f17c-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f17c-131">See also</span></span>

- [<span data-ttu-id="4f17c-132">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="4f17c-132">Lambda Expressions</span></span>](../procedures/lambda-expressions.md)
- [<span data-ttu-id="4f17c-133">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="4f17c-133">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="4f17c-134">Delegados</span><span class="sxs-lookup"><span data-stu-id="4f17c-134">Delegates</span></span>](index.md)
- [<span data-ttu-id="4f17c-135">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4f17c-135">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="4f17c-136">Inferência de Tipo de Variável Local</span><span class="sxs-lookup"><span data-stu-id="4f17c-136">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="4f17c-137">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="4f17c-137">Option Strict Statement</span></span>](../../../language-reference/statements/option-strict-statement.md)
