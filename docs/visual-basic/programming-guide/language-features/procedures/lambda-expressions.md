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
ms.openlocfilehash: e688beac18e782367bf39ddec8339df2b2735225
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928898"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="ed0f6-102">Expressões lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed0f6-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="ed0f6-103">Uma *expressão lambda* é uma função ou sub-rotina sem um nome que pode ser usado sempre que um delegado é válido.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="ed0f6-104">As expressões lambda podem ser funções ou sub-rotinas e podem ser de linha única ou várias linhas.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="ed0f6-105">Você pode passar valores do escopo atual para uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed0f6-106">A `RemoveHandler` instrução é uma exceção.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="ed0f6-107">Não é possível passar uma expressão lambda no para o parâmetro delegado `RemoveHandler`de.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="ed0f6-108">Você cria expressões lambda usando a `Function` palavra-chave ou `Sub` , assim como cria uma função ou sub-rotina padrão.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="ed0f6-109">No entanto, as expressões lambda são incluídas em uma instrução.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="ed0f6-110">O exemplo a seguir é uma expressão lambda que incrementa seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="ed0f6-111">O exemplo mostra a sintaxe de expressão lambda de linha única e de várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
 <span data-ttu-id="ed0f6-112">O exemplo a seguir é uma expressão lambda que grava um valor no console.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="ed0f6-113">O exemplo mostra a sintaxe de expressão lambda de linha única e de várias linhas para uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
 <span data-ttu-id="ed0f6-114">Observe que, nos exemplos anteriores, as expressões lambda são atribuídas a um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="ed0f6-115">Sempre que você se referir à variável, invocará a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="ed0f6-116">Você também pode declarar e invocar uma expressão lambda ao mesmo tempo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
 <span data-ttu-id="ed0f6-117">Uma expressão lambda pode ser retornada como o valor de uma chamada de função (como é mostrado no exemplo na seção de [contexto](#context) mais adiante neste tópico) ou passada como um argumento para um parâmetro que usa um tipo delegado, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 [!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="ed0f6-118">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="ed0f6-118">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="ed0f6-119">A sintaxe de uma expressão lambda é semelhante à de uma função padrão ou sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="ed0f6-120">As diferenças são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="ed0f6-120">The differences are as follows:</span></span>  
  
- <span data-ttu-id="ed0f6-121">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-121">A lambda expression does not have a name.</span></span>  
  
- <span data-ttu-id="ed0f6-122">Expressões lambda não podem ter modificadores, `Overloads` como ou. `Overrides`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
- <span data-ttu-id="ed0f6-123">As funções lambda de linha única não usam uma `As` cláusula para designar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="ed0f6-124">Em vez disso, o tipo é inferido do valor que o corpo da expressão lambda avalia.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="ed0f6-125">Por exemplo, se o corpo da expressão lambda for `cust.City = "London"`, seu tipo de retorno será. `Boolean`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
- <span data-ttu-id="ed0f6-126">Em funções lambda de várias linhas, você pode especificar um tipo de retorno usando uma `As` cláusula ou omitir a `As` cláusula para que o tipo de retorno seja inferido.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="ed0f6-127">Quando a `As` cláusula é omitida para uma função lambda de várias linhas, o tipo de retorno é inferido para ser o tipo dominante de `Return` todas as instruções na função lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="ed0f6-128">O *tipo dominante* é um tipo exclusivo para o qual todos os outros tipos podem ampliar.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="ed0f6-129">Se esse tipo exclusivo não puder ser determinado, o tipo dominante será o tipo exclusivo que todos os outros tipos na matriz podem restringir.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="ed0f6-130">Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="ed0f6-131">Nesse caso, se `Option Strict` for definido como `On`, ocorrerá um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="ed0f6-132">Por exemplo, se as expressões fornecidas para a `Return` instrução contiverem valores `Integer`do `Long`tipo, `Double`e, a matriz resultante será do `Double`tipo.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="ed0f6-133">`Integer` E amplie`Long` para e`Double` apenas .`Double`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="ed0f6-134">Portanto, `Double` é o tipo dominante.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="ed0f6-135">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="ed0f6-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
- <span data-ttu-id="ed0f6-136">O corpo de uma função de linha única deve ser uma expressão que retorne um valor, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="ed0f6-137">Não há nenhuma `Return` instrução para funções de linha única.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="ed0f6-138">O valor retornado pela função de linha única é o valor da expressão no corpo da função.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
- <span data-ttu-id="ed0f6-139">O corpo de uma sub-rotina de linha única deve ser uma instrução de linha única.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-139">The body of a single-line subroutine must be single-line statement.</span></span>  
  
- <span data-ttu-id="ed0f6-140">As funções e sub-rotinas de linha única não incluem uma `End Function` instrução ou. `End Sub`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
- <span data-ttu-id="ed0f6-141">Você pode especificar o tipo de dados de um parâmetro de expressão lambda usando `As` a palavra-chave ou o tipo de dados do parâmetro pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="ed0f6-142">Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-142">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
- <span data-ttu-id="ed0f6-143">`Optional`parâmetros `Paramarray` e não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
- <span data-ttu-id="ed0f6-144">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-144">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="ed0f6-145">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="ed0f6-145">Async Lambdas</span></span>  
 <span data-ttu-id="ed0f6-146">Você pode criar facilmente expressões lambda e instruções que incorporam o processamento assíncrono usando as palavras-chave operador [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [Await](../../../../visual-basic/language-reference/operators/await-operator.md) .</span><span class="sxs-lookup"><span data-stu-id="ed0f6-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="ed0f6-147">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="ed0f6-148">Você pode adicionar o mesmo manipulador de eventos usando um lambda assíncrono em uma [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ed0f6-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="ed0f6-149">Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="ed0f6-150">Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [programação assíncrona com Async e Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="ed0f6-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
## <a name="context"></a><span data-ttu-id="ed0f6-151">Noticioso</span><span class="sxs-lookup"><span data-stu-id="ed0f6-151">Context</span></span>  
 <span data-ttu-id="ed0f6-152">Uma expressão lambda compartilha seu contexto com o escopo no qual ele é definido.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="ed0f6-153">Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="ed0f6-154">Isso inclui acesso a variáveis de membro, funções e sub-rotinas `Me`, e parâmetros e variáveis locais no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="ed0f6-155">O acesso a variáveis locais e parâmetros no escopo de contenção pode se estender além do tempo de vida desse escopo.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="ed0f6-156">Desde que um delegado que se refira a uma expressão lambda não esteja disponível para a coleta de lixo, o acesso às variáveis no ambiente original é mantido.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="ed0f6-157">No exemplo a seguir, a `target` variável é local `makeTheGame`para, o método no qual a expressão `playTheGame` lambda é definida.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="ed0f6-158">Observe que a expressão lambda retornada, atribuída a `takeAGuess` no `Main`, ainda tem acesso à variável `target`local.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 [!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]  
  
 <span data-ttu-id="ed0f6-159">O exemplo a seguir demonstra a ampla variedade de direitos de acesso da expressão lambda aninhada.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="ed0f6-160">Quando a expressão lambda retornada é executada a `Main` partir `aDel`de, ela acessa esses elementos:</span><span class="sxs-lookup"><span data-stu-id="ed0f6-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
- <span data-ttu-id="ed0f6-161">Um campo da classe na qual está definido:`aField`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-161">A field of the class in which it is defined: `aField`</span></span>  
  
- <span data-ttu-id="ed0f6-162">Uma propriedade da classe na qual ela está definida:`aProp`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-162">A property of the class in which it is defined: `aProp`</span></span>  
  
- <span data-ttu-id="ed0f6-163">Um parâmetro do método `functionWithNestedLambda`, no qual ele é definido:`level1`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
- <span data-ttu-id="ed0f6-164">Uma variável local de `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
- <span data-ttu-id="ed0f6-165">Um parâmetro da expressão lambda no qual está aninhado:`level2`</span><span class="sxs-lookup"><span data-stu-id="ed0f6-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="ed0f6-166">Convertendo para um tipo delegado</span><span class="sxs-lookup"><span data-stu-id="ed0f6-166">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="ed0f6-167">Uma expressão lambda pode ser convertida implicitamente em um tipo de delegado compatível.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="ed0f6-168">Para obter informações sobre os requisitos gerais de compatibilidade, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="ed0f6-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="ed0f6-169">Por exemplo, o exemplo de código a seguir mostra uma expressão lambda que implicitamente `Func(Of Integer, Boolean)` converte para ou uma assinatura delegada correspondente.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]  
  
 <span data-ttu-id="ed0f6-170">O exemplo de código a seguir mostra uma expressão lambda que converte implicitamente em `Sub(Of Double, String, Double)` ou uma assinatura delegada correspondente.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 [!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]  
  
 <span data-ttu-id="ed0f6-171">Ao atribuir expressões lambda a delegados ou passá-las como argumentos para procedimentos, você pode especificar os nomes de parâmetro, mas omitir seus tipos de dados, permitindo que os tipos sejam extraídos do delegado.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ed0f6-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ed0f6-172">Examples</span></span>  
  
- <span data-ttu-id="ed0f6-173">O exemplo a seguir define uma expressão lambda que `True` retorna se o argumento anulável tem um valor atribuído e `False` se seu valor é `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-173">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]  
  
- <span data-ttu-id="ed0f6-174">O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="ed0f6-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="ed0f6-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ed0f6-175">See also</span></span>

- [<span data-ttu-id="ed0f6-176">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ed0f6-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="ed0f6-177">Introdução ao LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed0f6-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ed0f6-178">Delegados</span><span class="sxs-lookup"><span data-stu-id="ed0f6-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="ed0f6-179">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="ed0f6-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="ed0f6-180">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="ed0f6-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="ed0f6-181">Tipos de Valor Anulável</span><span class="sxs-lookup"><span data-stu-id="ed0f6-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="ed0f6-182">Como: Passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ed0f6-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="ed0f6-183">Como: Criar uma expressão lambda</span><span class="sxs-lookup"><span data-stu-id="ed0f6-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="ed0f6-184">Conversão de Delegado Reduzida</span><span class="sxs-lookup"><span data-stu-id="ed0f6-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
