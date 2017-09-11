---
title: "Iniciar várias tarefas assíncronas e processá-las assim que são concluídas (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 57ffb748-af40-4794-bedd-bdb7fea062de
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
ms.openlocfilehash: 6fbf4611ecd64abfd016963dff887d82aad333b7
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-visual-basic"></a><span data-ttu-id="22aba-102">Iniciar várias tarefas assíncronas e processá-las assim que são concluídas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22aba-102">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>
<span data-ttu-id="22aba-103">Usando <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, você pode iniciar várias tarefas ao mesmo tempo e processá-los individualmente eles estiverem concluídos, em vez de processá-los na ordem em que eles são iniciados.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="22aba-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>  
  
 <span data-ttu-id="22aba-104">O exemplo a seguir usa uma consulta para criar uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="22aba-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="22aba-105">Cada tarefa baixa o conteúdo de um site específico.</span><span class="sxs-lookup"><span data-stu-id="22aba-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="22aba-106">Em cada iteração de um pouco de loop, uma chamada aguardada para `WhenAny` retorna a tarefa na coleção de tarefas que conclui o download primeiro.</span><span class="sxs-lookup"><span data-stu-id="22aba-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="22aba-107">Essa tarefa é removida da coleção e processada.</span><span class="sxs-lookup"><span data-stu-id="22aba-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="22aba-108">O loop é repetido até que a coleção não contém mais tarefas.</span><span class="sxs-lookup"><span data-stu-id="22aba-108">The loop repeats until the collection contains no more tasks.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22aba-109">Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="22aba-109">To run the examples, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="22aba-110">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="22aba-110">Downloading the Example</span></span>  
 <span data-ttu-id="22aba-111">Você pode baixar o projeto completo do Windows Presentation Foundation (WPF) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="22aba-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="22aba-112">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="22aba-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="22aba-113">Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="22aba-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="22aba-114">No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução (. sln) para AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="22aba-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="22aba-115">Em **Solution Explorer**, abra o menu de atalho para o **ProcessTasksAsTheyFinish** do projeto e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="22aba-115">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="22aba-116">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="22aba-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="22aba-117">Escolha as teclas Ctrl + F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="22aba-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="22aba-118">Execute o projeto várias vezes para verificar se os comprimentos baixados sempre não aparecem na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="22aba-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
 <span data-ttu-id="22aba-119">Se você não quiser baixar o projeto, você pode examinar o arquivo MainWindow.xaml.vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="22aba-119">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="22aba-120">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="22aba-120">Building the Example</span></span>  
 <span data-ttu-id="22aba-121">Este exemplo adiciona o código desenvolvido em [Cancelar tarefas de Async restantes após um é concluído (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) e usa a mesma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="22aba-121">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and uses the same UI.</span></span>  
  
 <span data-ttu-id="22aba-122">Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelAfterOneTask** como o **projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="22aba-122">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAfterOneTask** as the **StartUp Project**.</span></span> <span data-ttu-id="22aba-123">Adicione as alterações neste tópico para o `AccessTheWebAsync` método nesse projeto.</span><span class="sxs-lookup"><span data-stu-id="22aba-123">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="22aba-124">As alterações são marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="22aba-124">The changes are marked with asterisks.</span></span>  
  
 <span data-ttu-id="22aba-125">O **CancelAfterOneTask** projeto já inclui uma consulta que, quando executado, cria uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="22aba-125">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="22aba-126">Cada chamada para `ProcessURLAsync` no código a seguir retorna um <xref:System.Threading.Tasks.Task%601>onde `TResult` é um inteiro.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="22aba-126">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="22aba-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="22aba-127"><CodeContentPlaceHolder>0</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="22aba-128">No arquivo MainWindow.xaml.vb do projeto, faça as seguintes alterações para o `AccessTheWebAsync` método.</span><span class="sxs-lookup"><span data-stu-id="22aba-128">In the MainWindow.xaml.vb file of the  project, make the following changes to the `AccessTheWebAsync` method.</span></span>  
  
-   <span data-ttu-id="22aba-129">Execute a consulta por meio da aplicação <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName>em vez de <xref:System.Linq.Enumerable.ToArray%2A>.</xref:System.Linq.Enumerable.ToArray%2A> </xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="22aba-129">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=fullName> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>  
  
<span data-ttu-id="22aba-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="22aba-130"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
-   <span data-ttu-id="22aba-131">Adicionar um while loop que executa as seguintes etapas para cada tarefa na coleção.</span><span class="sxs-lookup"><span data-stu-id="22aba-131">Add a while loop that performs the following steps for each task in the collection.</span></span>  
  
    1.  <span data-ttu-id="22aba-132">Espera de uma chamada para `WhenAny` para identificar a primeira tarefa na coleção para concluir o download.</span><span class="sxs-lookup"><span data-stu-id="22aba-132">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>  
  
<span data-ttu-id="22aba-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="22aba-133"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
    2.  <span data-ttu-id="22aba-134">Remove essa tarefa da coleção.</span><span class="sxs-lookup"><span data-stu-id="22aba-134">Removes that task from the collection.</span></span>  
  
<span data-ttu-id="22aba-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="22aba-135"><CodeContentPlaceHolder>3</CodeContentPlaceHolder></span></span>  
    3.  <span data-ttu-id="22aba-136">Awaits `firstFinishedTask`, que é retornado por uma chamada para `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="22aba-136">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="22aba-137">O `firstFinishedTask` variável é um <xref:System.Threading.Tasks.Task%601>onde `TReturn` é um inteiro.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="22aba-137">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="22aba-138">A tarefa já foi concluída, mas você espera para recuperar o tamanho do site baixado, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="22aba-138">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>  
  
        ```vb  
        Dim length = Await firstFinishedTask  
        resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
        ```  
  
 <span data-ttu-id="22aba-139">Você deve executar o projeto várias vezes para verificar se os comprimentos baixados sempre não aparecem na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="22aba-139">You should run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="22aba-140">Você pode usar `WhenAny` em um loop, conforme descrito no exemplo, para resolver problemas que envolvem um pequeno número de tarefas.</span><span class="sxs-lookup"><span data-stu-id="22aba-140">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="22aba-141">No entanto, outras abordagens são mais eficientes se você tiver um grande número de tarefas para processar.</span><span class="sxs-lookup"><span data-stu-id="22aba-141">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="22aba-142">Para obter mais informações e exemplos, consulte [tarefas de processamento como eles completa](http://go.microsoft.com/fwlink/?LinkId=260810).</span><span class="sxs-lookup"><span data-stu-id="22aba-142">For more information and examples, see [Processing Tasks as they complete](http://go.microsoft.com/fwlink/?LinkId=260810).</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="22aba-143">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="22aba-143">Complete Example</span></span>  
 <span data-ttu-id="22aba-144">O código a seguir é o texto completo do arquivo MainWindow.xaml.vb no exemplo.</span><span class="sxs-lookup"><span data-stu-id="22aba-144">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="22aba-145">Asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="22aba-145">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="22aba-146">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="22aba-146">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="22aba-147">Você pode baixar o projeto de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="22aba-147">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
' Length of the download:  226093  
' Length of the download:  412588  
' Length of the download:  175490  
' Length of the download:  204890  
' Length of the download:  158855  
' Length of the download:  145790  
' Length of the download:  44908  
' Downloads complete.  
```  
  
## <a name="see-also"></a><span data-ttu-id="22aba-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22aba-148">See Also</span></span>  
 <span data-ttu-id="22aba-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="22aba-149"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="22aba-150"> [Ajustando seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="22aba-150"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="22aba-151"> [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="22aba-151"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="22aba-152"> [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="22aba-152"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
