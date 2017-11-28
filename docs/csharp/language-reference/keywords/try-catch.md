---
title: "try-catch (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- try
- try_CSharpKeyword
- catch
- catch_CSharpKeyword
helpviewer_keywords:
- catch keyword [C#]
- try-catch statement [C#]
ms.assetid: cb5503c7-bfa1-4610-8fc2-ddcd2e84c438
caps.latest.revision: "45"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 753beb554796ad0aa2c5e15c715240453de9a3e1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="try-catch-c-reference"></a><span data-ttu-id="f3b8b-102">try-catch (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f3b8b-102">try-catch (C# Reference)</span></span>
<span data-ttu-id="f3b8b-103">A instrução try-catch consiste em um bloco `try` seguido por uma ou mais cláusulas `catch`, que especificam os manipuladores para diferentes exceções.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-103">The try-catch statement consists of a `try` block followed by one or more `catch` clauses, which specify handlers for different exceptions.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3b8b-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="f3b8b-104">Remarks</span></span>  
 <span data-ttu-id="f3b8b-105">Quando uma exceção é lançada, o CLR (Common Language Runtime) procura a instrução `catch` que trata essa exceção.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-105">When an exception is thrown, the common language runtime (CLR) looks for the `catch` statement that handles this exception.</span></span> <span data-ttu-id="f3b8b-106">Se o método em execução no momento não contiver um bloco `catch`, o CLR procurará no método que chamou o método atual e assim por diante para cima na pilha de chamadas.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-106">If the currently executing method does not contain such a `catch` block, the CLR looks at the method that called the current method, and so on up the call stack.</span></span> <span data-ttu-id="f3b8b-107">Se nenhum bloco `catch` for encontrado, o CLR exibirá uma mensagem de exceção sem tratamento para o usuário e interromperá a execução do programa.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-107">If no `catch` block is found, then the CLR displays an unhandled exception message to the user and stops execution of the program.</span></span>  
  
 <span data-ttu-id="f3b8b-108">O bloco `try` contém o código protegido que pode causar a exceção.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-108">The `try` block contains the guarded code that may cause the exception.</span></span> <span data-ttu-id="f3b8b-109">O bloco é executado até que uma exceção seja lançada ou ele seja concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-109">The block is executed until an exception is thrown or it is completed successfully.</span></span> <span data-ttu-id="f3b8b-110">Por exemplo, a tentativa a seguir de converter um objeto `null` gera a exceção <xref:System.NullReferenceException>:</span><span class="sxs-lookup"><span data-stu-id="f3b8b-110">For example, the following attempt to cast a `null` object raises the <xref:System.NullReferenceException> exception:</span></span>  
  
```csharp  
object o2 = null;  
try  
{  
    int i2 = (int)o2;   // Error  
}  
```  
  
 <span data-ttu-id="f3b8b-111">Embora a cláusula `catch` possa ser usada sem argumentos para capturar qualquer tipo de exceção, esse uso não é recomendado.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-111">Although the `catch` clause can be used without arguments to catch any type of exception, this usage is not recommended.</span></span> <span data-ttu-id="f3b8b-112">Em geral, você deve capturar apenas as exceções das quais você sabe se recuperar.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-112">In general, you should only catch those exceptions that you know how to recover from.</span></span> <span data-ttu-id="f3b8b-113">Portanto, você sempre deve especificar um argumento de objeto derivado de <xref:System.Exception?displayProperty=nameWithType>, por exemplo:</span><span class="sxs-lookup"><span data-stu-id="f3b8b-113">Therefore, you should always specify an object argument derived from <xref:System.Exception?displayProperty=nameWithType> For example:</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
}  
```  
  
 <span data-ttu-id="f3b8b-114">É possível usar mais de uma cláusula `catch` específica na mesma instrução try-catch.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-114">It is possible to use more than one specific `catch` clause in the same try-catch statement.</span></span> <span data-ttu-id="f3b8b-115">Nesse caso, a ordem das cláusulas `catch` é importante porque as cláusulas `catch` são examinadas em ordem.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-115">In this case, the order of the `catch` clauses is important because the `catch` clauses are examined in order.</span></span> <span data-ttu-id="f3b8b-116">Capture as exceções mais específicas antes das menos específicas.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-116">Catch the more specific exceptions before the less specific ones.</span></span> <span data-ttu-id="f3b8b-117">O compilador gerará um erro se você ordenar os blocos catch de forma que um bloco posterior nunca possa ser alcançado.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-117">The compiler produces an error if you order your catch blocks so that a later block can never be reached.</span></span>  
  
 <span data-ttu-id="f3b8b-118">Usar argumentos `catch` é uma maneira de filtrar as exceções que deseja manipular.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-118">Using `catch` arguments is one way to filter for the exceptions you want to handle.</span></span>  <span data-ttu-id="f3b8b-119">Você também pode usar uma expressão de predicado que examina ainda mais a exceção para decidir se deve manipulá-la.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-119">You can also use a predicate expression that further examines the exception to decide whether to handle it.</span></span>  <span data-ttu-id="f3b8b-120">Se a expressão de predicado retornar false, a pesquisa para um manipulador continua.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-120">If the predicate expression returns false, then the search for a handler continues.</span></span>  
  
```csharp  
catch (ArgumentException e) when (e.ParamName == "…")  
{  
}  
```  
  
 <span data-ttu-id="f3b8b-121">Os filtros de exceção são preferíveis em relação à captura e relançamento (explicados abaixo) porque os filtros deixam a pilha intacta.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-121">Exception filters are preferable to catching and rethrowing (explained below) because filters leave the stack unharmed.</span></span>  <span data-ttu-id="f3b8b-122">Se um manipulador posterior despeja a pilha, você pode ver de onde a exceção originalmente veio, em vez de apenas o último lugar em que ela foi relançada.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-122">If a later handler dumps the stack, you can see where the exception originally came from, rather than just the last place it was rethrown.</span></span>  <span data-ttu-id="f3b8b-123">Um uso comum de expressões de filtro de exceção é o registro em log.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-123">A common use of exception filter expressions is logging.</span></span>  <span data-ttu-id="f3b8b-124">Você pode criar uma função de predicado que sempre retorna false que também gera um log, pode registrar exceções conforme elas ocorrem sem precisar manipulá-las e relançá-las.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-124">You can create a predicate function that always returns false that also outputs to a log, you can log exceptions as they go by without having to handle them and rethrow.</span></span>  
  
 <span data-ttu-id="f3b8b-125">Uma instrução [throw](../../../csharp/language-reference/keywords/throw.md) pode ser usada em um bloco `catch` para relançar a exceção que foi capturada pela instrução `catch`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-125">A [throw](../../../csharp/language-reference/keywords/throw.md) statement can be used in a `catch` block to re-throw the exception that is caught by the `catch` statement.</span></span> <span data-ttu-id="f3b8b-126">O exemplo a seguir extrai informações de origem de uma exceção <xref:System.IO.IOException> e, em seguida, lança a exceção para o método pai.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-126">The following example extracts source information from an <xref:System.IO.IOException> exception, and then throws the exception to the parent method.</span></span>  
  
```csharp  
catch (FileNotFoundException e)  
{  
    // FileNotFoundExceptions are handled here.  
}  
catch (IOException e)  
{  
    // Extract some information from this exception, and then   
    // throw it to the parent method.  
    if (e.Source != null)  
        Console.WriteLine("IOException source: {0}", e.Source);  
    throw;  
}  
```  
  
 <span data-ttu-id="f3b8b-127">Você pode capturar uma exceção e lançar uma exceção diferente.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-127">You can catch one exception and throw a different exception.</span></span> <span data-ttu-id="f3b8b-128">Quando fizer isso, especifique a exceção capturada como a exceção interna, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-128">When you do this, specify the exception that you caught as the inner exception, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)   
{  
    // Perform some action here, and then throw a new exception.  
    throw new YourCustomException("Put your error message here.", e);  
}  
```  
  
 <span data-ttu-id="f3b8b-129">Você pode também relançar uma exceção quando uma determinada condição for verdadeira, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-129">You can also re-throw an exception when a specified condition is true, as shown in the following example.</span></span>  
  
```csharp  
catch (InvalidCastException e)  
{  
    if (e.Data == null)  
    {  
        throw;  
    }  
    else  
    {  
        // Take some action.  
    }  
 }  
```  
  
 <span data-ttu-id="f3b8b-130">De dentro de um bloco `try`, inicialize somente as variáveis que são declaradas nele.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-130">From inside a `try` block, initialize only variables that are declared therein.</span></span> <span data-ttu-id="f3b8b-131">Caso contrário, uma exceção pode ocorrer antes da conclusão da execução do bloco.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-131">Otherwise, an exception can occur before the execution of the block is completed.</span></span> <span data-ttu-id="f3b8b-132">Por exemplo, no exemplo de código a seguir, a variável `n` é inicializada dentro do bloco `try`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-132">For example, in the following code example, the variable `n` is initialized inside the `try` block.</span></span> <span data-ttu-id="f3b8b-133">Uma tentativa de usar essa variável fora do bloco `try` na instrução `Write(n)` gerará um erro de compilador.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-133">An attempt to use this variable outside the `try` block in the `Write(n)` statement will generate a compiler error.</span></span>  
  
```csharp  
static void Main()   
{  
    int n;  
    try   
    {  
        // Do not initialize this variable here.  
        n = 123;  
    }  
    catch  
    {  
    }  
    // Error: Use of unassigned local variable 'n'.  
    Console.Write(n);  
}  
```  
  
 <span data-ttu-id="f3b8b-134">Para obter mais informações sobre catch, consulte [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span><span class="sxs-lookup"><span data-stu-id="f3b8b-134">For more information about catch, see [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md).</span></span>  
  
## <a name="exceptions-in-async-methods"></a><span data-ttu-id="f3b8b-135">Exceções em métodos assíncronos</span><span class="sxs-lookup"><span data-stu-id="f3b8b-135">Exceptions in Async Methods</span></span>  
 <span data-ttu-id="f3b8b-136">Um método assíncrono é marcado por um modificador [async](../../../csharp/language-reference/keywords/async.md) e geralmente contém uma ou mais expressões ou instruções await.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-136">An async method is marked  by an  [async](../../../csharp/language-reference/keywords/async.md) modifier and usually contains one or more await expressions or statements.</span></span> <span data-ttu-id="f3b8b-137">Uma expressão await aplica o operador [await](../../../csharp/language-reference/keywords/await.md) a um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-137">An await expression applies the [await](../../../csharp/language-reference/keywords/await.md) operator to a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="f3b8b-138">Quando o controle atinge um `await` no método assíncrono, o progresso no método é suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-138">When control reaches an `await` in the async method, progress in the method is suspended until the awaited task completes.</span></span> <span data-ttu-id="f3b8b-139">Quando a tarefa for concluída, a execução poderá ser retomada no método.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-139">When the task  is complete, execution can resume in the method.</span></span> <span data-ttu-id="f3b8b-140">Para obter mais informações, consulte [Programação assíncrona com async e await (C#)](../../../csharp/programming-guide/concepts/async/index.md) e [Fluxo de controle em programas assíncronos](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span><span class="sxs-lookup"><span data-stu-id="f3b8b-140">For more information, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md) and [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).</span></span>  
  
 <span data-ttu-id="f3b8b-141">A tarefa concluída para a qual `await` é aplicada pode estar em um estado de falha devido a uma exceção sem tratamento no método que retorna a tarefa.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-141">The completed task to which `await` is applied might be in a faulted state because of an unhandled exception in the method that returns the task.</span></span> <span data-ttu-id="f3b8b-142">Aguardar a tarefa gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-142">Awaiting the task throws an exception.</span></span> <span data-ttu-id="f3b8b-143">Uma tarefa também poderá terminar em um estado cancelado se o processo assíncrono que a retorna for cancelado.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-143">A task can also end up in a canceled state if the asynchronous process that returns it is canceled.</span></span> <span data-ttu-id="f3b8b-144">Aguardar uma tarefa cancelada lança um `OperationCanceledException`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-144">Awaiting a canceled task throws  an `OperationCanceledException`.</span></span> <span data-ttu-id="f3b8b-145">Para obter mais informações sobre como cancelar um processo assíncrono, consulte [Ajuste fino de seu aplicativo assíncrono (C#)](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span><span class="sxs-lookup"><span data-stu-id="f3b8b-145">For more information about how to cancel an asynchronous process, see [Fine-Tuning Your Async Application](../../programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="f3b8b-146">Para capturar a exceção, aguarde a tarefa em um bloco `try` e capture a exceção no bloco `catch` associado.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-146">To catch the exception, await the task in a `try` block, and catch the exception in the associated `catch` block.</span></span> <span data-ttu-id="f3b8b-147">Para ver um exemplo, consulte a seção “Exemplo”.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-147">For an example, see the "Example" section.</span></span>  
  
 <span data-ttu-id="f3b8b-148">Uma tarefa pode estar em um estado de falha porque ocorreram várias exceções no método assíncrono esperado.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-148">A task can be in a faulted state because multiple exceptions occurred in the awaited async method.</span></span> <span data-ttu-id="f3b8b-149">Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-149">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3b8b-150">Quando você espera uma tarefa, somente uma das exceções é capturada e não é possível prever qual exceção será capturada.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-150">When you await such a task, only one of the exceptions is caught, and you can't predict which exception will be caught.</span></span> <span data-ttu-id="f3b8b-151">Para ver um exemplo, consulte a seção “Exemplo”.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-151">For an example, see the "Example" section.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3b8b-152">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3b8b-152">Example</span></span>  
 <span data-ttu-id="f3b8b-153">No exemplo a seguir, o bloco `try` contém uma chamada para o método `ProcessString` que pode causar uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-153">In the following example, the `try` block contains a call to the `ProcessString` method that may cause an exception.</span></span> <span data-ttu-id="f3b8b-154">A cláusula `catch` contém o manipulador de exceção que apenas exibe uma mensagem na tela.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-154">The `catch` clause contains the exception handler that just displays a message on the screen.</span></span> <span data-ttu-id="f3b8b-155">Quando instrução `throw` é chamada de dentro de `MyMethod`, o sistema procura a instrução `catch` e exibe a mensagem `Exception caught`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-155">When the `throw` statement is called from inside `MyMethod`, the system looks for the `catch` statement and displays the message `Exception caught`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3b8b-156">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3b8b-156">Example</span></span>  
 <span data-ttu-id="f3b8b-157">No exemplo a seguir, dois blocos catch são usados e a exceção mais específica, que vem primeiro, é capturada.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-157">In the following example, two catch blocks are used, and the most specific exception, which comes first, is caught.</span></span>  
  
 <span data-ttu-id="f3b8b-158">Para capturar a exceção menos específica, você pode substituir a instrução throw em `ProcessString` pela seguinte instrução: `throw new Exception()`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-158">To catch the least specific exception, you can replace the throw statement in `ProcessString` with the following statement: `throw new Exception()`.</span></span>  
  
 <span data-ttu-id="f3b8b-159">Se você colocar o bloco catch menos específica primeiro no exemplo, a seguinte mensagem de erro aparecerá: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-159">If you place the least-specific catch block first in the example, the following  error message appears: `A previous catch clause already catches all exceptions of this or a super type ('System.Exception')`.</span></span>  
  
 [!code-csharp[csrefKeywordsExceptions#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3b8b-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3b8b-160">Example</span></span>  
 <span data-ttu-id="f3b8b-161">O exemplo a seguir ilustra o tratamento de exceção para métodos assíncronos.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-161">The following example illustrates exception handling for async methods.</span></span> <span data-ttu-id="f3b8b-162">Para capturar uma exceção que lança uma tarefa assíncrona, coloque a expressão `await` em um bloco `try` e capture a exceção em um bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-162">To catch an exception that an async task throws, place the `await` expression in a `try` block, and catch the exception in a `catch` block.</span></span>  
  
 <span data-ttu-id="f3b8b-163">Remova a marca de comentário da linha `throw new Exception` no exemplo para demonstrar o tratamento de exceção.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-163">Uncomment the `throw new Exception` line in the example to demonstrate exception handling.</span></span> <span data-ttu-id="f3b8b-164">A propriedade `IsFaulted` da tarefa é definida para `True`, a propriedade `Exception.InnerException` da tarefa é definida para a exceção e a exceção é capturada em um bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-164">The task's `IsFaulted` property is set to `True`, the task's `Exception.InnerException` property is set to the exception, and the exception is caught in the `catch` block.</span></span>  
  
 <span data-ttu-id="f3b8b-165">Remova a marca de comentário da linha `throw new OperationCancelledException` para demonstrar o que acontece quando você cancela um processo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-165">Uncomment the `throw new OperationCancelledException` line to demonstrate what happens when you cancel an asynchronous process.</span></span> <span data-ttu-id="f3b8b-166">A propriedade `IsCanceled` da tarefa é definida para `true` e a exceção é capturada no bloco `catch`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-166">The task's `IsCanceled` property is set to `true`, and the exception is caught in the `catch` block.</span></span> <span data-ttu-id="f3b8b-167">Em algumas condições que não se aplicam a este exemplo, a propriedade `IsFaulted` da tarefa é definida para `true` e `IsCanceled` é definido para `false`.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-167">Under some conditions that don't apply to this example, the task's `IsFaulted` property is set to `true` and `IsCanceled` is set to `false`.</span></span>  
  
 [!code-csharp[csAsyncExceptions#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="f3b8b-168">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f3b8b-168">Example</span></span>  
 <span data-ttu-id="f3b8b-169">O exemplo a seguir ilustra a manipulação de exceção em que várias tarefas podem resultar em várias exceções.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-169">The following example illustrates exception handling where multiple tasks can result in multiple exceptions.</span></span> <span data-ttu-id="f3b8b-170">O bloco `try` aguarda a tarefa que é retornada por uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-170">The `try` block awaits the task that's returned by a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f3b8b-171">A tarefa é concluída quando as três tarefas às quais WhenAll se aplica são concluídas.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-171">The task is complete when the three tasks to which WhenAll is applied are complete.</span></span>  
  
 <span data-ttu-id="f3b8b-172">Cada uma das três tarefas causa uma exceção.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-172">Each of the three tasks causes an exception.</span></span> <span data-ttu-id="f3b8b-173">O bloco `catch` itera por meio de exceções, que são encontradas na propriedade `Exception.InnerExceptions` da tarefa que foi retornada por <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f3b8b-173">The `catch` block iterates through the exceptions, which are found in the `Exception.InnerExceptions` property of the task that was returned by <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[csAsyncExceptions#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/try-catch_4.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f3b8b-174">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f3b8b-174">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f3b8b-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f3b8b-175">See Also</span></span>  
 [<span data-ttu-id="f3b8b-176">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f3b8b-176">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f3b8b-177">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f3b8b-177">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f3b8b-178">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f3b8b-178">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f3b8b-179">Instruções try, throw e catch (C++)</span><span class="sxs-lookup"><span data-stu-id="f3b8b-179">try, throw, and catch Statements (C++)</span></span>](/cpp/cpp/try-throw-and-catch-statements-cpp)  
 [<span data-ttu-id="f3b8b-180">Instruções para manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="f3b8b-180">Exception Handling Statements</span></span>](../../../csharp/language-reference/keywords/exception-handling-statements.md)  
 [<span data-ttu-id="f3b8b-181">throw</span><span class="sxs-lookup"><span data-stu-id="f3b8b-181">throw</span></span>](../../../csharp/language-reference/keywords/throw.md)  
 [<span data-ttu-id="f3b8b-182">try-finally</span><span class="sxs-lookup"><span data-stu-id="f3b8b-182">try-finally</span></span>](../../../csharp/language-reference/keywords/try-finally.md)  
 [<span data-ttu-id="f3b8b-183">Como gerar exceções explicitamente</span><span class="sxs-lookup"><span data-stu-id="f3b8b-183">How to: Explicitly Throw Exceptions</span></span>](../../../standard/exceptions/how-to-explicitly-throw-exceptions.md)
