---
title: "Como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: af0917bebd54fe713b620be92087279e8f580fbb
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="c6178-102">Como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6178-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="c6178-103">Em um método assíncrono, as tarefas são iniciadas quando eles são criados.</span><span class="sxs-lookup"><span data-stu-id="c6178-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="c6178-104">O [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador é aplicado à tarefa no ponto em que o método em que o processamento não pode continuar até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="c6178-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="c6178-105">Geralmente, uma tarefa é aguardada assim que ele é criado, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c6178-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 <span data-ttu-id="c6178-106">No entanto, você pode separar a criação da tarefa de aguardando a tarefa se o programa tiver outro trabalho conseguir que não depende da conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="c6178-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
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
  
 <span data-ttu-id="c6178-107">Entre iniciando uma tarefa e aguardando a ele, você pode iniciar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="c6178-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="c6178-108">Tarefas adicionais implicitamente executem em paralelo, mas não há threads adicionais são criados.</span><span class="sxs-lookup"><span data-stu-id="c6178-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="c6178-109">O programa a seguir inicia três downloads da web assíncrona e, em seguida, aguarda-los na ordem em que são chamados.</span><span class="sxs-lookup"><span data-stu-id="c6178-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="c6178-110">Observe que, quando você executar o programa, o que as tarefas não são concluídas na ordem em que são criadas e espera sempre.</span><span class="sxs-lookup"><span data-stu-id="c6178-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="c6178-111">Eles comecem a ser executadas quando eles são criados e uma ou mais tarefas podem terminar antes do método atinge as expressões await.</span><span class="sxs-lookup"><span data-stu-id="c6178-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6178-112">Para concluir este projeto, você deve ter o Visual Studio 2012 ou posterior e o .NET Framework 4.5 ou posterior instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="c6178-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="c6178-113">Outro exemplo que inicia diversas tarefas ao mesmo tempo, consulte [como: estender o Async Walkthrough por usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="c6178-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="c6178-114">Você pode baixar o código deste exemplo de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=254906).</span><span class="sxs-lookup"><span data-stu-id="c6178-114">You can download the code for this example from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=254906).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="c6178-115">Para configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="c6178-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="c6178-116">Para configurar um aplicativo WPF, conclua as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="c6178-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="c6178-117">Você pode encontrar instruções detalhadas para essas etapas em [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="c6178-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="c6178-118">Crie um aplicativo WPF que contém uma caixa de texto e um botão.</span><span class="sxs-lookup"><span data-stu-id="c6178-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="c6178-119">Nomeie o botão `startButton`e a caixa de texto nome `resultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="c6178-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="c6178-120">Adicione uma referência para <xref:System.Net.Http>.</xref:System.Net.Http></span><span class="sxs-lookup"><span data-stu-id="c6178-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="c6178-121">No arquivo MainWindow.xaml.vb, adicione uma `Imports` instrução `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="c6178-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="c6178-122">Para adicionar o código</span><span class="sxs-lookup"><span data-stu-id="c6178-122">To add the code</span></span>  
  
1.  <span data-ttu-id="c6178-123">Na janela de design, MainWindow. XAML, clique duas vezes no botão para criar o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c6178-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="c6178-124">Copie o seguinte código e cole-o no corpo da `startButton_Click` em MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="c6178-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     <span data-ttu-id="c6178-125">O código chama um método assíncrono, `CreateMultipleTasksAsync`, que acionam o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c6178-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="c6178-126">Adicione os seguintes métodos de suporte ao projeto:</span><span class="sxs-lookup"><span data-stu-id="c6178-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="c6178-127">`ProcessURLAsync`usa um <xref:System.Net.Http.HttpClient>método para baixar o conteúdo de um site como uma matriz de bytes.</xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="c6178-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="c6178-128">O método de suporte, `ProcessURLAsync` , em seguida, exibe e retorna o comprimento da matriz.</span><span class="sxs-lookup"><span data-stu-id="c6178-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="c6178-129">`DisplayResults`Exibe o número de bytes na matriz de bytes para cada URL.</span><span class="sxs-lookup"><span data-stu-id="c6178-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="c6178-130">Essa exibição mostra quando cada tarefa terminou o download.</span><span class="sxs-lookup"><span data-stu-id="c6178-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="c6178-131">Copie os seguintes métodos e colá-los após o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="c6178-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
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
  
4.  <span data-ttu-id="c6178-132">Finalmente, defina o método `CreateMultipleTasksAsync`, que executa as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="c6178-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="c6178-133">O método declara uma `HttpClient` objeto, que você precisa para acessar o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>em `ProcessURLAsync`.</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A></span><span class="sxs-lookup"><span data-stu-id="c6178-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="c6178-134">O método cria e inicia três tarefas do tipo <xref:System.Threading.Tasks.Task%601>, onde `TResult` é um inteiro.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="c6178-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="c6178-135">Como cada tarefa termina, `DisplayResults` exibe a URL da tarefa e o comprimento do conteúdo baixado.</span><span class="sxs-lookup"><span data-stu-id="c6178-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="c6178-136">Como as tarefas estão em execução assíncrona, a ordem na qual os resultados são exibidos pode diferir da ordem na qual eles foram declarados.</span><span class="sxs-lookup"><span data-stu-id="c6178-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="c6178-137">O método aguarda a conclusão de cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="c6178-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="c6178-138">Cada `Await` operador suspende a execução de `CreateMultipleTasksAsync` até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="c6178-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="c6178-139">O operador também recupera o valor de retorno da chamada para `ProcessURLAsync` de cada tarefa concluída.</span><span class="sxs-lookup"><span data-stu-id="c6178-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="c6178-140">Quando as tarefas foram concluídas e os valores inteiros forem recuperados, o método soma os comprimentos dos sites e exibe o resultado.</span><span class="sxs-lookup"><span data-stu-id="c6178-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="c6178-141">Copie o seguinte método e cole-o em sua solução.</span><span class="sxs-lookup"><span data-stu-id="c6178-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
5.  <span data-ttu-id="c6178-142">Escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="c6178-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="c6178-143">Execute o programa várias vezes para verificar se as três tarefas não são concluídas sempre na mesma ordem e que a ordem em que elas sejam concluídas não é necessariamente a ordem em que elas são criadas e esperadas.</span><span class="sxs-lookup"><span data-stu-id="c6178-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6178-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6178-144">Example</span></span>  
 <span data-ttu-id="c6178-145">O código a seguir contém um exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="c6178-145">The following code contains the full example.</span></span>  
  
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
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c6178-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6178-146">See Also</span></span>  
 <span data-ttu-id="c6178-147">[Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="c6178-147">[Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="c6178-148"> [Programação assíncrona com Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="c6178-148"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="c6178-149"> [Como: estender o passo a passo assíncronas usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)</span><span class="sxs-lookup"><span data-stu-id="c6178-149"> [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)</span></span>

