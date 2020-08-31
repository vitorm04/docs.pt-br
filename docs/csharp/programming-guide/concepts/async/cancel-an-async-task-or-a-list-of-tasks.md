---
title: Cancelar uma lista de tarefas (C#)
description: Saiba como usar tokens de cancelamento para sinalizar uma solicitação de cancelamento para uma lista de tarefas.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: eec32dbb-70ea-4c88-bd27-fa2e34546914
ms.openlocfilehash: 30bef5d1a5082fbd3757377dbedb8f9b9d17e218
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053087"
---
# <a name="cancel-a-list-of-tasks-c"></a><span data-ttu-id="5e226-103">Cancelar uma lista de tarefas (C#)</span><span class="sxs-lookup"><span data-stu-id="5e226-103">Cancel a list of tasks (C#)</span></span>

<span data-ttu-id="5e226-104">Você pode cancelar um aplicativo de console assíncrono se não quiser esperar que ele seja concluído.</span><span class="sxs-lookup"><span data-stu-id="5e226-104">You can cancel an async console application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="5e226-105">Seguindo o exemplo neste tópico, você pode adicionar um cancelamento a um aplicativo que baixa o conteúdo de uma lista de sites.</span><span class="sxs-lookup"><span data-stu-id="5e226-105">By following the example in this topic, you can add a cancellation to an application that downloads the contents of a list of websites.</span></span> <span data-ttu-id="5e226-106">Você pode cancelar várias tarefas associando a <xref:System.Threading.CancellationTokenSource> instância a cada tarefa.</span><span class="sxs-lookup"><span data-stu-id="5e226-106">You can cancel many tasks by associating the <xref:System.Threading.CancellationTokenSource> instance with each task.</span></span> <span data-ttu-id="5e226-107">Se você selecionar a tecla <kbd>Enter</kbd> , cancelará todas as tarefas que ainda não foram concluídas.</span><span class="sxs-lookup"><span data-stu-id="5e226-107">If you select the <kbd>Enter</kbd> key, you cancel all tasks that aren't yet complete.</span></span>

<span data-ttu-id="5e226-108">Este tutorial abrange:</span><span class="sxs-lookup"><span data-stu-id="5e226-108">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5e226-109">Criando um aplicativo de console .NET</span><span class="sxs-lookup"><span data-stu-id="5e226-109">Creating a .NET console application</span></span>
> - <span data-ttu-id="5e226-110">Escrevendo um aplicativo assíncrono que dá suporte ao cancelamento</span><span class="sxs-lookup"><span data-stu-id="5e226-110">Writing an async application that supports cancellation</span></span>
> - <span data-ttu-id="5e226-111">Demonstrando o cancelamento de sinalização</span><span class="sxs-lookup"><span data-stu-id="5e226-111">Demonstrating signaling cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5e226-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5e226-112">Prerequisites</span></span>

<span data-ttu-id="5e226-113">Este tutorial exige o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5e226-113">This tutorial requires the following:</span></span>

- [<span data-ttu-id="5e226-114">SDK do .NET 5,0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="5e226-114">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="5e226-115">IDE (ambiente de desenvolvimento integrado)</span><span class="sxs-lookup"><span data-stu-id="5e226-115">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="5e226-116">Recomendamos o Visual Studio, Visual Studio Code ou Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="5e226-116">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

### <a name="create-example-application"></a><span data-ttu-id="5e226-117">Criar aplicativo de exemplo</span><span class="sxs-lookup"><span data-stu-id="5e226-117">Create example application</span></span>

<span data-ttu-id="5e226-118">Crie um novo aplicativo de console .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e226-118">Create a new .NET Core console application.</span></span> <span data-ttu-id="5e226-119">Você pode criar um usando o [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) comando ou do [Visual Studio](/visualstudio/install/install-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="5e226-119">You can create one by using the [`dotnet new console`](../../../../core/tools/dotnet-new.md#console) command or from [Visual Studio](/visualstudio/install/install-visual-studio).</span></span> <span data-ttu-id="5e226-120">Abra o arquivo *Program.cs* em seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="5e226-120">Open the *Program.cs* file in your favorite code editor.</span></span>

### <a name="replace-using-statements"></a><span data-ttu-id="5e226-121">Substituir usando instruções</span><span class="sxs-lookup"><span data-stu-id="5e226-121">Replace using statements</span></span>

<span data-ttu-id="5e226-122">Substitua as instruções using existentes por estas declarações:</span><span class="sxs-lookup"><span data-stu-id="5e226-122">Replace the existing using statements with these declarations:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Diagnostics;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

## <a name="add-fields"></a><span data-ttu-id="5e226-123">Adicionar campos</span><span class="sxs-lookup"><span data-stu-id="5e226-123">Add fields</span></span>

<span data-ttu-id="5e226-124">Na `Program` definição de classe, adicione estes três campos:</span><span class="sxs-lookup"><span data-stu-id="5e226-124">In the `Program` class definition, add these three fields:</span></span>

```csharp
static readonly CancellationTokenSource s_cts = new CancellationTokenSource();

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

<span data-ttu-id="5e226-125">O <xref:System.Threading.CancellationTokenSource> é usado para sinalizar um cancelamento solicitado para um <xref:System.Threading.CancellationToken> .</span><span class="sxs-lookup"><span data-stu-id="5e226-125">The <xref:System.Threading.CancellationTokenSource> is used to signal a requested cancellation to a <xref:System.Threading.CancellationToken>.</span></span> <span data-ttu-id="5e226-126">O `HttpClient` expõe a capacidade de enviar solicitações HTTP e receber respostas http.</span><span class="sxs-lookup"><span data-stu-id="5e226-126">The `HttpClient` exposes the ability to send HTTP requests and receive HTTP responses.</span></span> <span data-ttu-id="5e226-127">O `s_urlList` mantém todas as URLs que o aplicativo planeja processar.</span><span class="sxs-lookup"><span data-stu-id="5e226-127">The `s_urlList` holds all of the URLs that the application plans to process.</span></span>

## <a name="update-application-entry-point"></a><span data-ttu-id="5e226-128">Atualizar ponto de entrada do aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e226-128">Update application entry point</span></span>

<span data-ttu-id="5e226-129">O ponto de entrada principal no aplicativo de console é o `Main` método.</span><span class="sxs-lookup"><span data-stu-id="5e226-129">The main entry point into the console application is the `Main` method.</span></span> <span data-ttu-id="5e226-130">Substitua o método existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="5e226-130">Replace the existing method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");
    Console.WriteLine("Press the ENTER key to cancel...\n");

    Task cancelTask = Task.Run(() =>
    {
        while (Console.ReadKey().Key != ConsoleKey.Enter)
        {
            Console.WriteLine("Press the ENTER key to cancel...");
        }

        Console.WriteLine("\nENTER key pressed: cancelling downloads.\n");
        s_cts.Cancel();
    });

    Task sumPageSizesTask = SumPageSizesAsync();

    await Task.WhenAny(new[] { cancelTask, sumPageSizesTask });

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="5e226-131">O `Main` método atualizado agora é considerado um [Async Main](../../../whats-new/csharp-7-1.md#async-main), que permite um ponto de entrada assíncrono no executável.</span><span class="sxs-lookup"><span data-stu-id="5e226-131">The updated `Main` method is now considered an [Async main](../../../whats-new/csharp-7-1.md#async-main), which allows for an asynchronous entry point into the executable.</span></span> <span data-ttu-id="5e226-132">Ele grava algumas mensagens instrutivas no console e, em seguida, declara uma <xref:System.Threading.Tasks.Task> instância chamada `cancelTask` , que lerá os traços de tecla do console.</span><span class="sxs-lookup"><span data-stu-id="5e226-132">It writes a few instructional messages to the console, then declares a <xref:System.Threading.Tasks.Task> instance named `cancelTask`, which will read console key strokes.</span></span> <span data-ttu-id="5e226-133">Se a tecla <kbd>Enter</kbd> for pressionada, será feita uma chamada para <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e226-133">If the <kbd>Enter</kbd> key is pressed, a call to <xref:System.Threading.CancellationTokenSource.Cancel?displayProperty=nameWithType> is made.</span></span> <span data-ttu-id="5e226-134">Isso sinalizará o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="5e226-134">This will signal cancellation.</span></span> <span data-ttu-id="5e226-135">Em seguida, a `sumPageSizesTask` variável é atribuída a partir do `SumPageSizesAsync` método.</span><span class="sxs-lookup"><span data-stu-id="5e226-135">Next, the `sumPageSizesTask` variable is assigned from the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="5e226-136">Em seguida, as duas tarefas são passadas para <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType> o, o que continuará quando qualquer uma das duas tarefas for concluída.</span><span class="sxs-lookup"><span data-stu-id="5e226-136">Both tasks are then passed to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])?displayProperty=nameWithType>, which will continue when any of the two tasks have completed.</span></span>

## <a name="create-the-asynchronous-sum-page-sizes-method"></a><span data-ttu-id="5e226-137">Criar o método de tamanhos de página de soma assíncrona</span><span class="sxs-lookup"><span data-stu-id="5e226-137">Create the asynchronous sum page sizes method</span></span>

<span data-ttu-id="5e226-138">Abaixo do `Main` método, adicione o `SumPageSizesAsync` método:</span><span class="sxs-lookup"><span data-stu-id="5e226-138">Below the `Main` method, add the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task SumPageSizesAsync()
{
    var stopwatch = Stopwatch.StartNew();

    int total = 0;
    foreach (string url in s_urlList)
    {
        int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
        total += contentLength;
    }

    stopwatch.Stop();

    Console.WriteLine($"\nTotal bytes returned:  {total:#,#}");
    Console.WriteLine($"Elapsed time:          {stopwatch.Elapsed}\n");
}
```

<span data-ttu-id="5e226-139">O método começa instanciando e iniciando um <xref:System.Diagnostics.Stopwatch> .</span><span class="sxs-lookup"><span data-stu-id="5e226-139">The method starts by instantiating and starting a <xref:System.Diagnostics.Stopwatch>.</span></span> <span data-ttu-id="5e226-140">Em seguida, ele executa um loop em cada URL nas `s_urlList` chamadas e `ProcessUrlAsync` .</span><span class="sxs-lookup"><span data-stu-id="5e226-140">It then loops through each URL in the `s_urlList` and calls `ProcessUrlAsync`.</span></span> <span data-ttu-id="5e226-141">Com cada iteração, o `s_cts.Token` é passado para o `ProcessUrlAsync` método e o código retorna um <xref:System.Threading.Tasks.Task%601> , em que `TResult` é um inteiro:</span><span class="sxs-lookup"><span data-stu-id="5e226-141">With each iteration, the `s_cts.Token` is passed into the `ProcessUrlAsync` method and the code returns a <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer:</span></span>

```csharp
int total = 0;
foreach (string url in s_urlList)
{
    int contentLength = await ProcessUrlAsync(url, s_client, s_cts.Token);
    total += contentLength;
}
```

## <a name="add-process-method"></a><span data-ttu-id="5e226-142">Adicionar método de processo</span><span class="sxs-lookup"><span data-stu-id="5e226-142">Add process method</span></span>

<span data-ttu-id="5e226-143">Adicione o seguinte `ProcessUrlAsync` método abaixo do `SumPageSizesAsync` método:</span><span class="sxs-lookup"><span data-stu-id="5e226-143">Add the following `ProcessUrlAsync` method below the `SumPageSizesAsync` method:</span></span>

```csharp
static async Task<int> ProcessUrlAsync(string url, HttpClient client, CancellationToken token)
{
    HttpResponseMessage response = await client.GetAsync(url, token);
    byte[] content = await response.Content.ReadAsByteArrayAsync(token);
    Console.WriteLine($"{url,-60} {content.Length,10:#,#}");

    return content.Length;
}
```

<span data-ttu-id="5e226-144">Para qualquer URL fornecida, o método usará a `client` instância fornecida para obter a resposta como um `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="5e226-144">For any given URL, the method will use the `client` instance provided to get the response as a `byte[]`.</span></span> <span data-ttu-id="5e226-145">A <xref:System.Threading.CancellationToken> instância é passada para os <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> métodos e.</span><span class="sxs-lookup"><span data-stu-id="5e226-145">The <xref:System.Threading.CancellationToken> instance is passed into the <xref:System.Net.Http.HttpClient.GetAsync(System.String,System.Threading.CancellationToken)?displayProperty=nameWithType> and <xref:System.Net.Http.HttpContent.ReadAsByteArrayAsync(System.Threading.CancellationToken)?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5e226-146">O `token` é usado para se registrar para o cancelamento solicitado.</span><span class="sxs-lookup"><span data-stu-id="5e226-146">The `token` is used to register for requested cancellation.</span></span> <span data-ttu-id="5e226-147">O comprimento é retornado depois que a URL e o comprimento são gravados no console.</span><span class="sxs-lookup"><span data-stu-id="5e226-147">The length is returned after the URL and length is written to the console.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="5e226-148">Exemplo de saída de aplicativo</span><span class="sxs-lookup"><span data-stu-id="5e226-148">Example application output</span></span>

```console
Application started.
Press the ENTER key to cancel...

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663
https://docs.microsoft.com/dotnet                                67,452
https://docs.microsoft.com/dynamics365                           48,582
https://docs.microsoft.com/education                             22,924

ENTER key pressed: cancelling downloads.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="5e226-149">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="5e226-149">Complete example</span></span>

<span data-ttu-id="5e226-150">O código a seguir é o texto completo do arquivo *Program.cs* para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="5e226-150">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-tasks/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="5e226-151">Confira também</span><span class="sxs-lookup"><span data-stu-id="5e226-151">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="5e226-152">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="5e226-152">Asynchronous programming with async and await (C#)</span></span>](index.md)

## <a name="next-steps"></a><span data-ttu-id="5e226-153">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5e226-153">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5e226-154">Cancelar tarefas assíncronas após um período (C#)</span><span class="sxs-lookup"><span data-stu-id="5e226-154">Cancel async tasks after a period of time (C#)</span></span>](cancel-async-tasks-after-a-period-of-time.md)
