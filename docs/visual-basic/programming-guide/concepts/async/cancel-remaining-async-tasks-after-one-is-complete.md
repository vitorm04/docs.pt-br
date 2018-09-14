---
title: Cancelar as demais tarefas assíncronas depois que um é concluída (Visual Basic)
ms.date: 07/20/2015
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
ms.openlocfilehash: 0f241d2769edf3efbba0aca3b19ef35b9cdad601
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45517015"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="55ebb-102">Cancelar as demais tarefas assíncronas depois que um é concluída (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55ebb-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="55ebb-103">Usando o método <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> juntamente com um <xref:System.Threading.CancellationToken>, você pode cancelar todas as tarefas restantes quando uma tarefa é concluída.</span><span class="sxs-lookup"><span data-stu-id="55ebb-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="55ebb-104">O método `WhenAny` leva um argumento que é uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="55ebb-105">O método inicia todas as tarefas e retorna uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="55ebb-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="55ebb-106">A tarefa única será concluída quando qualquer tarefa na coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="55ebb-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="55ebb-107">Este exemplo demonstra como usar um token de cancelamento em conjunto com `WhenAny` para aguardar na primeira tarefa que for finalizada na coleção de tarefas e para cancelar as tarefas restantes.</span><span class="sxs-lookup"><span data-stu-id="55ebb-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="55ebb-108">Cada tarefa baixa o conteúdo de um site.</span><span class="sxs-lookup"><span data-stu-id="55ebb-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="55ebb-109">O exemplo exibe o comprimento do conteúdo do primeiro download que é concluído e cancela os outros downloads.</span><span class="sxs-lookup"><span data-stu-id="55ebb-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55ebb-110">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="55ebb-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="55ebb-111">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="55ebb-111">Downloading the Example</span></span>  
 <span data-ttu-id="55ebb-112">Você pode baixar o projeto completo do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, seguir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="55ebb-113">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55ebb-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="55ebb-114">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="55ebb-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="55ebb-115">No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (. sln) para AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="55ebb-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="55ebb-116">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelAfterOneTask** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="55ebb-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="55ebb-117">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="55ebb-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="55ebb-118">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="55ebb-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="55ebb-119">Execute o programa várias vezes para verificar que diferentes downloads são concluídos em primeiro.</span><span class="sxs-lookup"><span data-stu-id="55ebb-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="55ebb-120">Se você não quiser baixar o projeto, você pode examinar o arquivo. XAML. vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="55ebb-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="55ebb-121">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="55ebb-121">Building the Example</span></span>  
 <span data-ttu-id="55ebb-122">O exemplo neste tópico adiciona ao projeto que é desenvolvido no [cancelar uma tarefa assíncrona ou uma lista de tarefas](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) para cancelar uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="55ebb-123">O exemplo usa a mesma interface do usuário, embora o botão **Cancelar** não seja explicitamente usado.</span><span class="sxs-lookup"><span data-stu-id="55ebb-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="55ebb-124">Para compilar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixando o exemplo", mas escolha **CancelAListOfTasks** como o **Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="55ebb-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="55ebb-125">Adicione as alterações deste tópico ao projeto.</span><span class="sxs-lookup"><span data-stu-id="55ebb-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="55ebb-126">No arquivo. XAML. vb do **CancelAListOfTasks** do projeto, inicie a transição movendo as etapas de processamento para cada site do loop em `AccessTheWebAsync` para o seguinte método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="55ebb-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="55ebb-127">Em `AccessTheWebAsync`, este exemplo usa uma consulta, o método <xref:System.Linq.Enumerable.ToArray%2A> e o método `WhenAny` para criar e iniciar uma matriz de tarefas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="55ebb-128">A aplicação de `WhenAny` à matriz retorna uma única tarefa que, quando colocada em espera, resulta na primeira tarefa a alcançar a conclusão na matriz de tarefas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="55ebb-129">Faça as seguintes alterações em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="55ebb-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="55ebb-130">Os asteriscos marcam as alterações no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="55ebb-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="55ebb-131">Comente ou exclua o loop.</span><span class="sxs-lookup"><span data-stu-id="55ebb-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="55ebb-132">Crie uma consulta que, quando executada, produz uma coleção de tarefas genéricas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="55ebb-133">Cada chamada para `ProcessURLAsync` retorna um <xref:System.Threading.Tasks.Task%601> em que `TResult` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="55ebb-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```vb  
    ' ***Create a query that, when executed, returns a collection of tasks.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client, ct)  
    ```  
  
3.  <span data-ttu-id="55ebb-134">Chame `ToArray` para executar a consulta e iniciar as tarefas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="55ebb-135">A aplicação do método `WhenAny` na próxima etapa executaria a consulta e iniciaria as tarefas sem usar `ToArray`, mas outros métodos podem não fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="55ebb-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="55ebb-136">A prática mais segura é forçar a execução da consulta explicitamente.</span><span class="sxs-lookup"><span data-stu-id="55ebb-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```vb  
    ' ***Use ToArray to execute the query and start the download tasks.   
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="55ebb-137">Chame `WhenAny` na coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="55ebb-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="55ebb-138">`WhenAny` retorna um `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="55ebb-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="55ebb-139">Ou seja, `WhenAny` retorna uma tarefa que resulta em uma única `Task(Of Integer)` ou `Task<int>` quando é esperada.</span><span class="sxs-lookup"><span data-stu-id="55ebb-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="55ebb-140">Essa tarefa única é a primeira tarefa na coleção a ser concluída.</span><span class="sxs-lookup"><span data-stu-id="55ebb-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="55ebb-141">A tarefa que foi concluída em primeiro é atribuída a `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="55ebb-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="55ebb-142">O tipo de `firstFinishedTask` é <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro, porque esse é o tipo de retorno de `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="55ebb-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="55ebb-143">Neste exemplo, você está interessado apenas na tarefa que termina primeiro.</span><span class="sxs-lookup"><span data-stu-id="55ebb-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="55ebb-144">Portanto, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> para cancelar as tarefas restantes.</span><span class="sxs-lookup"><span data-stu-id="55ebb-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="55ebb-145">Por fim, aguarde que `firstFinishedTask` recupere o comprimento do conteúdo baixado.</span><span class="sxs-lookup"><span data-stu-id="55ebb-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="55ebb-146">Execute o programa várias vezes para verificar que diferentes downloads são concluídos em primeiro.</span><span class="sxs-lookup"><span data-stu-id="55ebb-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="55ebb-147">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="55ebb-147">Complete Example</span></span>  
 <span data-ttu-id="55ebb-148">O código a seguir é o arquivo completo de XAML. vb ou MainWindow.xaml.cs do exemplo.</span><span class="sxs-lookup"><span data-stu-id="55ebb-148">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="55ebb-149">Os asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="55ebb-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="55ebb-150">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="55ebb-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="55ebb-151">Você pode baixar o projeto de [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="55ebb-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
' Length of the downloaded website:  158856  
  
' Download complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="55ebb-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55ebb-152">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>  
- [<span data-ttu-id="55ebb-153">Ajustando seu aplicativo assíncrono (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55ebb-153">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [<span data-ttu-id="55ebb-154">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55ebb-154">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="55ebb-155">Exemplo assíncrono: ajuste fino de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="55ebb-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
