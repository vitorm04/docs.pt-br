---
title: Processar tarefas assíncronas conforme elas são concluídas
ms.date: 09/12/2018
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: ec5729eaa8d63eb18b1ac4dea5820cbf834d001b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152352"
---
# <a name="start-multiple-async-tasks-and-process-them-as-they-complete-c"></a><span data-ttu-id="bd4a8-102">Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)</span><span class="sxs-lookup"><span data-stu-id="bd4a8-102">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>

<span data-ttu-id="bd4a8-103">Usando <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, você pode iniciar várias tarefas ao mesmo tempo e processá-las individualmente conforme elas foram concluídas, em vez de processá-las na ordem em que foram iniciadas.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-103">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they’re completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="bd4a8-104">O exemplo a seguir usa uma consulta para criar uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-104">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="bd4a8-105">Cada tarefa baixa o conteúdo de um site especificado.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-105">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="bd4a8-106">Em cada iteração de um loop "while", uma chamada esperada para `WhenAny` retorna a tarefa na coleção de tarefas que concluir o download primeiro.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-106">In each iteration of a while loop, an awaited call to `WhenAny` returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="bd4a8-107">Essa tarefa é removida da coleção e processada.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-107">That task is removed from the collection and processed.</span></span> <span data-ttu-id="bd4a8-108">O loop é repetido até que a coleção não contenha mais tarefas.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-108">The loop repeats until the collection contains no more tasks.</span></span>

> [!NOTE]
> <span data-ttu-id="bd4a8-109">Para executar os exemplos, você precisa ter o Visual Studio (2012 ou mais recente) e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-109">To run the examples, you must have Visual Studio (2012 or newer) and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="download-an-example-solution"></a><span data-ttu-id="bd4a8-110">Baixar um exemplo de solução</span><span class="sxs-lookup"><span data-stu-id="bd4a8-110">Download an example solution</span></span>

<span data-ttu-id="bd4a8-111">Você pode baixar o projeto completo do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) e, em seguida, seguir estas etapas.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea) and then follow these steps.</span></span>

> [!TIP]
> <span data-ttu-id="bd4a8-112">Se você não quiser baixar o projeto, poderá examinar o arquivo MainWindow.xaml.cs no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-112">If you don't want to download the project, you can review the MainWindow.xaml.cs file at the end of this topic instead.</span></span>

1.  <span data-ttu-id="bd4a8-113">Extraia os arquivos baixados do arquivo .zip e, em seguida, inicie o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-113">Extract the files that you downloaded from the .zip file, and then start Visual Studio.</span></span>

2.  <span data-ttu-id="bd4a8-114">Na barra de menus, escolha **Arquivo** > **Abrir** > **Projeto/Solução**.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-114">On the menu bar, choose **File** > **Open** > **Project/Solution**.</span></span>

3.  <span data-ttu-id="bd4a8-115">Na caixa de diálogo **Abrir Projeto**, abra a pasta em que está o código de exemplo que você baixou e, em seguida, abra o arquivo de solução (.sln) de AsyncFineTuningCS.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-115">In the **Open Project** dialog box, open the folder that holds the sample code you downloaded, and then open the solution (.sln) file for AsyncFineTuningCS.</span></span>

4.  <span data-ttu-id="bd4a8-116">No **Gerenciador de Soluções**, abra o menu de atalho do projeto **ProcessTasksAsTheyFinish** e escolha **Definir como Projeto de Inicialização**.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-116">In **Solution Explorer**, open the shortcut menu for the **ProcessTasksAsTheyFinish** project, and then choose **Set as StartUp Project**.</span></span>

5.  <span data-ttu-id="bd4a8-117">Escolha a tecla **F5** para executar o programa (ou pressione as teclas **Ctrl**+**F5** para executar o programa sem depurá-lo).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-117">Choose the **F5** key to run the program (or, press **Ctrl**+**F5** keys to run the program without debugging it).</span></span>

6.  <span data-ttu-id="bd4a8-118">Execute o projeto várias vezes para verificar se os tamanhos baixados não aparecem sempre na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-118">Run the project several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

## <a name="create-the-program-yourself"></a><span data-ttu-id="bd4a8-119">Crie o programa sozinho</span><span class="sxs-lookup"><span data-stu-id="bd4a8-119">Create the program yourself</span></span>

<span data-ttu-id="bd4a8-120">Este exemplo adiciona ao código que é desenvolvido em [Cancelar tarefas assíncronas restantes após uma ser concluída (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) e usa a mesma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-120">This example adds to the code that’s developed in [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md), and it uses the same UI.</span></span>

<span data-ttu-id="bd4a8-121">Para compilar o exemplo por conta própria, passo a passo, siga as instruções na seção [Baixando o exemplo](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example), mas defina **CancelAfterOneTask** como o projeto de inicialização.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-121">To build the example yourself, step by step, follow the instructions in the [Downloading the Example](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md#downloading-the-example) section, but set **CancelAfterOneTask** as the startup project.</span></span> <span data-ttu-id="bd4a8-122">Adicione as alterações neste tópico ao método `AccessTheWebAsync` naquele projeto.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-122">Add the changes in this topic to the `AccessTheWebAsync` method in that project.</span></span> <span data-ttu-id="bd4a8-123">As alterações estão marcadas com asteriscos.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-123">The changes are marked with asterisks.</span></span>

<span data-ttu-id="bd4a8-124">O projeto **CancelAfterOneTask** já inclui uma consulta que, quando executada, cria uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-124">The **CancelAfterOneTask** project already includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="bd4a8-125">Cada chamada para `ProcessURLAsync` no código a seguir retorna um <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-125">Each call to `ProcessURLAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery = from url in urlList select ProcessURL(url, client, ct);
```

<span data-ttu-id="bd4a8-126">No arquivo MainWindow.xaml.cs do projeto, faça as seguintes alterações ao método `AccessTheWebAsync`.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-126">In the MainWindow.xaml.cs file of the project, make the following changes to the `AccessTheWebAsync` method.</span></span>

-   <span data-ttu-id="bd4a8-127">Execute a consulta aplicando <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> em vez de <xref:System.Linq.Enumerable.ToArray%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-127">Execute the query by applying <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> instead of <xref:System.Linq.Enumerable.ToArray%2A>.</span></span>

    ```csharp
    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
    ```

-   <span data-ttu-id="bd4a8-128">Adicione um loop `while` que executa as seguintes etapas para cada tarefa na coleção:</span><span class="sxs-lookup"><span data-stu-id="bd4a8-128">Add a `while` loop that performs the following steps for each task in the collection:</span></span>

    1.  <span data-ttu-id="bd4a8-129">Espera uma chamada para `WhenAny` para identificar a primeira tarefa na coleção a concluir o download.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-129">Awaits a call to `WhenAny` to identify the first task in the collection to finish its download.</span></span>

        ```csharp
        Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
        ```

    2.  <span data-ttu-id="bd4a8-130">Remove a tarefa da coleção.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-130">Removes that task from the collection.</span></span>

        ```csharp
        downloadTasks.Remove(firstFinishedTask);
        ```

    3.  <span data-ttu-id="bd4a8-131">Espera `firstFinishedTask`, que é retornado por uma chamada para `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-131">Awaits `firstFinishedTask`, which is returned by a call to `ProcessURLAsync`.</span></span> <span data-ttu-id="bd4a8-132">A variável `firstFinishedTask` é uma <xref:System.Threading.Tasks.Task%601> em que `TReturn` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-132">The `firstFinishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TReturn` is an integer.</span></span> <span data-ttu-id="bd4a8-133">A tarefa já foi concluída, mas você espera para recuperar o tamanho do site baixado, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-133">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span>

        ```csharp
        int length = await firstFinishedTask;
        resultsTextBox.Text += $"\r\nLength of the download:  {length}";
        ```

<span data-ttu-id="bd4a8-134">Execute o programa várias vezes para verificar se os tamanhos baixados não aparecem sempre na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-134">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="bd4a8-135">Você pode usar `WhenAny` em um loop, conforme descrito no exemplo, para resolver problemas que envolvem um número pequeno de tarefas.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-135">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="bd4a8-136">No entanto, outras abordagens são mais eficientes se você tiver um número grande de tarefas para processar.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-136">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="bd4a8-137">Para obter mais informações e exemplos, consulte [Processando tarefas quando elas são concluídas](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-137">For more information and examples, see [Processing tasks as they complete](https://blogs.msdn.microsoft.com/pfxteam/2012/08/02/processing-tasks-as-they-complete/).</span></span>

## <a name="complete-example"></a><span data-ttu-id="bd4a8-138">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="bd4a8-138">Complete example</span></span>

<span data-ttu-id="bd4a8-139">O código a seguir é o texto completo do arquivo MainWindow.xaml.cs para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-139">The following code is the complete text of the MainWindow.xaml.cs file for the example.</span></span> <span data-ttu-id="bd4a8-140">Os asteriscos marcam os elementos que foram adicionados para esse exemplo.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-140">Asterisks mark the elements that were added for this example.</span></span> <span data-ttu-id="bd4a8-141">Além disso, observe que você deve adicionar uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="bd4a8-141">Also, take note that you must add a reference for <xref:System.Net.Http>.</span></span>

<span data-ttu-id="bd4a8-142">Você pode baixar o projeto de [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="bd4a8-142">You can download the project from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>

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

namespace ProcessTasksAsTheyFinish
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
            resultsTextBox.Clear();

            // Instantiate the CancellationTokenSource.
            cts = new CancellationTokenSource();

            try
            {
                await AccessTheWebAsync(cts.Token);
                resultsTextBox.Text += "\r\nDownloads complete.";
            }
            catch (OperationCanceledException)
            {
                resultsTextBox.Text += "\r\nDownloads canceled.\r\n";
            }
            catch (Exception)
            {
                resultsTextBox.Text += "\r\nDownloads failed.\r\n";
            }

            cts = null;
        }

        private void cancelButton_Click(object sender, RoutedEventArgs e)
        {
            if (cts != null)
            {
                cts.Cancel();
            }
        }

        async Task AccessTheWebAsync(CancellationToken ct)
        {
            HttpClient client = new HttpClient();

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            // ***Create a query that, when executed, returns a collection of tasks.
            IEnumerable<Task<int>> downloadTasksQuery =
                from url in urlList select ProcessURL(url, client, ct);

            // ***Use ToList to execute the query and start the tasks.
            List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

            // ***Add a loop to process the tasks one at a time until none remain.
            while (downloadTasks.Count > 0)
            {
                    // Identify the first task that completes.
                    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);

                    // ***Remove the selected task from the list so that you don't
                    // process it more than once.
                    downloadTasks.Remove(firstFinishedTask);

                    // Await the completed task.
                    int length = await firstFinishedTask;
                    resultsTextBox.Text += $"\r\nLength of the download:  {length}";
            }
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
            {
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            };
            return urls;
        }

        async Task<int> ProcessURL(string url, HttpClient client, CancellationToken ct)
        {
            // GetAsync returns a Task<HttpResponseMessage>.
            HttpResponseMessage response = await client.GetAsync(url, ct);

            // Retrieve the website contents from the HttpResponseMessage.
            byte[] urlContents = await response.Content.ReadAsByteArrayAsync();

            return urlContents.Length;
        }
    }
}

// Sample Output:

// Length of the download:  226093
// Length of the download:  412588
// Length of the download:  175490
// Length of the download:  204890
// Length of the download:  158855
// Length of the download:  145790
// Length of the download:  44908
// Downloads complete.
```

## <a name="see-also"></a><span data-ttu-id="bd4a8-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd4a8-143">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="bd4a8-144">Ajuste fino de seu aplicativo assíncrono (C#)</span><span class="sxs-lookup"><span data-stu-id="bd4a8-144">Fine-Tuning Your Async Application (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)
- [<span data-ttu-id="bd4a8-145">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="bd4a8-145">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="bd4a8-146">Exemplo de assincronia: ajuste fino de seu aplicativo</span><span class="sxs-lookup"><span data-stu-id="bd4a8-146">Async Sample: Fine Tuning Your Application</span></span>](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)