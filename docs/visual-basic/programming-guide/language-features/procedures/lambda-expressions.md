---
title: "Expressões lambda (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.LambdaFunction
dev_langs:
- VB
helpviewer_keywords:
- functions [Visual Basic], lambda expressions
- lambda expressions [Visual Basic]
- expressions [Visual Basic], lambda
- inline functions [Visual Basic]
ms.assetid: 137064b0-3928-4bfa-ba71-c3f9cbd951e2
caps.latest.revision: 52
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: e4624e5f20beeebf85656c893043030566200557
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="lambda-expressions-visual-basic"></a><span data-ttu-id="0cd56-102">Expressões lambda (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cd56-102">Lambda Expressions (Visual Basic)</span></span>
<span data-ttu-id="0cd56-103">A *expressão lambda* é uma função ou sub-rotina sem um nome que pode ser usado sempre que um delegado é válido.</span><span class="sxs-lookup"><span data-stu-id="0cd56-103">A *lambda expression* is a function or subroutine without a name that can be used wherever a delegate is valid.</span></span> <span data-ttu-id="0cd56-104">Expressões lambda podem ser funções ou sub-rotinas e podem ser uma linha ou várias linhas.</span><span class="sxs-lookup"><span data-stu-id="0cd56-104">Lambda expressions can be functions or subroutines and can be single-line or multi-line.</span></span> <span data-ttu-id="0cd56-105">Você pode passar valores do escopo atual para uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="0cd56-105">You can pass values from the current scope to a lambda expression.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cd56-106">O `RemoveHandler` instrução é uma exceção.</span><span class="sxs-lookup"><span data-stu-id="0cd56-106">The `RemoveHandler` statement is an exception.</span></span> <span data-ttu-id="0cd56-107">Você não pode passar uma expressão lambda para o parâmetro de representante `RemoveHandler`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-107">You cannot pass a lambda expression in for the delegate parameter of `RemoveHandler`.</span></span>  
  
 <span data-ttu-id="0cd56-108">Criar expressões lambda usando o `Function` ou `Sub` palavra-chave, como criar uma função padrão ou sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="0cd56-108">You create lambda expressions by using the `Function` or `Sub` keyword, just as you create a standard function or subroutine.</span></span> <span data-ttu-id="0cd56-109">No entanto, as expressões lambda são incluídas em uma instrução.</span><span class="sxs-lookup"><span data-stu-id="0cd56-109">However, lambda expressions are included in a statement.</span></span>  
  
 <span data-ttu-id="0cd56-110">O exemplo a seguir é uma expressão lambda que aumenta seu argumento e retorna o valor.</span><span class="sxs-lookup"><span data-stu-id="0cd56-110">The following example is a lambda expression that increments its argument and returns the value.</span></span> <span data-ttu-id="0cd56-111">O exemplo mostra os dois a sintaxe da expressão lambda de linha e de várias linhas para uma função.</span><span class="sxs-lookup"><span data-stu-id="0cd56-111">The example shows both the single-line and multi-line lambda expression syntax for a function.</span></span>  
  
 <span data-ttu-id="0cd56-112">[!code-vb[VbVbalrLambdas&#14;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-112">[!code-vb[VbVbalrLambdas#14](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_1.vb)]</span></span>  
  
 <span data-ttu-id="0cd56-113">O exemplo a seguir é uma expressão lambda que grava um valor para o console.</span><span class="sxs-lookup"><span data-stu-id="0cd56-113">The following example is a lambda expression that writes a value to the console.</span></span> <span data-ttu-id="0cd56-114">O exemplo mostra os dois a sintaxe da expressão lambda de linha e de várias linhas de uma sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="0cd56-114">The example shows both the single-line and multi-line lambda expression syntax for a subroutine.</span></span>  
  
 <span data-ttu-id="0cd56-115">[!code-vb[VbVbalrLambdas&#15;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-115">[!code-vb[VbVbalrLambdas#15](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_2.vb)]</span></span>  
  
 <span data-ttu-id="0cd56-116">Observe que, nos exemplos anteriores, as expressões lambda são atribuídas a um nome de variável.</span><span class="sxs-lookup"><span data-stu-id="0cd56-116">Notice that in the previous examples the lambda expressions are assigned to a variable name.</span></span> <span data-ttu-id="0cd56-117">Sempre que você fizer referência à variável, você chama a expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="0cd56-117">Whenever you refer to the variable, you invoke the lambda expression.</span></span> <span data-ttu-id="0cd56-118">Você também pode declarar e chamar uma expressão lambda ao mesmo tempo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cd56-118">You can also declare and invoke a lambda expression at the same time, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0cd56-119">[!code-vb[VbVbalrLambdas n º&3;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-119">[!code-vb[VbVbalrLambdas#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_3.vb)]</span></span>  
  
 <span data-ttu-id="0cd56-120">Uma expressão lambda pode ser retornada como o valor de uma chamada de função (como é mostrado no exemplo o [contexto](#context) seção mais adiante neste tópico), ou passado como um argumento para um parâmetro que usa um tipo delegado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cd56-120">A lambda expression can be returned as the value of a function call (as is shown in the example in the [Context](#context) section later in this topic), or passed in as an argument to a parameter that takes a delegate type, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0cd56-121">[!code-vb[VbVbalrLambdas n º&8;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-121">[!code-vb[VbVbalrLambdas#8](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_4.vb)]</span></span>  
  
## <a name="lambda-expression-syntax"></a><span data-ttu-id="0cd56-122">Sintaxe da expressão lambda</span><span class="sxs-lookup"><span data-stu-id="0cd56-122">Lambda Expression Syntax</span></span>  
 <span data-ttu-id="0cd56-123">A sintaxe de uma expressão lambda lembra de uma função padrão ou sub-rotina.</span><span class="sxs-lookup"><span data-stu-id="0cd56-123">The syntax of a lambda expression resembles that of a standard function or subroutine.</span></span> <span data-ttu-id="0cd56-124">As diferenças são as seguintes:</span><span class="sxs-lookup"><span data-stu-id="0cd56-124">The differences are as follows:</span></span>  
  
-   <span data-ttu-id="0cd56-125">Uma expressão lambda não tem um nome.</span><span class="sxs-lookup"><span data-stu-id="0cd56-125">A lambda expression does not have a name.</span></span>  
  
-   <span data-ttu-id="0cd56-126">Expressões lambda não podem ter modificadores, como `Overloads` ou `Overrides`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-126">Lambda expressions cannot have modifiers, such as `Overloads` or `Overrides`.</span></span>  
  
-   <span data-ttu-id="0cd56-127">Funções lambda de linha única não usam um `As` cláusula para designar o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="0cd56-127">Single-line lambda functions do not use an `As` clause to designate the return type.</span></span> <span data-ttu-id="0cd56-128">Em vez disso, o tipo é inferido do valor que o corpo da expressão lambda avalia.</span><span class="sxs-lookup"><span data-stu-id="0cd56-128">Instead, the type is inferred from the value that the body of the lambda expression evaluates to.</span></span> <span data-ttu-id="0cd56-129">Por exemplo, se o corpo da expressão lambda é `cust.City = "London"`, seu tipo de retorno é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-129">For example, if the body of the lambda expression is `cust.City = "London"`, its return type is `Boolean`.</span></span>  
  
-   <span data-ttu-id="0cd56-130">Funções lambda de várias linhas, você pode especificar um tipo de retorno usando uma `As` cláusula, ou omita o `As` cláusula para que o tipo de retorno é inferido.</span><span class="sxs-lookup"><span data-stu-id="0cd56-130">In multi-line lambda functions, you can either specify a return type by using an `As` clause, or omit the `As` clause so that the return type is inferred.</span></span> <span data-ttu-id="0cd56-131">Quando o `As` cláusula for omitida para uma função lambda de várias linhas, o tipo de retorno é inferido para ser do tipo dominante de todos os `Return` instruções na função lambda de várias linhas.</span><span class="sxs-lookup"><span data-stu-id="0cd56-131">When the `As` clause is omitted for a multi-line lambda function, the return type is inferred to be the dominant type from all the `Return` statements in the multi-line lambda function.</span></span> <span data-ttu-id="0cd56-132">O *tipo dominante* é um tipo exclusivo que podem ampliar o todos os outros tipos.</span><span class="sxs-lookup"><span data-stu-id="0cd56-132">The *dominant type* is a unique type that all other types can widen to.</span></span> <span data-ttu-id="0cd56-133">Se esse tipo exclusivo não pode ser determinado, o tipo dominante é o tipo exclusivo que todos os outros tipos de matriz podem restringir a.</span><span class="sxs-lookup"><span data-stu-id="0cd56-133">If this unique type cannot be determined, the dominant type is the unique type that all other types in the array can narrow to.</span></span> <span data-ttu-id="0cd56-134">Se nenhum desses tipos exclusivos pode ser determinado, o tipo dominante é `Object`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-134">If neither of these unique types can be determined, the dominant type is `Object`.</span></span> <span data-ttu-id="0cd56-135">Nesse caso, se `Option Strict` é definido como `On`, ocorre um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="0cd56-135">In this case, if `Option Strict` is set to `On`, a compiler error occurs.</span></span>  
  
     <span data-ttu-id="0cd56-136">Por exemplo, se as expressões fornecido para o `Return` instrução contêm valores do tipo `Integer`, `Long`, e `Double`, a matriz resultante é do tipo `Double`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-136">For example, if the expressions supplied to the `Return` statement contain values of type `Integer`, `Long`, and `Double`, the resulting array is of type `Double`.</span></span> <span data-ttu-id="0cd56-137">Ambos `Integer` e `Long` ampliar a `Double` e apenas `Double`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-137">Both `Integer` and `Long` widen to `Double` and only `Double`.</span></span> <span data-ttu-id="0cd56-138">Portanto, `Double` é o tipo dominante.</span><span class="sxs-lookup"><span data-stu-id="0cd56-138">Therefore, `Double` is the dominant type.</span></span> <span data-ttu-id="0cd56-139">Para obter mais informações, consulte [Widening e conversões de estreitamento](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="0cd56-139">For more information, see [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
-   <span data-ttu-id="0cd56-140">O corpo de uma função de única linha deve ser uma expressão que retorna um valor, não uma instrução.</span><span class="sxs-lookup"><span data-stu-id="0cd56-140">The body of a single-line function must be an expression that returns a value, not a statement.</span></span> <span data-ttu-id="0cd56-141">Não há nenhum `Return` instrução para funções de única linha.</span><span class="sxs-lookup"><span data-stu-id="0cd56-141">There is no `Return` statement for single-line functions.</span></span> <span data-ttu-id="0cd56-142">O valor retornado pela função linha é o valor da expressão no corpo da função.</span><span class="sxs-lookup"><span data-stu-id="0cd56-142">The value returned by the single-line function is the value of the expression in the body of the function.</span></span>  
  
-   <span data-ttu-id="0cd56-143">O corpo de uma sub-rotina de linha deve ser a instrução de linha única.</span><span class="sxs-lookup"><span data-stu-id="0cd56-143">The body of a single-line subroutine must be single-line statement.</span></span>  
  
-   <span data-ttu-id="0cd56-144">As sub-rotinas e funções de linha única não incluem um `End Function` ou `End Sub` instrução.</span><span class="sxs-lookup"><span data-stu-id="0cd56-144">Single-line functions and subroutines do not include an `End Function` or `End Sub` statement.</span></span>  
  
-   <span data-ttu-id="0cd56-145">Você pode especificar o tipo de dados de um parâmetro de expressão lambda usando o `As` pode ser inferido a palavra-chave ou o tipo de dados do parâmetro.</span><span class="sxs-lookup"><span data-stu-id="0cd56-145">You can specify the data type of a lambda expression parameter by using the `As` keyword, or the data type of the parameter can be inferred.</span></span> <span data-ttu-id="0cd56-146">Todos os parâmetros devem especificar todos ou tipos de dados devem ser inferidos.</span><span class="sxs-lookup"><span data-stu-id="0cd56-146">Either all parameters must have specified data types or all must be inferred.</span></span>  
  
-   <span data-ttu-id="0cd56-147">`Optional`e `Paramarray` parâmetros não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="0cd56-147">`Optional` and `Paramarray` parameters are not permitted.</span></span>  
  
-   <span data-ttu-id="0cd56-148">Parâmetros genéricos não são permitidos.</span><span class="sxs-lookup"><span data-stu-id="0cd56-148">Generic parameters are not permitted.</span></span>  
  
## <a name="async-lambdas"></a><span data-ttu-id="0cd56-149">Lambdas assíncronos</span><span class="sxs-lookup"><span data-stu-id="0cd56-149">Async Lambdas</span></span>  
 <span data-ttu-id="0cd56-150">Você pode facilmente criar expressões lambda e instruções que incorporem processamento assíncrono usando o [Async](../../../../visual-basic/language-reference/modifiers/async.md) e [operador Await](../../../../visual-basic/language-reference/operators/await-operator.md) palavras-chave.</span><span class="sxs-lookup"><span data-stu-id="0cd56-150">You can easily create lambda expressions and statements that incorporate asynchronous processing by using the [Async](../../../../visual-basic/language-reference/modifiers/async.md) and [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) keywords.</span></span> <span data-ttu-id="0cd56-151">Por exemplo, o exemplo do Windows Forms a seguir contém um manipulador de eventos que chama e espera um método assíncrono `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-151">For example, the following Windows Forms example contains an event handler that calls and awaits an async method, `ExampleMethodAsync`.</span></span>  
  
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
  
 <span data-ttu-id="0cd56-152">Você pode adicionar o mesmo manipulador de eventos usando um lambda async em um [instrução AddHandler](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0cd56-152">You can add the same event handler by using an async lambda in an [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="0cd56-153">Para adicionar esse manipulador, adicione um modificador `Async` antes da lista de parâmetros lambda, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="0cd56-153">To add this handler, add an `Async` modifier before the lambda parameter list, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="0cd56-154">Para obter mais informações sobre como criar e usar métodos assíncronos, consulte [programação assíncrona com Async e Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="0cd56-154">For more information about how to create and use async methods, see [Asynchronous Programming with Async and Await](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
##  <span data-ttu-id="0cd56-155"><a name="context"></a>Contexto</span><span class="sxs-lookup"><span data-stu-id="0cd56-155"><a name="context"></a> Context</span></span>  
 <span data-ttu-id="0cd56-156">Uma expressão lambda compartilha seu contexto com o escopo dentro do qual ela está definida.</span><span class="sxs-lookup"><span data-stu-id="0cd56-156">A lambda expression shares its context with the scope within which it is defined.</span></span> <span data-ttu-id="0cd56-157">Ele tem os mesmos direitos de acesso que qualquer código escrito no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="0cd56-157">It has the same access rights as any code written in the containing scope.</span></span> <span data-ttu-id="0cd56-158">Isso inclui acesso a variáveis de membro, funções e sub-rotinas, `Me`e parâmetros e variáveis locais no escopo de contenção.</span><span class="sxs-lookup"><span data-stu-id="0cd56-158">This includes access to member variables, functions and subs, `Me`, and parameters and local variables in the containing scope.</span></span>  
  
 <span data-ttu-id="0cd56-159">Acesso a variáveis locais e parâmetros no escopo de contenção pode se estender além do tempo de vida desse escopo.</span><span class="sxs-lookup"><span data-stu-id="0cd56-159">Access to local variables and parameters in the containing scope can extend beyond the lifetime of that scope.</span></span> <span data-ttu-id="0cd56-160">Como um delegado referindo-se a uma expressão lambda não está disponível para coleta de lixo, o acesso às variáveis no ambiente original é mantido.</span><span class="sxs-lookup"><span data-stu-id="0cd56-160">As long as a delegate referring to a lambda expression is not available to garbage collection, access to the variables in the original environment is retained.</span></span> <span data-ttu-id="0cd56-161">No exemplo a seguir, a variável `target` é local para `makeTheGame`, o método no qual a expressão lambda `playTheGame` está definido.</span><span class="sxs-lookup"><span data-stu-id="0cd56-161">In the following example, variable `target` is local to `makeTheGame`, the method in which the lambda expression `playTheGame` is defined.</span></span> <span data-ttu-id="0cd56-162">Observe que a expressão lambda retornada, atribuída a `takeAGuess` na `Main`, ainda tem acesso à variável local `target`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-162">Note that the returned lambda expression, assigned to `takeAGuess` in `Main`, still has access to the local variable `target`.</span></span>  
  
 <span data-ttu-id="0cd56-163">[!code-vb[VbVbalrLambdas&#12;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-163">[!code-vb[VbVbalrLambdas#12](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_5.vb)]</span></span>  
  
 <span data-ttu-id="0cd56-164">O exemplo a seguir demonstra uma ampla variedade de direitos de acesso da expressão lambda aninhada.</span><span class="sxs-lookup"><span data-stu-id="0cd56-164">The following example demonstrates the wide range of access rights of the nested lambda expression.</span></span> <span data-ttu-id="0cd56-165">Quando a expressão lambda retornado é executada de `Main` como `aDel`, ela acessa estes elementos:</span><span class="sxs-lookup"><span data-stu-id="0cd56-165">When the returned lambda expression is executed from `Main` as `aDel`, it accesses these elements:</span></span>  
  
-   <span data-ttu-id="0cd56-166">Um campo da classe na qual ela está definida:`aField`</span><span class="sxs-lookup"><span data-stu-id="0cd56-166">A field of the class in which it is defined: `aField`</span></span>  
  
-   <span data-ttu-id="0cd56-167">Uma propriedade da classe na qual ela está definida:`aProp`</span><span class="sxs-lookup"><span data-stu-id="0cd56-167">A property of the class in which it is defined: `aProp`</span></span>  
  
-   <span data-ttu-id="0cd56-168">Um parâmetro do método `functionWithNestedLambda`, no qual ela está definida:`level1`</span><span class="sxs-lookup"><span data-stu-id="0cd56-168">A parameter of method `functionWithNestedLambda`, in which it is defined: `level1`</span></span>  
  
-   <span data-ttu-id="0cd56-169">Uma variável local de `functionWithNestedLambda`:`localVar`</span><span class="sxs-lookup"><span data-stu-id="0cd56-169">A local variable of `functionWithNestedLambda`: `localVar`</span></span>  
  
-   <span data-ttu-id="0cd56-170">Um parâmetro da expressão lambda no qual ela está aninhada:`level2`</span><span class="sxs-lookup"><span data-stu-id="0cd56-170">A parameter of the lambda expression in which it is nested: `level2`</span></span>  
  
 <span data-ttu-id="0cd56-171">[!code-vb[VbVbalrLambdas n º&9;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-171">[!code-vb[VbVbalrLambdas#9](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_6.vb)]</span></span>  
  
## <a name="converting-to-a-delegate-type"></a><span data-ttu-id="0cd56-172">Conversão para um tipo de delegado</span><span class="sxs-lookup"><span data-stu-id="0cd56-172">Converting to a Delegate Type</span></span>  
 <span data-ttu-id="0cd56-173">Uma expressão lambda pode ser convertida implicitamente para um tipo de representante compatível.</span><span class="sxs-lookup"><span data-stu-id="0cd56-173">A lambda expression can be implicitly converted to a compatible delegate type.</span></span> <span data-ttu-id="0cd56-174">Para obter informações sobre os requisitos gerais para compatibilidade, consulte [conversão de delegado reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span><span class="sxs-lookup"><span data-stu-id="0cd56-174">For information about the general requirements for compatibility, see [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).</span></span> <span data-ttu-id="0cd56-175">Por exemplo, o exemplo de código a seguir mostra uma expressão lambda que converte implicitamente em `Func(Of Integer, Boolean)` ou uma assinatura de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="0cd56-175">For example, the following code example shows a lambda expression that implicitly converts to `Func(Of Integer, Boolean)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="0cd56-176">[!code-vb[VbVbalrLambdas n º&16;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-176">[!code-vb[VbVbalrLambdas#16](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_7.vb)]</span></span>  
  
 <span data-ttu-id="0cd56-177">O exemplo de código a seguir mostra uma expressão lambda que converte implicitamente em `Sub(Of Double, String, Double)` ou uma assinatura de delegado correspondente.</span><span class="sxs-lookup"><span data-stu-id="0cd56-177">The following code example shows a lambda expression that implicitly converts to `Sub(Of Double, String, Double)` or a matching delegate signature.</span></span>  
  
 <span data-ttu-id="0cd56-178">[!code-vb[VbVbalrLambdas&#23;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-178">[!code-vb[VbVbalrLambdas#23](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_8.vb)]</span></span>  
  
 <span data-ttu-id="0cd56-179">Quando você atribui expressões lambda a representantes ou passá-las como argumentos para procedimentos, você pode especificar os nomes de parâmetro mas omitir seus tipos de dados, permitindo que os tipos ser extraídos do representante.</span><span class="sxs-lookup"><span data-stu-id="0cd56-179">When you assign lambda expressions to delegates or pass them as arguments to procedures, you can specify the parameter names but omit their data types, letting the types be taken from the delegate.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0cd56-180">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0cd56-180">Examples</span></span>  
  
-   <span data-ttu-id="0cd56-181">O exemplo a seguir define uma expressão lambda que retorna `True` se o argumento anulável tem um valor atribuído, e `False` se o valor for `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="0cd56-181">The following example defines a lambda expression that returns `True` if the nullable argument has an assigned value, and `False` if its value is `Nothing`.</span></span>  
  
     <span data-ttu-id="0cd56-182">[!code-vb[VbVbalrLambdas n º&4;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-182">[!code-vb[VbVbalrLambdas#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_9.vb)]</span></span>  
  
-   <span data-ttu-id="0cd56-183">O exemplo a seguir define uma expressão lambda que retorna o índice do último elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="0cd56-183">The following example defines a lambda expression that returns the index of the last element in an array.</span></span>  
  
     <span data-ttu-id="0cd56-184">[!code-vb[VbVbalrLambdas n º&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span><span class="sxs-lookup"><span data-stu-id="0cd56-184">[!code-vb[VbVbalrLambdas#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/lambda-expressions_10.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd56-185">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0cd56-185">See Also</span></span>  
 <span data-ttu-id="0cd56-186">[Procedimentos](./index.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-186">[Procedures](./index.md) </span></span>  
<span data-ttu-id="0cd56-187"> [Introdução ao LINQ no Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-187"> [Introduction to LINQ in Visual Basic](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="0cd56-188"> [Delegados](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-188"> [Delegates](../../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="0cd56-189"> [Instrução Function](../../../../visual-basic/language-reference/statements/function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-189"> [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) </span></span>  
<span data-ttu-id="0cd56-190"> [Instrução sub](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-190"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="0cd56-191"> [Tipos de valor anulável](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-191"> [Nullable Value Types](../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) </span></span>  
<span data-ttu-id="0cd56-192"> [Como: passar procedimentos para outro procedimento no Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-192"> [How to: Pass Procedures to Another Procedure in Visual Basic](../../../../visual-basic/programming-guide/language-features/delegates/how-to-pass-procedures-to-another-procedure.md) </span></span>  
<span data-ttu-id="0cd56-193"> [Como: criar uma expressão Lambda](./how-to-create-a-lambda-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0cd56-193"> [How to: Create a Lambda Expression](./how-to-create-a-lambda-expression.md) </span></span>  
<span data-ttu-id="0cd56-194"> [Conversão de Delegado Reduzida](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span><span class="sxs-lookup"><span data-stu-id="0cd56-194"> [Relaxed Delegate Conversion](../../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)</span></span>

