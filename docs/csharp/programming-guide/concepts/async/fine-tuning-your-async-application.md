---
title: "Ajuste fino de seu aplicativo assíncrono (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c42f51d627f827e216e6c25b3bde60e32b9ba027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="7fc17-102">Ajuste fino de seu aplicativo assíncrono (C#)</span><span class="sxs-lookup"><span data-stu-id="7fc17-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="7fc17-103">É possível adicionar flexibilidade e precisão a seus aplicativos assíncronos usando os métodos e propriedades que o tipo <xref:System.Threading.Tasks.Task> disponibiliza.</span><span class="sxs-lookup"><span data-stu-id="7fc17-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="7fc17-104">Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken> e métodos de `Task` importantes como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7fc17-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7fc17-105">Usando `WhenAny` e `WhenAll`, é possível, com facilidade, iniciar várias tarefas e aguardar sua conclusão monitorando uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="7fc17-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="7fc17-106">`WhenAny` retorna uma tarefa que é concluída quando qualquer tarefa em uma coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="7fc17-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="7fc17-107">Para obter exemplos que usam `WhenAny`, consulte [Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) e [Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="7fc17-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="7fc17-108">`WhenAll` retorna uma tarefa que é concluída quando todas as tarefas em uma coleção forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="7fc17-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="7fc17-109">Para obter mais informações e um exemplo que usa `WhenAll`, consulte [Como estender as instruções passo a passo assíncronas usando Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="7fc17-109">For more information and an example that uses `WhenAll`, see [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="7fc17-110">Esta seção inclui os seguintes exemplos.</span><span class="sxs-lookup"><span data-stu-id="7fc17-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="7fc17-111">[Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="7fc17-111">[Cancel an Async Task or a List of Tasks (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="7fc17-112">Cancelar tarefas assíncronas após um período (C#)</span><span class="sxs-lookup"><span data-stu-id="7fc17-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="7fc17-113">Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)</span><span class="sxs-lookup"><span data-stu-id="7fc17-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="7fc17-114">Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)</span><span class="sxs-lookup"><span data-stu-id="7fc17-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="7fc17-115">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="7fc17-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="7fc17-116">Os projetos criam uma interface do usuário que contém um botão que inicia o processo e um botão que o cancela, como mostra a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="7fc17-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="7fc17-117">Os botões são chamados `startButton` e `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="7fc17-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="7fc17-118">![Janela do WPF com o botão Cancelar](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancelamento")</span><span class="sxs-lookup"><span data-stu-id="7fc17-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="7fc17-119">É possível baixar projetos completos do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="7fc17-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fc17-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7fc17-120">See Also</span></span>  
 [<span data-ttu-id="7fc17-121">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="7fc17-121">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
