---
title: Como fazer várias solicitações da Web em paralelo usando Async e Await (C#)
description: Saiba como separar a criação de uma tarefa usando o operador Await em C#, em vez de aplicá-la quando uma tarefa é criada.
ms.date: 07/20/2015
ms.assetid: 19745899-f97a-4499-a7c7-e813d1447580
ms.openlocfilehash: 899dfd9165d199a67a5178bb351081ee544b231f
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925157"
---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-c"></a><span data-ttu-id="9f144-103">Como fazer várias solicitações da Web em paralelo usando Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="9f144-103">How to make multiple web requests in parallel by using async and await (C#)</span></span>
<span data-ttu-id="9f144-104">Em um método assíncrono, as tarefas são iniciadas quando são criadas.</span><span class="sxs-lookup"><span data-stu-id="9f144-104">In an async method, tasks are started when they're created.</span></span> <span data-ttu-id="9f144-105">O operador [Await](../../../language-reference/operators/await.md) é aplicado à tarefa no ponto do método em que o processamento não pode continuar até que a tarefa seja concluída.</span><span class="sxs-lookup"><span data-stu-id="9f144-105">The [await](../../../language-reference/operators/await.md) operator is applied to the task at the point in the method where processing can't continue until the task finishes.</span></span> <span data-ttu-id="9f144-106">Muitas vezes, uma tarefa é esperada assim que é criada, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9f144-106">Often a task is awaited as soon as it's created, as the following example shows.</span></span>  
  
```csharp  
var result = await someWebAccessMethodAsync(url);  
```  
  
 <span data-ttu-id="9f144-107">No entanto, você pode separar a criação da tarefa de esperar a tarefa se o programa tiver outro trabalho para realizar que não depende da conclusão da tarefa.</span><span class="sxs-lookup"><span data-stu-id="9f144-107">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn't depend on the completion of the task.</span></span>  
  
```csharp  
// The following line creates and starts the task.  
var myTask = someWebAccessMethodAsync(url);  
  
// While the task is running, you can do other work that doesn't depend  
// on the results of the task.  
// . . . . .  
  
// The application of await suspends the rest of this method until the task is complete.  
var result = await myTask;  
```  
  
 <span data-ttu-id="9f144-108">Entre o início de uma tarefa e a espera por ela, você pode iniciar outras tarefas.</span><span class="sxs-lookup"><span data-stu-id="9f144-108">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="9f144-109">As tarefas adicionais são executadas implicitamente em paralelo, mas não são criados threads adicionais.</span><span class="sxs-lookup"><span data-stu-id="9f144-109">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="9f144-110">O programa a seguir inicia três downloads da Web assíncronos e os aguarda na ordem em que são chamados.</span><span class="sxs-lookup"><span data-stu-id="9f144-110">The following program starts three asynchronous web downloads and then awaits them in the order in which they're called.</span></span> <span data-ttu-id="9f144-111">Observe que, quando você executa o programa, as tarefas nem sempre são concluídas na ordem em que são criadas e aguardadas.</span><span class="sxs-lookup"><span data-stu-id="9f144-111">Notice, when you run the program, that the tasks don't always finish in the order in which they're created and awaited.</span></span> <span data-ttu-id="9f144-112">Eles começam a ser executados quando são criados, e uma ou mais tarefas podem ser concluídas antes que o método atinja as expressões Await.</span><span class="sxs-lookup"><span data-stu-id="9f144-112">They start to run when they're created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f144-113">Para concluir esse projeto, você precisa ter o Visual Studio 2012 ou posterior e o .NET Framework 4.5 ou posterior instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9f144-113">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="9f144-114">Para obter outro exemplo que inicia várias tarefas ao mesmo tempo, consulte [como estender o passo a assíncrona usando Task. WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="9f144-114">For another example that starts multiple tasks at the same time, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="9f144-115">Você pode baixar o código deste exemplo de [Exemplos de código para desenvolvedores](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span><span class="sxs-lookup"><span data-stu-id="9f144-115">You can download the code for this example from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="9f144-116">Para configurar o projeto</span><span class="sxs-lookup"><span data-stu-id="9f144-116">To set up the project</span></span>  
  
1. <span data-ttu-id="9f144-117">Para configurar um aplicativo WPF, complete as etapas a seguir.</span><span class="sxs-lookup"><span data-stu-id="9f144-117">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="9f144-118">Você pode encontrar instruções detalhadas dessas etapas em [Passo a passo: acessando a Web usando async e await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="9f144-118">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using async and await (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    - <span data-ttu-id="9f144-119">Crie um aplicativo WPF que contenha uma caixa de texto e um botão.</span><span class="sxs-lookup"><span data-stu-id="9f144-119">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="9f144-120">Dê o nome `startButton` para o botão e `resultsTextBox`, para a caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="9f144-120">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    - <span data-ttu-id="9f144-121">Adicione uma referência para <xref:System.Net.Http>.</span><span class="sxs-lookup"><span data-stu-id="9f144-121">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    - <span data-ttu-id="9f144-122">No arquivo MainWindow.xaml.cs, adicione uma diretiva `using` para `System.Net.Http`.</span><span class="sxs-lookup"><span data-stu-id="9f144-122">In the MainWindow.xaml.cs file, add a `using` directive for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="9f144-123">Para adicionar o código</span><span class="sxs-lookup"><span data-stu-id="9f144-123">To add the code</span></span>  
  
1. <span data-ttu-id="9f144-124">Na janela de design, MainWindow.xaml, clique duas vezes no botão para criar o manipulador de eventos `startButton_Click` no MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9f144-124">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
2. <span data-ttu-id="9f144-125">Copie o seguinte código e cole-o no corpo do `startButton_Click` em MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9f144-125">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    resultsTextBox.Clear();  
    await CreateMultipleTasksAsync();  
    resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
    ```  
  
     <span data-ttu-id="9f144-126">O código chama um método assíncrono, `CreateMultipleTasksAsync`, que controla o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9f144-126">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3. <span data-ttu-id="9f144-127">Adicione os seguintes métodos de suporte ao projeto:</span><span class="sxs-lookup"><span data-stu-id="9f144-127">Add the following support methods to the project:</span></span>  
  
    - <span data-ttu-id="9f144-128">O `ProcessURLAsync` usa um método <xref:System.Net.Http.HttpClient> para baixar o conteúdo de um site como uma matriz de bytes.</span><span class="sxs-lookup"><span data-stu-id="9f144-128">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="9f144-129">Em seguida, o método de suporte `ProcessURLAsync` exibe e retorna o comprimento da matriz.</span><span class="sxs-lookup"><span data-stu-id="9f144-129">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    - <span data-ttu-id="9f144-130">O `DisplayResults` exibe o número de bytes na matriz de bytes para cada URL.</span><span class="sxs-lookup"><span data-stu-id="9f144-130">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="9f144-131">Essa exibição mostra quando cada tarefa termina o download.</span><span class="sxs-lookup"><span data-stu-id="9f144-131">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="9f144-132">Copie os seguintes métodos e cole-os depois do manipulador de eventos `startButton_Click` em MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="9f144-132">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>  
  
    ```csharp  
    async Task<int> ProcessURLAsync(string url, HttpClient client)  
    {  
        var byteArray = await client.GetByteArrayAsync(url);  
        DisplayResults(url, byteArray);  
        return byteArray.Length;  
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
    ```  
  
4. <span data-ttu-id="9f144-133">Finalmente, defina o método `CreateMultipleTasksAsync`, que executa as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="9f144-133">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    - <span data-ttu-id="9f144-134">O método declara um objeto `HttpClient`, que você precisa para acessar o método <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> em `ProcessURLAsync`.</span><span class="sxs-lookup"><span data-stu-id="9f144-134">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    - <span data-ttu-id="9f144-135">O método cria e inicia três tarefas do tipo <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="9f144-135">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="9f144-136">Conforme cada tarefa termina, `DisplayResults` exibe a URL da tarefa e o comprimento do conteúdo baixado.</span><span class="sxs-lookup"><span data-stu-id="9f144-136">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="9f144-137">Como as tarefas estão em execução de maneira assíncrona, a ordem na qual os resultados são exibidos pode diferir da ordem na qual elas foram declaradas.</span><span class="sxs-lookup"><span data-stu-id="9f144-137">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    - <span data-ttu-id="9f144-138">O método aguarda a conclusão de cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="9f144-138">The method awaits the completion of each task.</span></span> <span data-ttu-id="9f144-139">Cada operador `await` suspende a execução de `CreateMultipleTasksAsync` até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="9f144-139">Each `await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="9f144-140">O operador também recupera o valor retornado da chamada ao `ProcessURLAsync` de cada tarefa concluída.</span><span class="sxs-lookup"><span data-stu-id="9f144-140">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    - <span data-ttu-id="9f144-141">Quando as tarefas forem concluídas e os valores inteiros forem recuperados, o método somará os comprimentos dos sites e exibirá o resultado.</span><span class="sxs-lookup"><span data-stu-id="9f144-141">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="9f144-142">Copie o seguinte método e cole-o em sua solução.</span><span class="sxs-lookup"><span data-stu-id="9f144-142">Copy the following method, and paste it into your solution.</span></span>  
  
    ```csharp  
    private async Task CreateMultipleTasksAsync()  
    {  
        // Declare an HttpClient object, and increase the buffer size. The  
        // default buffer size is 65,536.  
        HttpClient client =  
            new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
        // Create and start the tasks. As each task finishes, DisplayResults
        // displays its length.  
        Task<int> download1 =
            ProcessURLAsync("https://msdn.microsoft.com", client);  
        Task<int> download2 =
            ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
        Task<int> download3 =
            ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
        // Await each task.  
        int length1 = await download1;  
        int length2 = await download2;  
        int length3 = await download3;  
  
        int total = length1 + length2 + length3;  
  
        // Display the total count for the downloaded websites.  
        resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
    }  
    ```  
  
5. <span data-ttu-id="9f144-143">Escolha a tecla F5 para executar o programa e, em seguida, o botão **Iniciar**.</span><span class="sxs-lookup"><span data-stu-id="9f144-143">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="9f144-144">Execute o programa várias vezes para verificar se as três tarefas nem sempre são concluídas na mesma ordem e se a ordem em que elas são concluídas não é necessariamente a ordem na qual elas são criadas e aguardadas.</span><span class="sxs-lookup"><span data-stu-id="9f144-144">Run the program several times to verify that the three tasks don't always finish in the same order and that the order in which they finish isn't necessarily the order in which they're created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f144-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9f144-145">Example</span></span>  
 <span data-ttu-id="9f144-146">O código a seguir contem o exemplo completo.</span><span class="sxs-lookup"><span data-stu-id="9f144-146">The following code contains the full example.</span></span>  
  
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
  
// Add the following using directive, and add a reference for System.Net.Http.  
using System.Net.Http;  
  
namespace AsyncExample_MultipleTasks  
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
            await CreateMultipleTasksAsync();  
            resultsTextBox.Text += "\r\n\r\nControl returned to startButton_Click.\r\n";  
        }  
  
        private async Task CreateMultipleTasksAsync()  
        {  
            // Declare an HttpClient object, and increase the buffer size. The  
            // default buffer size is 65,536.  
            HttpClient client =  
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };  
  
            // Create and start the tasks. As each task finishes, DisplayResults
            // displays its length.  
            Task<int> download1 =
                ProcessURLAsync("https://msdn.microsoft.com", client);  
            Task<int> download2 =
                ProcessURLAsync("https://msdn.microsoft.com/library/hh156528(VS.110).aspx", client);  
            Task<int> download3 =
                ProcessURLAsync("https://msdn.microsoft.com/library/67w7t67f.aspx", client);  
  
            // Await each task.  
            int length1 = await download1;  
            int length2 = await download2;  
            int length3 = await download3;  
  
            int total = length1 + length2 + length3;  
  
            // Display the total count for the downloaded websites.  
            resultsTextBox.Text += $"\r\n\r\nTotal bytes returned:  {total}\r\n";
        }  
  
        async Task<int> ProcessURLAsync(string url, HttpClient client)  
        {  
            var byteArray = await client.GetByteArrayAsync(url);  
            DisplayResults(url, byteArray);  
            return byteArray.Length;  
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
  
## <a name="see-also"></a><span data-ttu-id="9f144-147">Veja também</span><span class="sxs-lookup"><span data-stu-id="9f144-147">See also</span></span>

- [<span data-ttu-id="9f144-148">Passo a passo: acessando a Web usando async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="9f144-148">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="9f144-149">Programação assíncrona com Async e Await (C#)</span><span class="sxs-lookup"><span data-stu-id="9f144-149">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
- [<span data-ttu-id="9f144-150">Como estender a instrução assíncrona usando Task. WhenAll (C#)</span><span class="sxs-lookup"><span data-stu-id="9f144-150">How to extend the async walkthrough by using Task.WhenAll (C#)</span></span>](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
