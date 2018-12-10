---
title: Como estender as instruções passo a passo assíncronas usando Task.WhenAll (C#)
ms.date: 07/20/2015
ms.assetid: f6927ef2-dc6c-43f8-bc82-bbeac42de423
ms.openlocfilehash: 66636476d0c76f26f87198bc58146e034bdad6af
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151107"
---
# <a name="how-to-extend-the-async-walkthrough-by-using-taskwhenall-c"></a><span data-ttu-id="d9c27-102">Como estender as instruções passo a passo assíncronas usando Task.WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="d9c27-102">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>
<span data-ttu-id="d9c27-103">Você pode melhorar o desempenho da solução assíncrona em [Passo a passo: acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md), usando o método <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d9c27-103">You can improve the performance of the async solution in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) by using the <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d9c27-104">Esse método aguarda de maneira assíncrona várias operações assíncronas, que são representadas como uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d9c27-104">This method asynchronously awaits multiple asynchronous operations, which are represented as a collection of tasks.</span></span>  
  
 <span data-ttu-id="d9c27-105">Você deve ter notado no passo a passo que os sites fazem o download em taxas diferentes.</span><span class="sxs-lookup"><span data-stu-id="d9c27-105">You might have noticed in the walkthrough that the websites download at different rates.</span></span> <span data-ttu-id="d9c27-106">Às vezes, um dos sites está muito lento e isso atrasa todos os downloads restantes.</span><span class="sxs-lookup"><span data-stu-id="d9c27-106">Sometimes one of the websites is very slow, which delays all the remaining downloads.</span></span> <span data-ttu-id="d9c27-107">Ao executar as soluções assíncronas que você compilou no passo a passo, você poderá finalizar o programa facilmente se não quiser esperar, mas uma opção melhor seria iniciar todos os downloads ao mesmo tempo e permitir que os downloads mais rápidos continuem, sem aguardar o que está atrasado.</span><span class="sxs-lookup"><span data-stu-id="d9c27-107">When you run the asynchronous solutions that you build in the walkthrough, you can end the program easily if you don't want to wait, but a better option would be to start all the downloads at the same time and let faster downloads continue without waiting for the one that’s delayed.</span></span>  
  
 <span data-ttu-id="d9c27-108">Você aplica o método `Task.WhenAll` a uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d9c27-108">You apply the `Task.WhenAll` method to a collection of tasks.</span></span> <span data-ttu-id="d9c27-109">A aplicação de `WhenAll` retorna uma única tarefa que não será concluída até a conclusão de cada tarefa na coleção.</span><span class="sxs-lookup"><span data-stu-id="d9c27-109">The application of `WhenAll` returns a single task that isn’t complete until every task in the collection is completed.</span></span> <span data-ttu-id="d9c27-110">As tarefas parecem ser executadas em paralelo, mas não são criados threads adicionais.</span><span class="sxs-lookup"><span data-stu-id="d9c27-110">The tasks appear to run in parallel, but no additional threads are created.</span></span> <span data-ttu-id="d9c27-111">As tarefas podem ser concluídas em qualquer ordem.</span><span class="sxs-lookup"><span data-stu-id="d9c27-111">The tasks can complete in any order.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d9c27-112">Os procedimentos a seguir descrevem as extensões para os aplicativos assíncronos que são desenvolvidos no [Passo a passo: acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="d9c27-112">The following procedures describe extensions to the async applications that are developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="d9c27-113">Você pode desenvolver os aplicativos concluindo o passo a passo ou baixando o código em [Exemplos de código para desenvolvedores](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span><span class="sxs-lookup"><span data-stu-id="d9c27-113">You can develop the applications by either completing the walkthrough or downloading the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>  
>   
>  <span data-ttu-id="d9c27-114">Para executar o exemplo, você deve ter o Visual Studio 2012 ou mais recente instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d9c27-114">To run the example, you must have Visual Studio 2012 or later installed on your computer.</span></span>  
  
### <a name="to-add-taskwhenall-to-your-geturlcontentsasync-solution"></a><span data-ttu-id="d9c27-115">Para adicionar o Task.WhenAll à sua solução GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="d9c27-115">To add Task.WhenAll to your GetURLContentsAsync solution</span></span>  
  
1.  <span data-ttu-id="d9c27-116">Adicione o método `ProcessURLAsync` ao primeiro aplicativo que é desenvolvido no [Passo a passo: acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="d9c27-116">Add the `ProcessURLAsync` method to the first application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="d9c27-117">Se você baixou o código de [Exemplos de código para desenvolvedores](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), abra o projeto AsyncWalkthrough e, em seguida, adicione `ProcessURLAsync` ao arquivo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d9c27-117">If you downloaded the code from  [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="d9c27-118">Se você desenvolveu o código ao concluir o passo a passo, adicione `ProcessURLAsync` ao aplicativo que inclui o método `GetURLContentsAsync`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-118">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that includes the `GetURLContentsAsync` method.</span></span> <span data-ttu-id="d9c27-119">O arquivo MainWindow.xaml.cs para este aplicativo é o primeiro exemplo da seção "Exemplos de código completos do passo a passo".</span><span class="sxs-lookup"><span data-stu-id="d9c27-119">The MainWindow.xaml.cs file for this application is the first example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="d9c27-120">O método `ProcessURLAsync` consolida as ações no corpo do loop `foreach` em `SumPageSizesAsync` no passo a passo original.</span><span class="sxs-lookup"><span data-stu-id="d9c27-120">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="d9c27-121">O método baixa de maneira assíncrona o conteúdo de um site especificado como uma matriz de bytes e, em seguida, exibe e retorna o comprimento da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="d9c27-121">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
    ```csharp  
    private async Task<int> ProcessURLAsync(string url)  
    {  
        var byteArray = await GetURLContentsAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="d9c27-122">Comente ou exclua o loop `foreach` em `SumPageSizesAsync`, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d9c27-122">Comment out or delete the `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    byte[] urlContents = await GetURLContentsAsync(url);  
  
    //    // The previous line abbreviates the following two assignment statements.  
    //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
    //    //byte[] urlContents = await getContentsTask;  
  
    //    DisplayResults(url, urlContents);  
  
    //    // Update the total.            
    //    total += urlContents.Length;  
    //}  
    ```  
  
3.  <span data-ttu-id="d9c27-123">Crie uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="d9c27-123">Create a collection of tasks.</span></span> <span data-ttu-id="d9c27-124">O código a seguir define uma [consulta](../../../../csharp/programming-guide/concepts/linq/index.md) que, quando executada pelo método <xref:System.Linq.Enumerable.ToArray%2A>, cria uma coleção de tarefas que baixa o conteúdo de cada site.</span><span class="sxs-lookup"><span data-stu-id="d9c27-124">The following code defines a [query](../../../../csharp/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="d9c27-125">As tarefas são iniciadas quando a consulta é avaliada.</span><span class="sxs-lookup"><span data-stu-id="d9c27-125">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="d9c27-126">Adicione o seguinte código ao método `SumPageSizesAsync` depois da declaração da `urlList`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-126">Add the following code to method `SumPageSizesAsync` after the declaration of `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.   
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="d9c27-127">Aplique `Task.WhenAll` à coleção de tarefas `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-127">Apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="d9c27-128">O `Task.WhenAll` retorna uma única tarefa que será terminada quando todas as tarefas na coleção de tarefas forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="d9c27-128">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="d9c27-129">No exemplo a seguir, a expressão `await` aguarda a conclusão da única tarefa que o `WhenAll` retorna.</span><span class="sxs-lookup"><span data-stu-id="d9c27-129">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="d9c27-130">A expressão é avaliada para uma matriz de inteiros, em que cada inteiro é o comprimento de um site baixado.</span><span class="sxs-lookup"><span data-stu-id="d9c27-130">The expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="d9c27-131">Adicione o seguinte código ao `SumPageSizesAsync`, logo após o código que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="d9c27-131">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="d9c27-132">Por fim, use o método <xref:System.Linq.Enumerable.Sum%2A> para calcular a soma dos comprimentos de todos os sites.</span><span class="sxs-lookup"><span data-stu-id="d9c27-132">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to calculate the sum of the lengths of all the websites.</span></span> <span data-ttu-id="d9c27-133">Adicione a seguinte linha ao `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-133">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();  
    ```  
  
### <a name="to-add-taskwhenall-to-the-httpclientgetbytearrayasync-solution"></a><span data-ttu-id="d9c27-134">Para adicionar o Task.WhenAll à solução HttpClient.GetByteArrayAsync</span><span class="sxs-lookup"><span data-stu-id="d9c27-134">To add Task.WhenAll to the HttpClient.GetByteArrayAsync solution</span></span>  
  
1.  <span data-ttu-id="d9c27-135">Adicione a seguinte versão de `ProcessURLAsync` ao segundo aplicativo que é desenvolvido no [Passo a passo: acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="d9c27-135">Add the following version of `ProcessURLAsync` to the second application that's developed in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="d9c27-136">Se você baixou o código de [Exemplos de código para desenvolvedores](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), abra o projeto AsyncWalkthrough_HttpClient e, em seguida, adicione `ProcessURLAsync` ao arquivo MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="d9c27-136">If you downloaded the code from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f), open the AsyncWalkthrough_HttpClient project, and then add `ProcessURLAsync` to the MainWindow.xaml.cs file.</span></span>  
  
    -   <span data-ttu-id="d9c27-137">Se você desenvolveu o código ao concluir o passo a passo, adicione `ProcessURLAsync` ao aplicativo que usa o método `HttpClient.GetByteArrayAsync`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-137">If you developed the code by completing the walkthrough, add `ProcessURLAsync` to the application that uses the `HttpClient.GetByteArrayAsync` method.</span></span> <span data-ttu-id="d9c27-138">O arquivo MainWindow.xaml.cs para este aplicativo é o segundo exemplo da seção "Exemplos de código completos do passo a passo".</span><span class="sxs-lookup"><span data-stu-id="d9c27-138">The MainWindow.xaml.cs file for this application is the second example in the "Complete Code Examples from the Walkthrough" section.</span></span>  
  
     <span data-ttu-id="d9c27-139">O método `ProcessURLAsync` consolida as ações no corpo do loop `foreach` em `SumPageSizesAsync` no passo a passo original.</span><span class="sxs-lookup"><span data-stu-id="d9c27-139">The `ProcessURLAsync` method consolidates the actions in the body of the `foreach` loop in `SumPageSizesAsync` in the original walkthrough.</span></span> <span data-ttu-id="d9c27-140">O método baixa de maneira assíncrona o conteúdo de um site especificado como uma matriz de bytes e, em seguida, exibe e retorna o comprimento da matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="d9c27-140">The method asynchronously downloads the contents of a specified website as a byte array, and then displays and returns the length of the byte array.</span></span>  
  
     <span data-ttu-id="d9c27-141">A única diferença do método `ProcessURLAsync` no procedimento anterior é o uso da instância <xref:System.Net.Http.HttpClient>, a `client`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-141">The only difference from the `ProcessURLAsync` method in the previous procedure is the use of the <xref:System.Net.Http.HttpClient> instance, `client`.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        byte[] byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
    }  
    ```  
  
2.  <span data-ttu-id="d9c27-142">Comente ou exclua o `For Each` ou o loop `foreach` em `SumPageSizesAsync`, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d9c27-142">Comment out or delete the `For Each` or `foreach` loop in `SumPageSizesAsync`, as the following code shows.</span></span>  
  
    ```csharp  
    //var total = 0;  
    //foreach (var url in urlList)  
    //{  
    //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
    //    // produces a byte array.  
    //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
    //    // The previous line abbreviates the following two assignment  
    //    // statements.  
    //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
    //    byte[] urlContent = await getContentTask;  
  
    //    DisplayResults(url, urlContent);  
  
    //    // Update the total.  
    //    total += urlContent.Length;  
    //}  
    ```  
  
3.  <span data-ttu-id="d9c27-143">Defina uma [consulta](../../../../csharp/programming-guide/concepts/linq/index.md) que, quando executada pelo método <xref:System.Linq.Enumerable.ToArray%2A>, cria uma coleção de tarefas que baixa o conteúdo de cada site.</span><span class="sxs-lookup"><span data-stu-id="d9c27-143">Define a [query](../../../../csharp/programming-guide/concepts/linq/index.md) that, when executed by the <xref:System.Linq.Enumerable.ToArray%2A> method, creates a collection of tasks that download the contents of each website.</span></span> <span data-ttu-id="d9c27-144">As tarefas são iniciadas quando a consulta é avaliada.</span><span class="sxs-lookup"><span data-stu-id="d9c27-144">The tasks are started when the query is evaluated.</span></span>  
  
     <span data-ttu-id="d9c27-145">Adicione o seguinte código ao método `SumPageSizesAsync` depois da declaração de `client` e `urlList`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-145">Add the following code to method `SumPageSizesAsync` after the declaration of `client` and `urlList`.</span></span>  
  
    ```csharp  
    // Create a query.  
    IEnumerable<Task<int>> downloadTasksQuery =   
        from url in urlList select ProcessURLAsync(url, client);  
  
    // Use ToArray to execute the query and start the download tasks.  
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="d9c27-146">Em seguida, aplique `Task.WhenAll` à coleção de tarefas `downloadTasks`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-146">Next, apply `Task.WhenAll` to the collection of tasks, `downloadTasks`.</span></span> <span data-ttu-id="d9c27-147">O `Task.WhenAll` retorna uma única tarefa que será terminada quando todas as tarefas na coleção de tarefas forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="d9c27-147">`Task.WhenAll` returns a single task that finishes when all the tasks in the collection of tasks have completed.</span></span>  
  
     <span data-ttu-id="d9c27-148">No exemplo a seguir, a expressão `await` aguarda a conclusão da única tarefa que o `WhenAll` retorna.</span><span class="sxs-lookup"><span data-stu-id="d9c27-148">In the following example, the `await` expression awaits the completion of the single task that `WhenAll` returns.</span></span> <span data-ttu-id="d9c27-149">Quando concluída, a expressão `await` é avaliada para uma matriz de inteiros, em que cada inteiro é o comprimento de um site baixado.</span><span class="sxs-lookup"><span data-stu-id="d9c27-149">When complete, the `await` expression evaluates to an array of integers, where each integer is the length of a downloaded website.</span></span> <span data-ttu-id="d9c27-150">Adicione o seguinte código ao `SumPageSizesAsync`, logo após o código que você adicionou na etapa anterior.</span><span class="sxs-lookup"><span data-stu-id="d9c27-150">Add the following code to `SumPageSizesAsync`, just after the code that you added in the previous step.</span></span>  
  
    ```csharp  
    // Await the completion of all the running tasks.  
    int[] lengths = await Task.WhenAll(downloadTasks);  
  
    //// The previous line is equivalent to the following two statements.  
    //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
    //int[] lengths = await whenAllTask;  
    ```  
  
5.  <span data-ttu-id="d9c27-151">Por fim, use o método <xref:System.Linq.Enumerable.Sum%2A> para obter a soma dos comprimentos de todos os sites.</span><span class="sxs-lookup"><span data-stu-id="d9c27-151">Finally, use the <xref:System.Linq.Enumerable.Sum%2A> method to get the sum of the lengths of all the websites.</span></span> <span data-ttu-id="d9c27-152">Adicione a seguinte linha ao `SumPageSizesAsync`.</span><span class="sxs-lookup"><span data-stu-id="d9c27-152">Add the following line to `SumPageSizesAsync`.</span></span>  
  
    ```csharp  
    int total = lengths.Sum();
    ```  
  
### <a name="to-test-the-taskwhenall-solutions"></a><span data-ttu-id="d9c27-153">Para testar as soluções Task.WhenAll</span><span class="sxs-lookup"><span data-stu-id="d9c27-153">To test the Task.WhenAll solutions</span></span>  
  
-   <span data-ttu-id="d9c27-154">Para qualquer uma das soluções, escolha a tecla F5 para executar o programa e, em seguida, escolha o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="d9c27-154">For either solution, choose the F5 key to run the program, and then choose the **Start** button.</span></span> <span data-ttu-id="d9c27-155">A saída deve ser parecida com a saída das soluções assíncronas em [Passo a passo: acessando a Web usando async e await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="d9c27-155">The output should resemble the output from the async solutions in [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="d9c27-156">No entanto, observe que os sites aparecem em uma ordem diferente a cada vez.</span><span class="sxs-lookup"><span data-stu-id="d9c27-156">However, notice that the websites appear in a different order each time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c27-157">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9c27-157">Example</span></span>  
 <span data-ttu-id="d9c27-158">O código a seguir mostra as extensões para o projeto que usa o método `GetURLContentsAsync` para baixar conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="d9c27-158">The following code shows the extensions to the project that uses the `GetURLContentsAsync` method to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // Two-step async call.  
            Task sumTask = SumPageSizesAsync();  
            await sumTask;  
  
            // One-step async call.  
            //await SumPageSizesAsync();  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Create a query.   
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    byte[] urlContents = await GetURLContentsAsync(url);  
  
            //    // The previous line abbreviates the following two assignment statements.  
            //    // GetURLContentsAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);  
            //    //byte[] urlContents = await getContentsTask;  
  
            //    DisplayResults(url, urlContents);  
  
            //    // Update the total.            
            //    total += urlContents.Length;  
            //}  
  
            // Display the total count for all of the websites.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        private async Task<int> ProcessURLAsync(string url)  
        {  
            var byteArray = await GetURLContentsAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private async Task<byte[]> GetURLContentsAsync(string url)  
        {  
            // The downloaded resource ends up in the variable named content.  
            var content = new MemoryStream();  
  
            // Initialize an HttpWebRequest for the current URL.  
            var webReq = (HttpWebRequest)WebRequest.Create(url);  
  
            // Send the request to the Internet resource and wait for  
            // the response.  
            using (WebResponse response = await webReq.GetResponseAsync())  
            {  
                // Get the data stream that is associated with the specified url.  
                using (Stream responseStream = response.GetResponseStream())  
                {  
                    await responseStream.CopyToAsync(content);  
                }  
            }  
  
            // Return the result as a byte array.  
            return content.ToArray();  
  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each website. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }
    }  
}  
```  
  
## <a name="example"></a><span data-ttu-id="d9c27-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9c27-159">Example</span></span>  
 <span data-ttu-id="d9c27-160">O código a seguir mostra as extensões para o projeto que usa o método `HttpClient.GetByteArrayAsync` para baixar conteúdo da Web.</span><span class="sxs-lookup"><span data-stu-id="d9c27-160">The following code shows the extensions to the project that uses method `HttpClient.GetByteArrayAsync` to download content from the web.</span></span>  
  
```csharp  
// Add the following using directives, and add a reference for System.Net.Http.  
using System.Net.Http;  
using System.IO;  
using System.Net;  
  
namespace AsyncExampleWPF_HttpClient_WhenAll  
{  
    public partial class MainWindow : Window  
    {  
        public MainWindow()  
        {  
            InitializeComponent();  
        }  
  
        private async void startButton_Click(object sender, RoutedEventArgs e)  
        {  
            resultsTextBox.Clear();  
  
            // One-step async call.  
            await SumPageSizesAsync();  
  
            // Two-step async call.  
            //Task sumTask = SumPageSizesAsync();  
            //await sumTask;  
  
            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task SumPageSizesAsync()  
        {  
            // Make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // Declare an HttpClient object and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client = new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create a query.  
            IEnumerable<Task<int>> downloadTasksQuery =   
                from url in urlList select ProcessURLAsync(url, client);  
  
            // Use ToArray to execute the query and start the download tasks.  
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // You can do other work here before awaiting.  
  
            // Await the completion of all the running tasks.  
            int[] lengths = await Task.WhenAll(downloadTasks);  
  
            //// The previous line is equivalent to the following two statements.  
            //Task<int[]> whenAllTask = Task.WhenAll(downloadTasks);  
            //int[] lengths = await whenAllTask;  
  
            int total = lengths.Sum();  
  
            //var total = 0;  
            //foreach (var url in urlList)  
            //{  
            //    // GetByteArrayAsync returns a Task<T>. At completion, the task  
            //    // produces a byte array.  
            //    byte[] urlContent = await client.GetByteArrayAsync(url);  
  
            //    // The previous line abbreviates the following two assignment  
            //    // statements.  
            //    Task<byte[]> getContentTask = client.GetByteArrayAsync(url);  
            //    byte[] urlContent = await getContentTask;  
  
            //    DisplayResults(url, urlContent);  
  
            //    // Update the total.  
            //    total += urlContent.Length;  
            //}  
  
            // Display the total count for all of the web addresses.  
            resultsTextBox.Text +=  
                $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290136.aspx",  
                "https://msdn.microsoft.com/library/ee256749.aspx",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
  
        // The actions from the foreach loop are moved to this async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            byte[] byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
        }  
  
        private void DisplayResults(string url, byte[] content)  
        {  
            // Display the length of each web site. The string format   
            // is designed to be used with a monospaced font, such as  
            // Lucida Console or Global Monospace.  
            var bytes = content.Length;  
            // Strip off the "https://".  
            var displayURL = url.Replace("https://", "");  
            resultsTextBox.Text += $"\n{displayURL,-58} {bytes,8}";
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9c27-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9c27-161">See Also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="d9c27-162">Passo a passo: acessando a Web e usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="d9c27-162">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
