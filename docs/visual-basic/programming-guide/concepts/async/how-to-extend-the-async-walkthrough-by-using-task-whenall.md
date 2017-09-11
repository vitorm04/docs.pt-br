---
title: "Como: estender o passo a passo assíncronas usando Task. WhenAll (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: c06d386d-e996-4da9-bf3d-05a3b6c0a258
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 91cecc84899c9a87307ed5799485ec60ef341e65
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-visual-basic"></a><span data-ttu-id="4fdd7-102">Como: estender o passo a passo assíncronas usando Task. WhenAll (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fdd7-102">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>
<span data-ttu-id="4fdd7-103">Você pode melhorar o desempenho da solução assíncrona em [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) usando o <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>método.</xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4fdd7-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="4fdd7-104">Esse método espera assincronamente várias operações assíncronas, que são representadas como uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="4fdd7-105">Você pode ter notado no passo a passo que os sites baixem em taxas diferentes.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="4fdd7-106">Às vezes, um dos sites está muito lento, que atrasa todos os downloads restantes.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="4fdd7-107">Quando você executar as soluções assíncronas que você criou no passo a passo, você pode finalizar o programa facilmente se você não quiser esperar, mas uma opção melhor seria iniciar todos os downloads ao mesmo tempo e permitir que mais rápido downloads continuam sem esperar que está atrasada.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="4fdd7-108">Aplicar o `Task.WhenAll` método a uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="4fdd7-109">O aplicativo de `WhenAll` retorna uma única tarefa não será completa até a conclusão de cada tarefa na coleção.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="4fdd7-110">As tarefas parecem ser executados em paralelo, mas não há threads adicionais são criados.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="4fdd7-111">As tarefas podem ser concluídas em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4fdd7-112">Os procedimentos a seguir descrevem extensões para os aplicativos assíncronos que são desenvolvidos em [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd7-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="4fdd7-113">Você pode desenvolver os aplicativos por concluir o passo a passo ou baixar o código de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191).</span><span class="sxs-lookup"><span data-stu-id="4fdd7-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
>   
>  <span data-ttu-id="4fdd7-114">Para executar o exemplo, você deve ter o Visual Studio 2012 ou posterior instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="4fdd7-115">Para adicionar o Task. WhenAll à sua solução GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="4fdd7-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="4fdd7-116">Adicionar o `ProcessURLAsync` o primeiro aplicativo que é desenvolvido no método [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd7-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="4fdd7-117">Se você baixou o código de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191), abra o projeto AsyncWalkthrough e, em seguida, adicionar `ProcessURLAsync` para o arquivo MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-117">If you downloaded the code from  [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="4fdd7-118">Se você desenvolveu o código ao concluir o passo a passo, adicione `ProcessURLAsync` para o aplicativo que inclui o `GetURLContentsAsync` método.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="4fdd7-119">O arquivo MainWindow.xaml.vb para este aplicativo é o primeiro exemplo na seção "Exemplos de código completa a apresentação" do.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-119">The MainWindow.xaml.vb file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="4fdd7-120">O `ProcessURLAsync` método consolida as ações no corpo do `For Each` loop na `SumPageSizesAsync` no passo a passo original.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-120">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="4fdd7-121">O método assíncrona baixa o conteúdo de um site específico, como uma matriz de bytes e, em seguida, exibe e retorna o comprimento da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="4fdd7-122">Comentar ou excluir o `For Each` loop na `SumPageSizesAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-122">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0  
    'For Each url In urlList  
  
    '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
    '    ' The previous line abbreviates the following two assignment statements.  
  
    '    ' GetURLContentsAsync returns a task. At completion, the task  
    '    ' produces a byte array.  
    '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
    '    'Dim urlContents As Byte() = Await getContentsTask  
  
    '    DisplayResults(url, urlContents)  
  
    '    ' Update the total.  
    '    total += urlContents.Length  
    'Next  
    ```  
  
3.  <span data-ttu-id="4fdd7-123">Crie um conjunto de tarefas.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-123">Create a collection of tasks.</span></span> <span data-ttu-id="4fdd7-124">O código a seguir define uma [consulta](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) que, quando executado pelo <xref:System.Linq.Enumerable.ToArray%2A>método cria uma coleção de tarefas que baixar o conteúdo de cada site.</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="4fdd7-124">The following code defines a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="4fdd7-125">As tarefas são iniciadas quando a consulta é avaliada.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="4fdd7-126">Adicione o seguinte código ao método `SumPageSizesAsync` depois da declaração da `urlList`.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.   
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="4fdd7-127">Aplicar `Task.WhenAll` à coleção de tarefas, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="4fdd7-128">`Task.WhenAll`Retorna uma única tarefa termina quando tem concluído todas as tarefas na coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="4fdd7-129">No exemplo a seguir, o `Await` expressão aguarda a conclusão do único de tarefa que `WhenAll` retorna.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-129">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="4fdd7-130">A expressão é avaliada como uma matriz de inteiros, onde cada inteiro é o comprimento de um site de download.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="4fdd7-131">Adicione o seguinte código para `SumPageSizesAsync`, apenas após o código que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="4fdd7-132">Por fim, use o <xref:System.Linq.Enumerable.Sum%2A>método para calcular a soma dos comprimentos de todos os sites.</xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="4fdd7-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="4fdd7-133">Adicione a seguinte linha ao `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="4fdd7-134">Para adicionar o Task. WhenAll à solução HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="4fdd7-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="4fdd7-135">Adicione a seguinte versão `ProcessURLAsync` para o segundo aplicativo é desenvolvido no [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd7-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="4fdd7-136">Se você baixou o código de [amostras de código do desenvolvedor](http://go.microsoft.com/fwlink/?LinkId=255191), abra o projeto AsyncWalkthrough_HttpClient e, em seguida, adicionar `ProcessURLAsync` para o arquivo MainWindow.xaml.vb.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-136">If you downloaded the code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.vb file.</span></span>  
  
    -   <span data-ttu-id="4fdd7-137">Se você desenvolveu o código ao concluir o passo a passo, adicione `ProcessURLAsync` para o aplicativo que usa o `HttpClient.GetByteArrayAsync` método.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="4fdd7-138">O arquivo MainWindow.xaml.vb para este aplicativo é o segundo exemplo na seção "Exemplos de código completa a apresentação" do.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-138">The MainWindow.xaml.vb file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="4fdd7-139">O `ProcessURLAsync` método consolida as ações no corpo do `For Each` loop na `SumPageSizesAsync` no passo a passo original.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-139">The `ProcessURLAsync` method consolidates the actions in the body of the `For Each` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="4fdd7-140">O método assíncrona baixa o conteúdo de um site específico, como uma matriz de bytes e, em seguida, exibe e retorna o comprimento da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="4fdd7-141">A única diferença do `ProcessURLAsync` método no procedimento anterior é o uso da <xref:System.Net.Http.HttpClient>instância, `client`.</xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="4fdd7-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
    ```  
  
2.  <span data-ttu-id="4fdd7-142">Comentar ou excluir o `For Each` loop na `SumPageSizesAsync`, como mostra o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-142">Comment out or delete the `For Each` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```vb  
    'Dim total = 0   
    'For Each url In urlList   
    '    ' GetByteArrayAsync returns a task. At completion, the task   
    '    ' produces a byte array.   
    '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)   
  
    '    ' The following two lines can replace the previous assignment statement.   
    '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)   
    '    'Dim urlContents As Byte() = Await getContentsTask   
  
    '    DisplayResults(url, urlContents)   
  
    '    ' Update the total.   
    '    total += urlContents.Length   
    'Next  
  
    ```  
  
3.  <span data-ttu-id="4fdd7-143">Definir um [consulta](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) que, quando executado pelo <xref:System.Linq.Enumerable.ToArray%2A>método cria uma coleção de tarefas que baixar o conteúdo de cada site.</xref:System.Linq.Enumerable.ToArray%2A></span><span class="sxs-lookup"><span data-stu-id="4fdd7-143">Define a [query](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="4fdd7-144">As tarefas são iniciadas quando a consulta é avaliada.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="4fdd7-145">Adicione o seguinte código ao método `SumPageSizesAsync` depois da declaração da `client` e `urlList`.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```vb  
    ' Create a query.  
    Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
        From url In urlList Select ProcessURLAsync(url, client)  
  
    ' Use ToArray to execute the query and start the download tasks.  
    Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
    ```  
  
4.  <span data-ttu-id="4fdd7-146">Em seguida, aplicar `Task.WhenAll` à coleção de tarefas, `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="4fdd7-147">`Task.WhenAll`Retorna uma única tarefa termina quando tem concluído todas as tarefas na coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="4fdd7-148">No exemplo a seguir, o `Await` expressão aguarda a conclusão do único de tarefa que `WhenAll` retorna.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-148">In the following example, the `Await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="4fdd7-149">Ao concluir, o `Await` expressão é avaliada como uma matriz de inteiros, onde cada inteiro é o comprimento de um site de download.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-149">When complete, the `Await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="4fdd7-150">Adicione o seguinte código para `SumPageSizesAsync`, apenas após o código que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```vb  
    ' Await the completion of all the running tasks.  
    Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
    '' The previous line is equivalent to the following two statements.  
    'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
    'Dim lengths As Integer() = Await whenAllTask  
    ```  
  
5.  <span data-ttu-id="4fdd7-151">Por fim, use o <xref:System.Linq.Enumerable.Sum%2A>método para obter a soma dos comprimentos de todos os sites.</xref:System.Linq.Enumerable.Sum%2A></span><span class="sxs-lookup"><span data-stu-id="4fdd7-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="4fdd7-152">Adicione a seguinte linha ao `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```vb  
    Dim total = lengths.Sum()  
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="4fdd7-153">Para testar as soluções Task. WhenAll</span><span class="sxs-lookup"><span data-stu-id="4fdd7-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="4fdd7-154">Para qualquer solução, escolha a tecla F5 para executar o programa e, em seguida, escolha o **iniciar** botão.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="4fdd7-155">A saída deve se parecer com a saída das soluções assíncronas em [passo a passo: acessando a Web, usando Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4fdd7-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="4fdd7-156">No entanto, observe que os sites da Web aparecem em uma ordem diferente cada vez.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fdd7-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4fdd7-157">Example</span></span>  
 <span data-ttu-id="4fdd7-158">O código a seguir mostra as extensões para o projeto que usa o `GetURLContentsAsync` método para baixar conteúdo da web.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.   
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        'Dim total = 0  
        'For Each url In urlList  
  
        '    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
        '    ' The previous line abbreviates the following two assignment statements.  
  
        '    ' GetURLContentsAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    ' The actions from the foreach loop are moved to this async method.  
    Private Async Function ProcessURLAsync(url As String) As Task(Of Integer)  
  
        Dim byteArray = Await GetURLContentsAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                ' CopyToAsync returns a Task, not a Task<T>.  
                Await responseStream.CopyToAsync(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
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
  
## <a name="example"></a><span data-ttu-id="4fdd7-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4fdd7-159">Example</span></span>  
 <span data-ttu-id="4fdd7-160">O código a seguir mostra as extensões para o projeto que usa o método `HttpClient.GetByteArrayAsync` para baixar o conteúdo da web.</span><span class="sxs-lookup"><span data-stu-id="4fdd7-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Create a query.  
        Dim downloadTasksQuery As IEnumerable(Of Task(Of Integer)) =  
            From url In urlList Select ProcessURLAsync(url, client)  
  
        ' Use ToArray to execute the query and start the download tasks.  
        Dim downloadTasks As Task(Of Integer)() = downloadTasksQuery.ToArray()  
  
        ' You can do other work here before awaiting.  
  
        ' Await the completion of all the running tasks.  
        Dim lengths As Integer() = Await Task.WhenAll(downloadTasks)  
  
        '' The previous line is equivalent to the following two statements.  
        'Dim whenAllTask As Task(Of Integer()) = Task.WhenAll(downloadTasks)  
        'Dim lengths As Integer() = Await whenAllTask  
  
        Dim total = lengths.Sum()  
  
        ''<snippet7>  
        'Dim total = 0  
        'For Each url In urlList  
        '    ' GetByteArrayAsync returns a task. At completion, the task  
        '    ' produces a byte array.  
        '    '<snippet31>  
        '    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
        '    '</snippet31>  
  
        '    ' The following two lines can replace the previous assignment statement.  
        '    'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
        '    'Dim urlContents As Byte() = Await getContentsTask  
  
        '    DisplayResults(url, urlContents)  
  
        '    ' Update the total.  
        '    total += urlContents.Length  
        'NextNext  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://www.msdn.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
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
  
## <a name="see-also"></a><span data-ttu-id="4fdd7-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4fdd7-161">See Also</span></span>  
 <span data-ttu-id="4fdd7-162"><xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="4fdd7-162"><xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="4fdd7-163"> [Passo a passo: Acessando a Web usando o Async e Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="4fdd7-163"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)</span></span>
