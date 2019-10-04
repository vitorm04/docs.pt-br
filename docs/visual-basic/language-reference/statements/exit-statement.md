---
title: Instrução Exit (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 9c25653809c51662ea5b606ab97be6a9b50d5986
ms.sourcegitcommit: 7bfe1682d9368cf88d43e895d1e80ba2d88c3a99
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/04/2019
ms.locfileid: "71956943"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="8d2ab-102">Instrução Exit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8d2ab-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="8d2ab-103">Sai de um procedimento ou bloco e transfere o controle imediatamente para a instrução após a chamada de procedimento ou a definição de bloco.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="8d2ab-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d2ab-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="8d2ab-105">Instruções</span><span class="sxs-lookup"><span data-stu-id="8d2ab-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="8d2ab-106">Sai imediatamente do loop `Do` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="8d2ab-107">A execução continua com a instrução após a instrução `Loop`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="8d2ab-108">`Exit Do` pode ser usado somente dentro de um loop `Do`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="8d2ab-109">Quando usado em loops `Do` aninhados, `Exit Do` sai do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="8d2ab-110">Sai imediatamente do loop `For` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="8d2ab-111">A execução continua com a instrução após a instrução `Next`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="8d2ab-112">`Exit For` só pode ser usado dentro de um loop `For`... `Next` ou `For Each`... `Next`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="8d2ab-113">Quando usado em loops `For` aninhados, `Exit For` sai do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="8d2ab-114">Sai imediatamente do procedimento `Function` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="8d2ab-115">A execução continua com a instrução após a instrução que chamou o procedimento `Function`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="8d2ab-116">`Exit Function` só pode ser usado dentro de um procedimento `Function`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="8d2ab-117">Para especificar um valor de retorno, você pode atribuir o valor ao nome da função em uma linha antes da instrução `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="8d2ab-118">Para atribuir o valor de retorno e sair da função em uma instrução, em vez disso, você pode usar a [instrução return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="8d2ab-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="8d2ab-119">Sai imediatamente do procedimento `Property` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="8d2ab-120">A execução continua com a instrução que chamou o procedimento `Property`, ou seja, com a instrução solicitando ou definindo o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="8d2ab-121">`Exit Property` só pode ser usado dentro de um procedimento `Get` ou `Set` de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="8d2ab-122">Para especificar um valor de retorno em um procedimento `Get`, você pode atribuir o valor ao nome da função em uma linha antes da instrução `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="8d2ab-123">Para atribuir o valor de retorno e sair do procedimento `Get` em uma instrução, em vez disso, você pode usar a instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="8d2ab-124">Em um procedimento `Set`, a instrução `Exit Property` é equivalente à instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="8d2ab-125">Sai imediatamente do bloco `Select Case` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="8d2ab-126">A execução continua com a instrução após a instrução `End Select`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="8d2ab-127">`Exit Select` pode ser usado somente dentro de uma instrução `Select Case`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="8d2ab-128">Sai imediatamente do procedimento `Sub` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="8d2ab-129">A execução continua com a instrução após a instrução que chamou o procedimento `Sub`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="8d2ab-130">`Exit Sub` só pode ser usado dentro de um procedimento `Sub`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="8d2ab-131">Em um procedimento `Sub`, a instrução `Exit Sub` é equivalente à instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="8d2ab-132">Sai imediatamente do bloco `Try` ou `Catch` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="8d2ab-133">A execução continua com o bloco `Finally` se houver um, ou com a instrução após a instrução `End Try`, caso contrário.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="8d2ab-134">`Exit Try` pode ser usado somente dentro de um bloco `Try` ou `Catch` e não dentro de um bloco `Finally`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="8d2ab-135">Sai imediatamente do loop `While` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="8d2ab-136">A execução continua com a instrução após a instrução `End While`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="8d2ab-137">`Exit While` pode ser usado somente dentro de um loop `While`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="8d2ab-138">Quando usado em loops `While` aninhados, o `Exit While` transfere o controle para o loop que é um nível aninhado acima do loop onde `Exit While` ocorre.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="8d2ab-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d2ab-139">Remarks</span></span>

<span data-ttu-id="8d2ab-140">Não confunda instruções `Exit` com instruções `End`.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="8d2ab-141">`Exit` não define o fim de uma instrução.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="8d2ab-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d2ab-142">Example</span></span>

<span data-ttu-id="8d2ab-143">No exemplo a seguir, a condição de loop para o loop quando a variável `index` é maior que 100.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="8d2ab-144">No entanto, a instrução `If` no loop faz com que a instrução `Exit Do` Pare o loop quando a variável de índice é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="8d2ab-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="8d2ab-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d2ab-145">Example</span></span>

<span data-ttu-id="8d2ab-146">O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa `Exit Function` para retornar da função:</span><span class="sxs-lookup"><span data-stu-id="8d2ab-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="8d2ab-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8d2ab-147">Example</span></span>

<span data-ttu-id="8d2ab-148">O exemplo a seguir usa a [instrução return](return-statement.md) para atribuir o valor de retorno e sair da função:</span><span class="sxs-lookup"><span data-stu-id="8d2ab-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="8d2ab-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d2ab-149">See also</span></span>

- [<span data-ttu-id="8d2ab-150">Instrução Continue</span><span class="sxs-lookup"><span data-stu-id="8d2ab-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="8d2ab-151">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="8d2ab-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="8d2ab-152">Instrução End</span><span class="sxs-lookup"><span data-stu-id="8d2ab-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="8d2ab-153">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="8d2ab-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="8d2ab-154">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="8d2ab-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="8d2ab-155">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="8d2ab-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="8d2ab-156">Instrução Return</span><span class="sxs-lookup"><span data-stu-id="8d2ab-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="8d2ab-157">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="8d2ab-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="8d2ab-158">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="8d2ab-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="8d2ab-159">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="8d2ab-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
