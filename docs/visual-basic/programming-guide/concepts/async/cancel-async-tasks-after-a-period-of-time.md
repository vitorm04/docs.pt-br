---
title: "Cancelar tarefas assíncronas após um período de tempo (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6708bd92d8dc2455b9dcb8e02dcc0a4455e00cda
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a>Cancelar tarefas assíncronas após um período de tempo (Visual Basic)
Você pode cancelar uma operação assíncrona após um período de tempo usando o <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName>método se você não quiser aguardar a conclusão da operação.</xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName> Esse método agenda o cancelamento de quaisquer tarefas associadas que não estão concluídos dentro do período de tempo designado pelo `CancelAfter` expressão.  
  
 Este exemplo adiciona o código desenvolvido em [cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) para baixar uma lista de sites e exiba o comprimento do conteúdo de cada um.  
  
> [!NOTE]
>  Para executar os exemplos, você deve ter o Visual Studio 2012 ou posterior e o .NET Framework 4.5 ou posterior instalado no seu computador.  
  
## <a name="downloading-the-example"></a>Baixando o Exemplo  
 Você pode baixar o projeto completo do Windows Presentation Foundation (WPF) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.  
  
1.  Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.  
  
3.  No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução (. sln) para AsyncFineTuningVB.  
  
4.  Em **Solution Explorer**, abra o menu de atalho para o **CancelAfterTime** do projeto e escolha **Set as StartUp Project**.  
  
5.  Escolha a tecla F5 para executar o projeto.  
  
     Escolha as teclas Ctrl + F5 para executar o projeto sem depurá-lo.  
  
6.  Execute o programa várias vezes para verificar que a saída pode mostrar a saída para todos os sites, não há sites ou alguns sites da web.  
  
 Se você não quiser baixar o projeto, você pode examinar o arquivo MainWindow.xaml.vb no final deste tópico.  
  
## <a name="building-the-example"></a>Compilando o Exemplo  
 O exemplo neste tópico adiciona ao projeto que é desenvolvido no [cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) para cancelar uma lista de tarefas. O exemplo usa a mesma interface de usuário, embora o **Cancelar** botão não é usado explicitamente.  
  
 Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelAListOfTasks** como o **projeto de inicialização**. Adicione as alterações neste tópico para o projeto.  
  
 Para especificar um tempo máximo antes que as tarefas são marcadas como canceladas, adicione uma chamada para `CancelAfter` para `startButton_Click`, como mostra o exemplo a seguir. A adição é marcada com asteriscos.  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
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
```  
  
 Execute o programa várias vezes para verificar que a saída pode mostrar a saída para todos os sites, não há sites ou alguns sites da web. A saída a seguir é um exemplo.  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a>Exemplo completo  
 O código a seguir é o texto completo do arquivo MainWindow.xaml.vb no exemplo. Asteriscos marcam os elementos que foram adicionados para esse exemplo.  
  
 Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</xref:System.Net.Http>  
  
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
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
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
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a>Consulte também  
 [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)   
 [Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)   
 [Ajustando seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)   
 [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)
