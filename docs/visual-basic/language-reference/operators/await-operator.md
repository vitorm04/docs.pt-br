---
title: Operador Await (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d9d50433e3bc24df7cda137a145ab3f0f0302a1f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608655"
---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="27336-102">Operador Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27336-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="27336-103">Aplicar o `Await` operador para um operando em uma expressão lambda ou método assíncrono para suspender a execução do método até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="27336-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="27336-104">A tarefa representa um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="27336-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="27336-105">O método no qual `Await` é usada deve ter um [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="27336-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="27336-106">Esse tipo de método, definido pelo uso do modificador `Async` e, geralmente, contendo uma ou mais expressões `Await`, é conhecido como um *método assíncrono*.</span><span class="sxs-lookup"><span data-stu-id="27336-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27336-107">As palavras-chave `Async` e `Await` foram introduzidas no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="27336-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="27336-108">Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="27336-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="27336-109">Normalmente, a tarefa à qual aplicar a `Await` operador é o valor retornado de uma chamada para um método que implementa o [padrão assíncrono baseado em tarefa](https://go.microsoft.com/fwlink/?LinkId=204847), ou seja, uma <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="27336-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="27336-110">No código a seguir, o <xref:System.Net.Http.HttpClient> método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retorna `getContentsTask`, um `Task(Of Byte())`.</span><span class="sxs-lookup"><span data-stu-id="27336-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="27336-111">A tarefa é uma promessa de produzir a matriz de bytes real quando a operação for concluída.</span><span class="sxs-lookup"><span data-stu-id="27336-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="27336-112">O operador `Await` é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até que `getContentsTask` seja concluída.</span><span class="sxs-lookup"><span data-stu-id="27336-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="27336-113">Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="27336-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="27336-114">Quando `getContentsTask` for concluído, a expressão `Await` resulta em uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="27336-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
```vb  
Private Async Function SumPageSizesAsync() As Task  
  
    ' To use the HttpClient type in desktop apps, you must include a using directive and add a   
    ' reference for the System.Net.Http namespace.  
    Dim client As HttpClient = New HttpClient()   
    ' . . .   
    Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
    Dim urlContents As Byte() = Await getContentsTask  
  
    ' Equivalently, now that you see how it works, you can write the same thing in a single line.  
    'Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ' . . .  
End Function  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="27336-115">Para o exemplo completo, confira o [Passo a passo: Como acessar a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="27336-115">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="27336-116">Você pode baixar o exemplo em [Exemplos de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) no site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="27336-116">You can download the sample from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) on the Microsoft website.</span></span> <span data-ttu-id="27336-117">O exemplo está no projeto AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="27336-117">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="27336-118">Se `Await` é aplicada ao resultado de uma chamada de método que retorna um `Task(Of TResult)`, o tipo do `Await` expressão é TResult.</span><span class="sxs-lookup"><span data-stu-id="27336-118">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="27336-119">Se `Await` é aplicada ao resultado de uma chamada de método que retorna um `Task`, o `Await` expressão não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="27336-119">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="27336-120">O exemplo a seguir ilustra a diferença.</span><span class="sxs-lookup"><span data-stu-id="27336-120">The following example illustrates the difference.</span></span>  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 <span data-ttu-id="27336-121">Um `Await` expressão ou instrução não bloqueia o thread no qual ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="27336-121">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="27336-122">Em vez disso, ele faz com que o compilador Inscreva o restante do método assíncrono, após o `Await` expressão, como uma continuação da tarefa aguardada.</span><span class="sxs-lookup"><span data-stu-id="27336-122">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="27336-123">Em seguida, o controle retorna para o chamador do método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="27336-123">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="27336-124">Quando a tarefa for concluída, ela invoca a sua continuação e a execução do método assíncrono continua de onde parou.</span><span class="sxs-lookup"><span data-stu-id="27336-124">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="27336-125">Uma `Await` expressão pode ocorrer somente no corpo de uma expressão lambda ou método imediatamente delimitador que é marcado por um `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="27336-125">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="27336-126">O termo *Await* serve como uma palavra-chave somente nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="27336-126">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="27336-127">Em outro local, ele será interpretado como um identificador.</span><span class="sxs-lookup"><span data-stu-id="27336-127">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="27336-128">Dentro da expressão de lambda ou método assíncrono, uma `Await` expressão não pode ocorrer em uma expressão de consulta, em de `catch` ou `finally` block de um [tente... Catch... Por fim](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instrução na expressão variável de controle de loop de uma `For` ou `For Each` loop, ou no corpo de uma [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="27336-128">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="27336-129">Exceções</span><span class="sxs-lookup"><span data-stu-id="27336-129">Exceptions</span></span>  
 <span data-ttu-id="27336-130">A maioria dos métodos assíncronos retorna um <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="27336-130">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="27336-131">As propriedades da tarefa retornada transportam informações sobre seu status e histórico como: se a tarefa foi concluída, se o método assíncrono causou uma exceção ou se foi cancelado e qual foi o resultado final.</span><span class="sxs-lookup"><span data-stu-id="27336-131">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="27336-132">O operador `Await` acessa essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="27336-132">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="27336-133">Se você aguarda um método assíncrono de retorno de tarefa que causou uma exceção, o operador `Await` relançará a exceção.</span><span class="sxs-lookup"><span data-stu-id="27336-133">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="27336-134">Se você aguarda um método assíncrono de retorno de tarefa que é cancelado, o `Await` operador Relança uma <xref:System.OperationCanceledException>.</span><span class="sxs-lookup"><span data-stu-id="27336-134">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="27336-135">Uma tarefa única que está em um estado com falha pode refletir várias exceções.</span><span class="sxs-lookup"><span data-stu-id="27336-135">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="27336-136">Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="27336-136">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="27336-137">Quando você aguarda essa tarefa, a operação de aguardar relança apenas uma das exceções.</span><span class="sxs-lookup"><span data-stu-id="27336-137">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="27336-138">No entanto, você não pode prever qual das exceções será relançada.</span><span class="sxs-lookup"><span data-stu-id="27336-138">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="27336-139">Para obter exemplos de tratamento de erro em métodos assíncronos, consulte [tente... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="27336-139">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27336-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="27336-140">Example</span></span>  
 <span data-ttu-id="27336-141">O exemplo do Windows Forms a seguir ilustra o uso do `Await` em um método assíncrono `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="27336-141">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="27336-142">Compare o comportamento desse método com o comportamento de `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="27336-142">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="27336-143">Sem um `Await` operador `WaitSynchronously` é executado de forma síncrona, apesar do uso das `Async` modificador em sua definição e uma chamada para <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="27336-143">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> in its body.</span></span>  
  
```vb  
Private Async Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
    ' Call the method that runs asynchronously.  
    Dim result As String = Await WaitAsynchronouslyAsync()  
  
    ' Call the method that runs synchronously.  
    'Dim result As String = Await WaitSynchronously()  
  
    ' Display the result.  
    TextBox1.Text &= result  
End Sub  
  
' The following method runs asynchronously. The UI thread is not  
' blocked during the delay. You can move or resize the Form1 window   
' while Task.Delay is running.  
Public Async Function WaitAsynchronouslyAsync() As Task(Of String)  
    Await Task.Delay(10000)  
    Return "Finished"  
End Function  
  
' The following method runs synchronously, despite the use of Async.  
' You cannot move or resize the Form1 window while Thread.Sleep  
' is running because the UI thread is blocked.  
Public Async Function WaitSynchronously() As Task(Of String)  
    ' Import System.Threading for the Sleep method.  
    Thread.Sleep(10000)  
    Return "Finished"  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="27336-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27336-144">See also</span></span>

- [<span data-ttu-id="27336-145">Programação assíncrona com Async e Await</span><span class="sxs-lookup"><span data-stu-id="27336-145">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="27336-146">Passo a passo: acessar a Web usando Async e Await</span><span class="sxs-lookup"><span data-stu-id="27336-146">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="27336-147">Async</span><span class="sxs-lookup"><span data-stu-id="27336-147">Async</span></span>](../../../visual-basic/language-reference/modifiers/async.md)
