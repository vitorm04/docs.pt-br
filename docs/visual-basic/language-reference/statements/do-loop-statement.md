---
title: "Instrução Do...Loop (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- "conditional statements [Visual Basic], Do�Loop"
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- "loop structures [Visual Basic], Do�Loop statements"
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 79d25dce963f383a84b56ce2c9b600fc2d5a7937
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="82443-102">Instrução Do...Loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82443-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="82443-103">Repete um bloco de instruções enquanto uma `Boolean` condição é `True` ou até que a condição se torne `True`.</span><span class="sxs-lookup"><span data-stu-id="82443-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82443-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="82443-104">Syntax</span></span>  
  
```  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
-or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="82443-105">Partes</span><span class="sxs-lookup"><span data-stu-id="82443-105">Parts</span></span>  
  
|<span data-ttu-id="82443-106">Termo</span><span class="sxs-lookup"><span data-stu-id="82443-106">Term</span></span>|<span data-ttu-id="82443-107">Definição</span><span class="sxs-lookup"><span data-stu-id="82443-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="82443-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82443-108">Required.</span></span> <span data-ttu-id="82443-109">Inicia a definição do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="82443-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="82443-110">Necessário a menos que `Until` seja usado.</span><span class="sxs-lookup"><span data-stu-id="82443-110">Required unless `Until` is used.</span></span> <span data-ttu-id="82443-111">Repita o loop até `condition` é `False`.</span><span class="sxs-lookup"><span data-stu-id="82443-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="82443-112">Necessário a menos que `While` seja usado.</span><span class="sxs-lookup"><span data-stu-id="82443-112">Required unless `While` is used.</span></span> <span data-ttu-id="82443-113">Repita o loop até `condition` é `True`.</span><span class="sxs-lookup"><span data-stu-id="82443-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="82443-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="82443-114">Optional.</span></span> <span data-ttu-id="82443-115">Expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="82443-115">`Boolean` expression.</span></span> <span data-ttu-id="82443-116">Se `condition` é `Nothing`, Visual Basic trata isso `False`.</span><span class="sxs-lookup"><span data-stu-id="82443-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="82443-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="82443-117">Optional.</span></span> <span data-ttu-id="82443-118">Uma ou mais instruções que são repetidas enquanto, ou até que, `condition` é `True`.</span><span class="sxs-lookup"><span data-stu-id="82443-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="82443-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="82443-119">Optional.</span></span> <span data-ttu-id="82443-120">Transfere o controle para a próxima iteração do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="82443-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="82443-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="82443-121">Optional.</span></span> <span data-ttu-id="82443-122">Transfere o controle do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="82443-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="82443-123">Necessário.</span><span class="sxs-lookup"><span data-stu-id="82443-123">Required.</span></span> <span data-ttu-id="82443-124">Finaliza a definição do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="82443-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82443-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="82443-125">Remarks</span></span>  
 <span data-ttu-id="82443-126">Use um `Do...Loop` estrutura quando quiser repetir um conjunto de declarações por um número indefinido de vezes, até que uma condição é satisfeita.</span><span class="sxs-lookup"><span data-stu-id="82443-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="82443-127">Se você deseja repetir as instruções de um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="82443-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="82443-128">Você pode usar o `While` ou `Until` para especificar `condition`, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="82443-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="82443-129">Você pode testar `condition` apenas uma vez, ou o início ou o final do loop.</span><span class="sxs-lookup"><span data-stu-id="82443-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="82443-130">Se você testar `condition` no início do loop (no `Do` instrução), o loop não pode ser executado até mesmo uma vez.</span><span class="sxs-lookup"><span data-stu-id="82443-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="82443-131">Se você testar no final do loop (no `Loop` instrução), o loop sempre é executado pelo menos uma vez.</span><span class="sxs-lookup"><span data-stu-id="82443-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="82443-132">A condição normalmente resulta de uma comparação entre dois valores, mas pode ser qualquer expressão que é avaliada como um [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`).</span><span class="sxs-lookup"><span data-stu-id="82443-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="82443-133">Isso inclui os valores de outros tipos de dados, como tipos numéricos, que foram convertidos em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="82443-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="82443-134">Você pode aninhar `Do` loops colocando um loop dentro de outra.</span><span class="sxs-lookup"><span data-stu-id="82443-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="82443-135">Você também pode aninhar diferentes tipos de estruturas de controle dentro do outro.</span><span class="sxs-lookup"><span data-stu-id="82443-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="82443-136">Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="82443-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82443-137">O `Do...Loop` estrutura oferece maior flexibilidade do que o [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) porque ela permite que você decida se deseja terminar o loop quando `condition` deixa de ser `True` ou quando ela for primeiro `True`.</span><span class="sxs-lookup"><span data-stu-id="82443-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="82443-138">Ele também permite que você teste `condition` ou o início ou o final do loop.</span><span class="sxs-lookup"><span data-stu-id="82443-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="82443-139">Sair</span><span class="sxs-lookup"><span data-stu-id="82443-139">Exit Do</span></span>  
 <span data-ttu-id="82443-140">O [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer uma maneira alternativa para sair um `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="82443-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="82443-141">`Exit Do`transfere controle imediatamente para a instrução que segue o `Loop` instrução.</span><span class="sxs-lookup"><span data-stu-id="82443-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="82443-142">`Exit Do`é frequentemente usado após alguma condição é avaliada, por exemplo, em um `If...Then...Else` estrutura.</span><span class="sxs-lookup"><span data-stu-id="82443-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="82443-143">Você talvez queira encerrar um loop se você detectar uma condição que facilita o desnecessária ou impossível continuar iterando, como um valor errado ou uma solicitação de encerramento.</span><span class="sxs-lookup"><span data-stu-id="82443-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="82443-144">Um uso de `Exit Do` é testar uma condição que pode causar uma *loop infinito*, que é um loop que pode executar um número grande ou mesmo infinito de vezes.</span><span class="sxs-lookup"><span data-stu-id="82443-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="82443-145">Você pode usar `Exit Do` para escapar do loop.</span><span class="sxs-lookup"><span data-stu-id="82443-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="82443-146">Você pode incluir qualquer número de `Exit Do` instruções em qualquer lugar em um `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="82443-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="82443-147">Quando usado dentro aninhados `Do` loops, `Exit Do` transfere controle fora do loop interno e para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="82443-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82443-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82443-148">Example</span></span>  
 <span data-ttu-id="82443-149">No exemplo a seguir, as instruções no loop continuam em execução até que o `index` variável é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="82443-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="82443-150">O `Until` cláusula está no final do loop.</span><span class="sxs-lookup"><span data-stu-id="82443-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="82443-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82443-151">Example</span></span>  
 <span data-ttu-id="82443-152">O exemplo a seguir usa uma `While` cláusula em vez de um `Until` cláusula, e `condition` é testado no início do loop, em vez de no final.</span><span class="sxs-lookup"><span data-stu-id="82443-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="82443-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82443-153">Example</span></span>  
 <span data-ttu-id="82443-154">No exemplo a seguir, `condition` para o loop quando o `index` variável é maior que 100.</span><span class="sxs-lookup"><span data-stu-id="82443-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="82443-155">O `If` instrução no loop, no entanto, faz com que o `Exit Do` instrução para interromper o loop quando a variável de índice é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="82443-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="82443-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="82443-156">Example</span></span>  
 <span data-ttu-id="82443-157">O exemplo a seguir lê todas as linhas em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="82443-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="82443-158">O <xref:System.IO.File.OpenText%2A> método abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres.</span><span class="sxs-lookup"><span data-stu-id="82443-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="82443-159">No `Do...Loop` condição, o <xref:System.IO.StreamReader.Peek%2A> método o `StreamReader` determina se há quaisquer caracteres adicionais.</span><span class="sxs-lookup"><span data-stu-id="82443-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/do-loop-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="82443-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="82443-160">See Also</span></span>  
 [<span data-ttu-id="82443-161">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="82443-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="82443-162">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="82443-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="82443-163">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="82443-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)  
 [<span data-ttu-id="82443-164">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="82443-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="82443-165">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="82443-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="82443-166">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="82443-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
