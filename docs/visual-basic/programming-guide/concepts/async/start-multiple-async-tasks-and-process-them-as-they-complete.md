---
title: "Iniciar v&#225;rias tarefas ass&#237;ncronas e process&#225;-las assim que s&#227;o conclu&#237;das (Visual Basic) | Microsoft Docs"
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
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Iniciar v&#225;rias tarefas ass&#237;ncronas e process&#225;-las assim que s&#227;o conclu&#237;das (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Usando <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, você pode iniciar várias tarefas ao mesmo tempo e processá\-los individualmente eles estiverem concluídos, em vez de processá\-los na ordem em que eles são iniciados.  
  
 O exemplo a seguir usa uma consulta para criar uma coleção de tarefas. Cada tarefa baixa o conteúdo de um site específico. Em cada iteração de um pouco de loop, uma chamada aguardada para `WhenAny` retorna a tarefa na coleção de tarefas que conclui o download primeiro. Essa tarefa é removida da coleção e processada. O loop é repetido até que a coleção não contém mais tarefas.  
  
> [!NOTE]
>  Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
## Baixando o exemplo  
 Você pode baixar o projeto completo do Windows Presentation Foundation \(WPF\) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.  
  
1.  Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **Abrir**, **projeto\/solução**.  
  
3.  No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução \(. sln\) para AsyncFineTuningVB.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **ProcessTasksAsTheyFinish** do projeto e escolha **Set as StartUp Project**.  
  
5.  Escolha a tecla F5 para executar o projeto.  
  
     Escolha as teclas Ctrl \+ F5 para executar o projeto sem depurá\-lo.  
  
6.  Execute o projeto várias vezes para verificar se os comprimentos baixados sempre não aparecem na mesma ordem.  
  
 Se você não quiser baixar o projeto, você pode examinar o arquivo MainWindow.xaml.vb no final deste tópico.  
  
## Compilando o exemplo  
 Este exemplo adiciona ao código que é desenvolvido no [Cancelar as demais tarefas assíncronas após um completo \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) e usa a mesma interface do usuário.  
  
 Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelAfterOneTask** como o **projeto de inicialização**. Adicione as alterações neste tópico para o `AccessTheWebAsync` método nesse projeto. As alterações são marcadas com asteriscos.  
  
 O **CancelAfterOneTask** projeto já inclui uma consulta que, quando executado, cria uma coleção de tarefas. Cada chamada para `ProcessURLAsync` no código a seguir retorna um <xref:System.Threading.Tasks.Task%601> onde `TResult` é um inteiro.  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
 No arquivo MainWindow.xaml.vb do projeto, faça as seguintes alterações para o `AccessTheWebAsync` método.  
  
-   Execute a consulta aplicando <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> em vez de <xref:System.Linq.Enumerable.ToArray%2A>.  
  
<CodeContentPlaceHolder>1</CodeContentPlaceHolder>  
-   Adicionar um while loop que executa as seguintes etapas para cada tarefa na coleção.  
  
    1.  Espera de uma chamada para `WhenAny` para identificar a primeira tarefa na coleção para concluir o download.  
  
<CodeContentPlaceHolder>2</CodeContentPlaceHolder>  
    2.  Remove essa tarefa da coleção.  
  
<CodeContentPlaceHolder>3</CodeContentPlaceHolder>  
    3.  Espera de `firstFinishedTask`, que é retornado por uma chamada para `ProcessURLAsync`. O `firstFinishedTask` variável é um <xref:System.Threading.Tasks.Task%601> onde `TReturn` é um inteiro. A tarefa já foi concluída, mas você espera para recuperar o tamanho do site baixado, como mostra o exemplo a seguir.  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 Você deve executar o projeto várias vezes para verificar se os comprimentos baixados sempre não aparecem na mesma ordem.  
  
> [!CAUTION]
>  Você pode usar `WhenAny` em um loop, conforme descrito no exemplo, para resolver problemas que envolvem um pequeno número de tarefas. No entanto, outras abordagens são mais eficientes se você tiver um grande número de tarefas para processar. Para obter mais informações e exemplos, consulte [tarefas de processamento como eles completa](http://go.microsoft.com/fwlink/?LinkId=260810).  
  
## Exemplo completo  
 O código a seguir é o texto completo do arquivo MainWindow.xaml.vb no exemplo. Asteriscos marcam os elementos que foram adicionados para esse exemplo.  
  
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
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
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
  
        ' ***Create a query that, when executed, returns a collection of tasks.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client, ct)  
  
        ' ***Use ToList to execute the query and start the download tasks.   
        Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
  
        ' ***Add a loop to process the tasks one at a time until none remain.  
        While downloadTasks.Count > 0  
            ' ***Identify the first task that completes.  
            Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
  
            ' ***Remove the selected task from the list so that you don't  
            ' process it more than once.  
            downloadTasks.Remove(firstFinishedTask)  
  
            ' ***Await the first completed task and display the results.  
            Dim length = Await firstFinishedTask  
            resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        End While  
  
    End Function  
  
    ' Bundle the processing steps for a website into one async method.  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## Consulte também  
 <xref:System.Threading.Tasks.Task.WhenAny%2A>   
 [Ajustando seu aplicativo Async \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Programação assíncrona com Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)   
 [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)