---
title: Instrução Do...Loop
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
ms.openlocfilehash: 86a702aefeea1e5e359a579a3f29e9c06f1c619c
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90865930"
---
# <a name="doloop-statement-visual-basic"></a><span data-ttu-id="6beec-102">Instrução Do...Loop (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6beec-102">Do...Loop Statement (Visual Basic)</span></span>

<span data-ttu-id="6beec-103">Repete um bloco de instruções enquanto uma `Boolean` condição é `True` ou até que a condição se torne `True` .</span><span class="sxs-lookup"><span data-stu-id="6beec-103">Repeats a block of statements while a `Boolean` condition is `True` or until the condition becomes `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6beec-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6beec-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="6beec-105">Partes</span><span class="sxs-lookup"><span data-stu-id="6beec-105">Parts</span></span>  
  
|<span data-ttu-id="6beec-106">Termo</span><span class="sxs-lookup"><span data-stu-id="6beec-106">Term</span></span>|<span data-ttu-id="6beec-107">Definição</span><span class="sxs-lookup"><span data-stu-id="6beec-107">Definition</span></span>|  
|---|---|  
|`Do`|<span data-ttu-id="6beec-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6beec-108">Required.</span></span> <span data-ttu-id="6beec-109">Inicia a definição do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-109">Starts the definition of the `Do` loop.</span></span>|  
|`While`|<span data-ttu-id="6beec-110">Necessário a menos que `Until` seja usado.</span><span class="sxs-lookup"><span data-stu-id="6beec-110">Required unless `Until` is used.</span></span> <span data-ttu-id="6beec-111">Repita o loop até que `condition` esteja `False` .</span><span class="sxs-lookup"><span data-stu-id="6beec-111">Repeat the loop until `condition` is `False`.</span></span>|  
|`Until`|<span data-ttu-id="6beec-112">Necessário a menos que `While` seja usado.</span><span class="sxs-lookup"><span data-stu-id="6beec-112">Required unless `While` is used.</span></span> <span data-ttu-id="6beec-113">Repita o loop até que `condition` esteja `True` .</span><span class="sxs-lookup"><span data-stu-id="6beec-113">Repeat the loop until `condition` is `True`.</span></span>|  
|`condition`|<span data-ttu-id="6beec-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6beec-114">Optional.</span></span> <span data-ttu-id="6beec-115">Expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="6beec-115">`Boolean` expression.</span></span> <span data-ttu-id="6beec-116">Se `condition` for `Nothing` , Visual Basic tratará como `False` .</span><span class="sxs-lookup"><span data-stu-id="6beec-116">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="6beec-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6beec-117">Optional.</span></span> <span data-ttu-id="6beec-118">Uma ou mais instruções repetidas enquanto, ou até, `condition` são `True` .</span><span class="sxs-lookup"><span data-stu-id="6beec-118">One or more statements that are repeated while, or until, `condition` is `True`.</span></span>|  
|`Continue Do`|<span data-ttu-id="6beec-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6beec-119">Optional.</span></span> <span data-ttu-id="6beec-120">Transfere o controle para a próxima iteração do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-120">Transfers control to the next iteration of the `Do` loop.</span></span>|  
|`Exit Do`|<span data-ttu-id="6beec-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="6beec-121">Optional.</span></span> <span data-ttu-id="6beec-122">Transfere o controle do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-122">Transfers control out of the `Do` loop.</span></span>|  
|`Loop`|<span data-ttu-id="6beec-123">Necessário.</span><span class="sxs-lookup"><span data-stu-id="6beec-123">Required.</span></span> <span data-ttu-id="6beec-124">Encerra a definição do `Do` loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-124">Terminates the definition of the `Do` loop.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6beec-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="6beec-125">Remarks</span></span>  

 <span data-ttu-id="6beec-126">Use uma `Do...Loop` estrutura quando você quiser repetir um conjunto de instruções um número indefinido de vezes, até que uma condição seja satisfeita.</span><span class="sxs-lookup"><span data-stu-id="6beec-126">Use a `Do...Loop` structure when you want to repeat a set of statements an indefinite number of times, until a condition is satisfied.</span></span> <span data-ttu-id="6beec-127">Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](for-next-statement.md) é geralmente uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="6beec-127">If you want to repeat the statements a set number of times, the [For...Next Statement](for-next-statement.md) is usually a better choice.</span></span>  
  
 <span data-ttu-id="6beec-128">Você pode usar o `While` ou o `Until` para especificar `condition` , mas não ambos.</span><span class="sxs-lookup"><span data-stu-id="6beec-128">You can use either `While` or `Until` to specify `condition`, but not both.</span></span>  
  
 <span data-ttu-id="6beec-129">Você pode testar `condition` apenas uma vez, no início ou no fim do loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-129">You can test `condition` only one time, at either the start or the end of the loop.</span></span> <span data-ttu-id="6beec-130">Se você testar `condition` no início do loop (na `Do` instrução), o loop pode não ser executado mesmo uma vez.</span><span class="sxs-lookup"><span data-stu-id="6beec-130">If you test `condition` at the start of the loop (in the `Do` statement), the loop might not run even one time.</span></span> <span data-ttu-id="6beec-131">Se você testar no final do loop (na `Loop` instrução), o loop sempre será executado pelo menos uma vez.</span><span class="sxs-lookup"><span data-stu-id="6beec-131">If you test at the end of the loop (in the `Loop` statement), the loop always runs at least one time.</span></span>  
  
 <span data-ttu-id="6beec-132">A condição geralmente resulta de uma comparação de dois valores, mas pode ser qualquer expressão avaliada como um valor de [tipo de dados booliano](../data-types/boolean-data-type.md) ( `True` ou `False` ).</span><span class="sxs-lookup"><span data-stu-id="6beec-132">The condition usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="6beec-133">Isso inclui valores de outros tipos de dados, como tipos numéricos, que foram convertidos em `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="6beec-133">This includes values of other data types, such as numeric types, that have been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="6beec-134">Você pode aninhar `Do` loops colocando um loop dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="6beec-134">You can nest `Do` loops by putting one loop within another.</span></span> <span data-ttu-id="6beec-135">Você também pode aninhar diferentes tipos de estruturas de controle entre si.</span><span class="sxs-lookup"><span data-stu-id="6beec-135">You can also nest different kinds of control structures within each other.</span></span> <span data-ttu-id="6beec-136">Para obter mais informações, consulte [estruturas de controle aninhado](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="6beec-136">For more information, see [Nested Control Structures](../../programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6beec-137">A `Do...Loop` estrutura oferece mais flexibilidade do que o [while... Instrução End While](while-end-while-statement.md) porque ela permite que você decida se deseja encerrar o loop quando `condition` parar de ser `True` ou quando ele se tornar o primeiro `True` .</span><span class="sxs-lookup"><span data-stu-id="6beec-137">The `Do...Loop` structure gives you more flexibility than the [While...End While Statement](while-end-while-statement.md) because it enables you to decide whether to end the loop when `condition` stops being `True` or when it first becomes `True`.</span></span> <span data-ttu-id="6beec-138">Ele também permite que você teste `condition` no início ou no fim do loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-138">It also enables you to test `condition` at either the start or the end of the loop.</span></span>  
  
## <a name="exit-do"></a><span data-ttu-id="6beec-139">Sair do</span><span class="sxs-lookup"><span data-stu-id="6beec-139">Exit Do</span></span>  

 <span data-ttu-id="6beec-140">A instrução [Exit do](exit-statement.md) pode fornecer uma maneira alternativa de sair de um `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="6beec-140">The [Exit Do](exit-statement.md) statement can provide an alternative way to exit a `Do…Loop`.</span></span> <span data-ttu-id="6beec-141">`Exit Do` transfere o controle imediatamente para a instrução que segue a `Loop` instrução.</span><span class="sxs-lookup"><span data-stu-id="6beec-141">`Exit Do` transfers control immediately to the statement that follows the `Loop` statement.</span></span>  
  
 <span data-ttu-id="6beec-142">`Exit Do` geralmente é usado depois que alguma condição é avaliada, por exemplo, em uma `If...Then...Else` estrutura.</span><span class="sxs-lookup"><span data-stu-id="6beec-142">`Exit Do` is often used after some condition is evaluated, for example in an `If...Then...Else` structure.</span></span> <span data-ttu-id="6beec-143">Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento.</span><span class="sxs-lookup"><span data-stu-id="6beec-143">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="6beec-144">Um uso de `Exit Do` é testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número grande ou mesmo infinito de vezes.</span><span class="sxs-lookup"><span data-stu-id="6beec-144">One use of `Exit Do` is to test for a condition that could cause an *endless loop*, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="6beec-145">Você pode usar `Exit Do` para escapar o loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-145">You can use `Exit Do` to escape the loop.</span></span>  
  
 <span data-ttu-id="6beec-146">Você pode incluir qualquer número de `Exit Do` instruções em qualquer lugar em um `Do…Loop` .</span><span class="sxs-lookup"><span data-stu-id="6beec-146">You can include any number of `Exit Do` statements anywhere in a `Do…Loop`.</span></span>  
  
 <span data-ttu-id="6beec-147">Quando usado em `Do` loops aninhados, `Exit Do` o transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="6beec-147">When used within nested `Do` loops, `Exit Do` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6beec-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6beec-148">Example</span></span>  

 <span data-ttu-id="6beec-149">No exemplo a seguir, as instruções no loop continuam a ser executadas até que a `index` variável seja maior que 10.</span><span class="sxs-lookup"><span data-stu-id="6beec-149">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span> <span data-ttu-id="6beec-150">A `Until` cláusula está no final do loop.</span><span class="sxs-lookup"><span data-stu-id="6beec-150">The `Until` clause is at the end of the loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#131](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#131)]  
  
## <a name="example"></a><span data-ttu-id="6beec-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6beec-151">Example</span></span>  

 <span data-ttu-id="6beec-152">O exemplo a seguir usa uma `While` cláusula em vez de uma `Until` cláusula e `condition` é testada no início do loop em vez de no final.</span><span class="sxs-lookup"><span data-stu-id="6beec-152">The following example uses a `While` clause instead of an `Until` clause, and `condition` is tested at the start of the loop instead of at the end.</span></span>  
  
 [!code-vb[VbVbalrStatements#132](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#132)]  
  
## <a name="example"></a><span data-ttu-id="6beec-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6beec-153">Example</span></span>  

 <span data-ttu-id="6beec-154">No exemplo a seguir, `condition` interrompe o loop quando a `index` variável é maior que 100.</span><span class="sxs-lookup"><span data-stu-id="6beec-154">In the following example, `condition` stops the loop when the `index` variable is greater than 100.</span></span> <span data-ttu-id="6beec-155">No `If` entanto, a instrução no loop faz com que a `Exit Do` instrução pare o loop quando a variável de índice for maior que 10.</span><span class="sxs-lookup"><span data-stu-id="6beec-155">The `If` statement in the loop, however, causes the `Exit Do` statement to stop the loop when the index variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#133](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#133)]  
  
## <a name="example"></a><span data-ttu-id="6beec-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6beec-156">Example</span></span>  

 <span data-ttu-id="6beec-157">O exemplo a seguir lê todas as linhas em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="6beec-157">The following example reads all lines in a text file.</span></span> <span data-ttu-id="6beec-158">O <xref:System.IO.File.OpenText%2A> método abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres.</span><span class="sxs-lookup"><span data-stu-id="6beec-158">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="6beec-159">Na `Do...Loop` condição, o <xref:System.IO.StreamReader.Peek%2A> método de `StreamReader` determina se há caracteres adicionais.</span><span class="sxs-lookup"><span data-stu-id="6beec-159">In the `Do...Loop` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether there are any additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#134](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class10.vb#134)]  
  
## <a name="see-also"></a><span data-ttu-id="6beec-160">Confira também</span><span class="sxs-lookup"><span data-stu-id="6beec-160">See also</span></span>

- [<span data-ttu-id="6beec-161">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="6beec-161">Loop Structures</span></span>](../../programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="6beec-162">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="6beec-162">For...Next Statement</span></span>](for-next-statement.md)
- [<span data-ttu-id="6beec-163">Tipo de dados booliano</span><span class="sxs-lookup"><span data-stu-id="6beec-163">Boolean Data Type</span></span>](../data-types/boolean-data-type.md)
- [<span data-ttu-id="6beec-164">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="6beec-164">Nested Control Structures</span></span>](../../programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="6beec-165">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="6beec-165">Exit Statement</span></span>](exit-statement.md)
- [<span data-ttu-id="6beec-166">Instrução While...End While</span><span class="sxs-lookup"><span data-stu-id="6beec-166">While...End While Statement</span></span>](while-end-while-statement.md)
