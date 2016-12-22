---
title: "Como: fazer v&#225;rias solicita&#231;&#245;es da Web em paralelo usando Async e Await (Visual Basic) | Microsoft Docs"
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
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: fazer v&#225;rias solicita&#231;&#245;es da Web em paralelo usando Async e Await (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Em um método assíncrono, as tarefas são iniciadas quando eles são criados. O [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador é aplicado à tarefa no ponto em que o método em que o processamento não pode continuar até que a tarefa seja concluída. Geralmente, uma tarefa é aguardada assim que ele é criado, como mostra o exemplo a seguir.  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 No entanto, você pode separar a criação da tarefa de aguardando a tarefa se o programa tiver outro trabalho conseguir que não depende da conclusão da tarefa.  
  
```vb  
' The following line creates and starts the task.  
Dim myTask = someWebAccessMethodAsync(url)  
  
' While the task is running, you can do other work that does not depend  
' on the results of the task.  
' . . . . .  
  
' The application of Await suspends the rest of this method until the task is   
' complete.  
Dim result = Await myTask  
  
```  
  
 Entre iniciando uma tarefa e aguardando a ele, você pode iniciar outras tarefas. Tarefas adicionais implicitamente executem em paralelo, mas não há threads adicionais são criados.  
  
 O programa a seguir inicia três downloads da web assíncrona e, em seguida, aguarda\-los na ordem em que são chamados. Observe que, quando você executar o programa, o que as tarefas não são concluídas na ordem em que são criadas e espera sempre. Eles comecem a ser executadas quando eles são criados e uma ou mais tarefas podem terminar antes do método atinge as expressões await.  
  
> [!NOTE]
>  Para concluir este projeto, você deve ter o Visual Studio 2012 ou posterior e o .NET Framework 4.5 ou posterior instalado no computador.  
  
 Outro exemplo que inicia diversas tarefas ao mesmo tempo, consulte [Como: estender o passo a passo assíncronas usando Task. WhenAll \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
 Você pode baixar o código deste exemplo de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=254906).  
  
### Para configurar o projeto  
  
1.  Para configurar um aplicativo WPF, conclua as etapas a seguir. Você pode encontrar instruções detalhadas para essas etapas em [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).  
  
    -   Crie um aplicativo WPF que contém uma caixa de texto e um botão. Nomeie o botão `startButton`, e a caixa de texto nome `resultsTextBox`.  
  
    -   Adicione uma referência para <xref:System.Net.Http>.  
  
    -   No arquivo MainWindow.xaml.vb, adicione um `Imports` instrução `System.Net.Http`.  
  
### Para adicionar o código  
  
1.  Na janela de design, MainWindow. XAML, clique duas vezes no botão para criar o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.  
  
2.  Copie o seguinte código e cole\-o no corpo da `startButton_Click` em MainWindow.xaml.vb.  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     O código chama um método assíncrono, `CreateMultipleTasksAsync`, que acionam o aplicativo.  
  
3.  Adicione os seguintes métodos de suporte ao projeto:  
  
    -   `ProcessURLAsync` usa um <xref:System.Net.Http.HttpClient> método para baixar o conteúdo de um site como uma matriz de bytes. O método de suporte, `ProcessURLAsync` em seguida, exibe e retorna o comprimento da matriz.  
  
    -   `DisplayResults` Exibe o número de bytes na matriz de bytes para cada URL. Essa exibição mostra quando cada tarefa terminou o download.  
  
     Copie os seguintes métodos e colá\-los após o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.  
  
    ```vb  
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
    ```  
  
4.  Finalmente, defina o método `CreateMultipleTasksAsync`, que executa as seguintes etapas.  
  
    -   O método declara uma `HttpClient` objeto, que você precisa para acessar o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> em `ProcessURLAsync`.  
  
    -   O método cria e inicia três tarefas do tipo <xref:System.Threading.Tasks.Task%601>, onde `TResult` é um inteiro. Como cada tarefa termina, `DisplayResults` exibe a URL da tarefa e o comprimento do conteúdo baixado. Como as tarefas estão em execução assíncrona, a ordem na qual os resultados são exibidos pode diferir da ordem na qual eles foram declarados.  
  
    -   O método aguarda a conclusão de cada tarefa. Cada `Await` operador suspende a execução de `CreateMultipleTasksAsync` até que a tarefa aguardada seja concluída. O operador também recupera o valor de retorno da chamada para `ProcessURLAsync` de cada tarefa concluída.  
  
    -   Quando as tarefas foram concluídas e os valores inteiros forem recuperados, o método soma os comprimentos dos sites e exibe o resultado.  
  
     Copie o seguinte método e cole\-o em sua solução.  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/en-us/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/en-us/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
    ```  
  
5.  Escolha a tecla F5 para executar o programa e, em seguida, escolha o **Iniciar** botão.  
  
     Execute o programa várias vezes para verificar se as três tarefas não são concluídas sempre na mesma ordem e que a ordem em que elas sejam concluídas não é necessariamente a ordem em que elas são criadas e esperadas.  
  
## Exemplo  
 O código a seguir contém um exemplo completo.  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
        resultsTextBox.Clear()  
        Await CreateMultipleTasksAsync()  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/en-us/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/en-us/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
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
 [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Programação assíncrona com Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)   
 [Como: estender o passo a passo assíncronas usando Task. WhenAll \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)