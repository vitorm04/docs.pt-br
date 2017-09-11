---
title: "Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe2df73aaf49f1b61dafcad9a6c6e0f3d014f8ec
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="81ead-102">Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81ead-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="81ead-103">Você pode configurar um botão que você pode usar para cancelar um aplicativo assíncrono, se não desejar aguardar sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="81ead-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="81ead-104">Seguindo os exemplos neste tópico, você pode adicionar um botão de cancelamento para um aplicativo que baixa o conteúdo de um site ou uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="81ead-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="81ead-105">Os exemplos usam a interface do usuário que [ajuste seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) descreve.</span><span class="sxs-lookup"><span data-stu-id="81ead-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81ead-106">Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="81ead-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="81ead-107"><a name="BKMK_CancelaTask"></a>Cancelar uma tarefa</span><span class="sxs-lookup"><span data-stu-id="81ead-107"><a name="BKMK_CancelaTask"></a> Cancel a Task</span></span>  
 <span data-ttu-id="81ead-108">O primeiro exemplo associa o **Cancelar** botão com uma tarefa único download.</span><span class="sxs-lookup"><span data-stu-id="81ead-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="81ead-109">Se você escolher o botão enquanto o aplicativo é baixar o conteúdo, o download será cancelado.</span><span class="sxs-lookup"><span data-stu-id="81ead-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="81ead-110">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="81ead-110">Downloading the Example</span></span>  
 <span data-ttu-id="81ead-111">Você pode baixar o projeto completo do Windows Presentation Foundation (WPF) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="81ead-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="81ead-112">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81ead-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="81ead-113">Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="81ead-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="81ead-114">No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução (. sln) para AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="81ead-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="81ead-115">Em **Solution Explorer**, abra o menu de atalho para o **CancelATask** do projeto e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="81ead-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="81ead-116">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="81ead-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="81ead-117">Escolha as teclas Ctrl + F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="81ead-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="81ead-118">Se você não quiser baixar o projeto, você pode examinar os arquivos de MainWindow.xaml.vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="81ead-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="81ead-119">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="81ead-119">Building the Example</span></span>  
 <span data-ttu-id="81ead-120">Adicione as seguintes alterações um **Cancelar** botão a um aplicativo que faz o download de um site.</span><span class="sxs-lookup"><span data-stu-id="81ead-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="81ead-121">Se você não deseja baixar ou criar o exemplo, você pode examinar o produto final na seção "Exemplos concluída" no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="81ead-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="81ead-122">Asteriscos marcam as alterações no código.</span><span class="sxs-lookup"><span data-stu-id="81ead-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="81ead-123">Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **StarterCode** como o **projeto de inicialização** em vez de **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="81ead-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="81ead-124">Em seguida, adicione as seguintes alterações no arquivo MainWindow.xaml.vb do projeto.</span><span class="sxs-lookup"><span data-stu-id="81ead-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="81ead-125">Declarar uma `CancellationTokenSource` variável, `cts`, que está no escopo para todos os métodos para acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="81ead-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="81ead-126">Adicione o seguinte manipulador de eventos para o **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="81ead-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="81ead-127">O manipulador de eventos usa o <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>método notificar `cts` quando o usuário solicitar cancelamento.</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81ead-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="81ead-128">Faça as seguintes alterações no evento de manipulador para o **iniciar** botão, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="81ead-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="81ead-129">Criar uma instância de `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="81ead-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="81ead-130">Na chamada para `AccessTheWebAsync`, que baixa o conteúdo de um site específico, enviar o <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName>propriedade `cts` como um argumento.</xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81ead-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> property of `cts` as an argument.</span></span> <span data-ttu-id="81ead-131">O `Token` propriedade propaga a mensagem se o cancelamento foi solicitado.</span><span class="sxs-lookup"><span data-stu-id="81ead-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="81ead-132">Adicione um bloco catch que exibe uma mensagem se o usuário optar por cancelar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="81ead-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="81ead-133">O código a seguir mostra as alterações.</span><span class="sxs-lookup"><span data-stu-id="81ead-133">The following code shows the changes.</span></span>  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  <span data-ttu-id="81ead-134">Em `AccessTheWebAsync`, use o <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName>sobrecarga do `GetAsync` método o <xref:System.Net.Http.HttpClient>tipo para baixar o conteúdo de um site.</xref:System.Net.Http.HttpClient> </xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="81ead-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="81ead-135">Passar `ct`, o <xref:System.Threading.CancellationToken>parâmetro de `AccessTheWebAsync`, como o segundo argumento.</xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="81ead-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="81ead-136">O token executa a mensagem se o usuário escolhe o **Cancelar** botão.</span><span class="sxs-lookup"><span data-stu-id="81ead-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="81ead-137">O código a seguir mostra as alterações na `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="81ead-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="81ead-138">Se você não cancelar o programa, ele produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="81ead-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="81ead-139">Se você escolher o **Cancelar** botão antes do programa termina de baixar o conteúdo, o programa produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="81ead-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <span data-ttu-id="81ead-140"><a name="BKMK_CancelaListofTasks"></a>Cancelar uma lista de tarefas</span><span class="sxs-lookup"><span data-stu-id="81ead-140"><a name="BKMK_CancelaListofTasks"></a> Cancel a List of Tasks</span></span>  
 <span data-ttu-id="81ead-141">Você pode estender o exemplo anterior para cancelar muitas tarefas, associando a mesma `CancellationTokenSource` instância com cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="81ead-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="81ead-142">Se você escolher o **Cancelar** botão Cancelar todas as tarefas que ainda não concluídas.</span><span class="sxs-lookup"><span data-stu-id="81ead-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="81ead-143">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="81ead-143">Downloading the Example</span></span>  
 <span data-ttu-id="81ead-144">Você pode baixar o projeto completo do Windows Presentation Foundation (WPF) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="81ead-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="81ead-145">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="81ead-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="81ead-146">Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="81ead-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="81ead-147">No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução (. sln) para AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="81ead-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="81ead-148">Em **Solution Explorer**, abra o menu de atalho para o **CancelAListOfTasks** do projeto e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="81ead-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="81ead-149">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="81ead-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="81ead-150">Escolha as teclas Ctrl + F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="81ead-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="81ead-151">Se você não quiser baixar o projeto, você pode examinar os arquivos de MainWindow.xaml.vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="81ead-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="81ead-152">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="81ead-152">Building the Example</span></span>  
 <span data-ttu-id="81ead-153">Para estender o exemplo por conta própria, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelATask** como o **projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="81ead-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="81ead-154">Adicione as seguintes alterações para o projeto.</span><span class="sxs-lookup"><span data-stu-id="81ead-154">Add the following changes to that project.</span></span> <span data-ttu-id="81ead-155">Asteriscos marcam as alterações no programa.</span><span class="sxs-lookup"><span data-stu-id="81ead-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="81ead-156">Adicione um método para criar uma lista de endereços da web.</span><span class="sxs-lookup"><span data-stu-id="81ead-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
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
    ```  
  
2.  <span data-ttu-id="81ead-157">Chame o método em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="81ead-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="81ead-158">Adicione o seguinte loop em `AccessTheWebAsync` para processar cada endereço da web na lista.</span><span class="sxs-lookup"><span data-stu-id="81ead-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  <span data-ttu-id="81ead-159">Porque `AccessTheWebAsync` exibe os comprimentos, o método não precisa retornar nada.</span><span class="sxs-lookup"><span data-stu-id="81ead-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="81ead-160">Remova a instrução de retornada e altere o tipo de retorno do método para <xref:System.Threading.Tasks.Task>em vez de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="81ead-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
<span data-ttu-id="81ead-161"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="81ead-161"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="81ead-162">Chame o método de `startButton_Click` usando uma instrução, em vez de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="81ead-162">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="81ead-163">Se você não cancelar o programa, ele produz a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="81ead-163">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
  
    ```  
  
     <span data-ttu-id="81ead-164">Se você escolher o **Cancelar** botão antes dos downloads forem concluídos, a saída contém os comprimentos dos downloads concluído antes do cancelamento.</span><span class="sxs-lookup"><span data-stu-id="81ead-164">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
  
    ```  
  
##  <span data-ttu-id="81ead-165"><a name="BKMK_CompleteExamples"></a>Exemplos de conclusão</span><span class="sxs-lookup"><span data-stu-id="81ead-165"><a name="BKMK_CompleteExamples"></a> Complete Examples</span></span>  
 <span data-ttu-id="81ead-166">As seções a seguir contêm o código para cada um dos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="81ead-166">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="81ead-167">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="81ead-167">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="81ead-168">Você pode baixar os projetos de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="81ead-168">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="81ead-169">Cancelar um exemplo de tarefa</span><span class="sxs-lookup"><span data-stu-id="81ead-169">Cancel a Task Example</span></span>  
 <span data-ttu-id="81ead-170">O código a seguir é o arquivo MainWindow.xaml.vb completo para o exemplo que cancela uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="81ead-170">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="81ead-171">Cancelar uma lista de tarefas de exemplo</span><span class="sxs-lookup"><span data-stu-id="81ead-171">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="81ead-172">O código a seguir é o arquivo MainWindow.xaml.vb completo para o exemplo que cancela uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="81ead-172">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
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
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="81ead-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="81ead-173">See Also</span></span>  
 <span data-ttu-id="81ead-174"><xref:System.Threading.CancellationTokenSource></xref:System.Threading.CancellationTokenSource></span><span class="sxs-lookup"><span data-stu-id="81ead-174"><xref:System.Threading.CancellationTokenSource></span></span>   
 <span data-ttu-id="81ead-175"><xref:System.Threading.CancellationToken></xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="81ead-175"><xref:System.Threading.CancellationToken></span></span>   
<span data-ttu-id="81ead-176"> [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="81ead-176"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="81ead-177"> [Ajustando seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="81ead-177"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="81ead-178"> [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="81ead-178"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
