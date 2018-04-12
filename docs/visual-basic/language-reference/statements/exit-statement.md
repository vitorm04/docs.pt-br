---
title: Instrução Exit (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Exit
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- Exit statement [Visual Basic]
- program termination
- execution [Visual Basic], stopping
ms.assetid: 760bfb32-5c3f-4bdb-a432-9a6001c92db7
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2df63ecbf0605d07296e1692f18b1b015e27cd03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="4534a-102">Instrução Exit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4534a-102">Exit Statement (Visual Basic)</span></span>
<span data-ttu-id="4534a-103">Sai de um procedimento ou bloco e transfere controle imediatamente para a instrução após a chamada de procedimento ou a definição do bloco.</span><span class="sxs-lookup"><span data-stu-id="4534a-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4534a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4534a-104">Syntax</span></span>  
  
```  
Exit { Do | For | Function | Property | Select | Sub | Try | While }  
```  
  
## <a name="statements"></a><span data-ttu-id="4534a-105">Instruções</span><span class="sxs-lookup"><span data-stu-id="4534a-105">Statements</span></span>  
 `Exit Do`  
 <span data-ttu-id="4534a-106">Sai imediatamente o `Do` loop no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="4534a-107">A execução continua com a instrução após a `Loop` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="4534a-108">`Exit Do`pode ser usado somente dentro de um `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="4534a-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="4534a-109">Quando usado dentro aninhados `Do` loops, `Exit Do` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="4534a-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit For`  
 <span data-ttu-id="4534a-110">Sai imediatamente o `For` loop no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="4534a-111">A execução continua com a instrução após a `Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="4534a-112">`Exit For`pode ser usado somente dentro de um `For`... `Next` ou `For Each`... `Next` loop.</span><span class="sxs-lookup"><span data-stu-id="4534a-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="4534a-113">Quando usado dentro aninhados `For` loops, `Exit For` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="4534a-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 `Exit Function`  
 <span data-ttu-id="4534a-114">Sai imediatamente o `Function` procedimento no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="4534a-115">A execução continua com a instrução após a instrução que chamou o `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4534a-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="4534a-116">`Exit Function`pode ser usado somente dentro de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4534a-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>  
  
 <span data-ttu-id="4534a-117">Para especificar um valor de retorno, você pode atribuir o valor para o nome de função em uma linha antes do `Exit Function` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="4534a-118">Para atribuir o valor de retorno e a função em uma instrução de sair, em vez disso, você pode usar o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4534a-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 `Exit Property`  
 <span data-ttu-id="4534a-119">Sai imediatamente o `Property` procedimento no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="4534a-120">A execução continua com a instrução que chamou o `Property` procedimento, ou seja, com a instrução solicitando ou definindo o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="4534a-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="4534a-121">`Exit Property`pode ser usado somente dentro de uma propriedade `Get` ou `Set` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4534a-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>  
  
 <span data-ttu-id="4534a-122">Para especificar um valor de retorno em uma `Get` procedimento, você pode atribuir o valor para o nome de função em uma linha antes do `Exit Property` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="4534a-123">Para atribuir o valor de retorno e saia do `Get` procedimento em uma instrução, você pode usar o `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>  
  
 <span data-ttu-id="4534a-124">Em um `Set` procedimento, o `Exit Property` declaração equivale a `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Select`  
 <span data-ttu-id="4534a-125">Sai imediatamente o `Select Case` bloco no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="4534a-126">A execução continua com a instrução após a `End Select` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="4534a-127">`Exit Select`pode ser usado somente dentro de um `Select Case` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>  
  
 `Exit Sub`  
 <span data-ttu-id="4534a-128">Sai imediatamente o `Sub` procedimento no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="4534a-129">A execução continua com a instrução após a instrução que chamou o `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4534a-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="4534a-130">`Exit Sub`pode ser usado somente dentro de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4534a-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="4534a-131">Em um `Sub` procedimento, o `Exit Sub` declaração equivale a `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>  
  
 `Exit Try`  
 <span data-ttu-id="4534a-132">Sai imediatamente o `Try` ou `Catch` bloco no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="4534a-133">A execução continua com a `Finally` bloquear se houver, ou com a instrução após a `End Try` instrução caso contrário.</span><span class="sxs-lookup"><span data-stu-id="4534a-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="4534a-134">`Exit Try`pode ser usado somente dentro de um `Try` ou `Catch` bloco e não dentro um `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="4534a-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>  
  
 `Exit While`  
 <span data-ttu-id="4534a-135">Sai imediatamente o `While` loop no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="4534a-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="4534a-136">A execução continua com a instrução após a `End While` instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="4534a-137">`Exit While`pode ser usado somente dentro de um `While` loop.</span><span class="sxs-lookup"><span data-stu-id="4534a-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="4534a-138">Quando usado dentro aninhados `While` loops, `Exit While` transfere o controle para o loop que está um nível acima do loop onde `Exit While` ocorre.</span><span class="sxs-lookup"><span data-stu-id="4534a-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4534a-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="4534a-139">Remarks</span></span>  
 <span data-ttu-id="4534a-140">Não confunda `Exit` instruções com `End` instruções.</span><span class="sxs-lookup"><span data-stu-id="4534a-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="4534a-141">`Exit`não defina o final de uma instrução.</span><span class="sxs-lookup"><span data-stu-id="4534a-141">`Exit` does not define the end of a statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4534a-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4534a-142">Example</span></span>  
 <span data-ttu-id="4534a-143">No exemplo a seguir, a condição de loop para o loop quando o `index` variável é maior que 100.</span><span class="sxs-lookup"><span data-stu-id="4534a-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="4534a-144">O `If` instrução no loop, no entanto, faz com que o `Exit Do` instrução para interromper o loop quando a variável de índice é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="4534a-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="4534a-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4534a-145">Example</span></span>  
 <span data-ttu-id="4534a-146">O exemplo a seguir atribui o valor de retorno para o nome da função `myFunction`e, em seguida, usa `Exit Function` para retornar da função.</span><span class="sxs-lookup"><span data-stu-id="4534a-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="4534a-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4534a-147">Example</span></span>  
 <span data-ttu-id="4534a-148">O exemplo a seguir usa o [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md) para atribuir o valor de retorno e a função de saída.</span><span class="sxs-lookup"><span data-stu-id="4534a-148">The following example uses the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) to assign the return value and exit the function.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/exit-statement_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4534a-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4534a-149">See Also</span></span>  
 [<span data-ttu-id="4534a-150">Instrução Continue</span><span class="sxs-lookup"><span data-stu-id="4534a-150">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)  
 [<span data-ttu-id="4534a-151">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="4534a-151">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)  
 [<span data-ttu-id="4534a-152">Instrução End</span><span class="sxs-lookup"><span data-stu-id="4534a-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)  
 [<span data-ttu-id="4534a-153">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="4534a-153">For Each...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
 [<span data-ttu-id="4534a-154">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="4534a-154">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="4534a-155">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="4534a-155">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="4534a-156">Instrução Return</span><span class="sxs-lookup"><span data-stu-id="4534a-156">Return Statement</span></span>](../../../visual-basic/language-reference/statements/return-statement.md)  
 [<span data-ttu-id="4534a-157">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="4534a-157">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="4534a-158">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="4534a-158">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="4534a-159">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="4534a-159">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
