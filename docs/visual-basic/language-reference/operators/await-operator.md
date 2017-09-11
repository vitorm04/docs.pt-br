---
title: Operador await (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
caps.latest.revision: 30
author: stevehoag
ms.author: shoag
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
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b50b9c7283ddd4d3f8484854bdffff3d76181c9f
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="await-operator-visual-basic"></a><span data-ttu-id="fba1c-102">Operador Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fba1c-102">Await Operator (Visual Basic)</span></span>
<span data-ttu-id="fba1c-103">Aplicar o `Await` operador um operando em uma expressão lambda ou de método assíncrona para suspender a execução do método até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="fba1c-103">You apply the `Await` operator to an operand in an asynchronous method or lambda expression to suspend execution of the method until the awaited task completes.</span></span> <span data-ttu-id="fba1c-104">A tarefa representa um trabalho em andamento.</span><span class="sxs-lookup"><span data-stu-id="fba1c-104">The task represents ongoing work.</span></span>  
  
 <span data-ttu-id="fba1c-105">O método no qual `Await` é usada deve ter uma [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador.</span><span class="sxs-lookup"><span data-stu-id="fba1c-105">The method in which `Await` is used must have an [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="fba1c-106">Tal um método definido usando o `Async` modificador e geralmente contém um ou mais `Await` expressões, é conhecido como um *método assíncrono*.</span><span class="sxs-lookup"><span data-stu-id="fba1c-106">Such a method, defined by using the `Async` modifier, and usually containing one or more `Await` expressions, is referred to as an *async method*.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fba1c-107">O `Async` e `Await` palavras-chave foram introduzidas no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="fba1c-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="fba1c-108">Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="fba1c-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="fba1c-109">Normalmente, a tarefa que você aplicar o `Await` operador é o valor retornado de uma chamada para um método que implementa o [padrão assíncrono baseado em tarefa](http://go.microsoft.com/fwlink/?LinkId=204847), ou seja, um <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="fba1c-109">Typically, the task to which you apply the `Await` operator is the return value from a call to a method that implements the [Task-Based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=204847), that is, a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="fba1c-110">No código a seguir, o <xref:System.Net.Http.HttpClient>método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>retorna `getContentsTask`, um `Task(Of Byte())`.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="fba1c-110">In the following code, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> returns `getContentsTask`, a `Task(Of Byte())`.</span></span> <span data-ttu-id="fba1c-111">A tarefa é uma promessa de produzir a matriz de bytes reais quando a operação for concluída.</span><span class="sxs-lookup"><span data-stu-id="fba1c-111">The task is a promise to produce the actual byte array when the operation is complete.</span></span> <span data-ttu-id="fba1c-112">O `Await` operador é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até `getContentsTask` for concluída.</span><span class="sxs-lookup"><span data-stu-id="fba1c-112">The `Await` operator is applied to `getContentsTask` to suspend execution in `SumPageSizesAsync` until `getContentsTask` is complete.</span></span> <span data-ttu-id="fba1c-113">Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="fba1c-113">In the meantime, control is returned to the caller of `SumPageSizesAsync`.</span></span> <span data-ttu-id="fba1c-114">Quando `getContentsTask` for concluído, o `Await` expressão é avaliada como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="fba1c-114">When `getContentsTask` is finished, the `Await` expression evaluates to a byte array.</span></span>  
  
<span data-ttu-id="fba1c-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="fba1c-115"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
> [!IMPORTANT]
>  <span data-ttu-id="fba1c-116">Para o exemplo completo, consulte [passo a passo: acessando a Web, usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="fba1c-116">For the complete example, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="fba1c-117">Você pode baixar o exemplo de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) no site da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fba1c-117">You can download the sample from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) on the Microsoft website.</span></span> <span data-ttu-id="fba1c-118">O exemplo é no projeto AsyncWalkthrough_HttpClient.</span><span class="sxs-lookup"><span data-stu-id="fba1c-118">The example is in the AsyncWalkthrough_HttpClient project.</span></span>  
  
 <span data-ttu-id="fba1c-119">Se `Await` é aplicada ao resultado de uma chamada de método que retorna um `Task(Of TResult)`, o tipo do `Await` expressão é TResult.</span><span class="sxs-lookup"><span data-stu-id="fba1c-119">If `Await` is applied to the result of a method call that returns a `Task(Of TResult)`, the type of the `Await` expression is TResult.</span></span> <span data-ttu-id="fba1c-120">Se `Await` é aplicada ao resultado de uma chamada de método que retorna um `Task`, o `Await` expressão não retorna um valor.</span><span class="sxs-lookup"><span data-stu-id="fba1c-120">If `Await` is applied to the result of a method call that returns a `Task`, the `Await` expression doesn't return a value.</span></span> <span data-ttu-id="fba1c-121">O exemplo a seguir ilustra a diferença.</span><span class="sxs-lookup"><span data-stu-id="fba1c-121">The following example illustrates the difference.</span></span>  
  
<span data-ttu-id="fba1c-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="fba1c-122"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="fba1c-123">Um `Await` expressão ou instrução não bloqueia o thread no qual ele está em execução.</span><span class="sxs-lookup"><span data-stu-id="fba1c-123">An `Await` expression or statement does not block the thread on which it is executing.</span></span> <span data-ttu-id="fba1c-124">Em vez disso, ele faz com que o compilador inscrever-se o restante do método assíncrono, após o `Await` expressão, como uma continuação da tarefa awaited.</span><span class="sxs-lookup"><span data-stu-id="fba1c-124">Instead, it causes the compiler to sign up the rest of the async method, after the `Await` expression, as a continuation on the awaited task.</span></span> <span data-ttu-id="fba1c-125">Em seguida, o controle retorna para o chamador do método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="fba1c-125">Control then returns to the caller of the async method.</span></span> <span data-ttu-id="fba1c-126">Quando a tarefa for concluída, ele chama sua continuação e a execução dos currículos de método assíncrono onde parou.</span><span class="sxs-lookup"><span data-stu-id="fba1c-126">When the task completes, it invokes its continuation, and execution of the async method resumes where it left off.</span></span>  
  
 <span data-ttu-id="fba1c-127">Um `Await` expressão pode ocorrer somente no corpo de uma expressão lambda ou de método delimitador imediatamente marcada por um `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="fba1c-127">An `Await` expression can occur only in the body of an immediately enclosing method or lambda expression that is marked by an `Async` modifier.</span></span> <span data-ttu-id="fba1c-128">O termo *Await* serve como uma palavra-chave somente nesse contexto.</span><span class="sxs-lookup"><span data-stu-id="fba1c-128">The term *Await* serves as a keyword only in that context.</span></span> <span data-ttu-id="fba1c-129">Em outro lugar, ele será interpretado como um identificador.</span><span class="sxs-lookup"><span data-stu-id="fba1c-129">Elsewhere, it is interpreted as an identifier.</span></span> <span data-ttu-id="fba1c-130">Dentro da expressão de lambda ou de método assíncrono, um `Await` expressão não pode ocorrer em uma expressão de consulta, no `catch` ou `finally` bloco de um [Try... Catch... Por fim](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) instrução na expressão variável de controle de loop de uma `For` ou `For Each` loop, ou no corpo de uma [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="fba1c-130">Within the async method or lambda expression, an `Await` expression cannot occur in a query expression, in the `catch` or `finally` block of a [Try…Catch…Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) statement, in the loop control variable expression of a `For` or `For Each` loop, or in the body of a [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) statement.</span></span>  
  
## <a name="exceptions"></a><span data-ttu-id="fba1c-131">Exceções</span><span class="sxs-lookup"><span data-stu-id="fba1c-131">Exceptions</span></span>  
 <span data-ttu-id="fba1c-132">A maioria dos métodos assíncronos retornar uma <xref:System.Threading.Tasks.Task>ou <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="fba1c-132">Most async methods return a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="fba1c-133">As propriedades da tarefa retornada transportam informações sobre seu status e o histórico, como se a tarefa for concluída, se o método assíncrono causou uma exceção ou foi cancelado e que o resultado final é.</span><span class="sxs-lookup"><span data-stu-id="fba1c-133">The properties of the returned task carry information about its status and history, such as whether the task is complete, whether the async method caused an exception or was canceled, and what the final result is.</span></span> <span data-ttu-id="fba1c-134">O `Await` operador acessa as propriedades.</span><span class="sxs-lookup"><span data-stu-id="fba1c-134">The `Await` operator accesses those properties.</span></span>  
  
 <span data-ttu-id="fba1c-135">Se você espera que um método assíncrono retorno de tarefas que faz com que uma exceção, o `Await` operador Relança a exceção.</span><span class="sxs-lookup"><span data-stu-id="fba1c-135">If you await a task-returning async method that causes an exception, the  `Await` operator rethrows the exception.</span></span>  
  
 <span data-ttu-id="fba1c-136">Se você espera que um método assíncrono retornando a tarefa que é cancelado, o `Await` operador relança <xref:System.OperationCanceledException>.</xref:System.OperationCanceledException></span><span class="sxs-lookup"><span data-stu-id="fba1c-136">If you await a task-returning async method that is canceled, the `Await` operator rethrows an <xref:System.OperationCanceledException>.</span></span>  
  
 <span data-ttu-id="fba1c-137">Uma única tarefa que está em um estado de falha pode refletir várias exceções.</span><span class="sxs-lookup"><span data-stu-id="fba1c-137">A single task that is in a faulted state can reflect multiple exceptions.</span></span>  <span data-ttu-id="fba1c-138">Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fba1c-138">For example, the task might be the result of a call to <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="fba1c-139">Quando você espera uma tarefa, a operação de espera relança apenas uma das exceções.</span><span class="sxs-lookup"><span data-stu-id="fba1c-139">When you await such a task, the await operation rethrows only one of the exceptions.</span></span> <span data-ttu-id="fba1c-140">No entanto, você não pode prever qual das exceções é emitida novamente.</span><span class="sxs-lookup"><span data-stu-id="fba1c-140">However, you can't predict which of the exceptions is rethrown.</span></span>  
  
 <span data-ttu-id="fba1c-141">Para obter exemplos de tratamento de erros em métodos assíncronos, consulte [Try... Catch... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fba1c-141">For examples of error handling in async methods, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fba1c-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fba1c-142">Example</span></span>  
 <span data-ttu-id="fba1c-143">O exemplo de formulários do Windows a seguir ilustra o uso do `Await` em um método assíncrono, `WaitAsynchronouslyAsync`.</span><span class="sxs-lookup"><span data-stu-id="fba1c-143">The following Windows Forms example illustrates the use of `Await` in an async method, `WaitAsynchronouslyAsync`.</span></span> <span data-ttu-id="fba1c-144">Compare o comportamento do método com o comportamento de `WaitSynchronously`.</span><span class="sxs-lookup"><span data-stu-id="fba1c-144">Contrast the behavior of that method with the behavior of `WaitSynchronously`.</span></span> <span data-ttu-id="fba1c-145">Sem um `Await` operador, `WaitSynchronously` é executado de forma síncrona apesar do uso do `Async` modificador em sua definição e uma chamada para <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName>em seu corpo.</xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="fba1c-145">Without an `Await` operator, `WaitSynchronously` runs synchronously despite the use of the `Async` modifier in its definition and a call to <xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> in its body.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fba1c-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fba1c-146">See Also</span></span>  
 <span data-ttu-id="fba1c-147">[Programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="fba1c-147">[Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="fba1c-148"> [Passo a passo: Acessando a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="fba1c-148"> [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="fba1c-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span><span class="sxs-lookup"><span data-stu-id="fba1c-149"> [Async](../../../visual-basic/language-reference/modifiers/async.md)</span></span>
