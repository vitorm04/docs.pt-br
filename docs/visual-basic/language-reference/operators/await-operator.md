---
title: Operador Await (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Await
helpviewer_keywords:
- Await operator [Visual Basic]
- Await [Visual Basic]
ms.assetid: 6b1ce283-e92b-4ba7-b081-7be7b3d37af9
ms.openlocfilehash: d3bfafaa696955422c381aa1c17bc96591b44985
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962007"
---
# <a name="await-operator-visual-basic"></a>Operador Await (Visual Basic)
Você aplica o `Await` operador a um operando em um método assíncrono ou expressão lambda para suspender a execução do método até que a tarefa esperada seja concluída. A tarefa representa um trabalho em andamento.  
  
 O método no qual `Await` é usado deve ter um modificador [assíncrono](../../../visual-basic/language-reference/modifiers/async.md) . Esse tipo de método, definido pelo uso do modificador `Async` e, geralmente, contendo uma ou mais expressões `Await`, é conhecido como um *método assíncrono*.  
  
> [!NOTE]
> As palavras-chave `Async` e `Await` foram introduzidas no Visual Studio 2012. Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 Normalmente, a tarefa à qual você aplica o `Await` operador é o valor de retorno de uma chamada para um método que implementa o [padrão assíncrono baseado em tarefa](https://go.microsoft.com/fwlink/?LinkId=204847), ou seja, <xref:System.Threading.Tasks.Task> um ou <xref:System.Threading.Tasks.Task%601>um.  
  
 No código a seguir, o <xref:System.Net.Http.HttpClient> método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> retorna `getContentsTask`, a `Task(Of Byte())`. A tarefa é uma promessa de produzir a matriz de bytes real quando a operação é concluída. O operador `Await` é aplicado a `getContentsTask` para suspender a execução em `SumPageSizesAsync` até que `getContentsTask` seja concluída. Enquanto isso, o controle é retornado ao chamador de `SumPageSizesAsync`. Quando `getContentsTask` for concluído, a expressão `Await` resulta em uma matriz de bytes.  
  
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
> Para o exemplo completo, confira o [Passo a passo: Como acessar a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Você pode baixar o exemplo em [Exemplos de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) no site da Microsoft. O exemplo está no projeto AsyncWalkthrough_HttpClient.  
  
 Se `Await` for aplicado ao resultado de uma chamada de método que retorna um `Task(Of TResult)` `Await` , o tipo da expressão será TResult. Se `Await` for aplicado ao resultado de uma chamada de método que retorna um `Task`, a `Await` expressão não retornará um valor. O exemplo a seguir ilustra a diferença.  
  
```vb  
' Await used with a method that returns a Task(Of TResult).  
Dim result As TResult = Await AsyncMethodThatReturnsTaskTResult()  
  
' Await used with a method that returns a Task.  
Await AsyncMethodThatReturnsTask()  
```  
  
 Uma `Await` expressão ou instrução não bloqueia o thread no qual está sendo executada. Em vez disso, faz com que o compilador inscreva o restante do método assíncrono, após `Await` a expressão, como uma continuação na tarefa esperada. Em seguida, o controle retorna para o chamador do método assíncrono. Quando a tarefa for concluída, ela invoca a sua continuação e a execução do método assíncrono continua de onde parou.  
  
 Uma `Await` expressão só pode ocorrer no corpo de um método de circunscrição ou expressão lambda que é marcada por um `Async` modificador. O termo *Await* serve como uma palavra-chave somente nesse contexto. Em outro local, ele será interpretado como um identificador. Dentro do método Async ou da expressão lambda, `Await` uma expressão não pode ocorrer em uma expressão de consulta `catch` , `finally` no bloco ou de uma [tentativa... Capturar... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) , na expressão de variável de controle de loop `For` de `For Each` um loop ou, no corpo de uma instrução [SyncLock](../../../visual-basic/language-reference/statements/synclock-statement.md) .  
  
## <a name="exceptions"></a>Exceções  
 A maioria dos métodos assíncronos retorna um <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601>. As propriedades da tarefa retornada transportam informações sobre seu status e histórico como: se a tarefa foi concluída, se o método assíncrono causou uma exceção ou se foi cancelado e qual foi o resultado final. O operador `Await` acessa essas propriedades.  
  
 Se você aguarda um método assíncrono de retorno de tarefa que causou uma exceção, o operador `Await` relançará a exceção.  
  
 Se você aguardar um método assíncrono de retorno de tarefa que é cancelado, o `Await` operador relançará um. <xref:System.OperationCanceledException>  
  
 Uma tarefa única que está em um estado com falha pode refletir várias exceções.  Por exemplo, a tarefa pode ser o resultado de uma chamada para <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>. Quando você aguarda essa tarefa, a operação de aguardar relança apenas uma das exceções. No entanto, você não pode prever qual das exceções será relançada.  
  
 Para obter exemplos de tratamento de erros em métodos assíncronos, consulte [try... Capturar... Instrução Finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo do Windows Forms a seguir ilustra o uso do `Await` em um método assíncrono `WaitAsynchronouslyAsync`. Compare o comportamento desse método com o comportamento de `WaitSynchronously`. Sem um `Await` operador, `WaitSynchronously` é executado de forma síncrona, `Async` apesar do uso do modificador em sua definição <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> e uma chamada para em seu corpo.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Passo a passo: acessar a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [Async](../../../visual-basic/language-reference/modifiers/async.md)
