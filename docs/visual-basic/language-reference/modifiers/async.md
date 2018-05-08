---
title: Async (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Async
helpviewer_keywords:
- Async [Visual Basic]
- Async keyword [Visual Basic]
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
ms.openlocfilehash: 829128ff39c0c5e4f6cb140852228a028e39e69c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="async-visual-basic"></a>Async (Visual Basic)
O `Async` modificador indica que o método ou [expressão lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) que ela modifica é assíncrona. Esses métodos são chamados de *métodos assíncronos*.  
  
 Um método assíncrono fornece uma maneira conveniente de fazer o trabalho de longa execução potencialmente sem bloquear o thread do chamador. O chamador de um método assíncrono pode retomar o trabalho sem esperar que o método assíncrono concluir.  
  
> [!NOTE]
>  As palavras-chave `Async` e `Await` foram introduzidas no Visual Studio 2012. Para obter uma introdução à programação assíncrona, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md).  
  
 O exemplo a seguir mostra a estrutura de um método assíncrono. Por convenção, os nomes de método assíncrono terminam com "Async".  
  
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
  
 Normalmente, um método modificado pelo `Async` palavra-chave contém pelo menos um [Await](../../../visual-basic/language-reference/modifiers/async.md) expressão ou instrução. O método de forma síncrona executa até atingir o primeiro `Await`, no ponto em que ele suspende até que a tarefa em espera é concluída. Enquanto isso, o controle é retornado ao chamador do método. Se o método não contém um `Await` expressão ou instrução, o método não está suspenso e executa como um método síncrono. Um aviso do compilador alerta para todos os métodos assíncronos que não contêm `Await` porque essa situação pode indicar um erro. Para obter mais informações, consulte o [erro do compilador](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 O `Async` palavra-chave é uma palavra-chave não reservada. É uma palavra-chave quando ela modifica um método ou uma expressão lambda. Em outros contextos, ele será interpretado como um identificador.  
  
## <a name="return-types"></a>Tipos de Retorno  
 Um método assíncrono é um [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedimento, ou um [função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) procedimento que tem um tipo de retorno <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. O método não pode declarar qualquer [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parâmetros.  
  
 Especificar `Task(Of TResult)` para o tipo de retorno de um método assíncrono se o [retornar](../../../visual-basic/language-reference/statements/return-statement.md) declaração do método tem um operando do tipo TResult. Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído. Ou seja, uma chamada para o método retorna um `Task`, mas quando o `Task` for concluída, qualquer `Await` instrução que está aguardando o `Task` não produz um valor de resultado.  
  
 Sub-rotinas assíncronas são usadas principalmente para definir manipuladores de eventos onde uma `Sub` procedimento é necessário. O chamador de uma sub-rotina async não pode esperar e não é possível capturar exceções que o método gera.  
  
 Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="example"></a>Exemplo  
 Os exemplos a seguir mostram um manipulador de eventos assíncrono, uma expressão de lambda async e um método assíncrono. Para obter um exemplo completo que usa esses elementos, consulte [passo a passo: acessando a Web, usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). É possível baixar o código do passo a passo em [Exemplos de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
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
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [Operador Await](../../../visual-basic/language-reference/operators/await-operator.md)  
 [Programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md)  
 [Instruções passo a passo: acessando a Web e usando Async e Await](../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
