---
title: "Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2e34344c9cdf0717291c4c7375bab703679515a7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="cancel-an-async-task-or-a-list-of-tasks-c"></a><span data-ttu-id="4aec3-102">Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)</span><span class="sxs-lookup"><span data-stu-id="4aec3-102">Cancel an Async Task or a List of Tasks (C#)</span></span>
<span data-ttu-id="4aec3-103">Você pode configurar um botão que pode ser usado para cancelar um aplicativo assíncrono se não desejar aguardar sua conclusão.</span><span class="sxs-lookup"><span data-stu-id="4aec3-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="4aec3-104">Seguindo os exemplos neste tópico, você pode adicionar um botão de cancelamento a um aplicativo que baixa o conteúdo de um site ou uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="4aec3-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="4aec3-105">Os exemplos usam a interface do usuário que [Ajuste fino de seu aplicativo assíncrono (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) descreve.</span><span class="sxs-lookup"><span data-stu-id="4aec3-105">The examples use the UI that [Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4aec3-106">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="4aec3-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="4aec3-107"><a name="BKMK_CancelaTask"></a> Cancelar uma tarefa</span><span class="sxs-lookup"><span data-stu-id="4aec3-107"><a name="BKMK_CancelaTask"></a> Cancel a Task</span></span>  
 <span data-ttu-id="4aec3-108">O primeiro exemplo associa o botão **Cancelar** a uma única tarefa de download.</span><span class="sxs-lookup"><span data-stu-id="4aec3-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="4aec3-109">Se você escolher o botão enquanto o aplicativo está baixando conteúdo, o download será cancelado.</span><span class="sxs-lookup"><span data-stu-id="4aec3-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="4aec3-110">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="4aec3-110">Downloading the Example</span></span>  
 <span data-ttu-id="4aec3-111">Você pode baixar o projeto completo do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, seguir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="4aec3-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="4aec3-112">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4aec3-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4aec3-113">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="4aec3-114">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="4aec3-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="4aec3-115">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelATask** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="4aec3-116">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="4aec3-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="4aec3-117">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="4aec3-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="4aec3-118">Se você não quiser baixar o projeto, você poderá examinar o arquivo MainWindow.xaml.cs no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4aec3-118">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="4aec3-119">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="4aec3-119">Building the Example</span></span>  
 <span data-ttu-id="4aec3-120">As alterações a seguir adicionam um botão **Cancelar** a um aplicativo que baixa um site.</span><span class="sxs-lookup"><span data-stu-id="4aec3-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="4aec3-121">Se não desejar baixar ou compilar o exemplo, você poderá examinar o produto final na seção "Exemplos completos" no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4aec3-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="4aec3-122">Os asteriscos marcam as alterações no código.</span><span class="sxs-lookup"><span data-stu-id="4aec3-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="4aec3-123">Para compilar o exemplo você mesmo, passo a passo, siga as instruções na seção “Baixando o exemplo”, mas escolha **StarterCode** como o **Projeto de Inicialização** em vez de **CancelATask**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="4aec3-124">Em seguida, adicione as seguintes alterações ao arquivo MainWindow.xaml.cs desse projeto.</span><span class="sxs-lookup"><span data-stu-id="4aec3-124">Then add the following changes to the MainWindow.xaml.cs file of that project.</span></span>  
  
1.  <span data-ttu-id="4aec3-125">Declare uma variável `CancellationTokenSource`, `cts`, que está no escopo para todos os métodos a acessarem.</span><span class="sxs-lookup"><span data-stu-id="4aec3-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```csharp  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
    ```  
  
2.  <span data-ttu-id="4aec3-126">Adicione o seguinte manipulador de eventos para o botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="4aec3-127">O manipulador de eventos usa o método <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> para notificar `cts` quando o usuário solicita o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4aec3-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```csharp  
    // ***Add an event handler for the Cancel button.  
    private void cancelButton_Click(object sender, RoutedEventArgs e)  
    {  
        if (cts != null)  
        {  
            cts.Cancel();  
        }  
    }  
    ```  
  
3.  <span data-ttu-id="4aec3-128">Faça as seguintes alterações no manipulador de eventos para o botão **Iniciar**, `startButton_Click`.</span><span class="sxs-lookup"><span data-stu-id="4aec3-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="4aec3-129">Crie a instância de `CancellationTokenSource`, `cts`.</span><span class="sxs-lookup"><span data-stu-id="4aec3-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```csharp  
        // ***Instantiate the CancellationTokenSource.  
        cts = new CancellationTokenSource();  
        ```  
  
    -   <span data-ttu-id="4aec3-130">Na chamada para `AccessTheWebAsync`, que baixa o conteúdo de um site especificado, envie a propriedade <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> de `cts` como um argumento.</span><span class="sxs-lookup"><span data-stu-id="4aec3-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> property of `cts` as an argument.</span></span> <span data-ttu-id="4aec3-131">A propriedade `Token` propaga a mensagem se o cancelamento é solicitado.</span><span class="sxs-lookup"><span data-stu-id="4aec3-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="4aec3-132">Adicione um bloco catch que exibe uma mensagem se o usuário optar por cancelar a operação de download.</span><span class="sxs-lookup"><span data-stu-id="4aec3-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="4aec3-133">O código a seguir mostra as alterações.</span><span class="sxs-lookup"><span data-stu-id="4aec3-133">The following code shows the changes.</span></span>  
  
        ```csharp  
        try  
        {  
            // ***Send a token to carry the message if cancellation is requested.  
            int contentLength = await AccessTheWebAsync(cts.Token);  
            resultsTextBox.Text +=  
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
        // *** If cancellation is requested, an OperationCanceledException results.  
        catch (OperationCanceledException)  
        {  
            resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
        }  
        catch (Exception)  
        {  
            resultsTextBox.Text += "\r\nDownload failed.\r\n";  
        }  
        ```  
  
4.  <span data-ttu-id="4aec3-134">No `AccessTheWebAsync`, use a sobrecarga <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> do método `GetAsync` no tipo <xref:System.Net.Http.HttpClient> para baixar o conteúdo de um site.</span><span class="sxs-lookup"><span data-stu-id="4aec3-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="4aec3-135">Passe `ct`, o parâmetro <xref:System.Threading.CancellationToken> de `AccessTheWebAsync`, como o segundo argumento.</span><span class="sxs-lookup"><span data-stu-id="4aec3-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="4aec3-136">O token executa a mensagem se o usuário escolhe o botão **Cancelar**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="4aec3-137">O código a seguir mostra as alterações em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="4aec3-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Provide a parameter for the CancellationToken.  
    async Task<int> AccessTheWebAsync(CancellationToken ct)  
    {  
        HttpClient client = new HttpClient();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nReady to download.\r\n");  
  
        // You might need to slow things down to have a chance to cancel.  
        await Task.Delay(250);  
  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // ***The ct argument carries the message if the Cancel button is chosen.  
        HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        // The result of the method is the length of the downloaded website.  
        return urlContents.Length;  
    }  
    ```  
  
5.  <span data-ttu-id="4aec3-138">Se você não cancelar o programa, ele produzirá a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="4aec3-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="4aec3-139">Se você escolher o botão **Cancelar** antes de o programa terminar de baixar o conteúdo, o programa produzirá a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="4aec3-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <span data-ttu-id="4aec3-140"><a name="BKMK_CancelaListofTasks"></a> Cancelar uma lista de tarefas</span><span class="sxs-lookup"><span data-stu-id="4aec3-140"><a name="BKMK_CancelaListofTasks"></a> Cancel a List of Tasks</span></span>  
 <span data-ttu-id="4aec3-141">Você pode estender o exemplo anterior para cancelar muitas tarefas associando a mesma instância `CancellationTokenSource` a cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="4aec3-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="4aec3-142">Se você escolher o botão **Cancelar**, cancela todas as tarefas que ainda não estão concluídas.</span><span class="sxs-lookup"><span data-stu-id="4aec3-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="4aec3-143">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="4aec3-143">Downloading the Example</span></span>  
 <span data-ttu-id="4aec3-144">Você pode baixar o projeto completo do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, seguir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="4aec3-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="4aec3-145">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4aec3-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="4aec3-146">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="4aec3-147">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="4aec3-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="4aec3-148">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelAListOfTasks** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="4aec3-149">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="4aec3-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="4aec3-150">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="4aec3-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="4aec3-151">Se você não quiser baixar o projeto, você poderá examinar o arquivo MainWindow.xaml.cs no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="4aec3-151">If you don't want to download the project, you can review the MainWindow.xaml.cs files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="4aec3-152">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="4aec3-152">Building the Example</span></span>  
 <span data-ttu-id="4aec3-153">Para estender o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixando o exemplo", mas escolha **CancelATask** como o **Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="4aec3-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="4aec3-154">Adicione as seguintes alterações ao projeto.</span><span class="sxs-lookup"><span data-stu-id="4aec3-154">Add the following changes to that project.</span></span> <span data-ttu-id="4aec3-155">Os asteriscos marcam as alterações no programa.</span><span class="sxs-lookup"><span data-stu-id="4aec3-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="4aec3-156">Adicione um método para criar uma lista de endereços Web.</span><span class="sxs-lookup"><span data-stu-id="4aec3-156">Add a method to create a list of web addresses.</span></span>  
  
    ```csharp  
    // ***Add a method that creates a list of web addresses.  
    private List<string> SetUpURLList()  
    {  
        List<string> urls = new List<string>   
        {   
            "http://msdn.microsoft.com",  
            "http://msdn.microsoft.com/library/hh290138.aspx",  
            "http://msdn.microsoft.com/library/hh290140.aspx",  
            "http://msdn.microsoft.com/library/dd470362.aspx",  
            "http://msdn.microsoft.com/library/aa578028.aspx",  
            "http://msdn.microsoft.com/library/ms404677.aspx",  
            "http://msdn.microsoft.com/library/ff730837.aspx"  
        };  
        return urls;  
    }  
    ```  
  
2.  <span data-ttu-id="4aec3-157">Chame o método em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="4aec3-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```csharp  
    // ***Call SetUpURLList to make a list of web addresses.  
    List<string> urlList = SetUpURLList();  
    ```  
  
3.  <span data-ttu-id="4aec3-158">Adicione o seguinte loop em `AccessTheWebAsync` para processar cada endereço web na lista.</span><span class="sxs-lookup"><span data-stu-id="4aec3-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```csharp  
    // ***Add a loop to process the list of web addresses.  
    foreach (var url in urlList)  
    {  
        // GetAsync returns a Task<HttpResponseMessage>.   
        // Argument ct carries the message if the Cancel button is chosen.   
        // ***Note that the Cancel button can cancel all remaining downloads.  
        HttpResponseMessage response = await client.GetAsync(url, ct);  
  
        // Retrieve the website contents from the HttpResponseMessage.  
        byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
        resultsTextBox.Text +=  
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
    }  
    ```  
  
4.  <span data-ttu-id="4aec3-159">Como `AccessTheWebAsync` exibe os comprimentos, o método não precisa retornar nada.</span><span class="sxs-lookup"><span data-stu-id="4aec3-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="4aec3-160">Remova a instrução de retorno e altere o tipo de retorno do método para <xref:System.Threading.Tasks.Task> em vez de <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4aec3-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
    ```csharp  
    async Task AccessTheWebAsync(CancellationToken ct)  
    ```  
  
     <span data-ttu-id="4aec3-161">Chame o método de `startButton_Click` usando uma instrução em vez de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="4aec3-161">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```csharp  
    await AccessTheWebAsync(cts.Token);  
    ```  
  
5.  <span data-ttu-id="4aec3-162">Se você não cancelar o programa, ele produzirá a saída a seguir.</span><span class="sxs-lookup"><span data-stu-id="4aec3-162">If you don’t cancel the program, it produces the following output.</span></span>  
  
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
  
     <span data-ttu-id="4aec3-163">Se você escolher o botão **Cancelar** antes de os downloads serem concluídos, a saída conterá os tamanhos dos downloads que foram concluídos antes do cancelamento.</span><span class="sxs-lookup"><span data-stu-id="4aec3-163">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
    ```  
  
##  <span data-ttu-id="4aec3-164"><a name="BKMK_CompleteExamples"></a> Exemplos completos</span><span class="sxs-lookup"><span data-stu-id="4aec3-164"><a name="BKMK_CompleteExamples"></a> Complete Examples</span></span>  
 <span data-ttu-id="4aec3-165">As seções a seguir contêm o código para cada um dos exemplos anteriores.</span><span class="sxs-lookup"><span data-stu-id="4aec3-165">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="4aec3-166">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="4aec3-166">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="4aec3-167">Você pode baixar os projetos de [Exemplo assíncrono: ajuste fino de seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="4aec3-167">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="4aec3-168">Exemplo de cancelar uma tarefa</span><span class="sxs-lookup"><span data-stu-id="4aec3-168">Cancel a Task Example</span></span>  
 <span data-ttu-id="4aec3-169">O código a seguir é o arquivo MainWindow.xaml.cs completo do exemplo que cancela uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="4aec3-169">The following code is the complete MainWindow.xaml.cs file for the example that cancels a single task.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive for System.Threading.  
  
using System.Threading;  
namespace CancelATask  
{  
    public partial class MainWindow : Window  
    {  
        // ***Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // ***Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                // ***Send a token to carry the message if cancellation is requested.  
                int contentLength = await AccessTheWebAsync(cts.Token);  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
            // *** If cancellation is requested, an OperationCanceledException results.  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.\r\n";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.\r\n";  
            }  
  
            // ***Set the CancellationTokenSource to null when the download is complete.  
            cts = null;   
        }  
  
        // ***Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // ***Provide a parameter for the CancellationToken.  
        async Task<int> AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            resultsTextBox.Text +=  
                String.Format("\r\nReady to download.\r\n");  
  
            // You might need to slow things down to have a chance to cancel.  
            await Task.Delay(250);  
  
            // GetAsync returns a Task<HttpResponseMessage>.   
            // ***The ct argument carries the message if the Cancel button is chosen.  
            HttpResponseMessage response = await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            // The result of the method is the length of the downloaded website.  
            return urlContents.Length;  
        }  
    }  
  
    // Output for a successful download:  
  
    // Ready to download.  
  
    // Length of the downloaded string: 158125.  
  
    // Or, if you cancel:  
  
    // Ready to download.  
  
    // Download canceled.  
}  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="4aec3-170">Exemplo de cancelar uma lista de tarefas</span><span class="sxs-lookup"><span data-stu-id="4aec3-170">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="4aec3-171">O código a seguir é o arquivo MainWindow.xaml.cs completo do exemplo que cancela uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="4aec3-171">The following code is the complete MainWindow.xaml.cs file for the example that cancels a list of tasks.</span></span>  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http.  
using System.Net.Http;  
  
// Add the following using directive for System.Threading.  
using System.Threading;  
  
namespace CancelAListOfTasks  
{  
    public partial class MainWindow : Window  
    {  
        // Declare a System.Threading.CancellationTokenSource.  
        CancellationTokenSource cts;  
  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Instantiate the CancellationTokenSource.  
            cts = new CancellationTokenSource();  
  
            resultsTextBox.Clear();  
  
            try  
            {  
                await AccessTheWebAsync(cts.Token);  
                // ***Small change in the display lines.  
                resultsTextBox.Text += "\r\nDownloads complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownloads canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownloads failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // Add an event handler for the Cancel button.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        // ***Change the return type to Task because the method has no return statement.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            // Declare an HttpClient object.  
            HttpClient client = new HttpClient();  
  
            // ***Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Add a loop to process the list of web addresses.  
            foreach (var url in urlList)  
            {  
                // GetAsync returns a Task<HttpResponseMessage>.   
                // Argument ct carries the message if the Cancel button is chosen.   
                // ***Note that the Cancel button can cancel all remaining downloads.  
                HttpResponseMessage response = await client.GetAsync(url, ct);  
  
                // Retrieve the website contents from the HttpResponseMessage.  
                byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", urlContents.Length);  
            }  
        }  
  
        // ***Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
  
    // Output if you do not choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Length of the downloaded string: 158124.  
  
    //Length of the downloaded string: 204890.  
  
    //Length of the downloaded string: 175488.  
  
    //Length of the downloaded string: 145790.  
  
    //Downloads complete.  
  
    // Sample output if you choose to cancel:  
  
    //Length of the downloaded string: 35939.  
  
    //Length of the downloaded string: 237682.  
  
    //Length of the downloaded string: 128607.  
  
    //Downloads canceled.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="4aec3-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4aec3-172">See Also</span></span>  
 <span data-ttu-id="4aec3-173"><xref:System.Threading.CancellationTokenSource></span><span class="sxs-lookup"><span data-stu-id="4aec3-173"><xref:System.Threading.CancellationTokenSource></span></span>   
 <span data-ttu-id="4aec3-174"><xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="4aec3-174"><xref:System.Threading.CancellationToken></span></span>   
 <span data-ttu-id="4aec3-175">[Programação assíncrona com async e await (C#)](../../../../csharp/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="4aec3-175">[Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md) </span></span>  
 <span data-ttu-id="4aec3-176">[Ajuste fino de seu aplicativo assíncrono (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="4aec3-176">[Fine-Tuning Your Async Application (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
 [<span data-ttu-id="4aec3-177">Exemplo assíncrono: ajuste fino de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="4aec3-177">Async Sample: Fine Tuning Your Application</span></span>](http://go.microsoft.com/fwlink/?LinkId=255046)

