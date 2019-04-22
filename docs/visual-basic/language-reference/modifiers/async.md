---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: ad6d671a45cee7d534347d23963bb5035ecc8dac
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834576"
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
O `Async` modificador indica que o método ou [expressão lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) que ele modifica é assíncrona. Esses métodos são chamados de *métodos assíncronos*.  
  
 Um método async fornece uma maneira conveniente para fazer trabalhos potencialmente longos sem bloquear o thread do chamador. O chamador de um método assíncrono pode retomar seu trabalho sem aguardar o conclusão do método assíncrono.  
  
> [!NOTE]
>  As palavras-chave `Async` e `Await` foram introduzidas no Visual Studio 2012. Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 O exemplo a seguir mostra a estrutura de um método assíncrono. Por convenção, nomes de método assíncrono terminar com "Async".  
  
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
  
 Normalmente, um método modificado pela `Async` palavra-chave contém pelo menos um [Await](../../../visual-basic/language-reference/modifiers/async.md) expressão ou instrução. O método de forma síncrona executa até atingir o primeiro `Await`, no ponto em que ele suspende até que a tarefa aguardada seja concluída. Enquanto isso, o controle é retornado ao chamador do método. Se o método não contiver um `Await` expressão ou instrução, o método não está suspenso e executa como um método síncrono. Um aviso de compilador o alertará sobre quaisquer métodos assíncronos que não contêm `Await` porque essa situação poderá indicar um erro. Para obter mais informações, consulte o [erro do compilador](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 O `Async` palavra-chave é uma palavra-chave não reservada. É uma palavra-chave quando ela modifica um método ou uma expressão lambda. Em outros contextos, ele será interpretado como um identificador.  
  
## <a name="return-types"></a>Tipos de Retorno  
 Um método assíncrono é uma [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimento, ou um [função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) que tem um tipo de retorno do procedimento <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. O método não pode declarar nenhum [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parâmetros.  
  
 Você especifica `Task(Of TResult)` para o tipo de retorno de um método assíncrono se a [retornar](../../../visual-basic/language-reference/statements/return-statement.md) declaração do método tem um operando do tipo TResult. Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído. Ou seja, uma chamada para o método retorna um `Task`, mas quando o `Task` for concluída, qualquer `Await` instrução que está aguardando o `Task` não produz um valor de resultado.  
  
 Async sub-rotinas são usadas principalmente para definir manipuladores de eventos em que um `Sub` procedimento é necessário. O chamador de uma sub-rotina de async não pode aguardar e não pode capturar exceções que esse método gera.  
  
 Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram um manipulador de eventos assíncronos, uma expressão de lambda async e um método assíncrono. Para obter um exemplo completo que usa esses elementos, consulte [passo a passo: acessar a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). É possível baixar o código do passo a passo em [Exemplos de código do desenvolvedor](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).  
  
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
'      Dim result As Byte() = Await GetURLContents("http://msdn.com")  
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
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [Operador Await](../../../visual-basic/language-reference/operators/await-operator.md)
- [Programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md)
- [Passo a passo: acessar a Web usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
