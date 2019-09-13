---
title: Iniciar várias tarefas assíncronas e processá-las à medida que elas forem concluídas (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
ms.openlocfilehash: b103f385c804061c4df99dc9d1fdd54c7876151a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928463"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="73fde-102">Iniciar várias tarefas assíncronas e processá-las à medida que elas forem concluídas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73fde-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="73fde-103">Usando <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, você pode iniciar várias tarefas ao mesmo tempo e processá-las individualmente conforme elas foram concluídas, em vez de processá-las na ordem em que foram iniciadas.</span><span class="sxs-lookup"><span data-stu-id="73fde-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="73fde-104">O exemplo a seguir usa uma consulta para criar uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="73fde-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="73fde-105">Cada tarefa baixa o conteúdo de um site especificado.</span><span class="sxs-lookup"><span data-stu-id="73fde-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="73fde-106">Em cada iteração de um loop "while", uma chamada esperada para `WhenAny` retorna a tarefa na coleção de tarefas que concluir o download primeiro.</span><span class="sxs-lookup"><span data-stu-id="73fde-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="73fde-107">Essa tarefa é removida da coleção e processada.</span><span class="sxs-lookup"><span data-stu-id="73fde-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="73fde-108">O loop é repetido até que a coleção não contenha mais tarefas.</span><span class="sxs-lookup"><span data-stu-id="73fde-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73fde-109">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="73fde-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="73fde-110">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="73fde-110">Downloading the Example</span></span>  
 <span data-ttu-id="73fde-111">Baixe o projeto completo do WPF (Windows Presentation Foundation) em [Amostra assíncrona: Ajustando o aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="73fde-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1. <span data-ttu-id="73fde-112">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73fde-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2. <span data-ttu-id="73fde-113">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="73fde-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3. <span data-ttu-id="73fde-114">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="73fde-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4. <span data-ttu-id="73fde-115">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **ProcessTasksAsTheyFinish** e escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="73fde-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="73fde-116">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="73fde-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="73fde-117">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="73fde-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6. <span data-ttu-id="73fde-118">Execute o projeto várias vezes para verificar se os tamanhos baixados não aparecem sempre na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="73fde-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="73fde-119">Se não quiser baixar o projeto, você poderá examinar o arquivo MainWindow.xaml.vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="73fde-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="73fde-120">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="73fde-120">Building the Example</span></span>  
 <span data-ttu-id="73fde-121">Este exemplo adiciona ao código que é desenvolvido em [Cancelar tarefas assíncronas restantes após uma conclusão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) e usa a mesma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="73fde-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="73fde-122">Para compilar o exemplo por conta própria, passo a passo, siga as instruções na seção "Baixando o exemplo", mas escolha **CancelAfterOneTask** como o **Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="73fde-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="73fde-123">Adicione as alterações neste tópico ao método `AccessTheWebAsync` naquele projeto.</span><span class="sxs-lookup"><span data-stu-id="73fde-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="73fde-124">As alterações estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="73fde-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="73fde-125">O projeto **CancelAfterOneTask** já inclui uma consulta que, quando executada, cria uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="73fde-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="73fde-126">Cada chamada para `ProcessURLAsync` no código a seguir retorna um <xref:System.Threading.Tasks.Task%601> em que `TResult` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="73fde-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
```vb  
Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
    From url In urlList Select ProcessURLAsync(url, client, ct)  
```  
  
 <span data-ttu-id="73fde-127">No arquivo MainWindow. XAML. vb do projeto, faça as seguintes alterações `AccessTheWebAsync` no método.</span><span class="sxs-lookup"><span data-stu-id="73fde-127">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
- <span data-ttu-id="73fde-128">Execute a consulta aplicando <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> em vez de <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="73fde-128">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
    ```vb  
    Dim downloadTasks As List(Of Task(Of Integer)) = downloadTasksQuery.ToList()  
    ```  
  
- <span data-ttu-id="73fde-129">Adiciona um loop "while" que executa as seguintes etapas para cada tarefa na coleção.</span><span class="sxs-lookup"><span data-stu-id="73fde-129">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1. <span data-ttu-id="73fde-130">Espera uma chamada para `WhenAny` para identificar a primeira tarefa na coleção a concluir o download.</span><span class="sxs-lookup"><span data-stu-id="73fde-130">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
        ```vb  
        Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
        ```  
  
    2. <span data-ttu-id="73fde-131">Remove a tarefa da coleção.</span><span class="sxs-lookup"><span data-stu-id="73fde-131">Removes that task from the collection.</span></span>  
  
        ```vb  
        downloadTasks.Remove(firstFinishedTask)  
        ```  
  
    3. <span data-ttu-id="73fde-132">Espera `firstFinishedTask`, que é retornado por uma chamada para `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="73fde-132">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="73fde-133">A variável `firstFinishedTask` é uma <xref:System.Threading.Tasks.Task%601> em que `TReturn` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="73fde-133">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="73fde-134">A tarefa já foi concluída, mas você espera para recuperar o tamanho do site baixado, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="73fde-134">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="73fde-135">Você deve executar o projeto várias vezes para verificar se os tamanhos baixados não aparecem sempre na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="73fde-135">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="73fde-136">Você pode usar `WhenAny` em um loop, conforme descrito no exemplo, para resolver problemas que envolvem um número pequeno de tarefas.</span><span class="sxs-lookup"><span data-stu-id="73fde-136">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="73fde-137">No entanto, outras abordagens são mais eficientes se você tiver um número grande de tarefas para processar.</span><span class="sxs-lookup"><span data-stu-id="73fde-137">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="73fde-138">Para obter mais informações e exemplos, consulte [Processando tarefas quando elas são concluídas](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="73fde-138">For more information and examples, see [Processing Tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete/).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="73fde-139">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="73fde-139">Complete Example</span></span>  
 <span data-ttu-id="73fde-140">O código a seguir é o texto completo do arquivo MainWindow.xaml.vb para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="73fde-140">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="73fde-141">Os asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="73fde-141">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="73fde-142">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="73fde-142">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="73fde-143">Baixe o projeto em [Amostra assíncrona: Ajustando o aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="73fde-143">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73fde-144">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73fde-144">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="73fde-145">Ajustando seu aplicativo assíncrono (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73fde-145">Fine-Tuning Your Async Application (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="73fde-146">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73fde-146">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="73fde-147">Exemplo de Async: ajuste do seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="73fde-147">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
