---
title: "Como: estender o passo a passo ass&#237;ncronas usando Task. WhenAll (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: estender o passo a passo ass&#237;ncronas usando Task. WhenAll (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode melhorar o desempenho da solução assíncrona em [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) usando o <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> método. Esse método de forma assíncrona awaits várias operações assíncronas, que são representadas como uma coleção de tarefas.  
  
 Você pode ter notado no passo a passo que os sites baixem em taxas diferentes. Às vezes, um dos sites está muito lento, que atrasa todos os downloads restantes. Quando você executar as soluções assíncronas que você criou no passo a passo, você pode finalizar o programa facilmente se você não quiser esperar, mas uma opção melhor seria iniciar todos os downloads ao mesmo tempo e permitir que mais rápido downloads continuam sem esperar que está atrasada.  
  
 Aplicar o `Task.WhenAll` método a uma coleção de tarefas. O aplicativo de `WhenAll` retorna uma única tarefa não será completa até a conclusão de cada tarefa na coleção. As tarefas parecem ser executados em paralelo, mas não há threads adicionais são criados. As tarefas podem ser concluídas em qualquer ordem.  
  
> [!IMPORTANT]
>  Os procedimentos a seguir descrevem extensões para os aplicativos assíncronos que são desenvolvidos em [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). Você pode desenvolver os aplicativos por concluir o passo a passo ou baixar o código de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).  
>   
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou posterior instalado no seu computador.  
  
### Para adicionar o Task. WhenAll à sua solução GetURLContentsAsync  
  
1.  Adicionar o `ProcessURLAsync` o primeiro aplicativo que é desenvolvido no método [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Se você baixou o código de  [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191), abra o projeto AsyncWalkthrough e, em seguida, adicionar `ProcessURLAsync` para o arquivo MainWindow.xaml.vb.  
  
    -   Se você desenvolveu o código ao concluir o passo a passo, adicione `ProcessURLAsync` para o aplicativo que inclui o `GetURLContentsAsync` método. O arquivo MainWindow.xaml.vb para este aplicativo é o primeiro exemplo na seção "Exemplos de código completa a apresentação" do.  
  
     O `ProcessURLAsync` método consolida as ações no corpo do `For Each` loop na `SumPageSizesAsync` no passo a passo original. O método assíncrona baixa o conteúdo de um site específico, como uma matriz de bytes e, em seguida, exibe e retorna o comprimento da matriz de bytes.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Comentar ou excluir o `For Each` loop na `SumPageSizesAsync`, como mostra o código a seguir.  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  Crie um conjunto de tarefas. O código a seguir define uma [consulta](../Topic/LINQ%20\(Language-Integrated%20Query\).md) que, quando executado pelo <xref:System.Linq.Enumerable.ToArray%2A> método cria uma coleção de tarefas que baixar o conteúdo de cada site. As tarefas são iniciadas quando a consulta é avaliada.  
  
     Adicione o seguinte código ao método `SumPageSizesAsync` depois da declaração da `urlList`.  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Aplicar `Task.WhenAll` à coleção de tarefas, `downloadTasks`.`Task.WhenAll` Retorna uma única tarefa termina quando tem concluído todas as tarefas na coleção de tarefas.  
  
     No exemplo a seguir, o `Await` expressão aguarda a conclusão do único de tarefa que `WhenAll` retorna. A expressão é avaliada como uma matriz de inteiros, onde cada inteiro é o comprimento de um site de download. Adicione o seguinte código para `SumPageSizesAsync`, apenas após o código que você adicionou na etapa anterior.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Por fim, use o <xref:System.Linq.Enumerable.Sum%2A> método para calcular a soma dos comprimentos de todos os sites. Adicione a seguinte linha ao `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### Para adicionar o Task. WhenAll à solução HttpClient.GetByteArrayAsync  
  
1.  Adicione a seguinte versão `ProcessURLAsync` para o segundo aplicativo é desenvolvido no [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Se você baixou o código de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191), abra o projeto AsyncWalkthrough\_HttpClient e, em seguida, adicionar `ProcessURLAsync` para o arquivo MainWindow.xaml.vb.  
  
    -   Se você desenvolveu o código ao concluir o passo a passo, adicione `ProcessURLAsync` para o aplicativo que usa o `HttpClient.GetByteArrayAsync` método. O arquivo MainWindow.xaml.vb para este aplicativo é o segundo exemplo na seção "Exemplos de código completa a apresentação" do.  
  
     O `ProcessURLAsync` método consolida as ações no corpo do `For Each` loop na `SumPageSizesAsync` no passo a passo original. O método assíncrona baixa o conteúdo de um site específico, como uma matriz de bytes e, em seguida, exibe e retorna o comprimento da matriz de bytes.  
  
     A única diferença do `ProcessURLAsync` método no procedimento anterior é o uso da <xref:System.Net.Http.HttpClient> instância, `client`.  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  Comentar ou excluir o `For Each` loop na `SumPageSizesAsync`, como mostra o código a seguir.  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
  
    ```  
  
3.  Definir um [consulta](../Topic/LINQ%20\(Language-Integrated%20Query\).md) que, quando executado pelo <xref:System.Linq.Enumerable.ToArray%2A> método cria uma coleção de tarefas que baixar o conteúdo de cada site. As tarefas são iniciadas quando a consulta é avaliada.  
  
     Adicione o seguinte código ao método `SumPageSizesAsync` depois da declaração da `client` e `urlList`.  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  Em seguida, aplicar `Task.WhenAll` à coleção de tarefas, `downloadTasks`.`Task.WhenAll` Retorna uma única tarefa termina quando tem concluído todas as tarefas na coleção de tarefas.  
  
     No exemplo a seguir, o `Await` expressão aguarda a conclusão do único de tarefa que `WhenAll` retorna. Ao concluir, o `Await` expressão é avaliada como uma matriz de inteiros, onde cada inteiro é o comprimento de um site de download. Adicione o seguinte código para `SumPageSizesAsync`, apenas após o código que você adicionou na etapa anterior.  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  Por fim, use o <xref:System.Linq.Enumerable.Sum%2A> método para obter a soma dos comprimentos de todos os sites. Adicione a seguinte linha ao `SumPageSizesAsync`.  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### Para testar as soluções Task. WhenAll  
  
-   Para qualquer solução, escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão. A saída deve se parecer com a saída das soluções assíncronas em [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md). No entanto, observe que os sites da Web aparecem em uma ordem diferente cada vez.  
  
## Exemplo  
 O código a seguir mostra as extensões para o projeto que usa o `GetURLContentsAsync` método para baixar conteúdo da web.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/en-us/library/hh290136.aspx",  
                "http://msdn.microsoft.com/en-us/library/ee256749.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290138.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
                "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
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
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## Exemplo  
 O código a seguir mostra as extensões para o projeto que usa o método `HttpClient.GetByteArrayAsync` para baixar o conteúdo da web.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/en-us/library/hh290136.aspx",  
                "http://msdn.microsoft.com/en-us/library/ee256749.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290138.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
                "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
  
End Class  
```  
  
## Consulte também  
 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>   
 [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)