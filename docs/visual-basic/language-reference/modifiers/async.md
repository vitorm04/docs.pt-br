---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: aaf5a95edb9cba9726163be3925b006a7641597c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040854"
---
# <a name="async-visual-basic"></a><span data-ttu-id="f07a6-102">Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f07a6-102">Async (Visual Basic)</span></span>

<span data-ttu-id="f07a6-103">O modificador `Async` indica que o método ou a [expressão lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) que ele modifica é assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f07a6-103">The `Async` modifier indicates that the method or [lambda expression](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) that it modifies is asynchronous.</span></span> <span data-ttu-id="f07a6-104">Esses métodos são chamados de *métodos assíncronos*.</span><span class="sxs-lookup"><span data-stu-id="f07a6-104">Such methods are referred to as *async methods*.</span></span>

<span data-ttu-id="f07a6-105">Um método assíncrono fornece uma maneira conveniente de executar trabalhos potencialmente demorados sem bloquear o thread do chamador.</span><span class="sxs-lookup"><span data-stu-id="f07a6-105">An async method provides a convenient way to do potentially long-running work without blocking the caller's thread.</span></span> <span data-ttu-id="f07a6-106">O chamador de um método assíncrono pode retomar seu trabalho sem esperar que o método Async seja concluído.</span><span class="sxs-lookup"><span data-stu-id="f07a6-106">The caller of an async method can resume its work without waiting for the async method to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="f07a6-107">As palavras-chave `Async` e `Await` foram introduzidas no Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f07a6-107">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span> <span data-ttu-id="f07a6-108">Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="f07a6-108">For an introduction to async programming, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="f07a6-109">O exemplo a seguir mostra a estrutura de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="f07a6-109">The following example shows the structure of an async method.</span></span> <span data-ttu-id="f07a6-110">Por convenção, os nomes de método assíncronos terminam em "Async".</span><span class="sxs-lookup"><span data-stu-id="f07a6-110">By convention, async method names end in "Async."</span></span>

```vb
Public Async Function ExampleMethodAsync() As Task(Of Integer)
    ' . . .

    ' At the Await expression, execution in this method is suspended and,
    ' if AwaitedProcessAsync has not already finished, control returns
    ' to the caller of ExampleMethodAsync. When the awaited task is
    ' completed, this method resumes execution.
    Dim exampleInt As Integer = Await AwaitedProcessAsync()

    ' . . .

    ' The return statement completes the task. Any method that is
    ' awaiting ExampleMethodAsync can now get the integer result.
    Return exampleInt
End Function
```

<span data-ttu-id="f07a6-111">Normalmente, um método modificado pela palavra-chave `Async` contém pelo menos uma expressão ou instrução [Await](../../../visual-basic/language-reference/modifiers/async.md) .</span><span class="sxs-lookup"><span data-stu-id="f07a6-111">Typically, a method modified by the `Async` keyword contains at least one [Await](../../../visual-basic/language-reference/modifiers/async.md) expression or statement.</span></span> <span data-ttu-id="f07a6-112">O método é executado de forma síncrona até atingir o primeiro `Await`, no ponto em que ele é suspenso até que a tarefa esperada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="f07a6-112">The method runs synchronously until it reaches the first `Await`, at which point it suspends until the awaited task completes.</span></span> <span data-ttu-id="f07a6-113">Enquanto isso, o controle é retornado para o chamador do método.</span><span class="sxs-lookup"><span data-stu-id="f07a6-113">In the meantime, control is returned to the caller of the method.</span></span> <span data-ttu-id="f07a6-114">Se o método não contiver uma expressão `Await` ou instrução, o método não será suspenso e será executado como um método síncrono.</span><span class="sxs-lookup"><span data-stu-id="f07a6-114">If the method doesn't contain an `Await` expression or statement, the method isn't suspended and executes as a synchronous method does.</span></span> <span data-ttu-id="f07a6-115">Um aviso do compilador alerta você para quaisquer métodos assíncronos que não contenham `Await` porque essa situação pode indicar um erro.</span><span class="sxs-lookup"><span data-stu-id="f07a6-115">A compiler warning alerts you to any async methods that don't contain `Await` because that situation might indicate an error.</span></span> <span data-ttu-id="f07a6-116">Para obter mais informações, consulte o [erro do compilador](../error-messages/bc42358.md).</span><span class="sxs-lookup"><span data-stu-id="f07a6-116">For more information, see the [compiler error](../error-messages/bc42358.md).</span></span>

<span data-ttu-id="f07a6-117">A palavra-chave `Async` é uma palavra-chave não reservada.</span><span class="sxs-lookup"><span data-stu-id="f07a6-117">The `Async` keyword is an unreserved keyword.</span></span> <span data-ttu-id="f07a6-118">É uma palavra-chave quando modifica um método ou uma expressão lambda.</span><span class="sxs-lookup"><span data-stu-id="f07a6-118">It is a keyword when it modifies a method or a lambda expression.</span></span> <span data-ttu-id="f07a6-119">Em todos os outros contextos, ele é interpretado como um identificador.</span><span class="sxs-lookup"><span data-stu-id="f07a6-119">In all other contexts, it is interpreted as an identifier.</span></span>

## <a name="return-types"></a><span data-ttu-id="f07a6-120">Tipos de Retorno</span><span class="sxs-lookup"><span data-stu-id="f07a6-120">Return Types</span></span>

<span data-ttu-id="f07a6-121">Um método assíncrono é um procedimento [sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) ou um procedimento [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) que tem um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="f07a6-121">An async method is either a [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure, or a [Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedure that has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="f07a6-122">O método não pode declarar nenhum parâmetro [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="f07a6-122">The method cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="f07a6-123">Você especifica `Task(Of TResult)` para o tipo de retorno de um método assíncrono se a instrução [Return](../../../visual-basic/language-reference/statements/return-statement.md) do método tiver um operando do tipo TResult.</span><span class="sxs-lookup"><span data-stu-id="f07a6-123">You specify `Task(Of TResult)` for the return type of an async method if the [Return](../../../visual-basic/language-reference/statements/return-statement.md) statement of the method has an operand of type TResult.</span></span> <span data-ttu-id="f07a6-124">Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído.</span><span class="sxs-lookup"><span data-stu-id="f07a6-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="f07a6-125">Ou seja, uma chamada para o método retorna um `Task`, mas quando a `Task` é concluída, qualquer instrução `Await` que esteja aguardando o `Task` não produz um valor de resultado.</span><span class="sxs-lookup"><span data-stu-id="f07a6-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `Await` statement that's awaiting the `Task` doesn’t produce a result value.</span></span>

<span data-ttu-id="f07a6-126">As sub-rotinas assíncronas são usadas principalmente para definir manipuladores de eventos onde um procedimento de `Sub` é necessário.</span><span class="sxs-lookup"><span data-stu-id="f07a6-126">Async subroutines are used primarily to define event handlers where a `Sub` procedure is required.</span></span> <span data-ttu-id="f07a6-127">O chamador de uma sub-rotina assíncrona não pode aguardar e não pode capturar exceções que o método gera.</span><span class="sxs-lookup"><span data-stu-id="f07a6-127">The caller of an async subroutine can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="f07a6-128">Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="f07a6-128">For more information and examples, see [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="f07a6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f07a6-129">Example</span></span>

<span data-ttu-id="f07a6-130">Os exemplos a seguir mostram um manipulador de eventos assíncrono, uma expressão lambda Async e um método Async.</span><span class="sxs-lookup"><span data-stu-id="f07a6-130">The following examples show an async event handler, an async lambda expression, and an async method.</span></span> <span data-ttu-id="f07a6-131">Para obter um exemplo completo que usa esses elementos, consulte [Walkthrough: acessando a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="f07a6-131">For a full example that uses these elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="f07a6-132">É possível baixar o código do passo a passo em [Exemplos de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="f07a6-132">You can download the walkthrough code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

```vb
' An event handler must be a Sub procedure.
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click
    textBox1.Clear()
    ' SumPageSizesAsync is a method that returns a Task.
    Await SumPageSizesAsync()
    textBox1.Text = vbCrLf & "Control returned to button1_Click."
End Sub

' The following async lambda expression creates an equivalent anonymous
' event handler.
AddHandler button1.Click, Async Sub(sender, e)
                              textBox1.Clear()
                              ' SumPageSizesAsync is a method that returns a Task.
                              Await SumPageSizesAsync()
                              textBox1.Text = vbCrLf & "Control returned to button1_Click."
                          End Sub

' The following async method returns a Task(Of T).
' A typical call awaits the Byte array result:
'      Dim result As Byte() = Await GetURLContents("https://msdn.com")
Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

    ' The downloaded resource ends up in the variable named content.
    Dim content = New MemoryStream()

    ' Initialize an HttpWebRequest for the current URL.
    Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

    ' Send the request to the Internet resource and wait for
    ' the response.
    Using response As WebResponse = Await webReq.GetResponseAsync()
        ' Get the data stream that is associated with the specified URL.
        Using responseStream As Stream = response.GetResponseStream()
            ' Read the bytes in responseStream and copy them to content.
            ' CopyToAsync returns a Task, not a Task<T>.
            Await responseStream.CopyToAsync(content)
        End Using
    End Using

    ' Return the result as a byte array.
    Return content.ToArray()
End Function
```

## <a name="see-also"></a><span data-ttu-id="f07a6-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f07a6-133">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="f07a6-134">Operador Await</span><span class="sxs-lookup"><span data-stu-id="f07a6-134">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="f07a6-135">Programação assíncrona com Async e Await</span><span class="sxs-lookup"><span data-stu-id="f07a6-135">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="f07a6-136">Instruções passo a passo: acessando a Web e usando Async e Await</span><span class="sxs-lookup"><span data-stu-id="f07a6-136">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
