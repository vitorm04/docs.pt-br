---
title: Instrução While...End While (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.While
- vb.While...EndWhile
helpviewer_keywords:
- While statement [Visual Basic], While...End While
- While statement [Visual Basic]
- While...End While statements [Visual Basic]
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
ms.openlocfilehash: 00ca0ad24231128b25a988921386d6bd3265e9a0
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58843702"
---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="b6442-102">Instrução While...End While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b6442-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="b6442-103">Executa uma série de instruções desde que uma determinada condição seja `True`.</span><span class="sxs-lookup"><span data-stu-id="b6442-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6442-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b6442-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="b6442-105">Partes</span><span class="sxs-lookup"><span data-stu-id="b6442-105">Parts</span></span>  
  
|<span data-ttu-id="b6442-106">Termo</span><span class="sxs-lookup"><span data-stu-id="b6442-106">Term</span></span>|<span data-ttu-id="b6442-107">Definição</span><span class="sxs-lookup"><span data-stu-id="b6442-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="b6442-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b6442-108">Required.</span></span> <span data-ttu-id="b6442-109">Expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b6442-109">`Boolean` expression.</span></span> <span data-ttu-id="b6442-110">Se `condition` está `Nothing`, Visual Basic trata isso `False`.</span><span class="sxs-lookup"><span data-stu-id="b6442-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="b6442-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b6442-111">Optional.</span></span> <span data-ttu-id="b6442-112">Um ou mais instruções após `While`, que cada tempo de execução `condition` é `True`.</span><span class="sxs-lookup"><span data-stu-id="b6442-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="b6442-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b6442-113">Optional.</span></span> <span data-ttu-id="b6442-114">Transfere o controle para a próxima iteração do `While` bloco.</span><span class="sxs-lookup"><span data-stu-id="b6442-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="b6442-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b6442-115">Optional.</span></span> <span data-ttu-id="b6442-116">Transfere o controle do `While` bloco.</span><span class="sxs-lookup"><span data-stu-id="b6442-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="b6442-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="b6442-117">Required.</span></span> <span data-ttu-id="b6442-118">Finaliza a definição do bloco `While`.</span><span class="sxs-lookup"><span data-stu-id="b6442-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6442-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="b6442-119">Remarks</span></span>  
 <span data-ttu-id="b6442-120">Use uma `While...End While` estrutura quando desejar repetir um conjunto de declarações por um número indefinido de vezes, desde que uma condição permanece `True`.</span><span class="sxs-lookup"><span data-stu-id="b6442-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="b6442-121">Se você quiser mais flexibilidade com onde você testar a condição ou o que resulta é testá-lo para, talvez você prefira o [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6442-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="b6442-122">Se você quiser repetir as declarações de um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="b6442-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b6442-123">O `While` palavra-chave também é usado no [fazer... Instrução de loop](../../../visual-basic/language-reference/statements/do-loop-statement.md), o [cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) e o [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="b6442-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="b6442-124">Se `condition` está `True`, todos os da `statements` execução até que o `End While` instrução for encontrada.</span><span class="sxs-lookup"><span data-stu-id="b6442-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="b6442-125">Controlar, em seguida, retorna para o `While` instrução, e `condition` é verificada novamente.</span><span class="sxs-lookup"><span data-stu-id="b6442-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="b6442-126">Se `condition` ainda é `True`, o processo é repetido.</span><span class="sxs-lookup"><span data-stu-id="b6442-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="b6442-127">Se ele tiver `False`, controle passa para a instrução que segue o `End While` instrução.</span><span class="sxs-lookup"><span data-stu-id="b6442-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="b6442-128">O `While` instrução sempre verifica a condição antes de iniciar o loop.</span><span class="sxs-lookup"><span data-stu-id="b6442-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="b6442-129">Um loop continua enquanto a condição permaneça `True`.</span><span class="sxs-lookup"><span data-stu-id="b6442-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="b6442-130">Se `condition` é `False` quando você entra pela primeira vez no loop, ele não será executado até mesmo uma vez.</span><span class="sxs-lookup"><span data-stu-id="b6442-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="b6442-131">O `condition` normalmente, os resultados de uma comparação entre dois valores, mas ele podem ser qualquer expressão que é avaliada como uma [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`).</span><span class="sxs-lookup"><span data-stu-id="b6442-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="b6442-132">Esta expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b6442-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="b6442-133">Você pode aninhar `While` loops colocando um loop dentro de outra.</span><span class="sxs-lookup"><span data-stu-id="b6442-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="b6442-134">Você também pode aninhar diferentes tipos de estruturas de controle dentro uns dos outros.</span><span class="sxs-lookup"><span data-stu-id="b6442-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="b6442-135">Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="b6442-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="b6442-136">Saída ao mesmo tempo</span><span class="sxs-lookup"><span data-stu-id="b6442-136">Exit While</span></span>  
 <span data-ttu-id="b6442-137">O [sair enquanto](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer a outra maneira de se sair um `While` loop.</span><span class="sxs-lookup"><span data-stu-id="b6442-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="b6442-138">`Exit While` transfere o controle para a instrução que segue imediatamente o `End While` instrução.</span><span class="sxs-lookup"><span data-stu-id="b6442-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="b6442-139">Normalmente, você usa `Exit While` depois que alguma condição é avaliada (por exemplo, em um `If...Then...Else` estrutura).</span><span class="sxs-lookup"><span data-stu-id="b6442-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="b6442-140">Você talvez queira encerrar um loop se você detectar uma condição que torna desnecessária ou impossível continuar a iteração, como um valor errado ou uma solicitação de encerramento.</span><span class="sxs-lookup"><span data-stu-id="b6442-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="b6442-141">Você pode usar `Exit While` quando você testa uma condição que poderia causar uma *um loop infinito*, que é um loop que possa ser executada um número muito grande ou mesmo infinito de vezes.</span><span class="sxs-lookup"><span data-stu-id="b6442-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="b6442-142">Você pode usar `Exit While` para escapar do loop.</span><span class="sxs-lookup"><span data-stu-id="b6442-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="b6442-143">Você pode colocar qualquer número de `Exit While` as instruções no `While` loop.</span><span class="sxs-lookup"><span data-stu-id="b6442-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="b6442-144">Quando usado dentro aninhados `While` loops, `Exit While` transfere o controle para fora do loop interno e para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="b6442-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="b6442-145">O `Continue While` imediatamente transfere o controle para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="b6442-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="b6442-146">Para obter mais informações, consulte [instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b6442-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6442-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6442-147">Example</span></span>  
 <span data-ttu-id="b6442-148">No exemplo a seguir, as instruções no loop continuam em execução até que o `index` variável é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="b6442-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 [!code-vb[VbVbalrStatements#171](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#171)]  
  
## <a name="example"></a><span data-ttu-id="b6442-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6442-149">Example</span></span>  
 <span data-ttu-id="b6442-150">O exemplo a seguir ilustra o uso do `Continue While` e `Exit While` instruções.</span><span class="sxs-lookup"><span data-stu-id="b6442-150">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 [!code-vb[VbVbalrStatements#172](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#172)]  
  
## <a name="example"></a><span data-ttu-id="b6442-151">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6442-151">Example</span></span>  
 <span data-ttu-id="b6442-152">O exemplo a seguir lê todas as linhas em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="b6442-152">The following example reads all lines in a text file.</span></span> <span data-ttu-id="b6442-153">O <xref:System.IO.File.OpenText%2A> abre o arquivo de método e retorna um <xref:System.IO.StreamReader> que lê os caracteres.</span><span class="sxs-lookup"><span data-stu-id="b6442-153">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="b6442-154">No `While` condição, o <xref:System.IO.StreamReader.Peek%2A> método o `StreamReader` determina se o arquivo contém caracteres adicionais.</span><span class="sxs-lookup"><span data-stu-id="b6442-154">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 [!code-vb[VbVbalrStatements#173](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class14.vb#173)]  
  
## <a name="see-also"></a><span data-ttu-id="b6442-155">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b6442-155">See also</span></span>

- [<span data-ttu-id="b6442-156">Estruturas de Loop</span><span class="sxs-lookup"><span data-stu-id="b6442-156">Loop Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="b6442-157">Instrução Do...Loop</span><span class="sxs-lookup"><span data-stu-id="b6442-157">Do...Loop Statement</span></span>](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [<span data-ttu-id="b6442-158">Instrução For...Next</span><span class="sxs-lookup"><span data-stu-id="b6442-158">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="b6442-159">Tipo de Dados Boolean</span><span class="sxs-lookup"><span data-stu-id="b6442-159">Boolean Data Type</span></span>](../../../visual-basic/language-reference/data-types/boolean-data-type.md)
- [<span data-ttu-id="b6442-160">Estruturas de Controle Aninhadas</span><span class="sxs-lookup"><span data-stu-id="b6442-160">Nested Control Structures</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="b6442-161">Instrução Exit</span><span class="sxs-lookup"><span data-stu-id="b6442-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)
- [<span data-ttu-id="b6442-162">Instrução Continue</span><span class="sxs-lookup"><span data-stu-id="b6442-162">Continue Statement</span></span>](../../../visual-basic/language-reference/statements/continue-statement.md)
