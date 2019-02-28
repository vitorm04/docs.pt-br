---
title: Expressões lambda (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: de09612ee978ee809ee07f0db2e37b14533760da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974803"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="c880a-102">Expressões lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c880a-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="c880a-103">Um *expressão lambda* é uma função ou sub-rotina sem um nome que pode ser usada sempre que um representante é válido.</span><span class="sxs-lookup"><span data-stu-id="c880a-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="c880a-104">Expressões lambda podem ser funções ou sub-rotinas e podem ser uma linha ou várias linhas.</span><span class="sxs-lookup"><span data-stu-id="c880a-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="c880a-105">Você pode passar valores do escopo atual para uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c880a-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c880a-106">O `RemoveHandler` instrução é uma exceção.</span><span class="sxs-lookup"><span data-stu-id="c880a-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="c880a-107">Você não pode passar uma expressão lambda para o parâmetro de representante `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="c880a-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="c880a-108">Criar expressões lambda usando o `Function` ou `Sub` palavra-chave, assim como criar uma função padrão ou a sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="c880a-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="c880a-109">No entanto, as expressões lambda são incluídas em uma instrução.</span><span class="sxs-lookup"><span data-stu-id="c880a-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="c880a-110">O exemplo a seguir é uma expressão lambda que aumenta seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="c880a-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="c880a-111">O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="c880a-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 <span data-ttu-id="c880a-112">O exemplo a seguir é uma expressão lambda que grava um valor no console.</span><span class="sxs-lookup"><span data-stu-id="c880a-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="c880a-113">O exemplo mostra os dois a sintaxe da expressão lambda de linha única e várias linhas de uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="c880a-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 <span data-ttu-id="c880a-114">Observe que, nos exemplos anteriores, as expressões lambda são atribuídas a um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="c880a-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="c880a-115">Sempre que você faz referência à variável, você pode invocar a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c880a-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="c880a-116">Você também pode declarar e chamar uma expressão lambda ao mesmo tempo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c880a-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 <span data-ttu-id="c880a-117">Uma expressão lambda pode ser retornada como o valor de uma chamada de função (conforme mostrado no exemplo o [contexto](#context) seção mais adiante neste tópico), ou passada como um argumento para um parâmetro que usa um tipo de delegado, como mostrado a seguir exemplo.</span><span class="sxs-lookup"><span data-stu-id="c880a-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="c880a-118">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="c880a-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="c880a-119">A sintaxe de uma expressão lambda lembra a de uma função padrão ou a sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="c880a-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="c880a-120">As diferenças são da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="c880a-120">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="c880a-121">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="c880a-121">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="c880a-122">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="c880a-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="c880a-123">As funções lambda de linha única não usam um `As` cláusula para designar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="c880a-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="c880a-124">Em vez disso, o tipo é inferido do valor que avalia o corpo da expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="c880a-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="c880a-125">Por exemplo, se o corpo da expressão lambda é `cust.City = "London"`, seu tipo de retorno é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c880a-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="c880a-126">Em funções lambda de várias linhas, você pode especificar um tipo de retorno usando um `As` cláusula, ou omita o `As` cláusula para que o tipo de retorno é inferido.</span><span class="sxs-lookup"><span data-stu-id="c880a-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="c880a-127">Quando o `As` cláusula é omitida para uma função lambda de várias linhas, o tipo de retorno é inferido como o tipo dominante de todos os `Return` instruções na função lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="c880a-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="c880a-128">O *tipo dominante* é um tipo exclusivo que podem ampliar o todos os outros tipos.</span><span class="sxs-lookup"><span data-stu-id="c880a-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="c880a-129">Se esse tipo exclusivo não puder ser determinado, o tipo dominante é o tipo exclusivo que todos os outros tipos na matriz podem restringir a.</span><span class="sxs-lookup"><span data-stu-id="c880a-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="c880a-130">Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`.</span><span class="sxs-lookup"><span data-stu-id="c880a-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="c880a-131">Nesse caso, se `Option Strict` é definido como `On`, ocorre um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="c880a-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="c880a-132">Por exemplo, se as expressões são fornecidos para o `Return` instrução contêm valores do tipo `Integer`, `Long`, e `Double`, a matriz resultante é do tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="c880a-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="c880a-133">Ambos `Integer` e `Long` ampliados com `Double` e somente `Double`.</span><span class="sxs-lookup"><span data-stu-id="c880a-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="c880a-134">Portanto, `Double` é o tipo dominante.</span><span class="sxs-lookup"><span data-stu-id="c880a-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="c880a-135">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c880a-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="c880a-136">O corpo de uma função de única linha deve ser uma expressão que retorna um valor, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="c880a-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="c880a-137">Não há nenhum `Return` instrução para funções de linha única.</span><span class="sxs-lookup"><span data-stu-id="c880a-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="c880a-138">O valor retornado pela função linha única é o valor da expressão no corpo da função.</span><span class="sxs-lookup"><span data-stu-id="c880a-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="c880a-139">O corpo de uma sub-rotina de linha única deve ser uma instrução de linha única.</span><span class="sxs-lookup"><span data-stu-id="c880a-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="c880a-140">Funções de linha única e as sub-rotinas não incluem um `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="c880a-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="c880a-141">Você pode especificar o tipo de dados de um parâmetro de expressão lambda usando o `As` palavra-chave ou o tipo de dados do parâmetro pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="c880a-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="c880a-142">Ou todos os parâmetros devem ter especificado devem ser deduzidos a tipos de dados ou todos.</span><span class="sxs-lookup"><span data-stu-id="c880a-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="c880a-143">`Optional` e `Paramarray` parâmetros não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="c880a-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="c880a-144">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="c880a-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="c880a-145">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="c880a-145">Async Lambdas</span></span>  
 <span data-ttu-id="c880a-146">Você pode facilmente criar expressões lambda e instruções que incorporem processamento assíncrono usando o [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md) palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="c880a-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="c880a-147">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="c880a-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
```vb  
Public Class Form1  
  
    Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
        ' ExampleMethodAsync returns a Task.  
        Await ExampleMethodAsync()  
        TextBox1.Text = vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="c880a-148">Você pode adicionar o mesmo manipulador de eventos usando um lambda async em um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c880a-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="c880a-149">Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c880a-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
```vb  
Public Class Form1  
  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AddHandler Button1.Click,   
            Async Sub(sender1, e1)  
                ' ExampleMethodAsync returns a Task.  
                Await ExampleMethodAsync()  
                TextBox1.Text = vbCrLf & "Control returned to Button1_ Click."  
            End Sub  
    End Sub  
  
    Async Function ExampleMethodAsync() As Task  
        ' The following line simulates a task-returning asynchronous process.  
        Await Task.Delay(1000)  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="c880a-150">Para obter mais informações sobre como criar e usar os métodos assíncronos, consulte [programação assíncrona com Async e Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="c880a-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <a name="context"></a> <span data-ttu-id="c880a-151">Contexto</span><span class="sxs-lookup"><span data-stu-id="c880a-151">Context</span></span>  
 <span data-ttu-id="c880a-152">Uma expressão lambda compartilha seu contexto com o escopo dentro do qual ele está definido.</span><span class="sxs-lookup"><span data-stu-id="c880a-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="c880a-153">Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="c880a-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="c880a-154">Isso inclui acesso a variáveis de membro, funções e sub-rotinas, `Me`, parâmetros e variáveis locais no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="c880a-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="c880a-155">Acesso a variáveis locais e parâmetros no escopo de contenção pode ultrapassar o tempo de vida desse escopo.</span><span class="sxs-lookup"><span data-stu-id="c880a-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="c880a-156">Desde que um delegado referindo-se a uma expressão lambda não está disponível para coleta de lixo, o acesso às variáveis no ambiente original é mantido.</span><span class="sxs-lookup"><span data-stu-id="c880a-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="c880a-157">No exemplo a seguir, a variável `target` é local para `makeTheGame`, o método no qual a expressão lambda `playTheGame` está definido.</span><span class="sxs-lookup"><span data-stu-id="c880a-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="c880a-158">Observe que a expressão lambda retornado, atribuído a `takeAGuess` na `Main`, ainda tem acesso à variável local `target`.</span><span class="sxs-lookup"><span data-stu-id="c880a-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 <span data-ttu-id="c880a-159">O exemplo a seguir demonstra uma ampla variedade de direitos de acesso da expressão lambda aninhada.</span><span class="sxs-lookup"><span data-stu-id="c880a-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="c880a-160">Quando a expressão lambda retornado é executada a partir `Main` como `aDel`, ela acessa estes elementos:</span><span class="sxs-lookup"><span data-stu-id="c880a-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="c880a-161">Um campo da classe na qual ela é definida: `aField`</span><span class="sxs-lookup"><span data-stu-id="c880a-161">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="c880a-162">Uma propriedade da classe na qual ela é definida: `aProp`</span><span class="sxs-lookup"><span data-stu-id="c880a-162">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="c880a-163">Um parâmetro de método `functionWithNestedLambda`, no qual ela está definida: `level1`</span><span class="sxs-lookup"><span data-stu-id="c880a-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="c880a-164">Uma variável local de `functionWithNestedLambda`: `localVar`</span><span class="sxs-lookup"><span data-stu-id="c880a-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="c880a-165">Um parâmetro da expressão lambda na qual ele está aninhado: `level2`</span><span class="sxs-lookup"><span data-stu-id="c880a-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="c880a-166">Converter em um tipo de delegado</span><span class="sxs-lookup"><span data-stu-id="c880a-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="c880a-167">Uma expressão lambda pode ser convertida implicitamente em um tipo de delegado compatível.</span><span class="sxs-lookup"><span data-stu-id="c880a-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="c880a-168">Para obter informações sobre os requisitos gerais para compatibilidade, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="c880a-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="c880a-169">Por exemplo, o exemplo de código a seguir mostra uma expressão lambda que converte implicitamente a `Func(Of Integer, Boolean)` ou uma assinatura do delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="c880a-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 <span data-ttu-id="c880a-170">O exemplo de código a seguir mostra uma expressão lambda que converte implicitamente a `Sub(Of Double, String, Double)` ou uma assinatura do delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="c880a-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 <span data-ttu-id="c880a-171">Quando você atribuir as expressões lambda a delegados ou passá-los como argumentos para procedimentos, você pode especificar os nomes de parâmetro mas omitir seus tipos de dados, permitindo que os tipos a ser retirado do delegado.</span><span class="sxs-lookup"><span data-stu-id="c880a-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c880a-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c880a-172">Examples</span></span>  
  
-   <span data-ttu-id="c880a-173">O exemplo a seguir define uma expressão lambda que retorna `True` se o argumento que permitem valor nulo tem um valor atribuído, e `False` se o valor for `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c880a-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
-   <span data-ttu-id="c880a-174">O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c880a-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="c880a-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c880a-175">See also</span></span>
- [<span data-ttu-id="c880a-176">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="c880a-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="c880a-177">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c880a-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c880a-178">Delegados</span><span class="sxs-lookup"><span data-stu-id="c880a-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="c880a-179">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="c880a-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="c880a-180">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="c880a-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="c880a-181">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="c880a-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="c880a-182">Como: Passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c880a-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="c880a-183">Como: Criar uma expressão Lambda</span><span class="sxs-lookup"><span data-stu-id="c880a-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="c880a-184">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="c880a-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
