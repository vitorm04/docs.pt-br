---
title: "Async (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Async"
helpviewer_keywords: 
  - "Async [Visual Basic]"
  - "palavra-chave Async [Visual Basic]"
ms.assetid: 1be8b4b5-9689-41b5-bd33-b906bfd53bc5
caps.latest.revision: 37
caps.handback.revision: 37
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Async (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

O modificador de `Async` indica que o método ou [expressão lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) que altera são assíncrono.  Esses métodos são chamados *métodos de async*.  
  
 Um método async fornece uma maneira conveniente de fazer o trabalho potencialmente longo sem bloqueio do thread do chamador.  O chamador de um método assíncrono pode retomar seu trabalho sem aguardar a conclusão do método assíncrono.  
  
> [!NOTE]
>  As palavras\-chave de `Async` e de `Await` foram introduzidas no Visual Studio 2012.  Para uma introdução de programação async, consulte [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  
  
 O exemplo a seguir mostra a estrutura de um método de async.  Por convenção, os nomes de métodos de async terminam em “Async”.  
  
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
  
 Normalmente, um método modificado pela palavra\-chave `Async` contém pelo menos uma expressão ou instrução de [Espere](../../../visual-basic/language-reference/modifiers/async.md) .  O método executa forma até que o primeiro `Await`, ao ponto que ele suspende até que a tarefa deve terminar.  Entretanto, o controle é retornado para o chamador do método.  Se o método não contém uma expressão ou uma declaração de `Await` , o método não está suspensa e não é executado como um método síncrono faz.  Um aviso do compilador alerta você de todos os métodos async que não contêm `Await` porque essa situação pode indicar um erro.  Para obter mais informações, consulte [erro do compilador](../../../visual-basic/language-reference/error-messages/because-this-call-is-not-awaited-the-current-method-continues-to-run.md).  
  
 A palavra\-chave `Async` é uma palavra\-chave não reservadas.  É uma palavra\-chave quando altera um método ou uma expressão lambda.  Em todos contextos outros, é interpretado como um identificador.  
  
## Tipos de Retorno  
 Um método de async é um procedimento de [Sub](../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) , ou um procedimento de [Função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) que tenha um tipo de retorno de <xref:System.Threading.Tasks.Task> ou de <xref:System.Threading.Tasks.Task%601>.  O método não pode declarar os parâmetros de [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .  
  
 Você especifica `Task(Of TResult)` para o tipo de retorno de um método de async se a declaração de método [Retorno](../../../visual-basic/language-reference/statements/return-statement.md) de um operando tem o tipo TResult.  Você usa `Task` caso nenhum valor significativo seja retornado quando o método for concluído.  Ou seja, uma chamada para o método retorna `Task`, mas quando `Task` terminar, nenhuma instrução de `Await` que aguardar `Task` não gerencia um valor de resultado.  
  
 As sub\-rotinas de Async são usados principalmente para definir os manipuladores de eventos onde um procedimento de `Sub` é necessário.  O chamador de uma sub\-rotina de async não pode aguardar e não pode capturar exceções que os gera do método.  
  
 Para mais informações e exemplos, consulte [Tipos de retorno assíncronos](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Exemplo  
 Os exemplos a seguir mostram um manipulador de eventos de async, uma expressão lambda de async, e um método de async.  Para um exemplo completo que usa esses elementos, consulte [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md).  É possível baixar o código da explicação passo a passo de [Exemplos de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
  
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
  
## Consulte também  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [Operador Await](../../../visual-basic/language-reference/operators/await-operator.md)   
 [Programação assíncrona com Async e Await](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [Instruções passo a passo: acessando a Web e usando Async e Await](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)