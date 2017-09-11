---
title: "Como: criar uma expressão Lambda (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
caps.latest.revision: 27
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
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: edd475490dce81ff9cca32b5f9a5090d99f4d80d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="b8b93-102">Como criar uma expressão lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b8b93-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="b8b93-103">A *expressão lambda* é uma função ou sub-rotina que não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="b8b93-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="b8b93-104">Uma expressão lambda pode ser usada sempre que um tipo delegate é válido.</span><span class="sxs-lookup"><span data-stu-id="b8b93-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="b8b93-105">Para criar uma função de expressão lambda de linha única</span><span class="sxs-lookup"><span data-stu-id="b8b93-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="b8b93-106">Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Function`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8b93-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="b8b93-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="b8b93-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="b8b93-108">Entre parênteses, diretamente após `Function`, digite os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="b8b93-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="b8b93-109">Observe que você não especifica um nome após `Function`.</span><span class="sxs-lookup"><span data-stu-id="b8b93-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="b8b93-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="b8b93-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="b8b93-111">Após a lista de parâmetros, digite uma única expressão como corpo da função.</span><span class="sxs-lookup"><span data-stu-id="b8b93-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="b8b93-112">O valor que a expressão é avaliada como é o valor retornado pela função.</span><span class="sxs-lookup"><span data-stu-id="b8b93-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="b8b93-113">Você não usar um `As` cláusula para especificar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="b8b93-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="b8b93-114">[!code-vb[VbVbalrLambdas n º&1;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-114">[!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]</span></span>  
  
     <span data-ttu-id="b8b93-115">Você chama a expressão lambda passando um argumento integer.</span><span class="sxs-lookup"><span data-stu-id="b8b93-115">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="b8b93-116">[!code-vb[VbVbalrLambdas n º&2;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-116">[!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]</span></span>  
  
4.  <span data-ttu-id="b8b93-117">Como alternativa, o mesmo resultado é realizado pelo exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8b93-117">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     <span data-ttu-id="b8b93-118">[!code-vb[VbVbalrLambdas n º&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-118">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="b8b93-119">Para criar uma sub-rotina de expressão lambda de linha única</span><span class="sxs-lookup"><span data-stu-id="b8b93-119">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="b8b93-120">Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8b93-120">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="b8b93-121">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="b8b93-121">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="b8b93-122">Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="b8b93-122">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="b8b93-123">Observe que você não especifica um nome após `Sub`.</span><span class="sxs-lookup"><span data-stu-id="b8b93-123">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="b8b93-124">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="b8b93-124">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="b8b93-125">Após a lista de parâmetros, digite uma única instrução no corpo da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="b8b93-125">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     <span data-ttu-id="b8b93-126">[!code-vb[17 VbVbalrLambdas](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-126">[!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]</span></span>  
  
     <span data-ttu-id="b8b93-127">Você chama a expressão lambda passando um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8b93-127">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="b8b93-128">[!code-vb[VbVbalrLambdas n º&18;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-128">[!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="b8b93-129">Para criar uma função de expressão lambda com várias linhas</span><span class="sxs-lookup"><span data-stu-id="b8b93-129">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="b8b93-130">Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8b93-130">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="b8b93-131">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="b8b93-131">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="b8b93-132">Entre parênteses, diretamente após `Function`, digite os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="b8b93-132">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="b8b93-133">Observe que você não especifica um nome após `Function`.</span><span class="sxs-lookup"><span data-stu-id="b8b93-133">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="b8b93-134">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="b8b93-134">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="b8b93-135">Pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="b8b93-135">Press ENTER.</span></span> <span data-ttu-id="b8b93-136">O `End Function` instrução é adicionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b8b93-136">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="b8b93-137">Dentro do corpo da função, adicione o seguinte código para criar uma expressão e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="b8b93-137">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="b8b93-138">Você não usar um `As` cláusula para especificar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="b8b93-138">You do not use an `As` clause to specify the return type.</span></span>  
  
     <span data-ttu-id="b8b93-139">[!code-vb[19 VbVbalrLambdas](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-139">[!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]</span></span>  
  
     <span data-ttu-id="b8b93-140">Você chama a expressão lambda passando um argumento integer.</span><span class="sxs-lookup"><span data-stu-id="b8b93-140">You call the lambda expression by passing in an integer argument.</span></span>  
  
     <span data-ttu-id="b8b93-141">[!code-vb[20 VbVbalrLambdas](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-141">[!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]</span></span>  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="b8b93-142">Para criar uma sub-rotina de expressão lambda com várias linhas</span><span class="sxs-lookup"><span data-stu-id="b8b93-142">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="b8b93-143">Em qualquer situação em que um tipo delegate pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="b8b93-143">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="b8b93-144">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="b8b93-144">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="b8b93-145">Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="b8b93-145">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="b8b93-146">Observe que você não especifica um nome após `Sub`.</span><span class="sxs-lookup"><span data-stu-id="b8b93-146">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="b8b93-147">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="b8b93-147">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="b8b93-148">Pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="b8b93-148">Press ENTER.</span></span> <span data-ttu-id="b8b93-149">O `End Sub` instrução é adicionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b8b93-149">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="b8b93-150">Dentro do corpo da função, adicione o seguinte código para executar quando a sub-rotina é invocada.</span><span class="sxs-lookup"><span data-stu-id="b8b93-150">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     <span data-ttu-id="b8b93-151">[!code-vb[VbVbalrLambdas&#21;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-151">[!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]</span></span>  
  
     <span data-ttu-id="b8b93-152">Você chama a expressão lambda passando um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="b8b93-152">You call the lambda expression by passing in a string argument.</span></span>  
  
     <span data-ttu-id="b8b93-153">[!code-vb[VbVbalrLambdas&#22;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-153">[!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8b93-154">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8b93-154">Example</span></span>  
 <span data-ttu-id="b8b93-155">Um uso comum de expressões lambda é para definir uma função que pode ser passada como argumento para um parâmetro cujo tipo é `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="b8b93-155">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="b8b93-156">No exemplo a seguir, o <xref:System.Diagnostics.Process.GetProcesses%2A>método retorna uma matriz dos processos em execução no computador local.</xref:System.Diagnostics.Process.GetProcesses%2A></span><span class="sxs-lookup"><span data-stu-id="b8b93-156">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="b8b93-157">O <xref:System.Linq.Enumerable.Where%2A>método a partir de <xref:System.Linq.Enumerable>classe requer um `Boolean` delegar como seu argumento.</xref:System.Linq.Enumerable> </xref:System.Linq.Enumerable.Where%2A></span><span class="sxs-lookup"><span data-stu-id="b8b93-157">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="b8b93-158">A expressão lambda no exemplo é usada para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="b8b93-158">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="b8b93-159">Ele retorna `True` para cada processo que tem apenas um segmento, e aqueles selecionados na `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="b8b93-159">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 <span data-ttu-id="b8b93-160">[!code-vb[VbVbalrLambdas n º&10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-160">[!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]</span></span>  
  
 <span data-ttu-id="b8b93-161">O exemplo anterior é equivalente ao código a seguir, que é escrito em [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] sintaxe:</span><span class="sxs-lookup"><span data-stu-id="b8b93-161">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)] syntax:</span></span>  
  
 <span data-ttu-id="b8b93-162">[!code-vb[VbVbalrLambdas n º&11;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span><span class="sxs-lookup"><span data-stu-id="b8b93-162">[!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b93-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8b93-163">See Also</span></span>  
 <span data-ttu-id="b8b93-164"><xref:System.Linq.Enumerable></xref:System.Linq.Enumerable></span><span class="sxs-lookup"><span data-stu-id="b8b93-164"><xref:System.Linq.Enumerable></span></span>   
<span data-ttu-id="b8b93-165"> [Expressões lambda](./lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="b8b93-165"> [Lambda Expressions](./lambda-expressions.md) </span></span>  
<span data-ttu-id="b8b93-166"> [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8b93-166"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="b8b93-167"> [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8b93-167"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="b8b93-168"> [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="b8b93-168"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="b8b93-169"> [Como: passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="b8b93-169"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="b8b93-170"> [Instrução delegate](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span><span class="sxs-lookup"><span data-stu-id="b8b93-170"> [Delegate Statement](../../../../visual-basic/language-reference/statements/delegate-statement.md) </span></span>  
<span data-ttu-id="b8b93-171"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span><span class="sxs-lookup"><span data-stu-id="b8b93-171"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
