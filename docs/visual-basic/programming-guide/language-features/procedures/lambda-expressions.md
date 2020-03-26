---
title: Expressões lambda
ms.date: 07/20/2015
f1_keywords:
- vb.LambdaFunction
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
ms.openlocfilehash: 1827eb5630ed217527de25fc9d9c2bb8994b9aff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249663"
---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="fb80c-102">Expressões lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb80c-102">Lambda Expressions (Visual Basic)</span></span>

<span data-ttu-id="fb80c-103">Uma *expressão lambda* é uma função ou subrotina sem um nome que pode ser usado onde um delegado é válido.</span><span class="sxs-lookup"><span data-stu-id="fb80c-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="fb80c-104">Expressões Lambda podem ser funções ou subrotinas e podem ser de linha única ou multi-linha.</span><span class="sxs-lookup"><span data-stu-id="fb80c-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="fb80c-105">Você pode passar valores do escopo atual para uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="fb80c-105">You can pass values from the current scope to a lambda expression.</span></span>

> [!NOTE]
> <span data-ttu-id="fb80c-106">A `RemoveHandler` declaração é uma exceção.</span><span class="sxs-lookup"><span data-stu-id="fb80c-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="fb80c-107">Você não pode passar uma expressão lambda `RemoveHandler`para o parâmetro delegado de .</span><span class="sxs-lookup"><span data-stu-id="fb80c-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>

<span data-ttu-id="fb80c-108">Você cria expressões lambda `Function` `Sub` usando a palavra-chave, assim como você cria uma função padrão ou subrotina.</span><span class="sxs-lookup"><span data-stu-id="fb80c-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="fb80c-109">No entanto, expressões lambda são incluídas em uma declaração.</span><span class="sxs-lookup"><span data-stu-id="fb80c-109">However, lambda expressions are included in a statement.</span></span>

<span data-ttu-id="fb80c-110">O exemplo a seguir é uma expressão lambda que incrementa seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="fb80c-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="fb80c-111">O exemplo mostra a sintaxe de expressão lambda de linha única e multi-linha para uma função.</span><span class="sxs-lookup"><span data-stu-id="fb80c-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>

[!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]

<span data-ttu-id="fb80c-112">O exemplo a seguir é uma expressão lambda que escreve um valor para o console.</span><span class="sxs-lookup"><span data-stu-id="fb80c-112">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="fb80c-113">O exemplo mostra a sintaxe de expressão lambda de linha única e multilinha para uma subrotina.</span><span class="sxs-lookup"><span data-stu-id="fb80c-113">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>

[!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]

<span data-ttu-id="fb80c-114">Observe que nos exemplos anteriores as expressões lambda são atribuídas a um nome variável.</span><span class="sxs-lookup"><span data-stu-id="fb80c-114">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="fb80c-115">Sempre que você se refere à variável, você invoca a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="fb80c-115">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="fb80c-116">Você também pode declarar e invocar uma expressão lambda ao mesmo tempo, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb80c-116">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]

<span data-ttu-id="fb80c-117">Uma expressão lambda pode ser devolvida como o valor de uma chamada de função (como é mostrado no exemplo na seção [Contexto](#context) mais tarde neste tópico), ou passada como um argumento para um parâmetro que toma um tipo de delegado, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb80c-117">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>

[!code-vb[VbVbalrLambdas#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class2.vb#8)]

## <a name="lambda-expression-syntax"></a><span data-ttu-id="fb80c-118">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="fb80c-118">Lambda Expression Syntax</span></span>

<span data-ttu-id="fb80c-119">A sintaxe de uma expressão lambda se assemelha à de uma função padrão ou subrotina.</span><span class="sxs-lookup"><span data-stu-id="fb80c-119">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="fb80c-120">As diferenças são:</span><span class="sxs-lookup"><span data-stu-id="fb80c-120">The differences are as follows:</span></span>

- <span data-ttu-id="fb80c-121">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="fb80c-121">A lambda expression does not have a name.</span></span>

- <span data-ttu-id="fb80c-122">Expressões lambda não podem ter `Overloads` modificadores, tais como ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="fb80c-122">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>

- <span data-ttu-id="fb80c-123">As funções de lambda de `As` linha única não usam uma cláusula para designar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="fb80c-123">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="fb80c-124">Em vez disso, o tipo é inferido do valor que o corpo da expressão lambda avalia.</span><span class="sxs-lookup"><span data-stu-id="fb80c-124">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="fb80c-125">Por exemplo, se o corpo da `cust.City = "London"`expressão lambda `Boolean`é, seu tipo de retorno é .</span><span class="sxs-lookup"><span data-stu-id="fb80c-125">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>

- <span data-ttu-id="fb80c-126">Em funções de lambda multi-linha, você pode `As` especificar um tipo `As` de retorno usando uma cláusula ou omitir a cláusula para que o tipo de retorno seja inferido.</span><span class="sxs-lookup"><span data-stu-id="fb80c-126">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="fb80c-127">Quando `As` a cláusula é omitida para uma função lambda multi-linha, o `Return` tipo de retorno é inferido como o tipo dominante de todas as instruções na função lambda multi-linha.</span><span class="sxs-lookup"><span data-stu-id="fb80c-127">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="fb80c-128">O *tipo dominante* é um tipo único que todos os outros tipos podem ampliar.</span><span class="sxs-lookup"><span data-stu-id="fb80c-128">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="fb80c-129">Se este tipo único não puder ser determinado, o tipo dominante é o tipo único que todos os outros tipos na matriz podem se restringir.</span><span class="sxs-lookup"><span data-stu-id="fb80c-129">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="fb80c-130">Se nenhum desses tipos exclusivos puder ser determinado, o tipo dominante será `Object`.</span><span class="sxs-lookup"><span data-stu-id="fb80c-130">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="fb80c-131">Neste caso, `Option Strict` se for `On`definido como , um erro de compilador ocorre.</span><span class="sxs-lookup"><span data-stu-id="fb80c-131">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>

     <span data-ttu-id="fb80c-132">Por exemplo, se as expressões fornecidas à `Return` declaração contiverem valores de `Integer`tipo `Long`e `Double`, a matriz resultante for do tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="fb80c-132">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="fb80c-133">Ambos `Integer` `Long` e `Double` ampliam `Double`para e somente .</span><span class="sxs-lookup"><span data-stu-id="fb80c-133">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="fb80c-134">Portanto, `Double` é o tipo dominante.</span><span class="sxs-lookup"><span data-stu-id="fb80c-134">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="fb80c-135">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="fb80c-135">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

- <span data-ttu-id="fb80c-136">O corpo de uma função de linha única deve ser uma expressão que retorna um valor, não uma declaração.</span><span class="sxs-lookup"><span data-stu-id="fb80c-136">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="fb80c-137">Não há `Return` declaração para funções de linha única.</span><span class="sxs-lookup"><span data-stu-id="fb80c-137">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="fb80c-138">O valor devolvido pela função de linha única é o valor da expressão no corpo da função.</span><span class="sxs-lookup"><span data-stu-id="fb80c-138">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>

- <span data-ttu-id="fb80c-139">O corpo de uma sub-rotina de linha única deve ser uma declaração de linha única.</span><span class="sxs-lookup"><span data-stu-id="fb80c-139">The body of a single-line subroutine must be single-line statement.</span></span>

- <span data-ttu-id="fb80c-140">Funções e subrotinas de linha `End Function` única `End Sub` não incluem uma ou declaração.</span><span class="sxs-lookup"><span data-stu-id="fb80c-140">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>

- <span data-ttu-id="fb80c-141">Você pode especificar o tipo de dados de `As` um parâmetro de expressão lambda usando a palavra-chave, ou o tipo de dados do parâmetro pode ser inferido.</span><span class="sxs-lookup"><span data-stu-id="fb80c-141">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="fb80c-142">Todos os parâmetros devem ter tipos de dados especificados ou todos devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="fb80c-142">Either all parameters must have specified data types or all must be inferred.</span></span>

- <span data-ttu-id="fb80c-143">`Optional`e `Paramarray` parâmetros não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="fb80c-143">`Optional` and `Paramarray` parameters are not permitted.</span></span>

- <span data-ttu-id="fb80c-144">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="fb80c-144">Generic parameters are not permitted.</span></span>

## <a name="async-lambdas"></a><span data-ttu-id="fb80c-145">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="fb80c-145">Async Lambdas</span></span>

<span data-ttu-id="fb80c-146">Você pode facilmente criar expressões e instruções lambda que incorporam processamento assíncrono usando as palavras-chave [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [Aguardo Operador.](../../../../visual-basic/language-reference/operators/await-operator.md)</span><span class="sxs-lookup"><span data-stu-id="fb80c-146">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="fb80c-147">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="fb80c-147">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>

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

<span data-ttu-id="fb80c-148">Você pode adicionar o mesmo manipulador de eventos usando uma lambda assíncrona em uma [declaração addhandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fb80c-148">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="fb80c-149">Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="fb80c-149">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>

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

<span data-ttu-id="fb80c-150">Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [Programação Assíncrona com Assync e Aguarde](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="fb80c-150">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

## <a name="context"></a><span data-ttu-id="fb80c-151">Contexto</span><span class="sxs-lookup"><span data-stu-id="fb80c-151">Context</span></span>

<span data-ttu-id="fb80c-152">Uma expressão lambda compartilha seu contexto com o escopo dentro do qual é definida.</span><span class="sxs-lookup"><span data-stu-id="fb80c-152">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="fb80c-153">Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="fb80c-153">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="fb80c-154">Isso inclui acesso a variáveis, funções e `Me`subs membros, e parâmetros e variáveis locais no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="fb80c-154">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>

<span data-ttu-id="fb80c-155">O acesso a variáveis e parâmetros locais no escopo de contenção pode se estender além da vida útil desse escopo.</span><span class="sxs-lookup"><span data-stu-id="fb80c-155">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="fb80c-156">Enquanto um delegado referente a uma expressão lambda não estiver disponível para coleta de lixo, o acesso às variáveis no ambiente original é mantido.</span><span class="sxs-lookup"><span data-stu-id="fb80c-156">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="fb80c-157">No exemplo a `target` seguir, `makeTheGame`a variável é local para `playTheGame` , o método no qual a expressão lambda é definida.</span><span class="sxs-lookup"><span data-stu-id="fb80c-157">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="fb80c-158">Observe que a expressão lambda retornada, atribuída a `takeAGuess` in `Main` `target`, ainda tem acesso à variável local .</span><span class="sxs-lookup"><span data-stu-id="fb80c-158">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>

[!code-vb[VbVbalrLambdas#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class6.vb#12)]

<span data-ttu-id="fb80c-159">O exemplo a seguir demonstra a ampla gama de direitos de acesso da expressão lambda aninhada.</span><span class="sxs-lookup"><span data-stu-id="fb80c-159">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="fb80c-160">Quando a expressão lambda retornada `Main` `aDel`é executada a partir de como, ele acessa esses elementos:</span><span class="sxs-lookup"><span data-stu-id="fb80c-160">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>

- <span data-ttu-id="fb80c-161">Um campo da classe em que é definido:`aField`</span><span class="sxs-lookup"><span data-stu-id="fb80c-161">A field of the class in which it is defined: `aField`</span></span>

- <span data-ttu-id="fb80c-162">Uma propriedade da classe em que é definida:`aProp`</span><span class="sxs-lookup"><span data-stu-id="fb80c-162">A property of the class in which it is defined: `aProp`</span></span>

- <span data-ttu-id="fb80c-163">Um parâmetro de `functionWithNestedLambda`método, no qual é definido:`level1`</span><span class="sxs-lookup"><span data-stu-id="fb80c-163">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>

- <span data-ttu-id="fb80c-164">Uma variável `functionWithNestedLambda`local de:`localVar`</span><span class="sxs-lookup"><span data-stu-id="fb80c-164">A local variable of `functionWithNestedLambda`: `localVar`</span></span>

- <span data-ttu-id="fb80c-165">Um parâmetro da expressão lambda em que está aninhado:`level2`</span><span class="sxs-lookup"><span data-stu-id="fb80c-165">A parameter of the lambda expression in which it is nested: `level2`</span></span>

 [!code-vb[VbVbalrLambdas#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class3.vb#9)]

## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="fb80c-166">Conversão para um tipo de delegado</span><span class="sxs-lookup"><span data-stu-id="fb80c-166">Converting to a Delegate Type</span></span>

<span data-ttu-id="fb80c-167">Uma expressão lambda pode ser implicitamente convertida para um tipo de delegado compatível.</span><span class="sxs-lookup"><span data-stu-id="fb80c-167">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="fb80c-168">Para obter informações sobre os requisitos gerais para compatibilidade, consulte [Conversão de Delegado Relaxado](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="fb80c-168">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="fb80c-169">Por exemplo, o exemplo de código a seguir mostra `Func(Of Integer, Boolean)` uma expressão lambda que implicitamente converte ou uma assinatura de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="fb80c-169">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#16)]

<span data-ttu-id="fb80c-170">O exemplo de código a seguir mostra uma `Sub(Of Double, String, Double)` expressão lambda que implicitamente se converte ou uma assinatura de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="fb80c-170">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>

[!code-vb[VbVbalrLambdas#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/class7.vb#23)]

<span data-ttu-id="fb80c-171">Quando você atribui expressões lambda aos delegados ou passa-as como argumentos para os procedimentos, você pode especificar os nomes dos parâmetros, mas omitir seus tipos de dados, deixando que os tipos sejam retirados do delegado.</span><span class="sxs-lookup"><span data-stu-id="fb80c-171">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>

## <a name="examples"></a><span data-ttu-id="fb80c-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fb80c-172">Examples</span></span>

- <span data-ttu-id="fb80c-173">O exemplo a seguir define uma `True` expressão lambda que retorna se o `False` argumento do `Nothing`tipo de valor anulado tiver um valor atribuído e se seu valor for .</span><span class="sxs-lookup"><span data-stu-id="fb80c-173">The following example defines a lambda expression that returns `True` if the nullable value type argument has an assigned value, and `False` if its value is `Nothing`.</span></span>

     [!code-vb[VbVbalrLambdas#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#4)]

- <span data-ttu-id="fb80c-174">O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="fb80c-174">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>

     [!code-vb[VbVbalrLambdas#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#5)]

## <a name="see-also"></a><span data-ttu-id="fb80c-175">Confira também</span><span class="sxs-lookup"><span data-stu-id="fb80c-175">See also</span></span>

- [<span data-ttu-id="fb80c-176">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="fb80c-176">Procedures</span></span>](./index.md)
- [<span data-ttu-id="fb80c-177">Introdução a LINQ no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb80c-177">Introduction to LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="fb80c-178">Delegados</span><span class="sxs-lookup"><span data-stu-id="fb80c-178">Delegates</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [<span data-ttu-id="fb80c-179">Declaração de função</span><span class="sxs-lookup"><span data-stu-id="fb80c-179">Function Statement</span></span>](../../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fb80c-180">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="fb80c-180">Sub Statement</span></span>](../../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fb80c-181">Tipos de valor anulados</span><span class="sxs-lookup"><span data-stu-id="fb80c-181">Nullable Value Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="fb80c-182">Como passar procedimentos para outro procedimento no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fb80c-182">How to: Pass Procedures to Another Procedure in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md)
- [<span data-ttu-id="fb80c-183">Como criar uma expressão lambda</span><span class="sxs-lookup"><span data-stu-id="fb80c-183">How to: Create a Lambda Expression</span></span>](./how-to-create-a-lambda-expression.md)
- [<span data-ttu-id="fb80c-184">Conversão de delegado reduzida</span><span class="sxs-lookup"><span data-stu-id="fb80c-184">Relaxed Delegate Conversion</span></span>](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
