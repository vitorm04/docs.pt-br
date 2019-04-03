---
title: Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)
ms.date: 07/20/2015
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
ms.openlocfilehash: deb469f2c083870fc96c9217fa862d189629df1f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834979"
---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="cb18e-102">Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb18e-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="cb18e-103">Você pode configurar um botão que pode ser usado para cancelar um aplicativo assíncrono se não desejar aguardar sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="cb18e-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="cb18e-104">Seguindo os exemplos neste tópico, você pode adicionar um botão de cancelamento a um aplicativo que baixa o conteúdo de um site ou uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="cb18e-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="cb18e-105">Os exemplos usam a interface do usuário que [ajuste fino de seu aplicativo assíncrono (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) descreve.</span><span class="sxs-lookup"><span data-stu-id="cb18e-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cb18e-106">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="cb18e-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="BKMK_CancelaTask"></a> <span data-ttu-id="cb18e-107">Cancelar uma tarefa</span><span class="sxs-lookup"><span data-stu-id="cb18e-107">Cancel a Task</span></span>  
 <span data-ttu-id="cb18e-108">O primeiro exemplo associa o botão **Cancelar** a uma única tarefa de download.</span><span class="sxs-lookup"><span data-stu-id="cb18e-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="cb18e-109">Se você escolher o botão enquanto o aplicativo está baixando conteúdo, o download será cancelado.</span><span class="sxs-lookup"><span data-stu-id="cb18e-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="cb18e-110">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb18e-110">Downloading the Example</span></span>  
 <span data-ttu-id="cb18e-111">Baixe o projeto completo do WPF (Windows Presentation Foundation) em [Amostra assíncrona: Ajustando o aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="cb18e-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="cb18e-112">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb18e-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cb18e-113">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="cb18e-114">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="cb18e-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="cb18e-115">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelATask** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="cb18e-116">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="cb18e-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="cb18e-117">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="cb18e-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="cb18e-118">Se você não quiser baixar o projeto, você pode examinar os arquivos. XAML. vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cb18e-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="cb18e-119">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb18e-119">Building the Example</span></span>  
 <span data-ttu-id="cb18e-120">As alterações a seguir adicionam um botão **Cancelar** a um aplicativo que baixa um site.</span><span class="sxs-lookup"><span data-stu-id="cb18e-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="cb18e-121">Se não desejar baixar ou compilar o exemplo, você poderá examinar o produto final na seção "Exemplos completos" no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cb18e-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="cb18e-122">Os asteriscos marcam as alterações no código.</span><span class="sxs-lookup"><span data-stu-id="cb18e-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="cb18e-123">Para compilar o exemplo você mesmo, passo a passo, siga as instruções na seção “Baixando o exemplo”, mas escolha **StarterCode** como o **Projeto de Inicialização** em vez de **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="cb18e-124">Em seguida, adicione as seguintes alterações para o arquivo. XAML. vb desse projeto.</span><span class="sxs-lookup"><span data-stu-id="cb18e-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="cb18e-125">Declare uma variável `CancellationTokenSource`, `cts`, que está no escopo para todos os métodos a acessarem.</span><span class="sxs-lookup"><span data-stu-id="cb18e-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="cb18e-126">Adicione o seguinte manipulador de eventos para o botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="cb18e-127">O manipulador de eventos usa o método <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> para notificar `cts` quando o usuário solicita o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="cb18e-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="cb18e-128">Faça as seguintes alterações no manipulador de eventos para o botão **Iniciar**, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="cb18e-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="cb18e-129">Crie a instância de `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="cb18e-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="cb18e-130">Na chamada para `AccessTheWebAsync`, que baixa o conteúdo de um site especificado, envie a propriedade <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> de `cts` como um argumento.</span><span class="sxs-lookup"><span data-stu-id="cb18e-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=nameWithType> property of `cts` as an argument.</span></span> <span data-ttu-id="cb18e-131">A propriedade `Token` propaga a mensagem se o cancelamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="cb18e-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="cb18e-132">Adicione um bloco catch que exibe uma mensagem se o usuário optar por cancelar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="cb18e-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="cb18e-133">O código a seguir mostra as alterações.</span><span class="sxs-lookup"><span data-stu-id="cb18e-133">The following code shows the changes.</span></span>  
  
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
  
4.  <span data-ttu-id="cb18e-134">No `AccessTheWebAsync`, use a sobrecarga <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> do método `GetAsync` no tipo <xref:System.Net.Http.HttpClient> para baixar o conteúdo de um site.</span><span class="sxs-lookup"><span data-stu-id="cb18e-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=nameWithType> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="cb18e-135">Passe `ct`, o parâmetro <xref:System.Threading.CancellationToken> de `AccessTheWebAsync`, como o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="cb18e-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="cb18e-136">O token executa a mensagem se o usuário escolhe o botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="cb18e-137">O código a seguir mostra as alterações em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="cb18e-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
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
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="cb18e-138">Se você não cancelar o programa, ele produzirá a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb18e-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="cb18e-139">Se você escolher o botão **Cancelar** antes de o programa terminar de baixar o conteúdo, o programa produzirá a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb18e-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
## <a name="BKMK_CancelaListofTasks"></a> <span data-ttu-id="cb18e-140">Cancelar uma lista de tarefas</span><span class="sxs-lookup"><span data-stu-id="cb18e-140">Cancel a List of Tasks</span></span>  
 <span data-ttu-id="cb18e-141">Você pode estender o exemplo anterior para cancelar muitas tarefas associando a mesma instância `CancellationTokenSource` a cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="cb18e-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="cb18e-142">Se você escolher o botão **Cancelar**, cancela todas as tarefas que ainda não estão concluídas.</span><span class="sxs-lookup"><span data-stu-id="cb18e-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="cb18e-143">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb18e-143">Downloading the Example</span></span>  
 <span data-ttu-id="cb18e-144">Baixe o projeto completo do WPF (Windows Presentation Foundation) em [Amostra assíncrona: Ajustando o aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="cb18e-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="cb18e-145">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cb18e-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cb18e-146">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="cb18e-147">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="cb18e-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="cb18e-148">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelAListOfTasks** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="cb18e-149">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="cb18e-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="cb18e-150">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="cb18e-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="cb18e-151">Se você não quiser baixar o projeto, você pode examinar os arquivos. XAML. vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cb18e-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="cb18e-152">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb18e-152">Building the Example</span></span>  
 <span data-ttu-id="cb18e-153">Para estender o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixando o exemplo", mas escolha **CancelATask** como o **Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="cb18e-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="cb18e-154">Adicione as seguintes alterações ao projeto.</span><span class="sxs-lookup"><span data-stu-id="cb18e-154">Add the following changes to that project.</span></span> <span data-ttu-id="cb18e-155">Os asteriscos marcam as alterações no programa.</span><span class="sxs-lookup"><span data-stu-id="cb18e-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="cb18e-156">Adicione um método para criar uma lista de endereços Web.</span><span class="sxs-lookup"><span data-stu-id="cb18e-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
    ```  
  
2.  <span data-ttu-id="cb18e-157">Chame o método em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="cb18e-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="cb18e-158">Adicione o seguinte loop em `AccessTheWebAsync` para processar cada endereço web na lista.</span><span class="sxs-lookup"><span data-stu-id="cb18e-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
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
  
4.  <span data-ttu-id="cb18e-159">Como `AccessTheWebAsync` exibe os comprimentos, o método não precisa retornar nada.</span><span class="sxs-lookup"><span data-stu-id="cb18e-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="cb18e-160">Remova a instrução de retorno e altere o tipo de retorno do método para <xref:System.Threading.Tasks.Task> em vez de <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="cb18e-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```vb  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
    ```  
  
     <span data-ttu-id="cb18e-161">Chame o método de `startButton_Click` usando uma instrução em vez de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="cb18e-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="cb18e-162">Se você não cancelar o programa, ele produzirá a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="cb18e-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
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
  
     <span data-ttu-id="cb18e-163">Se você escolher o botão **Cancelar** antes de os downloads serem concluídos, a saída conterá os tamanhos dos downloads que foram concluídos antes do cancelamento.</span><span class="sxs-lookup"><span data-stu-id="cb18e-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
## <a name="BKMK_CompleteExamples"></a> <span data-ttu-id="cb18e-164">Exemplos completos</span><span class="sxs-lookup"><span data-stu-id="cb18e-164">Complete Examples</span></span>  
 <span data-ttu-id="cb18e-165">As seções a seguir contêm o código para cada um dos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="cb18e-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="cb18e-166">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="cb18e-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="cb18e-167">Você pode baixar os projetos de [exemplo assíncrono: Ajustando o aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="cb18e-167">You can download the projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="cb18e-168">Exemplo de cancelar uma tarefa</span><span class="sxs-lookup"><span data-stu-id="cb18e-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="cb18e-169">O código a seguir é o arquivo. XAML. vb completo para um exemplo que cancela uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="cb18e-169">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
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
        Dim response As HttpResponseMessage = Await client.GetAsync("https://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
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
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="cb18e-170">Exemplo de cancelar uma lista de tarefas</span><span class="sxs-lookup"><span data-stu-id="cb18e-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="cb18e-171">O código a seguir é o arquivo. XAML. vb completo para um exemplo que cancela uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cb18e-171">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
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
  
## <a name="see-also"></a><span data-ttu-id="cb18e-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb18e-172">See also</span></span>

- <xref:System.Threading.CancellationTokenSource>
- <xref:System.Threading.CancellationToken>
- [<span data-ttu-id="cb18e-173">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb18e-173">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="cb18e-174">Ajustando seu aplicativo assíncrono (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cb18e-174">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="cb18e-175">Exemplo de Async: ajuste do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="cb18e-175">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
