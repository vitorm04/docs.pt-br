---
title: "Tratando a reentrada em aplicativos ass&#237;ncronos (Visual Basic) | Microsoft Docs"
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
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Tratando a reentrada em aplicativos ass&#237;ncronos (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você inclui o código assíncrono em seu aplicativo, você deve considerar e possivelmente evitar reentrância, que se refere ao redigitando uma operação assíncrona, antes de ser concluído. Se você não identificar e lidar com possibilidades de reentrância, ele pode causar resultados inesperados.  
  
 **Neste tópico**  
  
-   [Recognizing Reentrancy](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_RecognizingReentrancy)  
  
-   [Handling Reentrancy](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_HandlingReentrancy)  
  
    -   [Disable the Start Button](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_DisableTheStartButton)  
  
    -   [Cancel and Restart the Operation](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_CancelAndRestart)  
  
    -   [Run Multiple Operations and Queue the Output](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_RunMultipleOperations)  
  
-   [Reviewing and Running the Example App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
##  <a name="BKMK_RecognizingReentrancy"></a> Reconhecendo reentrada  
 O exemplo neste tópico, os usuários escolhem um **Iniciar** botão para iniciar um aplicativo assíncrono que baixa uma série de sites e calcula o número total de bytes baixados. Uma versão síncrona do exemplo responderia a mesma forma independentemente de quantas vezes um usuário escolhe o botão porque, após a primeira vez, o thread de interface do usuário ignora esses eventos até que o aplicativo é encerrado. Em um aplicativo assíncrono, no entanto, o thread de interface do usuário continua a responder e você pode digitar novamente a operação assíncrona antes de ser concluído.  
  
 O exemplo a seguir mostra a esperada de saída se o usuário escolhe o **Iniciar** botão apenas uma vez. É exibida uma lista dos sites baixados com o tamanho, em bytes, de cada site. O número total de bytes é exibida no final.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 No entanto, se o usuário clica no botão de mais de uma vez, o manipulador de eventos é chamado repetidamente, e o processo de download é reinserido cada vez. Como resultado, várias operações assíncronas estão em execução ao mesmo tempo, a saída intercala os resultados e o número total de bytes é confuso.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/en-us/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Você pode examinar o código que produz esta saída navegado até o final deste tópico. Você pode experimentar o código baixando a solução em seu computador local e, em seguida, executando o projeto WebsiteDownload ou usando o código no final deste tópico para criar seu próprio projeto para obter mais informações e instruções, consulte [Reviewing and Running the Example App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMD_SettingUpTheExample).  
  
##  <a name="BKMK_HandlingReentrancy"></a> Tratando a reentrada  
 Você pode manipular reentrância de várias maneiras, dependendo do que você deseja que seu aplicativo faça. Este tópico apresenta os exemplos a seguir:  
  
-   [Disable the Start Button](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_DisableTheStartButton)  
  
     Desabilitar o **Iniciar** botão enquanto a operação está em execução para que o usuário não é possível interrompê\-lo.  
  
-   [Cancel and Restart the Operation](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_CancelAndRestart)  
  
     Cancelar qualquer operação que ainda está em execução quando o usuário escolhe o **Iniciar** novamente e, em seguida, continuar a permitir que a operação solicitada mais recentemente.  
  
-   [Run Multiple Operations and Queue the Output](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_RunMultipleOperations)  
  
     Permitir que todos os solicitados operações executadas de forma assíncrona, mas coordenar a exibição da saída de forma que os resultados de cada operação aparecem juntos e na ordem.  
  
###  <a name="BKMK_DisableTheStartButton"></a> Desabilitar o botão Iniciar  
 Você pode bloquear o **Iniciar** botão enquanto uma operação está em execução, desativando o botão na parte superior do `StartButton_Click` manipulador de eventos. Você pode reativar o botão de dentro um  `Finally` Bloquear quando a operação é concluída para que os usuários podem executar o aplicativo novamente.  
  
 O código a seguir mostra essas alterações, que são marcadas com asteriscos. Você pode adicionar as alterações ao código no final deste tópico, ou você pode baixar o aplicativo concluído de [Async exemplos: reentrada em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571). O nome do projeto é DisableStartButton.  
  
```vb  
  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 Como resultado das alterações, o botão não responde enquanto `AccessTheWebAsync` está baixando os sites da Web, para que o processo não pode ser restabelecido.  
  
###  <a name="BKMK_CancelAndRestart"></a> Cancelar e reiniciar a operação  
 Em vez de desativar o **Iniciar** botão, você pode manter o botão ativa, mas, se o usuário escolher o botão novamente, cancele a operação que já está em execução e permitir que a operação iniciada mais recentemente continuar.  
  
 Para obter mais informações sobre cancelamento, consulte [Ajustando seu aplicativo Async \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).  
  
 Para configurar esse cenário, faça as seguintes alterações para o código básico que é fornecido no [Reviewing and Running the Example App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMD_SettingUpTheExample). Você também pode baixar o aplicativo concluído de [Async exemplos: reentrada em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571). O nome do projeto é CancelAndRestart.  
  
1.  Declarar uma <xref:System.Threading.CancellationTokenSource> variável, `cts`, que está no escopo para todos os métodos.  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
  
    ```  
  
2.  Em `StartButton_Click`, determinar se uma operação já está em andamento. Se o valor de `cts` é `Nothing`, nenhuma operação já está ativa. Se o valor não for `Nothing`, a operação já está em execução foi cancelada.  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ```  
  
3.  Definir `cts` para um valor diferente que representa o processo atual.  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    ```  
  
4.  No final da `StartButton_Click`, o processo atual for concluído, então, defina o valor de `cts` para `Nothing`.  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
  
    ```  
  
 O código a seguir mostra todas as alterações na `StartButton_Click`. As adições são marcadas com asteriscos.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
  
```  
  
 Em `AccessTheWebAsync`, faça as seguintes alterações.  
  
-   Adicionar um parâmetro para aceitar o token de cancelamento de `StartButton_Click`.  
  
-   Use o <xref:System.Net.Http.HttpClient.GetAsync%2A> método para baixar os sites porque `GetAsync` aceita um <xref:System.Threading.CancellationToken> argumento.  
  
-   Antes de chamar `DisplayResults` para exibir os resultados para cada site baixado, verifique `ct` para verificar que a operação atual não foi cancelada.  
  
 O código a seguir mostra essas alterações, que são marcadas com asteriscos.  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
  
```  
  
 Se você escolher o **Iniciar** botão várias vezes enquanto este aplicativo é executado, ele deve produzir resultados semelhantes a saída a seguir.  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 Para eliminar as listas parciais, remova a primeira linha do código em `StartButton_Click` desmarcar a caixa de texto sempre que o usuário reinicia a operação.  
  
###  <a name="BKMK_RunMultipleOperations"></a> Executar várias operações e a fila de saída  
 Este exemplo terceiro é mais complicado que o aplicativo inicia outra operação assíncrona cada vez que o usuário escolhe o **Iniciar** botão e todas as operações executadas até a conclusão. Todas as operações solicitadas baixar sites da lista de forma assíncrona, mas a saída das operações é apresentada em sequência. Ou seja, a atividade de download real é intercalada, como a saída [Recognizing Reentrancy](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_RecognizingReentrancy) mostra, mas a lista de resultados para cada grupo é apresentado separadamente.  
  
 As operações de compartilham um global <xref:System.Threading.Tasks.Task>, `pendingWork`, que serve como um gatekeeper para o processo de exibição.  
  
 Você pode executar esse exemplo, colando as alterações no código no [Building the App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_BuildingTheApp), ou você pode seguir as instruções em [Downloading the App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_DownloadingTheApp) para baixar o exemplo e execute o projeto QueueResults.  
  
 A saída a seguir mostra o resultado se o usuário escolhe o **Iniciar** botão apenas uma vez. O rótulo de letra A, indica que o resultado é a primeira vez o **Iniciar** botão for escolhido. Os números mostram a ordem das URLs na lista de destinos de download.  
  
```  
  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 Se o usuário escolhe o **Iniciar** botão três vezes, o aplicativo produz uma saída semelhante das linhas a seguir. Inscreva\-as linhas de informações que começam com um sustenido \(\#\) rastrear o progresso do aplicativo.  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
  
```  
  
 Grupos de B e C iniciado antes de um grupo é concluída, mas a saída para cada grupo será exibido separadamente. Toda a saída para um grupo aparece primeira, seguido por toda a saída para o grupo B e, em seguida, toda a saída para o grupo C. O aplicativo sempre exibe os grupos em ordem e, para cada grupo, sempre exibe as informações sobre os sites individuais na ordem em que as URLs aparecem na lista de URLs.  
  
 No entanto, é possível prever a ordem na qual os downloads realmente acontecem. Depois que tiverem sido iniciados vários grupos, as tarefas de download que elas geram estão todos ativas. Você não pode presumir que\-1 será baixado antes de B\-1, e você não pode presumir que\-1 será baixado antes de A\-2.  
  
#### Definições globais  
 O código de exemplo contém as seguintes declarações globais dois que são visíveis a partir de todos os métodos.  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 O `Task` variável, `pendingWork`, supervisiona o processo de exibição e impede que qualquer grupo de interromper a operação de exibição do outro grupo. A variável de caractere, `group`, rótulos a saída de grupos diferentes para verificar se os resultados aparecem na ordem esperada.  
  
#### O manipulador de eventos de clique  
 O manipulador de eventos, `StartButton_Click`, a letra de grupo é incrementado toda vez que o usuário escolhe o **Iniciar** botão. Em seguida, chama o manipulador `AccessTheWebAsync` para executar a operação de download.  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### O método AccessTheWebAsync  
 Este exemplo divide `AccessTheWebAsync` em dois métodos. O primeiro método, `AccessTheWebAsync`, inicia todas as tarefas de download de um grupo e configura `pendingWork` para controlar o processo de exibição. O método usa uma consulta integrada à linguagem \(consulta LINQ\) e <xref:System.Linq.Enumerable.ToArray%2A> para iniciar todas as tarefas de download ao mesmo tempo.  
  
 `AccessTheWebAsync` em seguida, chama `FinishOneGroupAsync` para esperar pela conclusão de cada download e exibir seu comprimento.  
  
 `FinishOneGroupAsync` Retorna uma tarefa que é atribuída a `pendingWork` em `AccessTheWebAsync`. Que valor impede a interrupção por outra operação antes que a tarefa seja concluída.  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### O método FinishOneGroupAsync  
 Esse método percorre as tarefas de download em um grupo, aguardando a cada uma delas, exibindo o comprimento do site baixado e adicionando o comprimento para o total.  
  
 A primeira instrução em `FinishOneGroupAsync` usa `pendingWork` para certificar\-se de que inserindo o método não interfere com uma operação que já está no processo de exibição ou que já está aguardando. Se essa operação está em andamento, a operação de inserção deve esperar sua vez.  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 Você pode executar esse exemplo, colando as alterações no código no [Building the App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_BuildingTheApp), ou você pode seguir as instruções em [Downloading the App](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_DownloadingTheApp) para baixar o exemplo e execute o projeto QueueResults.  
  
#### Pontos de interesse  
 As linhas de informações que começam com um sinal de libra \(\#\) na saída esclarecem como este exemplo funciona.  
  
 A saída mostra os padrões a seguir.  
  
-   Um grupo pode ser iniciado enquanto um grupo anterior está exibindo a saída, mas a exibição da saída do grupo anterior não é interrompida.  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   O `pendingWork` tarefa é `Nothing` no início de `FinishOneGroupAsync` apenas para um grupo, que foi iniciado primeiro. Um grupo ainda não tiver concluído uma expressão await quando ele atinge `FinishOneGroupAsync`. Portanto, o controle não foi retornado ao `AccessTheWebAsync`, e a primeira atribuição para `pendingWork` não ocorreu.  
  
-   As duas linhas a seguir sempre aparecem juntos na saída. O código nunca é interrompido entre iniciando a operação de um grupo `StartButton_Click` e a atribuição de uma tarefa para o grupo de `pendingWork`.  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     Depois de insere um grupo `StartButton_Click`, a operação não conclui uma expressão await, até que a operação entre `FinishOneGroupAsync`. Portanto, nenhuma outra operação pode obter controle durante esse segmento de código.  
  
##  <a name="BKMD_SettingUpTheExample"></a> Examinar e executar o aplicativo de exemplo  
 Para entender melhor o aplicativo de exemplo, você pode baixá\-lo, compilá\-lo ou examinar o código no final deste tópico sem implementar o aplicativo.  
  
> [!NOTE]
>  Para executar o exemplo como um aplicativo de desktop do Windows Presentation Foundation \(WPF\), você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.  
  
###  <a name="BKMK_DownloadingTheApp"></a> Baixar o aplicativo  
  
1.  Baixe o arquivo compactado em [Async exemplos: reentrada em aplicativos de área de trabalho do .NET](http://go.microsoft.com/fwlink/?LinkId=266571).  
  
2.  Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.  
  
3.  Na barra de menus, escolha **arquivo**, **Abrir**, **projeto\/solução**.  
  
4.  Navegue até a pasta que contém o código de exemplo descompactado e, em seguida, abra o arquivo de solução \(. sln\).  
  
5.  Em **Solution Explorer**, abra o menu de atalho para o projeto que você deseja executar e, em seguida, escolha **definida como StartUpProject**.  
  
6.  Escolha as teclas CTRL \+ F5 para compilar e executar o projeto.  
  
###  <a name="BKMK_BuildingTheApp"></a> Criando o aplicativo  
 A seção a seguir fornece o código para criar o exemplo como um aplicativo WPF.  
  
##### Para criar um aplicativo WPF  
  
1.  Inicie o Visual Studio.  
  
2.  Na barra de menus, escolha **arquivo**, **novo**, **projeto**.  
  
     O **novo projeto** caixa de diálogo é aberta.  
  
3.  No **modelos instalados** painel, expanda **Visual Basic**, e, em seguida, expanda **Windows**.  
  
4.  Na lista de tipos de projeto, escolha **aplicativo WPF**.  
  
5.  Nomeie o projeto `WebsiteDownloadWPF`, e, em seguida, escolha o **OK** botão.  
  
     O novo projeto aparece na **Solution Explorer**.  
  
6.  No código de Editor do Visual Studio, escolha o **MainWindow** guia.  
  
     Se a guia não estiver visível, abra o menu de atalho de MainWindow. XAML no **Solution Explorer**, e, em seguida, escolha **Exibir código**.  
  
7.  No **XAML** exibir de MainWindow. XAML, substitua o código pelo código a seguir.  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     Uma janela simple que contém uma caixa de texto e um botão aparece no **Design** exibição de MainWindow. XAML.  
  
8.  Adicione uma referência para <xref:System.Net.Http>.  
  
9. Em **Solution Explorer**, abra o menu de atalho para MainWindow.xaml.vb e, em seguida, escolha **Exibir código**.  
  
10. Em MainWindow.xaml.vb, substitua o código com o código a seguir.  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/en-us/library/hh191443.aspx",  
                "http://msdn.microsoft.com/en-us/library/aa578028.aspx",  
                "http://msdn.microsoft.com/en-us/library/jj155761.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh290140.aspx",  
                "http://msdn.microsoft.com/en-us/library/hh524395.aspx",  
                "http://msdn.microsoft.com/en-us/library/ms404677.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/en-us/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("http://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. Escolha as teclas CTRL \+ F5 para executar o programa e, em seguida, escolha o **Iniciar** botão várias vezes.  
  
12. Faça as alterações de [Disable the Start Button](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_CancelAndRestart), ou [Run Multiple Operations and Queue the Output](../Topic/Handling%20Reentrancy%20in%20Async%20Apps%20\(C%23%20and%20Visual%20Basic\).md#BKMK_RunMultipleOperations) para lidar com a reentrância.  
  
## Consulte também  
 [Passo a passo: Acessando a Web usando o Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Programação assíncrona com Async e Await \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/async/asynchronous-programming-with-async-and-await.md)