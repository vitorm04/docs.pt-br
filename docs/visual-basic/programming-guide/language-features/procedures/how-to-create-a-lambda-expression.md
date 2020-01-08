---
title: Como criar uma expressão lambda
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
ms.assetid: 3279bd5c-80f7-410a-a7ba-f7085ed36aa5
ms.openlocfilehash: 1c65841e4c124252cfa41bcd4d0c305a426687ee
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75632344"
---
# <a name="how-to-create-a-lambda-expression-visual-basic"></a><span data-ttu-id="32e1c-102">Como criar uma expressão lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="32e1c-102">How to: Create a Lambda Expression (Visual Basic)</span></span>
<span data-ttu-id="32e1c-103">Uma *expressão lambda* é uma função ou sub-rotina que não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="32e1c-103">A *lambda expression* is a function or subroutine that does not have a name.</span></span> <span data-ttu-id="32e1c-104">Uma expressão lambda pode ser usada sempre que um tipo delegado é válido.</span><span class="sxs-lookup"><span data-stu-id="32e1c-104">A lambda expression can be used wherever a delegate type is valid.</span></span>  
  
### <a name="to-create-a-single-line-lambda-expression-function"></a><span data-ttu-id="32e1c-105">Para criar uma função de expressão lambda de linha única</span><span class="sxs-lookup"><span data-stu-id="32e1c-105">To create a single-line lambda expression function</span></span>  
  
1. <span data-ttu-id="32e1c-106">Em qualquer situação em que um tipo delegado possa ser usado, digite a palavra-chave `Function`, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="32e1c-106">In any situation where a delegate type could be used, type the keyword `Function`, as in the following example:</span></span>  
  
     <span data-ttu-id="32e1c-107">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="32e1c-107">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="32e1c-108">Entre parênteses, diretamente após `Function`, digite os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="32e1c-108">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="32e1c-109">Observe que você não especifica um nome após `Function`.</span><span class="sxs-lookup"><span data-stu-id="32e1c-109">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="32e1c-110">`Dim add1 = Function`   `(num As Integer)`</span><span class="sxs-lookup"><span data-stu-id="32e1c-110">`Dim add1 = Function`   `(num As Integer)`</span></span>  
  
3. <span data-ttu-id="32e1c-111">Após a lista de parâmetros, digite uma única expressão como o corpo da função.</span><span class="sxs-lookup"><span data-stu-id="32e1c-111">Following the parameter list, type a single expression as the body of the function.</span></span> <span data-ttu-id="32e1c-112">O valor que a expressão avalia é o valor retornado pela função.</span><span class="sxs-lookup"><span data-stu-id="32e1c-112">The value that the expression evaluates to is the value returned by the function.</span></span> <span data-ttu-id="32e1c-113">Você não usa uma cláusula `As` para especificar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="32e1c-113">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
     <span data-ttu-id="32e1c-114">Você chama a expressão lambda passando um argumento inteiro.</span><span class="sxs-lookup"><span data-stu-id="32e1c-114">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
4. <span data-ttu-id="32e1c-115">Como alternativa, o mesmo resultado é realizado pelo exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="32e1c-115">Alternatively, the same result is accomplished by the following example:</span></span>  
  
     [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
### <a name="to-create-a-single-line-lambda-expression-subroutine"></a><span data-ttu-id="32e1c-116">Para criar uma sub-rotina de expressão lambda de linha única</span><span class="sxs-lookup"><span data-stu-id="32e1c-116">To create a single-line lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="32e1c-117">Em qualquer situação em que um tipo delegado possa ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="32e1c-117">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="32e1c-118">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="32e1c-118">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="32e1c-119">Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="32e1c-119">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="32e1c-120">Observe que você não especifica um nome após `Sub`.</span><span class="sxs-lookup"><span data-stu-id="32e1c-120">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="32e1c-121">`Dim add1 = Sub`   `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="32e1c-121">`Dim add1 = Sub`   `(msg As String)`</span></span>  
  
3. <span data-ttu-id="32e1c-122">Após a lista de parâmetros, digite uma única instrução como o corpo da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="32e1c-122">Following the parameter list, type a single statement as the body of the subroutine.</span></span>  
  
     [!code-vb[VbVbalrLambdas#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#17)]  
  
     <span data-ttu-id="32e1c-123">Você chama a expressão lambda passando um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="32e1c-123">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#18)]  
  
### <a name="to-create-a-multiline-lambda-expression-function"></a><span data-ttu-id="32e1c-124">Para criar uma função de expressão lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="32e1c-124">To create a multiline lambda expression function</span></span>  
  
1. <span data-ttu-id="32e1c-125">Em qualquer situação em que um tipo delegado possa ser usado, digite a palavra-chave `Function`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="32e1c-125">In any situation where a delegate type could be used, type the keyword `Function`, as shown in the following example.</span></span>  
  
     <span data-ttu-id="32e1c-126">`Dim add1 =`   `Function`</span><span class="sxs-lookup"><span data-stu-id="32e1c-126">`Dim add1 =`   `Function`</span></span>  
  
2. <span data-ttu-id="32e1c-127">Entre parênteses, diretamente após `Function`, digite os parâmetros da função.</span><span class="sxs-lookup"><span data-stu-id="32e1c-127">In parentheses, directly after `Function`, type the parameters of the function.</span></span> <span data-ttu-id="32e1c-128">Observe que você não especifica um nome após `Function`.</span><span class="sxs-lookup"><span data-stu-id="32e1c-128">Notice that you do not specify a name after `Function`.</span></span>  
  
     <span data-ttu-id="32e1c-129">`Dim add1 = Function`   `(index As Integer)`</span><span class="sxs-lookup"><span data-stu-id="32e1c-129">`Dim add1 = Function`   `(index As Integer)`</span></span>  
  
3. <span data-ttu-id="32e1c-130">Pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="32e1c-130">Press ENTER.</span></span> <span data-ttu-id="32e1c-131">A instrução `End Function` é adicionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="32e1c-131">The `End Function` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="32e1c-132">No corpo da função, adicione o código a seguir para criar uma expressão e retornar o valor.</span><span class="sxs-lookup"><span data-stu-id="32e1c-132">Within the body of the function, add the following code to create an expression and return the value.</span></span> <span data-ttu-id="32e1c-133">Você não usa uma cláusula `As` para especificar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="32e1c-133">You do not use an `As` clause to specify the return type.</span></span>  
  
     [!code-vb[VbVbalrLambdas#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#19)]  
  
     <span data-ttu-id="32e1c-134">Você chama a expressão lambda passando um argumento inteiro.</span><span class="sxs-lookup"><span data-stu-id="32e1c-134">You call the lambda expression by passing in an integer argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#20)]  
  
### <a name="to-create-a-multiline-lambda-expression-subroutine"></a><span data-ttu-id="32e1c-135">Para criar uma sub-rotina de expressão lambda de várias linhas</span><span class="sxs-lookup"><span data-stu-id="32e1c-135">To create a multiline lambda expression subroutine</span></span>  
  
1. <span data-ttu-id="32e1c-136">Em qualquer situação em que um tipo delegado possa ser usado, digite a palavra-chave `Sub`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="32e1c-136">In any situation where a delegate type could be used, type the keyword `Sub`, as shown in the following example:</span></span>  
  
     <span data-ttu-id="32e1c-137">`Dim add1 =`   `Sub`</span><span class="sxs-lookup"><span data-stu-id="32e1c-137">`Dim add1 =`   `Sub`</span></span>  
  
2. <span data-ttu-id="32e1c-138">Entre parênteses, diretamente após `Sub`, digite os parâmetros da sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="32e1c-138">In parentheses, directly after `Sub`, type the parameters of the subroutine.</span></span> <span data-ttu-id="32e1c-139">Observe que você não especifica um nome após `Sub`.</span><span class="sxs-lookup"><span data-stu-id="32e1c-139">Notice that you do not specify a name after `Sub`.</span></span>  
  
     <span data-ttu-id="32e1c-140">`Dim add1 = Sub`  `(msg As String)`</span><span class="sxs-lookup"><span data-stu-id="32e1c-140">`Dim add1 = Sub`  `(msg As String)`</span></span>  
  
3. <span data-ttu-id="32e1c-141">Pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="32e1c-141">Press ENTER.</span></span> <span data-ttu-id="32e1c-142">A instrução `End Sub` é adicionada automaticamente.</span><span class="sxs-lookup"><span data-stu-id="32e1c-142">The `End Sub` statement is automatically added.</span></span>  
  
4. <span data-ttu-id="32e1c-143">No corpo da função, adicione o seguinte código a ser executado quando a sub-rotina for invocada.</span><span class="sxs-lookup"><span data-stu-id="32e1c-143">Within the body of the function, add the following code to execute when the subroutine is invoked.</span></span>  
  
     [!code-vb[VbVbalrLambdas#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#21)]  
  
     <span data-ttu-id="32e1c-144">Você chama a expressão lambda passando um argumento de cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="32e1c-144">You call the lambda expression by passing in a string argument.</span></span>  
  
     [!code-vb[VbVbalrLambdas#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="32e1c-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="32e1c-145">Example</span></span>  
 <span data-ttu-id="32e1c-146">Um uso comum de expressões lambda é definir uma função que pode ser passada como o argumento para um parâmetro cujo tipo é `Delegate`.</span><span class="sxs-lookup"><span data-stu-id="32e1c-146">A common use of lambda expressions is to define a function that can be passed in as the argument for a parameter whose type is `Delegate`.</span></span> <span data-ttu-id="32e1c-147">No exemplo a seguir, o método <xref:System.Diagnostics.Process.GetProcesses%2A> retorna uma matriz dos processos em execução no computador local.</span><span class="sxs-lookup"><span data-stu-id="32e1c-147">In the following example, the <xref:System.Diagnostics.Process.GetProcesses%2A> method returns an array of the processes running on the local computer.</span></span> <span data-ttu-id="32e1c-148">O método <xref:System.Linq.Enumerable.Where%2A> da classe <xref:System.Linq.Enumerable> requer um delegado `Boolean` como seu argumento.</span><span class="sxs-lookup"><span data-stu-id="32e1c-148">The <xref:System.Linq.Enumerable.Where%2A> method from the <xref:System.Linq.Enumerable> class requires a `Boolean` delegate as its argument.</span></span> <span data-ttu-id="32e1c-149">A expressão lambda no exemplo é usada para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="32e1c-149">The lambda expression in the example is used for that purpose.</span></span> <span data-ttu-id="32e1c-150">Ele retorna `True` para cada processo que tem apenas um thread, e eles são selecionados em `filteredList`.</span><span class="sxs-lookup"><span data-stu-id="32e1c-150">It returns `True` for each process that has only one thread, and those are selected in `filteredList`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class4.vb#10)]  
  
 <span data-ttu-id="32e1c-151">O exemplo anterior é equivalente ao código a seguir, que é escrito na sintaxe de LINQ (consulta integrada à linguagem):</span><span class="sxs-lookup"><span data-stu-id="32e1c-151">The previous example is equivalent to the following code, which is written in Language-Integrated Query (LINQ) syntax:</span></span>  
  
 [!code-vb[VbVbalrLambdas#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class5.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="32e1c-152">Veja também</span><span class="sxs-lookup"><span data-stu-id="32e1c-152">See also</span></span>

- <xref:System.Linq.Enumerable>
- [<span data-ttu-id="32e1c-153">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="32e1c-153">Lambda Expressions</span></span>](./lambda-expressions.md)
- [<span data-ttu-id="32e1c-154">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="32e1c-154">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="32e1c-155">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="32e1c-155">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="32e1c-156">Delegados</span><span class="sxs-lookup"><span data-stu-id="32e1c-156">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="32e1c-157">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32e1c-157">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="32e1c-158">Instrução Delegate</span><span class="sxs-lookup"><span data-stu-id="32e1c-158">Delegate Statement</span></span>](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="32e1c-159">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="32e1c-159">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
