---
title: 'Como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
ms.openlocfilehash: 4d4ccda6657dd4d889e8495fa000715c1f7a5ba6
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728437"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="44f49-102">Como: fazer várias solicitações da Web em paralelo usando Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f49-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="44f49-103">Em um método assíncrono, as tarefas são iniciadas quando elas são criadas.</span><span class="sxs-lookup"><span data-stu-id="44f49-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="44f49-104">O [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operador é aplicado para a tarefa no momento no método em que o processamento não pode continuar até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="44f49-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="44f49-105">Geralmente, uma tarefa é aguardada assim que ela é criada, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="44f49-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 <span data-ttu-id="44f49-106">No entanto, você pode separar a criação da tarefa da espera da tarefa se o programa tiver outro trabalho a realizar, que não depende da conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="44f49-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
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
  
 <span data-ttu-id="44f49-107">Entre o início de uma tarefa e a espera por ela, você pode iniciar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="44f49-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="44f49-108">As tarefas adicionais são executadas implicitamente em paralelo, mas não são criados threads adicionais.</span><span class="sxs-lookup"><span data-stu-id="44f49-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="44f49-109">O programa a seguir inicia três downloads assíncronos na Web e, em seguida, os aguarda na ordem em que foram chamados.</span><span class="sxs-lookup"><span data-stu-id="44f49-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="44f49-110">Observe ao executar o programa, que as tarefas nem sempre são concluídas na ordem em que foram criadas e aguardadas.</span><span class="sxs-lookup"><span data-stu-id="44f49-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="44f49-111">Eles começam a ser executadas quando são criadas e uma ou mais tarefas podem terminar antes que o método alcance as expressões await.</span><span class="sxs-lookup"><span data-stu-id="44f49-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44f49-112">Para concluir esse projeto, você precisa ter o Visual Studio 2012 ou posterior e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="44f49-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="44f49-113">Outro exemplo que inicia várias tarefas ao mesmo tempo, consulte [como: estender a Async Walkthrough por usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="44f49-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="44f49-114">Você pode baixar o código deste exemplo de [Exemplos de código para desenvolvedores](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="44f49-114">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="44f49-115">Para configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="44f49-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="44f49-116">Para configurar um aplicativo WPF, complete as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="44f49-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="44f49-117">Você pode encontrar instruções detalhadas para essas etapas em [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="44f49-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="44f49-118">Crie um aplicativo WPF que contenha uma caixa de texto e um botão.</span><span class="sxs-lookup"><span data-stu-id="44f49-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="44f49-119">Dê o nome `startButton` para o botão e `resultsTextBox`, para a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="44f49-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="44f49-120">Adicione uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="44f49-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="44f49-121">No arquivo MainWindow.xaml.vb, adicione um `Imports` instrução para `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="44f49-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="44f49-122">Para adicionar o código</span><span class="sxs-lookup"><span data-stu-id="44f49-122">To add the code</span></span>  
  
1.  <span data-ttu-id="44f49-123">Na janela de design, MainWindow. XAML, clique duas vezes no botão para criar o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="44f49-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="44f49-124">Copie o seguinte código e cole-o no corpo da `startButton_Click` em MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="44f49-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     <span data-ttu-id="44f49-125">O código chama um método assíncrono, `CreateMultipleTasksAsync`, que controla o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="44f49-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="44f49-126">Adicione os seguintes métodos de suporte ao projeto:</span><span class="sxs-lookup"><span data-stu-id="44f49-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="44f49-127">O `ProcessURLAsync` usa um método <xref:System.Net.Http.HttpClient> para baixar o conteúdo de um site como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="44f49-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="44f49-128">Em seguida, o método de suporte `ProcessURLAsync` exibe e retorna o comprimento da matriz.</span><span class="sxs-lookup"><span data-stu-id="44f49-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="44f49-129">O `DisplayResults` exibe o número de bytes na matriz de bytes para cada URL.</span><span class="sxs-lookup"><span data-stu-id="44f49-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="44f49-130">Essa exibição mostra quando cada tarefa termina o download.</span><span class="sxs-lookup"><span data-stu-id="44f49-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="44f49-131">Copie os seguintes métodos e colá-los após o `startButton_Click` MainWindow.xaml.vb manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="44f49-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
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
  
4.  <span data-ttu-id="44f49-132">Finalmente, defina o método `CreateMultipleTasksAsync`, que executa as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="44f49-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="44f49-133">O método declara um objeto `HttpClient`, que você precisa para acessar o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> em `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="44f49-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="44f49-134">O método cria e inicia três tarefas do tipo <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="44f49-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="44f49-135">Conforme cada tarefa termina, `DisplayResults` exibe a URL da tarefa e o comprimento do conteúdo baixado.</span><span class="sxs-lookup"><span data-stu-id="44f49-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="44f49-136">Como as tarefas estão em execução de maneira assíncrona, a ordem na qual os resultados são exibidos pode diferir da ordem na qual elas foram declaradas.</span><span class="sxs-lookup"><span data-stu-id="44f49-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="44f49-137">O método aguarda a conclusão de cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="44f49-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="44f49-138">Cada operador `Await` suspende a execução de `CreateMultipleTasksAsync` até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="44f49-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="44f49-139">O operador também recupera o valor retornado da chamada ao `ProcessURLAsync` de cada tarefa concluída.</span><span class="sxs-lookup"><span data-stu-id="44f49-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="44f49-140">Quando as tarefas forem concluídas e os valores inteiros forem recuperados, o método somará os comprimentos dos sites e exibirá o resultado.</span><span class="sxs-lookup"><span data-stu-id="44f49-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="44f49-141">Copie o seguinte método e cole-o em sua solução.</span><span class="sxs-lookup"><span data-stu-id="44f49-141">Copy the following method, and paste it into your solution.</span></span>  
  
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
  
5.  <span data-ttu-id="44f49-142">Escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="44f49-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="44f49-143">Execute o programa várias vezes para ver que as três tarefas nem sempre são concluídas na mesma ordem e que a ordem em que elas são concluídas não é, necessariamente, a ordem em que elas foram criadas e aguardadas.</span><span class="sxs-lookup"><span data-stu-id="44f49-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44f49-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44f49-144">Example</span></span>  
 <span data-ttu-id="44f49-145">O código a seguir contem o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="44f49-145">The following code contains the full example.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="44f49-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44f49-146">See Also</span></span>  
 [<span data-ttu-id="44f49-147">Instruções passo a passo: acessando a Web usando Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f49-147">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="44f49-148">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f49-148">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="44f49-149">Como estender as instruções passo a passo assíncronas usando Task.WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="44f49-149">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
