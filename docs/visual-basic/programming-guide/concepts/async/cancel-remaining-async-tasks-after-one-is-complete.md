---
title: "Cancelar as demais tarefas ass&#237;ncronas ap&#243;s um completo (Visual Basic) | Microsoft Docs"
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
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Cancelar as demais tarefas ass&#237;ncronas ap&#243;s um completo (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Usando o <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> método junto com um <xref:System.Threading.CancellationToken>, você pode cancelar todas as tarefas restantes quando uma tarefa é concluída. O `WhenAny` método tem um argumento que é um conjunto de tarefas. O método inicia todas as tarefas e retorna uma única tarefa. A tarefa é concluída quando qualquer tarefa na coleção é concluída.  
  
 Este exemplo demonstra como usar um token de cancelamento em conjunto com `WhenAny` para manter a primeira tarefa ao fim da coleção de tarefas e para cancelar as tarefas restantes. Cada tarefa baixa o conteúdo de um site. O exemplo exibe o comprimento do conteúdo do primeiro download para concluir e cancela os outros downloads.  
  
> [!NOTE]
>  Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
## Baixando o exemplo  
 Você pode baixar o projeto completo do Windows Presentation Foundation \(WPF\) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.  
  
1.  Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **Abrir**, **projeto\/solução**.  
  
3.  No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução \(. sln\) para AsyncFineTuningVB.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **CancelAfterOneTask** do projeto e escolha **Set as StartUp Project**.  
  
5.  Escolha a tecla F5 para executar o projeto.  
  
     Escolha as teclas Ctrl \+ F5 para executar o projeto sem depurá\-lo.  
  
6.  Execute o programa várias vezes para verificar que diferentes downloads concluir primeiro.  
  
 Se você não quiser baixar o projeto, você pode examinar o arquivo MainWindow.xaml.vb no final deste tópico.  
  
## Compilando o exemplo  
 O exemplo neste tópico adiciona ao projeto que é desenvolvido no [Cancelar uma tarefa assíncrona ou uma lista de tarefas](../Topic/Cancel%20an%20Async%20Task%20or%20a%20List%20of%20Tasks%20\(C%23%20and%20Visual%20Basic\).md) para cancelar uma lista de tarefas. O exemplo usa a mesma interface de usuário, embora o **Cancelar** botão não é usado explicitamente.  
  
 Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelAListOfTasks** como o **projeto de inicialização**. Adicione as alterações neste tópico para o projeto.  
  
 No arquivo MainWindow.xaml.vb do **CancelAListOfTasks** de projeto, iniciar a transição movendo as etapas de processamento para cada site do loop na `AccessTheWebAsync` para o seguinte método assíncrono.  
  
```vb  
' ***Bundle the processing steps for a website into one async method.  
Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
    ' GetAsync returns a Task(Of HttpResponseMessage).   
    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
    ' Retrieve the website contents from the HttpResponseMessage.  
    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
    Return urlContents.Length  
End Function  
```  
  
 Em `AccessTheWebAsync`, este exemplo usa uma consulta, o  <xref:System.Linq.Enumerable.ToArray%2A> método e o `WhenAny` método para criar e iniciar uma matriz de tarefas. O aplicativo de `WhenAny` à matriz retorna uma única tarefa que, quando colocado em espera, é avaliada para a primeira tarefa para alcançar a conclusão da matriz de tarefas.  
  
 Faça as seguintes alterações em `AccessTheWebAsync`. Asteriscos marcam as alterações no arquivo de código.  
  
1.  Comentar ou excluir o loop.  
  
2.  Criar uma consulta que, quando executado, produz uma coleção de tarefas genéricas. Cada chamada para `ProcessURLAsync` retorna um <xref:System.Threading.Tasks.Task%601> onde `TResult` é um inteiro.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
3.  Chamar `ToArray` para executar a consulta e iniciar as tarefas. O aplicativo do `WhenAny` método na próxima etapa seria executar a consulta e iniciar as tarefas sem usar `ToArray`, mas outros métodos não podem. A prática mais segura é forçar a execução da consulta explicitamente.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
4.  Chamar `WhenAny` na coleção de tarefas.`WhenAny` Retorna um `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.  Ou seja, `WhenAny` retorna uma tarefa que avalia para um único `Task(Of Integer)` ou `Task<int>` quando é esperado. Essa única tarefa é a primeira tarefa na coleção para concluir. A tarefa que concluiu o primeiro é atribuída a `firstFinishedTask`. O tipo de `firstFinishedTask` é <xref:System.Threading.Tasks.Task%601> onde `TResult` é um inteiro, porque esse é o tipo de retorno de `ProcessURLAsync`.  
  
    ```vb  
    ' ***Call WhenAny and then await the result. The task that finishes   
    ' first is assigned to firstFinishedTask.  
    Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
    ```  
  
5.  Neste exemplo, você está interessado apenas na tarefa que termina primeiro. Portanto, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> para cancelar as tarefas restantes.  
  
    ```vb  
    ' ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel()  
    ```  
  
6.  Por fim, await `firstFinishedTask` para recuperar o comprimento do conteúdo baixado.  
  
    ```vb  
    Dim length = Await firstFinishedTask  
    resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    ```  
  
 Execute o programa várias vezes para verificar que diferentes downloads concluir primeiro.  
  
## Exemplo completo  
 O código a seguir é o arquivo MainWindow.xaml.vb ou MainWindow.xaml.cs completo para o exemplo. Asteriscos marcam os elementos que foram adicionados para esse exemplo.  
  
 Observe que você deve adicionar uma referência para <xref:System.Net.Http>.  
  
 Você pode baixar o projeto de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Download complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        '' Comment out or delete the loop.  
        ''For Each url In urlList  
        ''    ' GetAsync returns a Task(Of HttpResponseMessage).   
        ''    ' Argument ct carries the message if the Cancel button is chosen.   
        ''    ' Note that the Cancel button can cancel all remaining downloads.  
        ''    Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ''    ' Retrieve the website contents from the HttpResponseMessage.  
        ''    Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ''    resultsTextBox.Text &=  
        ''        String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        ''Next  
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToArray to execute the query and start the download tasks.   
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' ***Call WhenAny and then await the result. The task that finishes   
        ' first is assigned to firstFinishedTask.  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
        ' ***Cancel the rest of the downloads. You just want the first one.  
        cts.Cancel()  
  
        ' ***Await the first completed task and display the results  
        ' Run the program several times to demonstrate that different  
        ' websites can finish first.  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
    End Function  
  
    ' ***Bundle the processing steps for a website into one async method.  
    Async Function ProcessURLAsync(url As String, client As HttpClient, ct As CancellationToken) As Task(Of Integer)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        Return urlContents.Length  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/en-us/library/hh290138.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
                "http://msdn.microsoft.com/en-us/library/dd470362.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## Consulte também  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [Ajustando seu aplicativo Async \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Programação assíncrona com Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)   
 [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)