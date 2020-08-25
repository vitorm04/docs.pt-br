---
title: Cancelar tarefas assíncronas após um período de tempo (C#) "
description: Saiba como agendar o cancelamento de todas as tarefas associadas que não foram concluídas em um período de tempo.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: ad9064f8f45a737982ffc35ab4ea2395ddae9016
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811412"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="65756-103">Cancelar tarefas assíncronas após um período (C#)</span><span class="sxs-lookup"><span data-stu-id="65756-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="65756-104">Você pode cancelar uma operação assíncrona após um período de tempo usando o <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> método se não quiser aguardar a conclusão da operação.</span><span class="sxs-lookup"><span data-stu-id="65756-104">You can cancel an asynchronous operation after a period of time by using the <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="65756-105">Esse método agenda o cancelamento de todas as tarefas associadas que não são concluídas dentro do período designado pela `CancelAfter` expressão.</span><span class="sxs-lookup"><span data-stu-id="65756-105">This method schedules the cancellation of any associated tasks that aren't complete within the period of time that's designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="65756-106">Este exemplo adiciona ao código desenvolvido em [cancelar uma lista de tarefas (C#)](cancel-an-async-task-or-a-list-of-tasks.md) para baixar uma lista de sites e exibir o comprimento do conteúdo de cada um.</span><span class="sxs-lookup"><span data-stu-id="65756-106">This example adds to the code that's developed in [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

<span data-ttu-id="65756-107">Este tutorial abrange:</span><span class="sxs-lookup"><span data-stu-id="65756-107">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="65756-108">Atualizando um aplicativo de console .NET existente</span><span class="sxs-lookup"><span data-stu-id="65756-108">Updating an existing .NET console application</span></span>
> - <span data-ttu-id="65756-109">Agendando um cancelamento</span><span class="sxs-lookup"><span data-stu-id="65756-109">Scheduling a cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65756-110">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="65756-110">Prerequisites</span></span>

<span data-ttu-id="65756-111">Este tutorial exige o seguinte:</span><span class="sxs-lookup"><span data-stu-id="65756-111">This tutorial requires the following:</span></span>

- <span data-ttu-id="65756-112">Você deve ter criado um aplicativo no tutorial [cancelar uma lista de tarefas (C#)](cancel-an-async-task-or-a-list-of-tasks.md)</span><span class="sxs-lookup"><span data-stu-id="65756-112">You're expected to have created an application in the [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) tutorial</span></span>
- [<span data-ttu-id="65756-113">SDK do .NET 5,0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="65756-113">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="65756-114">IDE (ambiente de desenvolvimento integrado)</span><span class="sxs-lookup"><span data-stu-id="65756-114">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="65756-115">Recomendamos o Visual Studio, Visual Studio Code ou Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="65756-115">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a><span data-ttu-id="65756-116">Atualizar ponto de entrada do aplicativo</span><span class="sxs-lookup"><span data-stu-id="65756-116">Update application entry point</span></span>

<span data-ttu-id="65756-117">Substitua o `Main` método existente pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="65756-117">Replace the existing `Main` method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500);

        await SumPageSizesAsync();
    }
    catch (TaskCanceledException)
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="65756-118">O `Main` método atualizado grava algumas mensagens instrutivas no console do.</span><span class="sxs-lookup"><span data-stu-id="65756-118">The updated `Main` method writes a few instructional messages to the console.</span></span> <span data-ttu-id="65756-119">Dentro de [try catch](../../../language-reference/keywords/try-catch.md), uma chamada para <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> para agendar um cancelamento.</span><span class="sxs-lookup"><span data-stu-id="65756-119">Within the [try catch](../../../language-reference/keywords/try-catch.md), a call to <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> to schedule a cancellation.</span></span> <span data-ttu-id="65756-120">Isso sinalizará o cancelamento após um período de tempo.</span><span class="sxs-lookup"><span data-stu-id="65756-120">This will signal cancellation after a period of time.</span></span>

<span data-ttu-id="65756-121">Em seguida, o `SumPageSizesAsync` método é aguardado.</span><span class="sxs-lookup"><span data-stu-id="65756-121">Next, the `SumPageSizesAsync` method is awaited.</span></span> <span data-ttu-id="65756-122">Se o processamento de todas as URLs ocorrer mais rápido do que o cancelamento agendado, o aplicativo será encerrado.</span><span class="sxs-lookup"><span data-stu-id="65756-122">If processing all of the URLs occurs faster than the scheduled cancellation, the application ends.</span></span> <span data-ttu-id="65756-123">No entanto, se o cancelamento agendado for disparado antes que todas as URLs sejam processadas, um <xref:System.Threading.Tasks.TaskCanceledException> será lançado.</span><span class="sxs-lookup"><span data-stu-id="65756-123">However, if the scheduled cancellation is triggered before all of the URLs are processed, a <xref:System.Threading.Tasks.TaskCanceledException> is thrown.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="65756-124">Exemplo de saída de aplicativo</span><span class="sxs-lookup"><span data-stu-id="65756-124">Example application output</span></span>

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="65756-125">Exemplo completo</span><span class="sxs-lookup"><span data-stu-id="65756-125">Complete example</span></span>

<span data-ttu-id="65756-126">O código a seguir é o texto completo do arquivo *Program.cs* para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="65756-126">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="65756-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="65756-127">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="65756-128">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="65756-128">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="65756-129">Cancelar uma lista de tarefas (C#)</span><span class="sxs-lookup"><span data-stu-id="65756-129">Cancel a list of tasks (C#)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
