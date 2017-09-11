---
title: While... End While Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.While
- vb.While...EndWhile
dev_langs:
- VB
helpviewer_keywords:
- While statement, While...End While
- While statement
- While...End While statements
ms.assetid: b931d1ce-e8ed-44d8-a13d-92a4f5458a1e
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 4cec1165abfeb756d8e20df7ca5c6d6e4a577dc6
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="whileend-while-statement-visual-basic"></a><span data-ttu-id="7fc79-102">Instrução While...End While (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fc79-102">While...End While Statement (Visual Basic)</span></span>
<span data-ttu-id="7fc79-103">Executa uma série de instruções desde que uma determinada condição é `True`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-103">Runs a series of statements as long as a given condition is `True`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fc79-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7fc79-104">Syntax</span></span>  
  
```  
While condition  
    [ statements ]  
    [ Continue While ]  
    [ statements ]  
    [ Exit While ]  
    [ statements ]  
End While  
```  
  
## <a name="parts"></a><span data-ttu-id="7fc79-105">Partes</span><span class="sxs-lookup"><span data-stu-id="7fc79-105">Parts</span></span>  
  
|<span data-ttu-id="7fc79-106">Termo</span><span class="sxs-lookup"><span data-stu-id="7fc79-106">Term</span></span>|<span data-ttu-id="7fc79-107">Definição</span><span class="sxs-lookup"><span data-stu-id="7fc79-107">Definition</span></span>|  
|---|---|  
|`condition`|<span data-ttu-id="7fc79-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7fc79-108">Required.</span></span> <span data-ttu-id="7fc79-109">Expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-109">`Boolean` expression.</span></span> <span data-ttu-id="7fc79-110">Se `condition` é `Nothing`, Visual Basic trata isso `False`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-110">If `condition` is `Nothing`, Visual Basic treats it as `False`.</span></span>|  
|`statements`|<span data-ttu-id="7fc79-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7fc79-111">Optional.</span></span> <span data-ttu-id="7fc79-112">Uma ou mais instruções após `While`, que cada tempo de execução `condition` é `True`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-112">One or more statements following `While`, which run every time `condition` is `True`.</span></span>|  
|`Continue While`|<span data-ttu-id="7fc79-113">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7fc79-113">Optional.</span></span> <span data-ttu-id="7fc79-114">Transfere o controle para a próxima iteração do `While` bloco.</span><span class="sxs-lookup"><span data-stu-id="7fc79-114">Transfers control to the next iteration of the `While` block.</span></span>|  
|`Exit While`|<span data-ttu-id="7fc79-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="7fc79-115">Optional.</span></span> <span data-ttu-id="7fc79-116">Transfere o controle do `While` bloco.</span><span class="sxs-lookup"><span data-stu-id="7fc79-116">Transfers control out of the `While` block.</span></span>|  
|`End While`|<span data-ttu-id="7fc79-117">Necessário.</span><span class="sxs-lookup"><span data-stu-id="7fc79-117">Required.</span></span> <span data-ttu-id="7fc79-118">Finaliza a definição do bloco `While`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-118">Terminates the definition of the `While` block.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7fc79-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="7fc79-119">Remarks</span></span>  
 <span data-ttu-id="7fc79-120">Use um `While...End While` estrutura quando você desejar repetir um conjunto de declarações por um número indefinido de vezes, enquanto uma condição permanece `True`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-120">Use a `While...End While` structure when you want to repeat a set of statements an indefinite number of times, as long as a condition remains `True`.</span></span> <span data-ttu-id="7fc79-121">Se você quiser mais flexibilidade com onde você testar a condição ou o resultado é testá-lo para, talvez você prefira a [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7fc79-121">If you want more flexibility with where you test the condition or what result you test it for, you might prefer the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md).</span></span> <span data-ttu-id="7fc79-122">Se você quiser repetir as declarações um determinado número de vezes, o [para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) geralmente é uma opção melhor.</span><span class="sxs-lookup"><span data-stu-id="7fc79-122">If you want to repeat the statements a set number of times, the [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) is usually a better choice.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7fc79-123">O `While` palavra-chave também é usada a [fazer... Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), o [cláusula Skip While](../../../visual-basic/language-reference/queries/skip-while-clause.md) e [cláusula Take While](../../../visual-basic/language-reference/queries/take-while-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7fc79-123">The `While` keyword is also used in the [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md), the [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md) and the [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md).</span></span>  
  
 <span data-ttu-id="7fc79-124">Se `condition` é `True`, todos os do `statements` execução até que o `End While` declaração é encontrada.</span><span class="sxs-lookup"><span data-stu-id="7fc79-124">If `condition` is `True`, all of the `statements` run until the `End While` statement is encountered.</span></span> <span data-ttu-id="7fc79-125">Controle retorna para o `While` instrução, e `condition` é verificada novamente.</span><span class="sxs-lookup"><span data-stu-id="7fc79-125">Control then returns to the `While` statement, and `condition` is again checked.</span></span> <span data-ttu-id="7fc79-126">Se `condition` ainda é `True`, o processo é repetido.</span><span class="sxs-lookup"><span data-stu-id="7fc79-126">If `condition` is still `True`, the process is repeated.</span></span> <span data-ttu-id="7fc79-127">Se ele tiver `False`, controle passa para a instrução que segue o `End While` instrução.</span><span class="sxs-lookup"><span data-stu-id="7fc79-127">If it’s `False`, control passes to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="7fc79-128">O `While` instrução sempre verifica a condição antes de iniciar o loop.</span><span class="sxs-lookup"><span data-stu-id="7fc79-128">The `While` statement always checks the condition before it starts the loop.</span></span> <span data-ttu-id="7fc79-129">Loop continua mantendo a condição `True`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-129">Looping continues while the condition remains `True`.</span></span> <span data-ttu-id="7fc79-130">Se `condition` é `False` quando você entra no loop, ela não executa uma única vez.</span><span class="sxs-lookup"><span data-stu-id="7fc79-130">If `condition` is `False` when you first enter the loop, it doesn’t run even once.</span></span>  
  
 <span data-ttu-id="7fc79-131">O `condition` normalmente resultados de uma comparação de dois valores, mas ele podem ser qualquer expressão que é avaliada como um [tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) valor (`True` ou `False`).</span><span class="sxs-lookup"><span data-stu-id="7fc79-131">The `condition` usually results from a comparison of two values, but it can be any expression that evaluates to a [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) value (`True` or `False`).</span></span> <span data-ttu-id="7fc79-132">Esta expressão pode incluir um valor de outro tipo de dados, como um tipo numérico, que foi convertido em `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7fc79-132">This expression can include a value of another data type, such as a numeric type, that has been converted to `Boolean`.</span></span>  
  
 <span data-ttu-id="7fc79-133">Você pode aninhar `While` loops colocando um loop dentro de outro.</span><span class="sxs-lookup"><span data-stu-id="7fc79-133">You can nest `While` loops by placing one loop within another.</span></span> <span data-ttu-id="7fc79-134">Você também pode aninhar diferentes tipos de estruturas de controle uma dentro da outra.</span><span class="sxs-lookup"><span data-stu-id="7fc79-134">You can also nest different kinds of control structures within one another.</span></span> <span data-ttu-id="7fc79-135">Para obter mais informações, consulte [estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span><span class="sxs-lookup"><span data-stu-id="7fc79-135">For more information, see [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md).</span></span>  
  
## <a name="exit-while"></a><span data-ttu-id="7fc79-136">Saída ao mesmo tempo</span><span class="sxs-lookup"><span data-stu-id="7fc79-136">Exit While</span></span>  
 <span data-ttu-id="7fc79-137">O [sair enquanto](../../../visual-basic/language-reference/statements/exit-statement.md) instrução pode fornecer outra maneira de sair de um `While` loop.</span><span class="sxs-lookup"><span data-stu-id="7fc79-137">The [Exit While](../../../visual-basic/language-reference/statements/exit-statement.md) statement can provide another way to exit a `While` loop.</span></span> <span data-ttu-id="7fc79-138">`Exit While`transfere o controle para a instrução que segue imediatamente o `End While` instrução.</span><span class="sxs-lookup"><span data-stu-id="7fc79-138">`Exit While` immediately transfers control to the statement that follows the `End While` statement.</span></span>  
  
 <span data-ttu-id="7fc79-139">Você normalmente usa `Exit While` depois que alguma condição é avaliada (por exemplo, em um `If...Then...Else` estrutura).</span><span class="sxs-lookup"><span data-stu-id="7fc79-139">You typically use `Exit While` after some condition is evaluated (for example, in an `If...Then...Else` structure).</span></span> <span data-ttu-id="7fc79-140">Você talvez queira encerrar um loop se você detectar uma condição que torna desnecessária ou impossível de se continuar iterando, como um valor errôneo ou uma solicitação de encerramento.</span><span class="sxs-lookup"><span data-stu-id="7fc79-140">You might want to exit a loop if you detect a condition that makes it unnecessary or impossible to continue iterating, such as an erroneous value or a termination request.</span></span> <span data-ttu-id="7fc79-141">Você pode usar `Exit While` quando você testa uma condição que pode causar uma *loop infinito*, que é um loop que pode executar um número extremamente grande ou mesmo infinito de vezes.</span><span class="sxs-lookup"><span data-stu-id="7fc79-141">You can use `Exit While` when you test for a condition that could cause an *endless loop*, which is a loop that could run an extremely large or even infinite number of times.</span></span> <span data-ttu-id="7fc79-142">Você pode usar `Exit While` para escapar do loop.</span><span class="sxs-lookup"><span data-stu-id="7fc79-142">You can then use `Exit While` to escape the loop.</span></span>  
  
 <span data-ttu-id="7fc79-143">Você pode colocar qualquer número de `Exit While` instruções em qualquer lugar no `While` loop.</span><span class="sxs-lookup"><span data-stu-id="7fc79-143">You can place any number of `Exit While` statements anywhere in the `While` loop.</span></span>  
  
 <span data-ttu-id="7fc79-144">Quando usado dentro aninhados `While` loops, `Exit While` transfere o controle para fora do loop interno e para o próximo nível mais alto de aninhamento.</span><span class="sxs-lookup"><span data-stu-id="7fc79-144">When used within nested `While` loops, `Exit While` transfers control out of the innermost loop and into the next higher level of nesting.</span></span>  
  
 <span data-ttu-id="7fc79-145">O `Continue While` instrução imediatamente transfere o controle para a próxima iteração do loop.</span><span class="sxs-lookup"><span data-stu-id="7fc79-145">The `Continue While` statement immediately transfers control to the next iteration of the loop.</span></span> <span data-ttu-id="7fc79-146">Para obter mais informações, consulte [continuar instrução](../../../visual-basic/language-reference/statements/continue-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7fc79-146">For more information, see [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fc79-147">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fc79-147">Example</span></span>  
 <span data-ttu-id="7fc79-148">No exemplo a seguir, as instruções no loop continuam a executar até o `index` variável é maior que 10.</span><span class="sxs-lookup"><span data-stu-id="7fc79-148">In the following example, the statements in the loop continue to run until the `index` variable is greater than 10.</span></span>  
  
 <span data-ttu-id="7fc79-149">[!code-vb[VbVbalrStatements&#171;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7fc79-149">[!code-vb[VbVbalrStatements#171](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fc79-150">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fc79-150">Example</span></span>  
 <span data-ttu-id="7fc79-151">O exemplo a seguir ilustra o uso do `Continue While` e `Exit While` instruções.</span><span class="sxs-lookup"><span data-stu-id="7fc79-151">The following example illustrates the use of the `Continue While` and `Exit While` statements.</span></span>  
  
 <span data-ttu-id="7fc79-152">[!code-vb[VbVbalrStatements&#172;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7fc79-152">[!code-vb[VbVbalrStatements#172](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fc79-153">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7fc79-153">Example</span></span>  
 <span data-ttu-id="7fc79-154">O exemplo a seguir lê todas as linhas em um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="7fc79-154">The following example reads all lines in a text file.</span></span> <span data-ttu-id="7fc79-155">O <xref:System.IO.File.OpenText%2A>método abre o arquivo e retorna um <xref:System.IO.StreamReader>que lê os caracteres.</xref:System.IO.StreamReader> </xref:System.IO.File.OpenText%2A></span><span class="sxs-lookup"><span data-stu-id="7fc79-155">The <xref:System.IO.File.OpenText%2A> method opens the file and returns a <xref:System.IO.StreamReader> that reads the characters.</span></span> <span data-ttu-id="7fc79-156">No `While` condição, o <xref:System.IO.StreamReader.Peek%2A>método o `StreamReader` determina se o arquivo contém caracteres adicionais.</xref:System.IO.StreamReader.Peek%2A></span><span class="sxs-lookup"><span data-stu-id="7fc79-156">In the `While` condition, the <xref:System.IO.StreamReader.Peek%2A> method of the `StreamReader` determines whether the file contains additional characters.</span></span>  
  
 <span data-ttu-id="7fc79-157">[!code-vb[VbVbalrStatements&#173;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7fc79-157">[!code-vb[VbVbalrStatements#173](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/while-end-while-statement_3.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc79-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fc79-158">See Also</span></span>  
 <span data-ttu-id="7fc79-159">[Estruturas de loop](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span><span class="sxs-lookup"><span data-stu-id="7fc79-159">[Loop Structures](../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md) </span></span>  
<span data-ttu-id="7fc79-160"> [Fazer... Instrução loop](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7fc79-160"> [Do...Loop Statement](../../../visual-basic/language-reference/statements/do-loop-statement.md) </span></span>  
<span data-ttu-id="7fc79-161"> [Para... Próxima instrução](../../../visual-basic/language-reference/statements/for-next-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7fc79-161"> [For...Next Statement](../../../visual-basic/language-reference/statements/for-next-statement.md) </span></span>  
<span data-ttu-id="7fc79-162"> [Tipo de dados Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) </span><span class="sxs-lookup"><span data-stu-id="7fc79-162"> [Boolean Data Type](../../../visual-basic/language-reference/data-types/boolean-data-type.md) </span></span>  
<span data-ttu-id="7fc79-163"> [Estruturas de controle aninhadas](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span><span class="sxs-lookup"><span data-stu-id="7fc79-163"> [Nested Control Structures](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md) </span></span>  
<span data-ttu-id="7fc79-164"> [Instrução Exit](../../../visual-basic/language-reference/statements/exit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7fc79-164"> [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md) </span></span>  
<span data-ttu-id="7fc79-165"> [Instrução Continue](../../../visual-basic/language-reference/statements/continue-statement.md)</span><span class="sxs-lookup"><span data-stu-id="7fc79-165"> [Continue Statement](../../../visual-basic/language-reference/statements/continue-statement.md)</span></span>

