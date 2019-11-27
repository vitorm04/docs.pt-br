---
title: Instrução While...End While
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 87f6fbd6147b6dbfbe08c93e862d58b9868f9201
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352744"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="90aa2-102">Instrução While...End While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="90aa2-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="90aa2-103">Executa uma série de instruções desde que uma determinada condição seja `True`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90aa2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90aa2-104">Syntax</span></span>  
  
```vb  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="90aa2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="90aa2-105">Parts</span></span>  
  
|<span data-ttu-id="90aa2-106">Termo</span><span class="sxs-lookup"><span data-stu-id="90aa2-106">Term</span></span>|<span data-ttu-id="90aa2-107">Definição</span><span class="sxs-lookup"><span data-stu-id="90aa2-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="90aa2-108">Necessária.</span><span class="sxs-lookup"><span data-stu-id="90aa2-108">Required.</span></span> <span data-ttu-id="90aa2-109">Expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-109">`Boolean` expression.</span></span> <span data-ttu-id="90aa2-110">Se `condition` for `Nothing`, Visual Basic o tratará como `False`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="90aa2-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="90aa2-111">Optional.</span></span> <span data-ttu-id="90aa2-112">Uma ou mais instruções a seguir `While`, que são executadas sempre que `condition` é `True`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="90aa2-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="90aa2-113">Optional.</span></span> <span data-ttu-id="90aa2-114">Transfere o controle para a próxima iteração do bloco de `While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="90aa2-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="90aa2-115">Optional.</span></span> <span data-ttu-id="90aa2-116">Transfere o controle do bloco de `While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="90aa2-117">Necessária.</span><span class="sxs-lookup"><span data-stu-id="90aa2-117">Required.</span></span> <span data-ttu-id="90aa2-118">Finaliza a definição do bloco `While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90aa2-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="90aa2-119">Remarks</span></span>  
 <span data-ttu-id="90aa2-120">Use uma estrutura de `While...End While` quando quiser repetir um conjunto de instruções um número indefinido de vezes, desde que uma condição permaneça `True`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="90aa2-121">Se você quiser mais flexibilidade com o local em que você testa a condição ou o resultado para o qual você o testa, talvez prefira o [... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="90aa2-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="90aa2-122">Se você quiser repetir as instruções um número definido de vezes, o [para... A próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) é geralmente uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="90aa2-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90aa2-123">A palavra-chave `While` também é usada no... [ Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), a [cláusula Skip while](../../../visual-basic/language-reference/queries/skip-while-clause.md) e a [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="90aa2-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="90aa2-124">Se `condition` for `True`, todos os `statements` executados até que a instrução `End While` seja encontrada.</span><span class="sxs-lookup"><span data-stu-id="90aa2-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="90aa2-125">Em seguida, o controle retorna à instrução `While` e `condition` é verificado novamente.</span><span class="sxs-lookup"><span data-stu-id="90aa2-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="90aa2-126">Se `condition` ainda estiver `True`, o processo será repetido.</span><span class="sxs-lookup"><span data-stu-id="90aa2-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="90aa2-127">Se for `False`, o controle passará para a instrução que segue a instrução `End While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="90aa2-128">A instrução `While` sempre verifica a condição antes de iniciar o loop.</span><span class="sxs-lookup"><span data-stu-id="90aa2-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="90aa2-129">O loop continua enquanto a condição permanece `True`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="90aa2-130">Se `condition` for `False` quando você inserir o loop pela primeira vez, ele não será executado de uma maneira.</span><span class="sxs-lookup"><span data-stu-id="90aa2-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="90aa2-131">O `condition` geralmente resulta de uma comparação de dois valores, mas pode ser qualquer expressão avaliada como um valor de [tipo de dados booliano](../../../visual-basic/language-reference/data-types/boolean-data-type.md) (`True` ou `False`).</span><span class="sxs-lookup"><span data-stu-id="90aa2-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="90aa2-132">Essa expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="90aa2-133">Você pode aninhar loops de `While` colocando um loop dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="90aa2-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="90aa2-134">Você também pode aninhar diferentes tipos de estruturas de controle entre si.</span><span class="sxs-lookup"><span data-stu-id="90aa2-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="90aa2-135">Para obter mais informações, consulte [estruturas de controle aninhado](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="90aa2-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="90aa2-136">Sair enquanto</span><span class="sxs-lookup"><span data-stu-id="90aa2-136">Exit While</span></span>  
 <span data-ttu-id="90aa2-137">A instrução [Exit while](../../../visual-basic/language-reference/statements/exit-statement.md) pode fornecer outra maneira de sair de um loop de `While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="90aa2-138">`Exit While` transfere imediatamente o controle para a instrução que segue a instrução `End While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="90aa2-139">Normalmente, você usa `Exit While` depois que alguma condição é avaliada (por exemplo, em uma estrutura de `If...Then...Else`).</span><span class="sxs-lookup"><span data-stu-id="90aa2-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="90aa2-140">Talvez você queira sair de um loop se detectar uma condição que o torne desnecessário ou impossível para continuar a iteração, como um valor errado ou uma solicitação de encerramento.</span><span class="sxs-lookup"><span data-stu-id="90aa2-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="90aa2-141">Você pode usar `Exit While` ao testar uma condição que poderia causar um *loop infinito*, que é um loop que poderia executar um número muito grande ou mesmo infinito de vezes.</span><span class="sxs-lookup"><span data-stu-id="90aa2-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="90aa2-142">Em seguida, você pode usar `Exit While` para escapar o loop.</span><span class="sxs-lookup"><span data-stu-id="90aa2-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="90aa2-143">Você pode inserir qualquer número de instruções `Exit While` em qualquer lugar no loop `While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="90aa2-144">Quando usado em loops de `While` aninhados, `Exit While` transfere o controle do loop mais interno e para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="90aa2-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="90aa2-145">A instrução `Continue While` transfere imediatamente o controle para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="90aa2-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="90aa2-146">Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="90aa2-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90aa2-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90aa2-147">Example</span></span>  
 <span data-ttu-id="90aa2-148">No exemplo a seguir, as instruções no loop continuam a ser executadas até que a variável de `index` seja maior que 10.</span><span class="sxs-lookup"><span data-stu-id="90aa2-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="90aa2-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90aa2-149">Example</span></span>  
 <span data-ttu-id="90aa2-150">O exemplo a seguir ilustra o uso das instruções `Continue While` e `Exit While`.</span><span class="sxs-lookup"><span data-stu-id="90aa2-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="90aa2-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="90aa2-151">Example</span></span>  
 <span data-ttu-id="90aa2-152">O exemplo a seguir lê todas as linhas em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="90aa2-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="90aa2-153">O método <xref:System.IO.File.OpenText%2A> abre o arquivo e retorna um <xref:System.IO.StreamReader> que lê os caracteres.</span><span class="sxs-lookup"><span data-stu-id="90aa2-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="90aa2-154">Na condição de `While`, o método <xref:System.IO.StreamReader.Peek%2A> da `StreamReader` determina se o arquivo contém caracteres adicionais.</span><span class="sxs-lookup"><span data-stu-id="90aa2-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="90aa2-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90aa2-155">See also</span></span>

- [<span data-ttu-id="90aa2-156">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="90aa2-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="90aa2-157">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="90aa2-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="90aa2-158">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="90aa2-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="90aa2-159">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="90aa2-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="90aa2-160">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="90aa2-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="90aa2-161">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="90aa2-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="90aa2-162">Instrução Continue</span><span class="sxs-lookup"><span data-stu-id="90aa2-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
