---
title: Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)
ms.date: 07/20/2015
ms.assetid: d3cebc74-c392-497b-b1e6-62a262eabe05
ms.openlocfilehash: 969309f50f59a413e731113b6daec0c32bd1b540
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126908"
---
# <a name="cancel-remaining-async-tasks-after-one-is-complete-c"></a><span data-ttu-id="cf730-102">Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)</span><span class="sxs-lookup"><span data-stu-id="cf730-102">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>
<span data-ttu-id="cf730-103">Usando o método <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> juntamente com um <xref:System.Threading.CancellationToken>, você pode cancelar todas as tarefas restantes quando uma tarefa é concluída.</span><span class="sxs-lookup"><span data-stu-id="cf730-103">By using the <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> method together with a <xref:System.Threading.CancellationToken>, you can cancel all remaining tasks when one task is complete.</span></span> <span data-ttu-id="cf730-104">O método `WhenAny` leva um argumento que é uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf730-104">The `WhenAny` method takes an argument that’s a collection of tasks.</span></span> <span data-ttu-id="cf730-105">O método inicia todas as tarefas e retorna uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="cf730-105">The method starts all the tasks and returns a single task.</span></span> <span data-ttu-id="cf730-106">A tarefa única será concluída quando qualquer tarefa na coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="cf730-106">The single task is complete when any task in the collection is complete.</span></span>  
  
 <span data-ttu-id="cf730-107">Este exemplo demonstra como usar um token de cancelamento em conjunto com `WhenAny` para aguardar na primeira tarefa que for finalizada na coleção de tarefas e para cancelar as tarefas restantes.</span><span class="sxs-lookup"><span data-stu-id="cf730-107">This example demonstrates how to use a cancellation token in conjunction with `WhenAny` to hold onto the first task to finish from the collection of tasks and to cancel the remaining tasks.</span></span> <span data-ttu-id="cf730-108">Cada tarefa baixa o conteúdo de um site.</span><span class="sxs-lookup"><span data-stu-id="cf730-108">Each task downloads the contents of a website.</span></span> <span data-ttu-id="cf730-109">O exemplo exibe o comprimento do conteúdo do primeiro download que é concluído e cancela os outros downloads.</span><span class="sxs-lookup"><span data-stu-id="cf730-109">The example displays the length of the contents of the first download to complete and cancels the other downloads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cf730-110">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="cf730-110">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="cf730-111">Baixando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf730-111">Downloading the Example</span></span>  
 <span data-ttu-id="cf730-112">Você pode baixar o projeto completo do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, seguir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="cf730-112">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="cf730-113">Descompacte o arquivo baixado e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="cf730-113">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="cf730-114">Na barra de menus, escolha **Arquivo**, **Abrir**, **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="cf730-114">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="cf730-115">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você descompactou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="cf730-115">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>  
  
4.  <span data-ttu-id="cf730-116">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **CancelAfterOneTask** e, em seguida, escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="cf730-116">In **Solution Explorer**, open the shortcut menu for the **CancelAfterOneTask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="cf730-117">Escolha a tecla F5 para executar o projeto.</span><span class="sxs-lookup"><span data-stu-id="cf730-117">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="cf730-118">Escolha as teclas CTRL+F5 para executar o projeto sem depurá-lo.</span><span class="sxs-lookup"><span data-stu-id="cf730-118">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="cf730-119">Execute o programa várias vezes para verificar que diferentes downloads são concluídos em primeiro.</span><span class="sxs-lookup"><span data-stu-id="cf730-119">Run the program several times to verify that different downloads finish first.</span></span>  
  
 <span data-ttu-id="cf730-120">Se você não quiser baixar o projeto, você poderá examinar o arquivo MainWindow.xaml.cs no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="cf730-120">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="cf730-121">Compilando o Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf730-121">Building the Example</span></span>  
 <span data-ttu-id="cf730-122">O exemplo neste tópico adiciona ao projeto que é desenvolvido em [Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) para cancelar uma lista de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf730-122">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="cf730-123">O exemplo usa a mesma interface do usuário, embora o botão **Cancelar** não seja explicitamente usado.</span><span class="sxs-lookup"><span data-stu-id="cf730-123">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="cf730-124">Para compilar o exemplo você mesmo, passo a passo, siga as instruções na seção "Baixando o exemplo", mas escolha **CancelAListOfTasks** como o **Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="cf730-124">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="cf730-125">Adicione as alterações deste tópico ao projeto.</span><span class="sxs-lookup"><span data-stu-id="cf730-125">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="cf730-126">No arquivo MainWindow.xaml.cs do projeto **CancelAListOfTasks**, inicie a transição, movendo as etapas de processamento de cada site do loop em `AccessTheWebAsync` para o seguinte método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="cf730-126">In the MainWindow.xaml.cs file of the **CancelAListOfTasks** project, start the transition by moving the processing steps for each website from the loop in `AccessTheWebAsync` to the following async method.</span></span>  
  
```csharp  
/ ***Bundle the processing steps for a website into one async method.  
async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
{  
    // GetAsync returns a Task<HttpResponseMessage>.   
    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
    // Retrieve the website contents from the HttpResponseMessage.  
    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
    return urlContents.Length;  
}  
```  
  
 <span data-ttu-id="cf730-127">Em `AccessTheWebAsync`, este exemplo usa uma consulta, o método <xref:System.Linq.Enumerable.ToArray%2A> e o método `WhenAny` para criar e iniciar uma matriz de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf730-127">In `AccessTheWebAsync`, this example uses a query, the  <xref:System.Linq.Enumerable.ToArray%2A> method, and the `WhenAny` method to create and start an array of tasks.</span></span> <span data-ttu-id="cf730-128">A aplicação de `WhenAny` à matriz retorna uma única tarefa que, quando colocada em espera, resulta na primeira tarefa a alcançar a conclusão na matriz de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf730-128">The application of `WhenAny` to the array returns a single task that, when awaited, evaluates to the first task to reach completion in the array of tasks.</span></span>  
  
 <span data-ttu-id="cf730-129">Faça as seguintes alterações em `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="cf730-129">Make the following changes in `AccessTheWebAsync`.</span></span> <span data-ttu-id="cf730-130">Os asteriscos marcam as alterações no arquivo de código.</span><span class="sxs-lookup"><span data-stu-id="cf730-130">Asterisks mark the changes in the code file.</span></span>  
  
1.  <span data-ttu-id="cf730-131">Comente ou exclua o loop.</span><span class="sxs-lookup"><span data-stu-id="cf730-131">Comment out or delete the loop.</span></span>  
  
2.  <span data-ttu-id="cf730-132">Crie uma consulta que, quando executada, produz uma coleção de tarefas genéricas.</span><span class="sxs-lookup"><span data-stu-id="cf730-132">Create a query that, when executed, produces a collection of generic tasks.</span></span> <span data-ttu-id="cf730-133">Cada chamada para `ProcessURLAsync` retorna um <xref:System.Threading.Tasks.Task%601> em que `TResult` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="cf730-133">Each call to `ProcessURLAsync` returns a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span>  
  
    ```csharp  
    // ***Create a query that, when executed, returns a collection of tasks.  
    IEnumerable<Task<int>> downloadTasksQuery =  
        from url in urlList select ProcessURLAsync(url, client, ct);  
    ```  
  
3.  <span data-ttu-id="cf730-134">Chame `ToArray` para executar a consulta e iniciar as tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf730-134">Call `ToArray` to execute the query and start the tasks.</span></span> <span data-ttu-id="cf730-135">A aplicação do método `WhenAny` na próxima etapa executaria a consulta e iniciaria as tarefas sem usar `ToArray`, mas outros métodos podem não fazê-lo.</span><span class="sxs-lookup"><span data-stu-id="cf730-135">The application of the `WhenAny` method in the next step would execute the query and start the tasks without using `ToArray`, but other methods might not.</span></span> <span data-ttu-id="cf730-136">A prática mais segura é forçar a execução da consulta explicitamente.</span><span class="sxs-lookup"><span data-stu-id="cf730-136">The safest practice is to force execution of the query explicitly.</span></span>  
  
    ```csharp  
    // ***Use ToArray to execute the query and start the download tasks.   
    Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
    ```  
  
4.  <span data-ttu-id="cf730-137">Chame `WhenAny` na coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cf730-137">Call `WhenAny` on the collection of tasks.</span></span> <span data-ttu-id="cf730-138">`WhenAny` retorna um `Task(Of Task(Of Integer))` ou `Task<Task<int>>`.</span><span class="sxs-lookup"><span data-stu-id="cf730-138">`WhenAny` returns a `Task(Of Task(Of Integer))` or `Task<Task<int>>`.</span></span>  <span data-ttu-id="cf730-139">Ou seja, `WhenAny` retorna uma tarefa que resulta em uma única `Task(Of Integer)` ou `Task<int>` quando é esperada.</span><span class="sxs-lookup"><span data-stu-id="cf730-139">That is, `WhenAny` returns a task that evaluates to a single `Task(Of Integer)` or `Task<int>` when it’s awaited.</span></span> <span data-ttu-id="cf730-140">Essa tarefa única é a primeira tarefa na coleção a ser concluída.</span><span class="sxs-lookup"><span data-stu-id="cf730-140">That single task is the first task in the collection to finish.</span></span> <span data-ttu-id="cf730-141">A tarefa que foi concluída em primeiro é atribuída a `firstFinishedTask`.</span><span class="sxs-lookup"><span data-stu-id="cf730-141">The task that finished first is assigned to `firstFinishedTask`.</span></span> <span data-ttu-id="cf730-142">O tipo de `firstFinishedTask` é <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro, porque esse é o tipo de retorno de `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="cf730-142">The type of `firstFinishedTask` is <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer because that's the return type of `ProcessURLAsync`.</span></span>  
  
    ```csharp  
    // ***Call WhenAny and then await the result. The task that finishes   
    // first is assigned to firstFinishedTask.  
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
    ```  
  
5.  <span data-ttu-id="cf730-143">Neste exemplo, você está interessado apenas na tarefa que termina primeiro.</span><span class="sxs-lookup"><span data-stu-id="cf730-143">In this example, you’re interested only in the task that finishes first.</span></span> <span data-ttu-id="cf730-144">Portanto, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> para cancelar as tarefas restantes.</span><span class="sxs-lookup"><span data-stu-id="cf730-144">Therefore, use <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> to cancel the remaining tasks.</span></span>  
  
    ```csharp  
    // ***Cancel the rest of the downloads. You just want the first one.  
    cts.Cancel();  
    ```  
  
6.  <span data-ttu-id="cf730-145">Por fim, aguarde que `firstFinishedTask` recupere o comprimento do conteúdo baixado.</span><span class="sxs-lookup"><span data-stu-id="cf730-145">Finally, await `firstFinishedTask` to retrieve the length of the downloaded content.</span></span>  
  
    ```csharp  
    var length = await firstFinishedTask;  
    resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
    ```  
  
 <span data-ttu-id="cf730-146">Execute o programa várias vezes para verificar que diferentes downloads são concluídos em primeiro.</span><span class="sxs-lookup"><span data-stu-id="cf730-146">Run the program several times to verify that different downloads finish first.</span></span>  
  
## <a name="complete-example"></a><span data-ttu-id="cf730-147">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="cf730-147">Complete Example</span></span>  
 <span data-ttu-id="cf730-148">O código a seguir é o arquivo MainWindow.xaml.cs completo para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="cf730-148">The following code is the complete MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="cf730-149">Os asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="cf730-149">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="cf730-150">Observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="cf730-150">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="cf730-151">Você pode baixar o projeto de [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="cf730-151">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
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
  
// Add the following using directive.  
using System.Threading;  
  
namespace CancelAfterOneTask  
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
                resultsTextBox.Text += "\r\nDownload complete.";  
            }  
            catch (OperationCanceledException)  
            {  
                resultsTextBox.Text += "\r\nDownload canceled.";  
            }  
            catch (Exception)  
            {  
                resultsTextBox.Text += "\r\nDownload failed.";  
            }  
  
            // Set the CancellationTokenSource to null when the download is complete.  
            cts = null;  
        }  
  
        // You can still include a Cancel button if you want to.  
        private void cancelButton_Click(object sender, RoutedEventArgs e)  
        {  
            if (cts != null)  
            {  
                cts.Cancel();  
            }  
        }  
  
        // Provide a parameter for the CancellationToken.  
        async Task AccessTheWebAsync(CancellationToken ct)  
        {  
            HttpClient client = new HttpClient();  
  
            // Call SetUpURLList to make a list of web addresses.  
            List<string> urlList = SetUpURLList();  
  
            // ***Comment out or delete the loop.  
            //foreach (var url in urlList)  
            //{  
            //    // GetAsync returns a Task<HttpResponseMessage>.   
            //    // Argument ct carries the message if the Cancel button is chosen.   
            //    // ***Note that the Cancel button can cancel all remaining downloads.  
            //    HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            //    // Retrieve the website contents from the HttpResponseMessage.  
            //    byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            //    resultsTextBox.Text +=  
            //        $"\r\nLength of the downloaded string: {urlContents.Length}.\r\n";
            //}  
  
            // ***Create a query that, when executed, returns a collection of tasks.  
            IEnumerable<Task<int>> downloadTasksQuery =  
                from url in urlList select ProcessURLAsync(url, client, ct);  
  
            // ***Use ToArray to execute the query and start the download tasks.   
            Task<int>[] downloadTasks = downloadTasksQuery.ToArray();  
  
            // ***Call WhenAny and then await the result. The task that finishes   
            // first is assigned to firstFinishedTask.  
            Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);  
  
            // ***Cancel the rest of the downloads. You just want the first one.  
            cts.Cancel();  
  
            // ***Await the first completed task and display the results.   
            // Run the program several times to demonstrate that different  
            // websites can finish first.  
            var length = await firstFinishedTask;  
            resultsTextBox.Text += $"\r\nLength of the downloaded website:  {length}\r\n";
        }  
  
        // ***Bundle the processing steps for a website into one async method.  
        async Task<int> ProcessURLAsync(string url, HttpClient client, CancellationToken ct)  
        {  
            // GetAsync returns a Task<HttpResponseMessage>.   
            HttpResponseMessage response = await client.GetAsync(url, ct);  
  
            // Retrieve the website contents from the HttpResponseMessage.  
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();  
  
            return urlContents.Length;  
        }  
  
        // Add a method that creates a list of web addresses.  
        private List<string> SetUpURLList()  
        {  
            List<string> urls = new List<string>   
            {   
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/hh290138.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/dd470362.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            };  
            return urls;  
        }  
    }  
    // Sample output:  
  
    // Length of the downloaded website:  158856  
  
    // Download complete.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf730-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf730-152">See Also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>  
- [<span data-ttu-id="cf730-153">Ajuste fino de seu aplicativo assíncrono (C#)</span><span class="sxs-lookup"><span data-stu-id="cf730-153">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)  
- [<span data-ttu-id="cf730-154">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="cf730-154">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
- [<span data-ttu-id="cf730-155">Exemplo de assincronia: ajuste fino de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="cf730-155">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)
