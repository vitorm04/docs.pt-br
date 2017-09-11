---
title: Para... Next Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Step
- vb.Next
- vb.To
- vb.for
dev_langs:
- VB
helpviewer_keywords:
- infinite loops
- Next keyword, For...Next statements
- For keyword [Visual Basic], For...Next statements
- Step keyword, For...Next statements
- operator overloading, For...Next statement
- To keyword, For...Next statements
- endless loops
- loops, endless
- instructions, repeating
- Next statement, For...Next
- For...Next statements
- loop structures, For...Next
- loops, infinite
- Exit statement, For...Next statements
- For statement
ms.assetid: f5fc0d51-67ce-4c36-9f09-31c9a91c94e9
caps.latest.revision: 64
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 74c5a867a1b3332b741f29a2fcae23eb5d07ae0a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="fornext-statement-visual-basic"></a><span data-ttu-id="507f2-102">Instrução For...Next (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="507f2-102">For...Next Statement (Visual Basic)</span></span>
<span data-ttu-id="507f2-103">Repete um grupo de instruções um número especificado de vezes.</span><span class="sxs-lookup"><span data-stu-id="507f2-103">Repeats a group of statements a specified number of times.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="507f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="507f2-104">Syntax</span></span>  
  
```  
For counter [ As datatype ] = start To end [ Step step ]  
    [ statements ]  
    [ Continue For ]  
    [ statements ]  
    [ Exit For ]  
    [ statements ]  
Next [ counter ]  
```  
  
## <a name="parts"></a><span data-ttu-id="507f2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="507f2-105">Parts</span></span>  
  
|<span data-ttu-id="507f2-106">Parte</span><span class="sxs-lookup"><span data-stu-id="507f2-106">Part</span></span>|<span data-ttu-id="507f2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="507f2-107">Description</span></span>|  
|----------|-----------------|  
|`counter`|<span data-ttu-id="507f2-108">Necessário o `For` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-108">Required in the `For` statement.</span></span> <span data-ttu-id="507f2-109">Variável numérica.</span><span class="sxs-lookup"><span data-stu-id="507f2-109">Numeric variable.</span></span> <span data-ttu-id="507f2-110">A variável de controle do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-110">The control variable for the loop.</span></span> <span data-ttu-id="507f2-111">Para obter mais informações, consulte [contra-argumento](#BKMK_Counter) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="507f2-111">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|  
|`datatype`|<span data-ttu-id="507f2-112">Opcional.</span><span class="sxs-lookup"><span data-stu-id="507f2-112">Optional.</span></span> <span data-ttu-id="507f2-113">Tipo de dados de `counter`.</span><span class="sxs-lookup"><span data-stu-id="507f2-113">Data type of `counter`.</span></span> <span data-ttu-id="507f2-114">Para obter mais informações, consulte [contra-argumento](#BKMK_Counter) mais adiante neste tópico.</span><span class="sxs-lookup"><span data-stu-id="507f2-114">For more information, see [Counter Argument](#BKMK_Counter) later in this topic.</span></span>|  
|`start`|<span data-ttu-id="507f2-115">Necessário.</span><span class="sxs-lookup"><span data-stu-id="507f2-115">Required.</span></span> <span data-ttu-id="507f2-116">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="507f2-116">Numeric expression.</span></span> <span data-ttu-id="507f2-117">O valor inicial de `counter`.</span><span class="sxs-lookup"><span data-stu-id="507f2-117">The initial value of `counter`.</span></span>|  
|`end`|<span data-ttu-id="507f2-118">Necessário.</span><span class="sxs-lookup"><span data-stu-id="507f2-118">Required.</span></span> <span data-ttu-id="507f2-119">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="507f2-119">Numeric expression.</span></span> <span data-ttu-id="507f2-120">O valor final do `counter`.</span><span class="sxs-lookup"><span data-stu-id="507f2-120">The final value of `counter`.</span></span>|  
|`step`|<span data-ttu-id="507f2-121">Opcional.</span><span class="sxs-lookup"><span data-stu-id="507f2-121">Optional.</span></span> <span data-ttu-id="507f2-122">Expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="507f2-122">Numeric expression.</span></span> <span data-ttu-id="507f2-123">O valor pelo qual `counter` é incrementado toda vez pelo loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-123">The amount by which `counter` is incremented each time through the loop.</span></span>|  
|`statements`|<span data-ttu-id="507f2-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="507f2-124">Optional.</span></span> <span data-ttu-id="507f2-125">Uma ou mais instruções entre `For` e `Next` que executam o número de vezes especificado.</span><span class="sxs-lookup"><span data-stu-id="507f2-125">One or more statements between `For` and `Next` that run the specified number of times.</span></span>|  
|`Continue For`|<span data-ttu-id="507f2-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="507f2-126">Optional.</span></span> <span data-ttu-id="507f2-127">Transfere o controle para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-127">Transfers control to the next loop iteration.</span></span>|  
|`Exit For`|<span data-ttu-id="507f2-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="507f2-128">Optional.</span></span> <span data-ttu-id="507f2-129">Transfere o controle do `For` loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-129">Transfers control out of the `For` loop.</span></span>|  
|`Next`|<span data-ttu-id="507f2-130">Necessário.</span><span class="sxs-lookup"><span data-stu-id="507f2-130">Required.</span></span> <span data-ttu-id="507f2-131">Finaliza a definição de `For` loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-131">Terminates the definition of the `For` loop.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="507f2-132">O `To` nesta declaração, a palavra-chave é usada para especificar o intervalo para o contador.</span><span class="sxs-lookup"><span data-stu-id="507f2-132">The `To` keyword is used in this statement to specify the range for the counter.</span></span> <span data-ttu-id="507f2-133">Você também pode usar essa palavra-chave no [selecione... Instrução Case](../../../visual-basic/language-reference/statements/select-case-statement.md) e nas declarações de matriz.</span><span class="sxs-lookup"><span data-stu-id="507f2-133">You can also use this keyword in the [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md) and in array declarations.</span></span> <span data-ttu-id="507f2-134">Para obter mais informações sobre declarações de matriz, consulte [instrução Dim](../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-134">For more information about array declarations, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).</span></span>  
  
## <a name="simple-examples"></a><span data-ttu-id="507f2-135">Exemplos simples</span><span class="sxs-lookup"><span data-stu-id="507f2-135">Simple Examples</span></span>  
 <span data-ttu-id="507f2-136">Você usa um `For`... `Next` estrutura quando quiser repetir um conjunto de instruções um número definido de vezes.</span><span class="sxs-lookup"><span data-stu-id="507f2-136">You use a `For`...`Next` structure when you want to repeat a set of statements a set number of times.</span></span>  
  
 <span data-ttu-id="507f2-137">No exemplo a seguir, o `index` variável começa com um valor de 1 e incrementado com cada iteração do loop, terminando após o valor de `index` atinge 5.</span><span class="sxs-lookup"><span data-stu-id="507f2-137">In the following example, the `index` variable starts with a value of 1 and is incremented with each iteration of the loop, ending after the value of `index` reaches 5.</span></span>  
  
 <span data-ttu-id="507f2-138">[!code-vb[VbVbalrStatements&#111;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-138">[!code-vb[VbVbalrStatements#111](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="507f2-139">No exemplo a seguir, o `number` variável começa em 2 e será reduzida 0,25 em cada iteração do loop, terminando após o valor do `number` chegar a 0.</span><span class="sxs-lookup"><span data-stu-id="507f2-139">In the following example, the `number` variable starts at 2 and is reduced by 0.25 on each iteration of the loop, ending after the value of `number` reaches 0.</span></span> <span data-ttu-id="507f2-140">O `Step` argumento `-.25` reduz o valor por 0,25 em cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-140">The `Step` argument of `-.25` reduces the value by 0.25 on each iteration of the loop.</span></span>  
  
 <span data-ttu-id="507f2-141">[!code-vb[VbVbalrStatements&#112;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-141">[!code-vb[VbVbalrStatements#112](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_2.vb)]</span></span>  
  
> [!TIP]
>  <span data-ttu-id="507f2-142">Um [enquanto... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) ou [fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) funciona bem quando você não sabe com antecedência quantas vezes para executar as instruções no loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-142">A [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) or [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) works well when you don't know in advance how many times to run the statements in the loop.</span></span> <span data-ttu-id="507f2-143">No entanto, quando você pretende executar o loop um número específico de vezes, uma `For`... `Next` loop é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="507f2-143">However, when you expect to run the loop a specific number of times, a `For`...`Next` loop is a better choice.</span></span> <span data-ttu-id="507f2-144">Determinar o número de iterações quando você entra no loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-144">You determine the number of iterations when you first enter the loop.</span></span>  
  
## <a name="nesting-loops"></a><span data-ttu-id="507f2-145">Loops aninhados</span><span class="sxs-lookup"><span data-stu-id="507f2-145">Nesting Loops</span></span>  
 <span data-ttu-id="507f2-146">Você pode aninhar `For` loops colocando um loop dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="507f2-146">You can nest `For` loops by putting one loop within another.</span></span> <span data-ttu-id="507f2-147">O exemplo a seguir demonstra aninhada `For`... `Next` estruturas que têm valores diferentes.</span><span class="sxs-lookup"><span data-stu-id="507f2-147">The following example demonstrates nested `For`...`Next` structures that have different step values.</span></span> <span data-ttu-id="507f2-148">O loop externo cria uma cadeia de caracteres para cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-148">The outer loop creates a string for every iteration of the loop.</span></span> <span data-ttu-id="507f2-149">Interno loop decrementa uma variável de contador de loop para cada iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-149">The inner loop decrements a loop counter variable for every iteration of the loop.</span></span>  
  
 <span data-ttu-id="507f2-150">[!code-vb[VbVbalrStatements&#113;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-150">[!code-vb[VbVbalrStatements#113](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="507f2-151">Ao aninhar loops, cada loop deve ter um único `counter` variável.</span><span class="sxs-lookup"><span data-stu-id="507f2-151">When nesting loops, each loop must have a unique `counter` variable.</span></span>  
  
 <span data-ttu-id="507f2-152">Você também pode aninhar diferentes tipos de estruturas de controle dentro do outro.</span><span class="sxs-lookup"><span data-stu-id="507f2-152">You can also nest different kinds control structures within each other.</span></span> <span data-ttu-id="507f2-153">Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-153">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-for-and-continue-for"></a><span data-ttu-id="507f2-154">Sair para e continuar</span><span class="sxs-lookup"><span data-stu-id="507f2-154">Exit For and Continue For</span></span>  
 <span data-ttu-id="507f2-155">O `Exit For` instrução imediatamente encerra o `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="507f2-155">The `Exit For` statement immediately exits the `For`…`Next`</span></span> <span data-ttu-id="507f2-156">loop for e transfere o controle para a instrução que segue o `Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-156">loop and transfers control to the statement that follows the `Next` statement.</span></span>  
  
 <span data-ttu-id="507f2-157">O `Continue For` instrução transfere o controle imediatamente para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-157">The `Continue For` statement transfers control immediately to the next iteration of the loop.</span></span> <span data-ttu-id="507f2-158">Para obter mais informações, consulte [continuar instrução](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-158">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
 <span data-ttu-id="507f2-159">O exemplo a seguir ilustra o uso do `Continue For` e `Exit For` instruções.</span><span class="sxs-lookup"><span data-stu-id="507f2-159">The following example illustrates the use of the `Continue For` and `Exit For` statements.</span></span>  
  
 <span data-ttu-id="507f2-160">[!code-vb[VbVbalrStatements&#115;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-160">[!code-vb[VbVbalrStatements#115](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_4.vb)]</span></span>  
  
 <span data-ttu-id="507f2-161">Você pode colocar qualquer número de `Exit For` instruções em um `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="507f2-161">You can put any number of `Exit For` statements in a `For`…`Next`</span></span> <span data-ttu-id="507f2-162">loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-162">loop.</span></span> <span data-ttu-id="507f2-163">Quando usado dentro aninhadas `For`...`Next`</span><span class="sxs-lookup"><span data-stu-id="507f2-163">When used within nested `For`…`Next`</span></span> <span data-ttu-id="507f2-164">loops, `Exit For` sai do loop interno e transfere o controle para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="507f2-164">loops, `Exit For` exits the innermost loop and transfers control to the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="507f2-165">`Exit For`é frequentemente usado após avaliar alguma condição (por exemplo, em um `If`... `Then`... `Else` estrutura).</span><span class="sxs-lookup"><span data-stu-id="507f2-165">`Exit For` is often used after you evaluate some condition (for example, in an `If`...`Then`...`Else` structure).</span></span> <span data-ttu-id="507f2-166">Você talvez queira usar `Exit For` para as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="507f2-166">You might want to use `Exit For` for the following conditions:</span></span>  
  
-   <span data-ttu-id="507f2-167">Continuando a iteração é desnecessária ou impossível.</span><span class="sxs-lookup"><span data-stu-id="507f2-167">Continuing to iterate is unnecessary or impossible.</span></span> <span data-ttu-id="507f2-168">Um valor errado ou uma solicitação de encerramento pode criar essa condição.</span><span class="sxs-lookup"><span data-stu-id="507f2-168">An erroneous value or a termination request might create this condition.</span></span>  
  
-   <span data-ttu-id="507f2-169">A `Try`... `Catch`... `Finally` instrução captura uma exceção.</span><span class="sxs-lookup"><span data-stu-id="507f2-169">A `Try`...`Catch`...`Finally` statement catches an exception.</span></span> <span data-ttu-id="507f2-170">Você pode usar `Exit For` no final o `Finally` bloco.</span><span class="sxs-lookup"><span data-stu-id="507f2-170">You might use `Exit For` at the end of the `Finally` block.</span></span>  
  
-   <span data-ttu-id="507f2-171">Você tem um loop infinito, o que é um loop que pode executar um número grande ou mesmo infinito de vezes.</span><span class="sxs-lookup"><span data-stu-id="507f2-171">You have an endless loop, which is a loop that could run a large or even infinite number of times.</span></span> <span data-ttu-id="507f2-172">Se você detectar tal condição, você pode usar `Exit For` para escapar do loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-172">If you detect such a condition, you can use `Exit For` to escape the loop.</span></span> <span data-ttu-id="507f2-173">Para obter mais informações, consulte [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-173">For more information, see [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span>  
  
## <a name="technical-implementation"></a><span data-ttu-id="507f2-174">Implementação Técnica</span><span class="sxs-lookup"><span data-stu-id="507f2-174">Technical Implementation</span></span>  
 <span data-ttu-id="507f2-175">Quando um `For`... `Next` loop é iniciado, Visual Basic avalia `start`, `end`, e `step`.</span><span class="sxs-lookup"><span data-stu-id="507f2-175">When a `For`...`Next` loop starts, Visual Basic evaluates `start`, `end`, and `step`.</span></span> <span data-ttu-id="507f2-176">Visual Basic avalia esses valores apenas nesse momento e, em seguida, atribui `start` para `counter`.</span><span class="sxs-lookup"><span data-stu-id="507f2-176">Visual Basic evaluates these values only at this time and then assigns `start` to `counter`.</span></span> <span data-ttu-id="507f2-177">Antes da instrução do bloco é executado, Visual Basic compara `counter` para `end`.</span><span class="sxs-lookup"><span data-stu-id="507f2-177">Before the statement block runs, Visual Basic compares `counter` to `end`.</span></span> <span data-ttu-id="507f2-178">Se `counter` já é maior do que o `end` valor (ou menor se `step` é negativo), o `For` loop termina e o controle passa para a instrução que segue o `Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-178">If `counter` is already larger than the `end` value (or smaller if `step` is negative), the `For` loop ends and control passes to the statement that follows the `Next` statement.</span></span> <span data-ttu-id="507f2-179">Caso contrário, o bloco de instrução é executada.</span><span class="sxs-lookup"><span data-stu-id="507f2-179">Otherwise, the statement block runs.</span></span>  
  
 <span data-ttu-id="507f2-180">Cada vez que o Visual Basic encontra o `Next` instrução, ele é incrementado `counter` por `step` e retorna para o `For` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-180">Each time Visual Basic encounters the `Next` statement, it increments `counter` by `step` and returns to the `For` statement.</span></span> <span data-ttu-id="507f2-181">Novamente, ele compara `counter` para `end`, e novamente ele executa o bloco ou sai do loop, dependendo do resultado.</span><span class="sxs-lookup"><span data-stu-id="507f2-181">Again it compares `counter` to `end`, and again it either runs the block or exits the loop, depending on the result.</span></span> <span data-ttu-id="507f2-182">Esse processo continua até `counter` passa `end` ou um `Exit For` declaração é encontrada.</span><span class="sxs-lookup"><span data-stu-id="507f2-182">This process continues until `counter` passes `end` or an `Exit For` statement is encountered.</span></span>  
  
 <span data-ttu-id="507f2-183">O loop não para até `counter` passou `end`.</span><span class="sxs-lookup"><span data-stu-id="507f2-183">The loop doesn't stop until `counter` has passed `end`.</span></span> <span data-ttu-id="507f2-184">Se `counter` é igual a `end`, o loop continua.</span><span class="sxs-lookup"><span data-stu-id="507f2-184">If `counter` is equal to `end`, the loop continues.</span></span> <span data-ttu-id="507f2-185">A comparação que determina se deve executar o bloco for `counter`  <=  `end` se `step` for positivo e `counter`  >=  `end` se `step` for negativo.</span><span class="sxs-lookup"><span data-stu-id="507f2-185">The comparison that determines whether to run the block is `counter` <= `end` if `step` is positive and `counter` >= `end` if `step` is negative.</span></span>  
  
 <span data-ttu-id="507f2-186">Se você alterar o valor de `counter` enquanto dentro de um loop, seu código pode ser mais difícil de ler e de depuração.</span><span class="sxs-lookup"><span data-stu-id="507f2-186">If you change the value of `counter` while inside a loop, your code might be more difficult to read and debug.</span></span> <span data-ttu-id="507f2-187">Alterar o valor de `start`, `end`, ou `step` não afeta os valores de iteração determinadas quando o loop foi acessado pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="507f2-187">Changing the value of `start`, `end`, or `step` doesn't affect the iteration values that were determined when the loop was first entered.</span></span>  
  
 <span data-ttu-id="507f2-188">Se você aninhar loops, o compilador sinaliza um erro se encontra o `Next` declaração de um nível de aninhamento externo antes do `Next` declaração de um nível interno.</span><span class="sxs-lookup"><span data-stu-id="507f2-188">If you nest loops, the compiler signals an error if it encounters the `Next` statement of an outer nesting level before the `Next` statement of an inner level.</span></span> <span data-ttu-id="507f2-189">No entanto, o compilador pode detectar isso sobreposição de erro somente se você especificar `counter` em cada `Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-189">However, the compiler can detect this overlapping error only if you specify `counter` in every `Next` statement.</span></span>  
  
### <a name="step-argument"></a><span data-ttu-id="507f2-190">Argumento de etapa</span><span class="sxs-lookup"><span data-stu-id="507f2-190">Step Argument</span></span>  
 <span data-ttu-id="507f2-191">O valor de `step` pode ser positivo ou negativo.</span><span class="sxs-lookup"><span data-stu-id="507f2-191">The value of `step` can be either positive or negative.</span></span> <span data-ttu-id="507f2-192">Esse parâmetro determina o processamento de loop de acordo com a tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="507f2-192">This parameter determines loop processing according to the following table:</span></span>  
  
|<span data-ttu-id="507f2-193">**Valor da etapa**</span><span class="sxs-lookup"><span data-stu-id="507f2-193">**Step value**</span></span>|<span data-ttu-id="507f2-194">**O loop é executado se**</span><span class="sxs-lookup"><span data-stu-id="507f2-194">**Loop executes if**</span></span>|  
|--------------------|--------------------------|  
|<span data-ttu-id="507f2-195">Positivo ou zero</span><span class="sxs-lookup"><span data-stu-id="507f2-195">Positive or zero</span></span>|`counter` <= `end`|  
|<span data-ttu-id="507f2-196">Negativo</span><span class="sxs-lookup"><span data-stu-id="507f2-196">Negative</span></span>|`counter` >= `end`|  
  
 <span data-ttu-id="507f2-197">O valor padrão de `step` é 1.</span><span class="sxs-lookup"><span data-stu-id="507f2-197">The default value of `step` is 1.</span></span>  
  
###  <span data-ttu-id="507f2-198"><a name="BKMK_Counter"></a>Argumento do contador</span><span class="sxs-lookup"><span data-stu-id="507f2-198"><a name="BKMK_Counter"></a> Counter Argument</span></span>  
 <span data-ttu-id="507f2-199">A tabela a seguir indica se `counter` define uma nova variável local com escopo para todo o `For…Next` loop.</span><span class="sxs-lookup"><span data-stu-id="507f2-199">The following table indicates whether `counter` defines a new local variable that’s scoped to the entire `For…Next` loop.</span></span> <span data-ttu-id="507f2-200">Essa decisão depende se `datatype` está presente e se `counter` já está definido.</span><span class="sxs-lookup"><span data-stu-id="507f2-200">This determination depends on whether `datatype` is present and whether `counter` is already defined.</span></span>  
  
|<span data-ttu-id="507f2-201">É `datatype` presente?</span><span class="sxs-lookup"><span data-stu-id="507f2-201">Is `datatype` present?</span></span>|<span data-ttu-id="507f2-202">É `counter` já definido?</span><span class="sxs-lookup"><span data-stu-id="507f2-202">Is `counter` already defined?</span></span>|<span data-ttu-id="507f2-203">Resultado (se `counter` define uma nova variável local com escopo para todo o `For...Next` loop)</span><span class="sxs-lookup"><span data-stu-id="507f2-203">Result (whether `counter` defines a new local variable that’s scoped to the entire `For...Next` loop)</span></span>|  
|----------------------------|-----------------------------------|-------------------------------------------------------------------------------------------------------------|  
|<span data-ttu-id="507f2-204">Não</span><span class="sxs-lookup"><span data-stu-id="507f2-204">No</span></span>|<span data-ttu-id="507f2-205">Sim</span><span class="sxs-lookup"><span data-stu-id="507f2-205">Yes</span></span>|<span data-ttu-id="507f2-206">Não, porque `counter` já está definido.</span><span class="sxs-lookup"><span data-stu-id="507f2-206">No, because `counter` is already defined.</span></span> <span data-ttu-id="507f2-207">Se o escopo de `counter` não são locais para o procedimento, ocorre um aviso de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="507f2-207">If the scope of `counter` isn't local to the procedure, a compile-time warning occurs.</span></span>|  
|<span data-ttu-id="507f2-208">Não</span><span class="sxs-lookup"><span data-stu-id="507f2-208">No</span></span>|<span data-ttu-id="507f2-209">Não</span><span class="sxs-lookup"><span data-stu-id="507f2-209">No</span></span>|<span data-ttu-id="507f2-210">Sim.</span><span class="sxs-lookup"><span data-stu-id="507f2-210">Yes.</span></span> <span data-ttu-id="507f2-211">O tipo de dados é inferido a partir do `start`, `end`, e `step` expressões.</span><span class="sxs-lookup"><span data-stu-id="507f2-211">The data type is inferred from the `start`, `end`, and `step` expressions.</span></span> <span data-ttu-id="507f2-212">Para obter informações sobre a inferência de tipo, consulte [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) e [inferência de tipo Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-212">For information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>|  
|<span data-ttu-id="507f2-213">Sim</span><span class="sxs-lookup"><span data-stu-id="507f2-213">Yes</span></span>|<span data-ttu-id="507f2-214">Sim</span><span class="sxs-lookup"><span data-stu-id="507f2-214">Yes</span></span>|<span data-ttu-id="507f2-215">Sim, mas somente se existente `counter` variável é definida fora do procedimento.</span><span class="sxs-lookup"><span data-stu-id="507f2-215">Yes, but only if the existing `counter` variable is defined outside the procedure.</span></span> <span data-ttu-id="507f2-216">Essa variável permanece separada.</span><span class="sxs-lookup"><span data-stu-id="507f2-216">That variable remains separate.</span></span> <span data-ttu-id="507f2-217">Se o escopo de existente `counter` variável é local para o procedimento, ocorre um erro de tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="507f2-217">If the scope of the existing `counter` variable is local to the procedure, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="507f2-218">Sim</span><span class="sxs-lookup"><span data-stu-id="507f2-218">Yes</span></span>|<span data-ttu-id="507f2-219">Não</span><span class="sxs-lookup"><span data-stu-id="507f2-219">No</span></span>|<span data-ttu-id="507f2-220">Sim.</span><span class="sxs-lookup"><span data-stu-id="507f2-220">Yes.</span></span>|  
  
 <span data-ttu-id="507f2-221">O tipo de dados `counter` determina o tipo da iteração, que deve ser um dos seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="507f2-221">The data type of `counter` determines the type of the iteration, which must be one of the following types:</span></span>  
  
-   <span data-ttu-id="507f2-222">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span><span class="sxs-lookup"><span data-stu-id="507f2-222">A `Byte`, `SByte`, `UShort`, `Short`, `UInteger`, `Integer`, `ULong`, `Long`, `Decimal`, `Single`, or `Double`.</span></span>  
  
-   <span data-ttu-id="507f2-223">Uma enumeração que declarar usando um [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-223">An enumeration that you declare by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
-   <span data-ttu-id="507f2-224">Um `Object`.</span><span class="sxs-lookup"><span data-stu-id="507f2-224">An `Object`.</span></span>  
  
-   <span data-ttu-id="507f2-225">Um tipo `T` que tem os seguintes operadores, onde `B` é um tipo que pode ser usado em um `Boolean` expressão.</span><span class="sxs-lookup"><span data-stu-id="507f2-225">A type `T` that has the following operators, where `B` is a type that can be used in a `Boolean` expression.</span></span>  
  
     `Public Shared Operator >= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator <= (op1 As T, op2 As T) As B`  
  
     `Public Shared Operator - (op1 As T, op2 As T) As T`  
  
     `Public Shared Operator + (op1 As T, op2 As T) As T`  
  
 <span data-ttu-id="507f2-226">Opcionalmente, você pode especificar o `counter` variável no `Next` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-226">You can optionally specify the `counter` variable in the `Next` statement.</span></span> <span data-ttu-id="507f2-227">Essa sintaxe melhora a legibilidade do programa, especialmente se você tiver aninhado `For` loops.</span><span class="sxs-lookup"><span data-stu-id="507f2-227">This syntax improves the readability of your program, especially if you have nested `For` loops.</span></span> <span data-ttu-id="507f2-228">Você deve especificar a variável que aparece no correspondente `For` instrução.</span><span class="sxs-lookup"><span data-stu-id="507f2-228">You must specify the variable that appears in the corresponding `For` statement.</span></span>  
  
 <span data-ttu-id="507f2-229">O `start`, `end`, e `step` expressões podem ser avaliada como qualquer tipo de dados que amplia para o tipo de `counter`.</span><span class="sxs-lookup"><span data-stu-id="507f2-229">The `start`, `end`, and `step` expressions can evaluate to any data type that widens to the type of `counter`.</span></span> <span data-ttu-id="507f2-230">Se você usar um tipo definido pelo usuário para `counter`, talvez você precise definir o `CType` operador de conversão para converter os tipos de `start`, `end`, ou `step` para o tipo de `counter`.</span><span class="sxs-lookup"><span data-stu-id="507f2-230">If you use a user-defined type for `counter`, you might have to define the `CType` conversion operator to convert the types of `start`, `end`, or `step` to the type of `counter`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="507f2-231">Exemplo</span><span class="sxs-lookup"><span data-stu-id="507f2-231">Example</span></span>  
 <span data-ttu-id="507f2-232">O exemplo a seguir remove todos os elementos de uma lista genérica.</span><span class="sxs-lookup"><span data-stu-id="507f2-232">The following example removes all elements from a generic list.</span></span> <span data-ttu-id="507f2-233">Em vez de um [para cada uma... Próxima instrução](../../../visual-basic/language-reference/statements/for-each-next-statement.md), o exemplo mostra uma `For`... `Next` instrução que itera em ordem decrescente.</span><span class="sxs-lookup"><span data-stu-id="507f2-233">Instead of a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md), the example shows a `For`...`Next` statement that iterates in descending order.</span></span> <span data-ttu-id="507f2-234">O exemplo usa essa técnica porque o `removeAt` método faz com que elementos após o elemento removido para ter um valor de índice mais baixo.</span><span class="sxs-lookup"><span data-stu-id="507f2-234">The example uses this technique because the `removeAt` method causes elements after the removed element to have a lower index value.</span></span>  
  
 <span data-ttu-id="507f2-235">[!code-vb[VbVbalrStatements&#114;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-235">[!code-vb[VbVbalrStatements#114](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_5.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="507f2-236">Exemplo</span><span class="sxs-lookup"><span data-stu-id="507f2-236">Example</span></span>  
 <span data-ttu-id="507f2-237">O exemplo a seguir itera por meio de uma enumeração que é declarada usando um [instrução Enum](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="507f2-237">The following example iterates through an enumeration that's declared by using an [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 <span data-ttu-id="507f2-238">[!code-vb[VbVbalrStatements&#116;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-238">[!code-vb[VbVbalrStatements#116](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_6.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="507f2-239">Exemplo</span><span class="sxs-lookup"><span data-stu-id="507f2-239">Example</span></span>  
 <span data-ttu-id="507f2-240">No exemplo a seguir, os parâmetros da instrução usam uma classe que tenha sobrecargas do operador para o `+`, `-`, `>=`, e `<=` operadores.</span><span class="sxs-lookup"><span data-stu-id="507f2-240">In the following example, the statement parameters use a class that has operator overloads for the `+`, `-`, `>=`, and `<=` operators.</span></span>  
  
 <span data-ttu-id="507f2-241">[!code-vb[VbVbalrStatements&#117;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="507f2-241">[!code-vb[VbVbalrStatements#117](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/for-next-statement_7.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="507f2-242">Consulte também</span><span class="sxs-lookup"><span data-stu-id="507f2-242">See Also</span></span>  
 <span data-ttu-id="507f2-243"><xref:System.Collections.Generic.List%601></xref:System.Collections.Generic.List%601></span><span class="sxs-lookup"><span data-stu-id="507f2-243"><xref:System.Collections.Generic.List%601></span></span>   
<span data-ttu-id="507f2-244"> [Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="507f2-244"> [Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="507f2-245"> [While... End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) </span><span class="sxs-lookup"><span data-stu-id="507f2-245"> [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md) </span></span>  
<span data-ttu-id="507f2-246"> [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span><span class="sxs-lookup"><span data-stu-id="507f2-246"> [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span></span>  
<span data-ttu-id="507f2-247"> [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="507f2-247"> [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="507f2-248"> [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="507f2-248"> [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md) </span></span>  
<span data-ttu-id="507f2-249"> [Coleções](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)</span><span class="sxs-lookup"><span data-stu-id="507f2-249"> [Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)</span></span>
