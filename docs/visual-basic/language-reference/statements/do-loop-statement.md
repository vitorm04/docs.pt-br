---
title: Instrução Do...Loop (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Do
- vb.Loop
- vb.Until
helpviewer_keywords:
- conditional statements [Visual Basic], Do�Loop
- while statement [Visual Basic], Do...Loop
- execution [Visual Basic], conditional
- Do loops
- Until keyword [Visual Basic], Do...Loop statement
- Do...Loop statement
- instructions, repeating
- Do statement [Visual Basic]
- Exit statement [Visual Basic], in Do...Loop statements
- loop structures [Visual Basic], Do�Loop statements
- do-while statements [Visual Basic]
- loops, exiting
- Loop keyword [Visual Basic], Do...Loop statement
ms.assetid: 892f9096-b3e2-4aee-834d-83bc4e2c379d
ms.openlocfilehash: eff5239e07ca27f40ece5af68f46c491be91cf09
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583436"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="29259-102">Instrução Do...Loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29259-102">Do...Loop Statement (Visual Basic)</span></span>
<span data-ttu-id="29259-103">Repete um bloco de instruções enquanto uma condição de `Boolean` é `True` ou até que a condição se torne `True`.</span><span class="sxs-lookup"><span data-stu-id="29259-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29259-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29259-104">Syntax</span></span>  
  
```vb  
Do { While | Until } condition  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop  
' -or-  
Do  
    [ statements ]  
    [ Continue Do ]  
    [ statements ]  
    [ Exit Do ]  
    [ statements ]  
Loop { While | Until } condition  
```  
  
## <a name="parts"></a><span data-ttu-id="29259-105">Partes</span><span class="sxs-lookup"><span data-stu-id="29259-105">Parts</span></span>  
  
|<span data-ttu-id="29259-106">Termo</span><span class="sxs-lookup"><span data-stu-id="29259-106">Term</span></span>|<span data-ttu-id="29259-107">Definição</span><span class="sxs-lookup"><span data-stu-id="29259-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="29259-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="29259-108">Required.</span></span> <span data-ttu-id="29259-109">Inicia a definição do loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="29259-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="29259-110">Necessário a menos que `Until` seja usado.</span><span class="sxs-lookup"><span data-stu-id="29259-110">Required unless `Until` is used.</span></span> <span data-ttu-id="29259-111">Repita o loop até que `condition` seja `False`.</span><span class="sxs-lookup"><span data-stu-id="29259-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="29259-112">Necessário a menos que `While` seja usado.</span><span class="sxs-lookup"><span data-stu-id="29259-112">Required unless `While` is used.</span></span> <span data-ttu-id="29259-113">Repita o loop até que `condition` seja `True`.</span><span class="sxs-lookup"><span data-stu-id="29259-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="29259-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="29259-114">Optional.</span></span> <span data-ttu-id="29259-115">Expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="29259-115">`Boolean` expression.</span></span> <span data-ttu-id="29259-116">Se `condition` for `Nothing`, Visual Basic o tratará como `False`.</span><span class="sxs-lookup"><span data-stu-id="29259-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="29259-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="29259-117">Optional.</span></span> <span data-ttu-id="29259-118">Uma ou mais instruções repetidas enquanto, ou até `condition`, são `True`.</span><span class="sxs-lookup"><span data-stu-id="29259-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="29259-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="29259-119">Optional.</span></span> <span data-ttu-id="29259-120">Transfere o controle para a próxima iteração do loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="29259-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="29259-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="29259-121">Optional.</span></span> <span data-ttu-id="29259-122">Transfere o controle do loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="29259-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="29259-123">Necessário.</span><span class="sxs-lookup"><span data-stu-id="29259-123">Required.</span></span> <span data-ttu-id="29259-124">Encerra a definição do loop de `Do`.</span><span class="sxs-lookup"><span data-stu-id="29259-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29259-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="29259-125">Remarks</span></span>  
 <span data-ttu-id="29259-126">Use uma estrutura `Do...Loop` quando quiser repetir um conjunto de instruções um número indefinido de vezes, até que uma condição seja satisfeita.</span><span class="sxs-lookup"><span data-stu-id="29259-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="29259-127">Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) é geralmente uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="29259-127">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="29259-128">Você pode usar `While` ou `Until` para especificar `condition`, mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="29259-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="29259-129">Você pode testar `condition` apenas uma vez, no início ou no fim do loop.</span><span class="sxs-lookup"><span data-stu-id="29259-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="29259-130">Se você testar `condition` no início do loop (na instrução `Do`), o loop poderá não ser executado mesmo uma vez.</span><span class="sxs-lookup"><span data-stu-id="29259-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="29259-131">Se você testar no final do loop (na instrução `Loop`), o loop sempre será executado pelo menos uma vez.</span><span class="sxs-lookup"><span data-stu-id="29259-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="29259-132">A condição geralmente resulta de uma comparação de dois valores, mas pode ser qualquer expressão avaliada como um valor de [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`).</span><span class="sxs-lookup"><span data-stu-id="29259-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="29259-133">Isso inclui valores de outros tipos de dados, como tipos numéricos, que foram convertidos em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="29259-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="29259-134">Você pode aninhar loops de `Do` colocando um loop dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="29259-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="29259-135">Você também pode aninhar diferentes tipos de estruturas de controle entre si.</span><span class="sxs-lookup"><span data-stu-id="29259-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="29259-136">Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="29259-136">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="29259-137">A estrutura de `Do...Loop` oferece mais flexibilidade do que o [while... Instrução End While](../../../visual-basic/language-reference/statements/while-end-while-statement.md) porque ela permite que você decida se deseja encerrar o loop quando `condition` parar de ser `True` ou quando ele se tornar `True` pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="29259-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="29259-138">Ele também permite que você teste `condition` no início ou no fim do loop.</span><span class="sxs-lookup"><span data-stu-id="29259-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="29259-139">Sair do</span><span class="sxs-lookup"><span data-stu-id="29259-139">Exit Do</span></span>  
 <span data-ttu-id="29259-140">A instrução [Exit do](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer uma maneira alternativa de sair de um `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="29259-140">The [Exit Do](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="29259-141">`Exit Do` transfere o controle imediatamente para a instrução que segue a instrução `Loop`.</span><span class="sxs-lookup"><span data-stu-id="29259-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="29259-142">`Exit Do` geralmente é usado depois que alguma condição é avaliada, por exemplo, em uma estrutura de `If...Then...Else`.</span><span class="sxs-lookup"><span data-stu-id="29259-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="29259-143">Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento.</span><span class="sxs-lookup"><span data-stu-id="29259-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="29259-144">Um uso de `Exit Do` é testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número grande ou mesmo infinita de vezes.</span><span class="sxs-lookup"><span data-stu-id="29259-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="29259-145">Você pode usar `Exit Do` para escapar o loop.</span><span class="sxs-lookup"><span data-stu-id="29259-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="29259-146">Você pode incluir qualquer número de instruções `Exit Do` em qualquer lugar em um `Do…Loop`.</span><span class="sxs-lookup"><span data-stu-id="29259-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="29259-147">Quando usado em loops de `Do` aninhados, `Exit Do` transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="29259-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29259-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29259-148">Example</span></span>  
 <span data-ttu-id="29259-149">No exemplo a seguir, as instruções no loop continuam a ser executadas até que a variável de `index` seja maior que 10.</span><span class="sxs-lookup"><span data-stu-id="29259-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="29259-150">A cláusula `Until` está no final do loop.</span><span class="sxs-lookup"><span data-stu-id="29259-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="29259-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29259-151">Example</span></span>  
 <span data-ttu-id="29259-152">O exemplo a seguir usa uma cláusula `While` em vez de uma cláusula `Until` e `condition` é testado no início do loop em vez de no final.</span><span class="sxs-lookup"><span data-stu-id="29259-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="29259-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29259-153">Example</span></span>  
 <span data-ttu-id="29259-154">No exemplo a seguir, `condition` para o loop quando a variável `index` é maior que 100.</span><span class="sxs-lookup"><span data-stu-id="29259-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="29259-155">No entanto, a instrução `If` no loop faz com que a instrução `Exit Do` pare o loop quando a variável de índice é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="29259-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="29259-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29259-156">Example</span></span>  
 <span data-ttu-id="29259-157">O exemplo a seguir lê todas as linhas em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="29259-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="29259-158">O método <xref:System.IO.File.OpenText%2A> abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres.</span><span class="sxs-lookup"><span data-stu-id="29259-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="29259-159">Na condição de `Do...Loop`, o método <xref:System.IO.StreamReader.Peek%2A> da `StreamReader` determina se há caracteres adicionais.</span><span class="sxs-lookup"><span data-stu-id="29259-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="29259-160">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29259-160">See also</span></span>

- [<span data-ttu-id="29259-161">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="29259-161">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="29259-162">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="29259-162">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="29259-163">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="29259-163">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="29259-164">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="29259-164">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="29259-165">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="29259-165">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="29259-166">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="29259-166">While...End While Statement</span></span>](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
