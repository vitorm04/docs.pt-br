---
title: Instrução Exit
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
ms.openlocfilehash: 1bfe81428fd3c50663fd8978e05c6a945cd47df8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345933"
---
# <a name="exit-statement-visual-basic"></a><span data-ttu-id="07867-102">Instrução Exit (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="07867-102">Exit Statement (Visual Basic)</span></span>

<span data-ttu-id="07867-103">Sai de um procedimento ou bloco e transfere o controle imediatamente para a instrução após a chamada de procedimento ou a definição de bloco.</span><span class="sxs-lookup"><span data-stu-id="07867-103">Exits a procedure or block and transfers control immediately to the statement following the procedure call or the block definition.</span></span>

## <a name="syntax"></a><span data-ttu-id="07867-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07867-104">Syntax</span></span>

```vb
Exit { Do | For | Function | Property | Select | Sub | Try | While }
```

## <a name="statements"></a><span data-ttu-id="07867-105">Instruções</span><span class="sxs-lookup"><span data-stu-id="07867-105">Statements</span></span>

 `Exit Do`  
 <span data-ttu-id="07867-106">Sai imediatamente do loop de `Do` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-106">Immediately exits the `Do` loop in which it appears.</span></span> <span data-ttu-id="07867-107">A execução continua com a instrução após a instrução `Loop`.</span><span class="sxs-lookup"><span data-stu-id="07867-107">Execution continues with the statement following the `Loop` statement.</span></span> <span data-ttu-id="07867-108">`Exit Do` pode ser usado somente dentro de um loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="07867-108">`Exit Do` can be used only inside a `Do` loop.</span></span> <span data-ttu-id="07867-109">Quando usado em loops de `Do` aninhados, `Exit Do` sai do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="07867-109">When used within nested `Do` loops, `Exit Do` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit For`  
 <span data-ttu-id="07867-110">Sai imediatamente do loop de `For` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-110">Immediately exits the `For` loop in which it appears.</span></span> <span data-ttu-id="07867-111">A execução continua com a instrução após a instrução `Next`.</span><span class="sxs-lookup"><span data-stu-id="07867-111">Execution continues with the statement following the `Next` statement.</span></span> <span data-ttu-id="07867-112">`Exit For` só pode ser usada dentro de um loop `For`...`Next` ou `For Each`...`Next`.</span><span class="sxs-lookup"><span data-stu-id="07867-112">`Exit For` can be used only inside a `For`...`Next` or `For Each`...`Next` loop.</span></span> <span data-ttu-id="07867-113">Quando usado em loops de `For` aninhados, `Exit For` sai do loop mais interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="07867-113">When used within nested `For` loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>

 `Exit Function`  
 <span data-ttu-id="07867-114">Sai imediatamente do procedimento `Function` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-114">Immediately exits the `Function` procedure in which it appears.</span></span> <span data-ttu-id="07867-115">A execução continua com a instrução após a instrução que chamou o procedimento de `Function`.</span><span class="sxs-lookup"><span data-stu-id="07867-115">Execution continues with the statement following the statement that called the `Function` procedure.</span></span> <span data-ttu-id="07867-116">`Exit Function` pode ser usado somente dentro de um procedimento de `Function`.</span><span class="sxs-lookup"><span data-stu-id="07867-116">`Exit Function` can be used only inside a `Function` procedure.</span></span>

 <span data-ttu-id="07867-117">Para especificar um valor de retorno, você pode atribuir o valor ao nome da função em uma linha antes da instrução de `Exit Function`.</span><span class="sxs-lookup"><span data-stu-id="07867-117">To specify a return value, you can assign the value to the function name on a line before the `Exit Function` statement.</span></span> <span data-ttu-id="07867-118">Para atribuir o valor de retorno e sair da função em uma instrução, em vez disso, você pode usar a [instrução return](return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="07867-118">To assign the return value and exit the function in one statement, you can instead use the [Return Statement](return-statement.md).</span></span>

 `Exit Property`  
 <span data-ttu-id="07867-119">Sai imediatamente do procedimento `Property` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-119">Immediately exits the `Property` procedure in which it appears.</span></span> <span data-ttu-id="07867-120">A execução continua com a instrução que chamou o procedimento `Property`, ou seja, com a instrução solicitando ou definindo o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="07867-120">Execution continues with the statement that called the `Property` procedure, that is, with the statement requesting or setting the property's value.</span></span> <span data-ttu-id="07867-121">`Exit Property` só pode ser usada dentro de um procedimento `Get` ou `Set` de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="07867-121">`Exit Property` can be used only inside a property's `Get` or `Set` procedure.</span></span>

 <span data-ttu-id="07867-122">Para especificar um valor de retorno em um procedimento `Get`, você pode atribuir o valor ao nome da função em uma linha antes da instrução `Exit Property`.</span><span class="sxs-lookup"><span data-stu-id="07867-122">To specify a return value in a `Get` procedure, you can assign the value to the function name on a line before the `Exit Property` statement.</span></span> <span data-ttu-id="07867-123">Para atribuir o valor de retorno e sair do procedimento de `Get` em uma instrução, você pode usar a instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="07867-123">To assign the return value and exit the `Get` procedure in one statement, you can instead use the `Return` statement.</span></span>

 <span data-ttu-id="07867-124">Em um procedimento `Set`, a instrução `Exit Property` é equivalente à instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="07867-124">In a `Set` procedure, the `Exit Property` statement is equivalent to the `Return` statement.</span></span>

 `Exit Select`  
 <span data-ttu-id="07867-125">Sai imediatamente do bloco de `Select Case` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-125">Immediately exits the `Select Case` block in which it appears.</span></span> <span data-ttu-id="07867-126">A execução continua com a instrução após a instrução `End Select`.</span><span class="sxs-lookup"><span data-stu-id="07867-126">Execution continues with the statement following the `End Select` statement.</span></span> <span data-ttu-id="07867-127">`Exit Select` só pode ser usada dentro de uma instrução `Select Case`.</span><span class="sxs-lookup"><span data-stu-id="07867-127">`Exit Select` can be used only inside a `Select Case` statement.</span></span>

 `Exit Sub`  
 <span data-ttu-id="07867-128">Sai imediatamente do procedimento `Sub` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-128">Immediately exits the `Sub` procedure in which it appears.</span></span> <span data-ttu-id="07867-129">A execução continua com a instrução após a instrução que chamou o procedimento de `Sub`.</span><span class="sxs-lookup"><span data-stu-id="07867-129">Execution continues with the statement following the statement that called the `Sub` procedure.</span></span> <span data-ttu-id="07867-130">`Exit Sub` pode ser usado somente dentro de um procedimento de `Sub`.</span><span class="sxs-lookup"><span data-stu-id="07867-130">`Exit Sub` can be used only inside a `Sub` procedure.</span></span>

 <span data-ttu-id="07867-131">Em um procedimento `Sub`, a instrução `Exit Sub` é equivalente à instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="07867-131">In a `Sub` procedure, the `Exit Sub` statement is equivalent to the `Return` statement.</span></span>

 `Exit Try`  
 <span data-ttu-id="07867-132">Sai imediatamente do `Try` ou `Catch` bloco no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-132">Immediately exits the `Try` or `Catch` block in which it appears.</span></span> <span data-ttu-id="07867-133">A execução continua com o bloco de `Finally` se houver um, ou com a instrução a seguir a instrução `End Try` caso contrário.</span><span class="sxs-lookup"><span data-stu-id="07867-133">Execution continues with the `Finally` block if there is one, or with the statement following the `End Try` statement otherwise.</span></span> <span data-ttu-id="07867-134">`Exit Try` pode ser usado somente dentro de um bloco de `Try` ou `Catch` e não dentro de um bloco de `Finally`.</span><span class="sxs-lookup"><span data-stu-id="07867-134">`Exit Try` can be used only inside a `Try` or `Catch` block, and not inside a `Finally` block.</span></span>

 `Exit While`  
 <span data-ttu-id="07867-135">Sai imediatamente do loop de `While` no qual ele aparece.</span><span class="sxs-lookup"><span data-stu-id="07867-135">Immediately exits the `While` loop in which it appears.</span></span> <span data-ttu-id="07867-136">A execução continua com a instrução após a instrução `End While`.</span><span class="sxs-lookup"><span data-stu-id="07867-136">Execution continues with the statement following the `End While` statement.</span></span> <span data-ttu-id="07867-137">`Exit While` pode ser usado somente dentro de um loop de `While`.</span><span class="sxs-lookup"><span data-stu-id="07867-137">`Exit While` can be used only inside a `While` loop.</span></span> <span data-ttu-id="07867-138">Quando usado em loops de `While` aninhados, `Exit While` transfere o controle para o loop que é um nível aninhado acima do loop em que `Exit While` ocorre.</span><span class="sxs-lookup"><span data-stu-id="07867-138">When used within nested `While` loops, `Exit While` transfers control to the loop that is one nested level above the loop where `Exit While` occurs.</span></span>

## <a name="remarks"></a><span data-ttu-id="07867-139">Comentários</span><span class="sxs-lookup"><span data-stu-id="07867-139">Remarks</span></span>

<span data-ttu-id="07867-140">Não confunda `Exit` instruções com `End` instruções.</span><span class="sxs-lookup"><span data-stu-id="07867-140">Do not confuse `Exit` statements with `End` statements.</span></span> <span data-ttu-id="07867-141">`Exit` não define o fim de uma instrução.</span><span class="sxs-lookup"><span data-stu-id="07867-141">`Exit` does not define the end of a statement.</span></span>

## <a name="example"></a><span data-ttu-id="07867-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07867-142">Example</span></span>

<span data-ttu-id="07867-143">No exemplo a seguir, a condição de loop para o loop quando a variável `index` é maior que 100.</span><span class="sxs-lookup"><span data-stu-id="07867-143">In the following example, the loop condition stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="07867-144">No entanto, a instrução `If` no loop faz com que a instrução `Exit Do` pare o loop quando a variável de índice é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="07867-144">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>

[!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]

## <a name="example"></a><span data-ttu-id="07867-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07867-145">Example</span></span>

<span data-ttu-id="07867-146">O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction`e, em seguida, usa `Exit Function` para retornar da função:</span><span class="sxs-lookup"><span data-stu-id="07867-146">The following example assigns the return value to the function name `myFunction`, and then uses `Exit Function` to return from the function:</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

## <a name="example"></a><span data-ttu-id="07867-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="07867-147">Example</span></span>

<span data-ttu-id="07867-148">O exemplo a seguir usa a [instrução return](return-statement.md) para atribuir o valor de retorno e sair da função:</span><span class="sxs-lookup"><span data-stu-id="07867-148">The following example uses the [Return Statement](return-statement.md) to assign the return value and exit the function:</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

## <a name="see-also"></a><span data-ttu-id="07867-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07867-149">See also</span></span>

- [<span data-ttu-id="07867-150">Instrução Continue</span><span class="sxs-lookup"><span data-stu-id="07867-150">Continue Statement</span></span>](continue-statement.md)
- [<span data-ttu-id="07867-151">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="07867-151">Do...Loop Statement</span></span>](do-loop-statement.md)
- [<span data-ttu-id="07867-152">Instrução End</span><span class="sxs-lookup"><span data-stu-id="07867-152">End Statement</span></span>](end-statement.md)
- [<span data-ttu-id="07867-153">Instrução For Each...Next</span><span class="sxs-lookup"><span data-stu-id="07867-153">For Each...Next Statement</span></span>](for-each-next-statement.md)
- [<span data-ttu-id="07867-154">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="07867-154">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="07867-155">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="07867-155">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="07867-156">Instrução Return</span><span class="sxs-lookup"><span data-stu-id="07867-156">Return Statement</span></span>](return-statement.md)
- [<span data-ttu-id="07867-157">Instrução Stop</span><span class="sxs-lookup"><span data-stu-id="07867-157">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="07867-158">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="07867-158">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="07867-159">Instrução Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="07867-159">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
