---
title: "Cancelar as demais tarefas assíncronas após um completo (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: c928b5a1-622f-4441-8baf-adca1dde197f
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
ms.openlocfilehash: 1b70822edd972ac33614ab49faad6ff50b0e80b7
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-visual-basic"></a><span data-ttu-id="01d0c-102">Cancelar as demais tarefas assíncronas após um completo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01d0c-102">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>
<span data-ttu-id="01d0c-103">Usando o <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>método junto com um <xref:System.Threading.CancellationToken>, você pode cancelar todas as tarefas restantes quando uma tarefa é concluída.</xref:System.Threading.CancellationToken> </xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="01d0c-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="01d0c-104">O `WhenAny` método tem um argumento que é um conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="01d0c-105">O método inicia todas as tarefas e retorna uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="01d0c-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="01d0c-106">A tarefa é concluída quando qualquer tarefa na coleção é concluída.</span><span class="sxs-lookup"><span data-stu-id="01d0c-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="01d0c-107">Este exemplo demonstra como usar um token de cancelamento em conjunto com `WhenAny` para manter a primeira tarefa ao fim da coleção de tarefas e para cancelar as tarefas restantes.</span><span class="sxs-lookup"><span data-stu-id="01d0c-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="01d0c-108">Cada tarefa baixa o conteúdo de um site.</span><span class="sxs-lookup"><span data-stu-id="01d0c-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="01d0c-109">O exemplo exibe o comprimento do conteúdo do primeiro download para concluir e cancela os outros downloads.</span><span class="sxs-lookup"><span data-stu-id="01d0c-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01d0c-110">Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="01d0c-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="01d0c-111">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="01d0c-111">Downloading the Example</span></span>  
 <span data-ttu-id="01d0c-112">Você pode baixar o projeto completo do Windows Presentation Foundation (WPF) de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046) e, em seguida, siga estas etapas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="01d0c-113">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="01d0c-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="01d0c-114">Na barra de menus, escolha **arquivo**, **abrir**, **projeto/solução**.</span><span class="sxs-lookup"><span data-stu-id="01d0c-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="01d0c-115">No **Abrir projeto** caixa de diálogo, abra a pasta que contém o código de exemplo é descompactado e, em seguida, abra o arquivo de solução (. sln) para AsyncFineTuningVB.</span><span class="sxs-lookup"><span data-stu-id="01d0c-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="01d0c-116">Em **Solution Explorer**, abra o menu de atalho para o **CancelAfterOneTask** do projeto e escolha **Set as StartUp Project**.</span><span class="sxs-lookup"><span data-stu-id="01d0c-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="01d0c-117">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="01d0c-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="01d0c-118">Escolha as teclas Ctrl + F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="01d0c-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="01d0c-119">Execute o programa várias vezes para verificar que diferentes downloads concluir primeiro.</span><span class="sxs-lookup"><span data-stu-id="01d0c-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="01d0c-120">Se você não quiser baixar o projeto, você pode examinar o arquivo MainWindow.xaml.vb no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="01d0c-120">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="01d0c-121">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="01d0c-121">Building the Example</span></span>  
 <span data-ttu-id="01d0c-122">O exemplo neste tópico adiciona ao projeto que é desenvolvido no [cancelar uma tarefa assíncrona ou uma lista de tarefas](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) para cancelar uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks](http://msdn.microsoft.com/library/d6e4e801-df64-4705-98fc-df725a577fb0) to cancel a list of tasks.</span></span> <span data-ttu-id="01d0c-123">O exemplo usa a mesma interface de usuário, embora o **Cancelar** botão não é usado explicitamente.</span><span class="sxs-lookup"><span data-stu-id="01d0c-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="01d0c-124">Para criar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixar o exemplo", mas escolha **CancelAListOfTasks** como o **projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="01d0c-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="01d0c-125">Adicione as alterações neste tópico para o projeto.</span><span class="sxs-lookup"><span data-stu-id="01d0c-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="01d0c-126">No arquivo MainWindow.xaml.vb do **CancelAListOfTasks** de projeto, iniciar a transição movendo as etapas de processamento para cada site do loop na `AccessTheWebAsync` para o seguinte método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="01d0c-126">In the MainWindow.xaml.vb file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
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
  
 <span data-ttu-id="01d0c-127">Em `AccessTheWebAsync`, este exemplo usa uma consulta, o <xref:System.Linq.Enumerable.ToArray%2A>método e o `WhenAny` método para criar e iniciar uma matriz de tarefas.</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="01d0c-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="01d0c-128">O aplicativo de `WhenAny` à matriz retorna uma única tarefa que, quando colocado em espera, é avaliada para a primeira tarefa para alcançar a conclusão da matriz de tarefas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="01d0c-129">Faça as seguintes alterações em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="01d0c-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="01d0c-130">Asteriscos marcam as alterações no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="01d0c-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="01d0c-131">Comentar ou excluir o loop.</span><span class="sxs-lookup"><span data-stu-id="01d0c-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="01d0c-132">Criar uma consulta que, quando executado, produz uma coleção de tarefas genéricas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="01d0c-133">Cada chamada para `ProcessURLAsync` retorna um <xref:System.Threading.Tasks.Task%601>onde `TResult` é um inteiro.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="01d0c-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
<span data-ttu-id="01d0c-134"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="01d0c-134"><CodeContentPlaceHolder>1</CodeContentPlaceHolder></span></span>  
3.  <span data-ttu-id="01d0c-135">Chamar `ToArray` para executar a consulta e iniciar as tarefas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-135">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="01d0c-136">O aplicativo do `WhenAny` método na próxima etapa seria executar a consulta e iniciar as tarefas sem usar `ToArray`, mas outros métodos não podem.</span><span class="sxs-lookup"><span data-stu-id="01d0c-136">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="01d0c-137">A prática mais segura é forçar a execução da consulta explicitamente.</span><span class="sxs-lookup"><span data-stu-id="01d0c-137">The safest practice is to force execution of the query explicitly.</span></span>  
  
<span data-ttu-id="01d0c-138"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="01d0c-138"><CodeContentPlaceHolder>2</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="01d0c-139">Chamar `WhenAny` na coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="01d0c-139">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="01d0c-140">`WhenAny`Retorna um `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="01d0c-140">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="01d0c-141">Ou seja, `WhenAny` retorna uma tarefa que avalia para um único `Task(Of Integer)` ou `Task<int>` quando é esperado.</span><span class="sxs-lookup"><span data-stu-id="01d0c-141">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="01d0c-142">Essa única tarefa é a primeira tarefa na coleção para concluir.</span><span class="sxs-lookup"><span data-stu-id="01d0c-142">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="01d0c-143">A tarefa que concluiu o primeiro é atribuída a `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="01d0c-143">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="01d0c-144">O tipo de `firstFinishedTask` é <xref:System.Threading.Tasks.Task%601>onde `TResult` é um inteiro, porque esse é o tipo de retorno de `ProcessURLAsync`.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="01d0c-144">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
```vb  
' ***Call WhenAny and then await the result. The task that finishes   
' first is assigned to firstFinishedTask.  
Dim firstFinishedTask As Task(Of Integer) = Await Task.WhenAny(downloadTasks)  
```  
  
5.  <span data-ttu-id="01d0c-145">Neste exemplo, você está interessado apenas na tarefa que termina primeiro.</span><span class="sxs-lookup"><span data-stu-id="01d0c-145">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="01d0c-146">Portanto, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>para cancelar as tarefas restantes.</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="01d0c-146">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> to cancel the remaining tasks.</span></span>  
  
```vb  
' ***Cancel the rest of the downloads. You just want the first one.  
cts.Cancel()  
```  
  
6.  <span data-ttu-id="01d0c-147">Por fim, await `firstFinishedTask` para recuperar o comprimento do conteúdo baixado.</span><span class="sxs-lookup"><span data-stu-id="01d0c-147">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
```vb  
Dim length = Await firstFinishedTask  
resultsTextBox.Text &= String.Format(vbCrLf & "Length of the downloaded website:  {0}" & vbCrLf, length)  
```  
  
 <span data-ttu-id="01d0c-148">Execute o programa várias vezes para verificar que diferentes downloads concluir primeiro.</span><span class="sxs-lookup"><span data-stu-id="01d0c-148">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="01d0c-149">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="01d0c-149">Complete Example</span></span>  
 <span data-ttu-id="01d0c-150">O código a seguir é o arquivo MainWindow.xaml.vb ou MainWindow.xaml.cs completo para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="01d0c-150">The following code is the complete MainWindow.xaml.vb or MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="01d0c-151">Asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="01d0c-151">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="01d0c-152">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="01d0c-152">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="01d0c-153">Você pode baixar o projeto de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="01d0c-153">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01d0c-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="01d0c-154">See Also</span></span>  
 <span data-ttu-id="01d0c-155"><xref:System.Threading.Tasks.Task.WhenAny%2A></xref:System.Threading.Tasks.Task.WhenAny%2A></span><span class="sxs-lookup"><span data-stu-id="01d0c-155"><xref:System.Threading.Tasks.Task.WhenAny%2A></span></span>   
<span data-ttu-id="01d0c-156"> [Ajustando seu aplicativo Async (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="01d0c-156"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="01d0c-157"> [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="01d0c-157"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="01d0c-158"> [Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="01d0c-158"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
