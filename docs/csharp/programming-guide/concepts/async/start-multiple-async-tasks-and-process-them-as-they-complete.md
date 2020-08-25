---
title: Processar tarefas assíncronas conforme elas são concluídas
description: Este exemplo mostra como usar Task. WhenAny em C# para iniciar várias tarefas e processar seus resultados à medida que eles são concluídos, em vez de processá-los no pedido iniciado.
ms.date: 08/19/2020
ms.assetid: 25331850-35a7-43b3-ab76-3908e4346b9d
ms.openlocfilehash: c2fe66e865a2c88f4cae50b816f9326614fcbb89
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812023"
---
# <a name="process-asynchronous-tasks-as-they-complete-c"></a><span data-ttu-id="9b786-103">Processar tarefas assíncronas conforme elas são concluídas (C#)</span><span class="sxs-lookup"><span data-stu-id="9b786-103">Process asynchronous tasks as they complete (C#)</span></span>

<span data-ttu-id="9b786-104">Usando <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> o, você pode iniciar várias tarefas ao mesmo tempo e processá-las uma a uma conforme elas são concluídas, em vez de processá-las na ordem em que elas são iniciadas.</span><span class="sxs-lookup"><span data-stu-id="9b786-104">By using <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, you can start multiple tasks at the same time and process them one by one as they're completed rather than process them in the order in which they're started.</span></span>

<span data-ttu-id="9b786-105">O exemplo a seguir usa uma consulta para criar uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="9b786-105">The following example uses a query to create a collection of tasks.</span></span> <span data-ttu-id="9b786-106">Cada tarefa baixa o conteúdo de um site especificado.</span><span class="sxs-lookup"><span data-stu-id="9b786-106">Each task downloads the contents of a specified website.</span></span> <span data-ttu-id="9b786-107">Em cada iteração de um loop "while", uma chamada esperada para <xref:System.Threading.Tasks.Task.WhenAny%2A> retorna a tarefa na coleção de tarefas que concluir o download primeiro.</span><span class="sxs-lookup"><span data-stu-id="9b786-107">In each iteration of a while loop, an awaited call to <xref:System.Threading.Tasks.Task.WhenAny%2A> returns the task in the collection of tasks that finishes its download first.</span></span> <span data-ttu-id="9b786-108">Essa tarefa é removida da coleção e processada.</span><span class="sxs-lookup"><span data-stu-id="9b786-108">That task is removed from the collection and processed.</span></span> <span data-ttu-id="9b786-109">O loop é repetido até que a coleção não contenha mais tarefas.</span><span class="sxs-lookup"><span data-stu-id="9b786-109">The loop repeats until the collection contains no more tasks.</span></span>

## <a name="create-example-application"></a><span data-ttu-id="9b786-110">Criar aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="9b786-110">Create example application</span></span>

<span data-ttu-id="9b786-111">Crie um novo aplicativo de console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9b786-111">Create a new .NET Core console application.</span></span> <span data-ttu-id="9b786-112">Você pode criar um usando o comando [dotnet New console](../../../../core/tools/dotnet-new.md#console) ou do [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9b786-112">You can create one by using the [dotnet new console](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="9b786-113">Abra o arquivo *Program.cs* em seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="9b786-113">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="9b786-114">Substituir usando instruções</span><span class="sxs-lookup"><span data-stu-id="9b786-114">Replace using statements</span></span>

<span data-ttu-id="9b786-115">Substitua as instruções using existentes por estas declarações:</span><span class="sxs-lookup"><span data-stu-id="9b786-115">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Linq;
using System.Net.Http;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="9b786-116">Adicionar campos</span><span class="sxs-lookup"><span data-stu-id="9b786-116">Add fields</span></span>

<span data-ttu-id="9b786-117">Na `Program` definição de classe, adicione os dois campos a seguir:</span><span class="sxs-lookup"><span data-stu-id="9b786-117">In the `Program` class definition, add the following two fields:</span></span>

```csharp
static readonly HttpClient s_client = new HttpClient
{
    MaxResponseContentBufferSize = 1_000_000
};

static readonly IEnumerable<string> s_urlList = new string[]
{
    "https://docs.microsoft.com",
    "https://docs.microsoft.com/aspnet/core",
    "https://docs.microsoft.com/azure",
    "https://docs.microsoft.com/azure/devops",
    "https://docs.microsoft.com/dotnet",
    "https://docs.microsoft.com/dynamics365",
    "https://docs.microsoft.com/education",
    "https://docs.microsoft.com/enterprise-mobility-security",
    "https://docs.microsoft.com/gaming",
    "https://docs.microsoft.com/graph",
    "https://docs.microsoft.com/microsoft-365",
    "https://docs.microsoft.com/office",
    "https://docs.microsoft.com/powershell",
    "https://docs.microsoft.com/sql",
    "https://docs.microsoft.com/surface",
    "https://docs.microsoft.com/system-center",
    "https://docs.microsoft.com/visualstudio",
    "https://docs.microsoft.com/windows",
    "https://docs.microsoft.com/xamarin"
};
```

<span data-ttu-id="9b786-118">O `HttpClient` expõe a capacidade de enviar solicitações HTTP e receber respostas http.</span><span class="sxs-lookup"><span data-stu-id="9b786-118">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="9b786-119">O `s_urlList` mantém todas as URLs que o aplicativo planeja processar.</span><span class="sxs-lookup"><span data-stu-id="9b786-119">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="9b786-120">Atualizar ponto de entrada do aplicativo</span><span class="sxs-lookup"><span data-stu-id="9b786-120">Update application entry point</span></span>

<span data-ttu-id="9b786-121">O ponto de entrada principal no aplicativo de console é o `Main` método.</span><span class="sxs-lookup"><span data-stu-id="9b786-121">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="9b786-122">Substitua o método existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="9b786-122">Replace the existing method with the following:</span></span>

```csharp
static Task Main() => SumPageSizesAsync();
```

<span data-ttu-id="9b786-123">O `Main` método atualizado agora é considerado um [Async Main](../../../whats-new/csharp-7-1.md#async-main), que permite um ponto de entrada assíncrono no executável.</span><span class="sxs-lookup"><span data-stu-id="9b786-123">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="9b786-124">É expressa uma chamada para `SumPageSizesAsync` .</span><span class="sxs-lookup"><span data-stu-id="9b786-124">It is expressed a call to `SumPageSizesAsync`.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="9b786-125">Criar o método de tamanhos de página de soma assíncrona</span><span class="sxs-lookup"><span data-stu-id="9b786-125">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="9b786-126">Abaixo do `Main` método, adicione o `SumPageSizesAsync` método:</span><span class="sxs-lookup"><span data-stu-id="9b786-126">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    IEnumerable<Task<int>> downloadTasksQuery =
        from url in s_urlList
        select ProcessUrlAsync(url, s_client);

    List<Task<int>> downloadTasks = downloadTasksQuery.ToList();

    int total = 0;
    while (downloadTasks.Any())
    {
        Task<int> finishedTask = await Task.WhenAny(downloadTasks);
        downloadTasks.Remove(finishedTask);
        total += await finishedTask;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="9b786-127">O método começa instanciando e iniciando um <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="9b786-127">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="9b786-128">Em seguida, ele inclui uma consulta que, quando executada, cria uma coleção de tarefas.</span><span class="sxs-lookup"><span data-stu-id="9b786-128">It then includes a query that, when executed, creates a collection of tasks.</span></span> <span data-ttu-id="9b786-129">Cada chamada para `ProcessUrlAsync` no código a seguir retorna um <xref:System.Threading.Tasks.Task%601>, em que `TResult` é um inteiro:</span><span class="sxs-lookup"><span data-stu-id="9b786-129">Each call to `ProcessUrlAsync` in the following code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
IEnumerable<Task<int>> downloadTasksQuery =
    from url in s_urlList
    select ProcessUrlAsync(url, s_client);
```

<span data-ttu-id="9b786-130">Devido à [execução retardada](../linq/deferred-execution-example.md) com o LINQ, você chama <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> para iniciar cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="9b786-130">Due to [deferred execution](../linq/deferred-execution-example.md) with the LINQ, you call <xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> to start each task.</span></span>

```csharp
List<Task<int>> downloadTasks = downloadTasksQuery.ToList();
```

<span data-ttu-id="9b786-131">O `while` loop executa as seguintes etapas para cada tarefa na coleção:</span><span class="sxs-lookup"><span data-stu-id="9b786-131">The `while` loop performs the following steps for each task in the collection:</span></span>

1. <span data-ttu-id="9b786-132">Aguarda uma chamada para `WhenAny` para identificar a primeira tarefa na coleção que concluiu seu download.</span><span class="sxs-lookup"><span data-stu-id="9b786-132">Awaits a call to `WhenAny` to identify the first task in the collection that has finished its download.</span></span>

    ```csharp
    Task<int> firstFinishedTask = await Task.WhenAny(downloadTasks);
    ```

1. <span data-ttu-id="9b786-133">Remove a tarefa da coleção.</span><span class="sxs-lookup"><span data-stu-id="9b786-133">Removes that task from the collection.</span></span>

    ```csharp
    downloadTasks.Remove(firstFinishedTask);
    ```

1. <span data-ttu-id="9b786-134">Espera `finishedTask`, que é retornado por uma chamada para `ProcessUrlAsync`.</span><span class="sxs-lookup"><span data-stu-id="9b786-134">Awaits `finishedTask`, which is returned by a call to `ProcessUrlAsync`.</span></span> <span data-ttu-id="9b786-135">A variável `finishedTask` é uma <xref:System.Threading.Tasks.Task%601> em que `TResult` é um inteiro.</span><span class="sxs-lookup"><span data-stu-id="9b786-135">The `finishedTask` variable is a <xref:System.Threading.Tasks.Task%601> where `TResult` is an integer.</span></span> <span data-ttu-id="9b786-136">A tarefa já foi concluída, mas você espera para recuperar o tamanho do site baixado, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9b786-136">The task is already complete, but you await it to retrieve the length of the downloaded website, as the following example shows.</span></span> <span data-ttu-id="9b786-137">Se a tarefa tiver falhado, `await` o lançará a primeira exceção filha armazenada no `AggregateException` , ao contrário da leitura da <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> propriedade, que geraria o `AggregateException` .</span><span class="sxs-lookup"><span data-stu-id="9b786-137">If the task is faulted, `await` will throw the first child exception stored in the `AggregateException`, unlike reading the <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> property, which would throw the `AggregateException`.</span></span>

    ```csharp
    total += await finishedTask;
    ```

## <a name="add-process-method"></a><span data-ttu-id="9b786-138">Adicionar método de processo</span><span class="sxs-lookup"><span data-stu-id="9b786-138">Add process method</span></span>

<span data-ttu-id="9b786-139">Adicione o seguinte `ProcessUrlAsync` método abaixo do `SumPageSizesAsync` método:</span><span class="sxs-lookup"><span data-stu-id="9b786-139">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client)
{
    byte[] content = await client.GetByteArrayAsync(url);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="9b786-140">Para qualquer URL fornecida, o método usará a `client` instância fornecida para obter a resposta como um `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="9b786-140">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="9b786-141">O comprimento é retornado depois que a URL e o comprimento são gravados no console.</span><span class="sxs-lookup"><span data-stu-id="9b786-141">The length is returned after the URL and length is written to the console.</span></span>

<span data-ttu-id="9b786-142">Execute o programa várias vezes para verificar se os tamanhos baixados não aparecem sempre na mesma ordem.</span><span class="sxs-lookup"><span data-stu-id="9b786-142">Run the program several times to verify that the downloaded lengths don't always appear in the same order.</span></span>

> [!CAUTION]
> <span data-ttu-id="9b786-143">Você pode usar `WhenAny` em um loop, conforme descrito no exemplo, para resolver problemas que envolvem um número pequeno de tarefas.</span><span class="sxs-lookup"><span data-stu-id="9b786-143">You can use `WhenAny` in a loop, as described in the example, to solve problems that involve a small number of tasks.</span></span> <span data-ttu-id="9b786-144">No entanto, outras abordagens são mais eficientes se você tiver um número grande de tarefas para processar.</span><span class="sxs-lookup"><span data-stu-id="9b786-144">However, other approaches are more efficient if you have a large number of tasks to process.</span></span> <span data-ttu-id="9b786-145">Para obter mais informações e exemplos, consulte [Processando tarefas quando elas são concluídas](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span><span class="sxs-lookup"><span data-stu-id="9b786-145">For more information and examples, see [Processing tasks as they complete](https://devblogs.microsoft.com/pfxteam/processing-tasks-as-they-complete).</span></span>

## <a name="complete-example"></a><span data-ttu-id="9b786-146">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="9b786-146">Complete example</span></span>

<span data-ttu-id="9b786-147">O código a seguir é o texto completo do arquivo *Program.cs* para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="9b786-147">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/multiple-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="9b786-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="9b786-148">See also</span></span>

- <xref:System.Threading.Tasks.Task.WhenAny%2A>
- [<span data-ttu-id="9b786-149">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="9b786-149">Asynchronous programming with async and await (C#)</span></span>](index.md)
