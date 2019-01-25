---
title: 'Como: Criar uma expressão Lambda (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: e7302304fe6c44b0143d7f12ec272d597b313fdd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492396"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="231c1-102">Como: Criar uma expressão Lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="231c1-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="231c1-103">Um *expressão lambda* é uma função ou sub-rotina que não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="231c1-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="231c1-104">Uma expressão lambda pode ser usada sempre que um tipo de delegado é válido.</span><span class="sxs-lookup"><span data-stu-id="231c1-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="231c1-105">Para criar uma função de expressão lambda de linha única</span><span class="sxs-lookup"><span data-stu-id="231c1-105">To create a single-line lambda expression function</span></span>  
  
1.  <span data-ttu-id="231c1-106">Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="231c1-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="231c1-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="231c1-107">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="231c1-108">Entre parênteses, diretamente após `Function`, digite os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="231c1-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="231c1-109">Observe que você não especificar um nome após `Function`.</span><span class="sxs-lookup"><span data-stu-id="231c1-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="231c1-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="231c1-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3.  <span data-ttu-id="231c1-111">A seguir a lista de parâmetros, digite uma única expressão como corpo da função.</span><span class="sxs-lookup"><span data-stu-id="231c1-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="231c1-112">O valor que avalia a expressão é o valor retornado pela função.</span><span class="sxs-lookup"><span data-stu-id="231c1-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="231c1-113">Você não usar um `As` cláusula para especificar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="231c1-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_1.vb)]  
  
     <span data-ttu-id="231c1-114">Para chamar a expressão lambda, passando um argumento de inteiro.</span><span class="sxs-lookup"><span data-stu-id="231c1-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_2.vb)]  
  
4.  <span data-ttu-id="231c1-115">Como alternativa, o mesmo resultado é realizado pelo exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="231c1-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_3.vb)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="231c1-116">Para criar uma sub-rotina de expressão lambda de linha única</span><span class="sxs-lookup"><span data-stu-id="231c1-116">To create a single-line lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="231c1-117">Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="231c1-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="231c1-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="231c1-118">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="231c1-119">Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="231c1-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="231c1-120">Observe que você não especificar um nome após `Sub`.</span><span class="sxs-lookup"><span data-stu-id="231c1-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="231c1-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="231c1-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="231c1-122">A seguir a lista de parâmetros, digite uma única instrução, como o corpo da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="231c1-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_4.vb)]  
  
     <span data-ttu-id="231c1-123">Para chamar a expressão lambda, passando um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="231c1-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_5.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="231c1-124">Para criar uma função de expressão lambda com várias linhas</span><span class="sxs-lookup"><span data-stu-id="231c1-124">To create a multiline lambda expression function</span></span>  
  
1.  <span data-ttu-id="231c1-125">Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="231c1-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="231c1-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="231c1-126">`Dim add1 =`   `Function`</span></span>  
  
2.  <span data-ttu-id="231c1-127">Entre parênteses, diretamente após `Function`, digite os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="231c1-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="231c1-128">Observe que você não especificar um nome após `Function`.</span><span class="sxs-lookup"><span data-stu-id="231c1-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="231c1-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="231c1-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3.  <span data-ttu-id="231c1-130">Pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="231c1-130">Press ENTER.</span></span> <span data-ttu-id="231c1-131">O `End Function` instrução é adicionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="231c1-131">The `End Function` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="231c1-132">Dentro do corpo da função, adicione o seguinte código para criar uma expressão e o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="231c1-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="231c1-133">Você não usar um `As` cláusula para especificar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="231c1-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_6.vb)]  
  
     <span data-ttu-id="231c1-134">Para chamar a expressão lambda, passando um argumento de inteiro.</span><span class="sxs-lookup"><span data-stu-id="231c1-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_7.vb)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="231c1-135">Para criar uma sub-rotina de expressão lambda com várias linhas</span><span class="sxs-lookup"><span data-stu-id="231c1-135">To create a multiline lambda expression subroutine</span></span>  
  
1.  <span data-ttu-id="231c1-136">Em qualquer situação em que um tipo de delegado pode ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="231c1-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="231c1-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="231c1-137">`Dim add1 =`   `Sub`</span></span>  
  
2.  <span data-ttu-id="231c1-138">Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="231c1-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="231c1-139">Observe que você não especificar um nome após `Sub`.</span><span class="sxs-lookup"><span data-stu-id="231c1-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="231c1-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="231c1-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3.  <span data-ttu-id="231c1-141">Pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="231c1-141">Press ENTER.</span></span> <span data-ttu-id="231c1-142">O `End Sub` instrução é adicionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="231c1-142">The `End Sub` statement is automatically added.</span></span>  
  
4.  <span data-ttu-id="231c1-143">Dentro do corpo da função, adicione o seguinte código para ser executado quando a sub-rotina é invocada.</span><span class="sxs-lookup"><span data-stu-id="231c1-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_8.vb)]  
  
     <span data-ttu-id="231c1-144">Para chamar a expressão lambda, passando um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="231c1-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_9.vb)]  
  
## <a name="example"></a><span data-ttu-id="231c1-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="231c1-145">Example</span></span>  
 <span data-ttu-id="231c1-146">Um uso comum de expressões lambda é definir uma função que pode ser passada como o argumento para um parâmetro cujo tipo é `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="231c1-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="231c1-147">No exemplo a seguir, o <xref:System.Diagnostics.Process.GetProcesses%2A> método retorna uma matriz de processos em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="231c1-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="231c1-148">O <xref:System.Linq.Enumerable.Where%2A> método a partir de <xref:System.Linq.Enumerable> classe requer um `Boolean` delegar como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="231c1-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="231c1-149">A expressão lambda no exemplo é usada para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="231c1-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="231c1-150">Ele retorna `True` para cada processo que tem apenas um thread, e eles estão selecionados em `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="231c1-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_10.vb)]  
  
 <span data-ttu-id="231c1-151">O exemplo anterior é equivalente ao código a seguir, que é escrito em [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] sintaxe:</span><span class="sxs-lookup"><span data-stu-id="231c1-151">The previous example is equivalent to the following code, which is written in [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-a-lambda-expression_11.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="231c1-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="231c1-152">See also</span></span>
- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="231c1-153">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="231c1-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="231c1-154">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="231c1-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="231c1-155">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="231c1-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="231c1-156">Delegados</span><span class="sxs-lookup"><span data-stu-id="231c1-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="231c1-157">Como: Passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="231c1-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="231c1-158">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="231c1-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="231c1-159">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="231c1-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
