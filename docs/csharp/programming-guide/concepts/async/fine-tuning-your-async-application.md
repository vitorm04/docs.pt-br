---
title: Ajuste fino de seu aplicativo assíncrono (C#)
ms.date: 07/20/2015
ms.assetid: 97696eb9-81fc-4940-9655-84daa8eb4d5c
ms.openlocfilehash: cff50e62ff62b70e97e7ea6e03714326d774e407
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73970237"
---
# <a name="fine-tuning-your-async-application-c"></a><span data-ttu-id="48ad8-102">Ajuste fino de seu aplicativo assíncrono (C#)</span><span class="sxs-lookup"><span data-stu-id="48ad8-102">Fine-Tuning Your Async Application (C#)</span></span>
<span data-ttu-id="48ad8-103">É possível adicionar flexibilidade e precisão a seus aplicativos assíncronos usando os métodos e propriedades que o tipo <xref:System.Threading.Tasks.Task> disponibiliza.</span><span class="sxs-lookup"><span data-stu-id="48ad8-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="48ad8-104">Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken> e métodos de `Task` importantes como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="48ad8-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="48ad8-105">Usando `WhenAny` e `WhenAll`, é possível, com facilidade, iniciar várias tarefas e aguardar sua conclusão monitorando uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="48ad8-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="48ad8-106">`WhenAny` retorna uma tarefa que é concluída quando qualquer tarefa em uma coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="48ad8-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="48ad8-107">Para obter exemplos que usam `WhenAny`, consulte [Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) e [Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="48ad8-107">For examples that use `WhenAny`, see [Cancel Remaining Async Tasks after One Is Complete (C#)](./cancel-remaining-async-tasks-after-one-is-complete.md) and [Start Multiple Async Tasks and Process Them As They Complete (C#)](./start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="48ad8-108">`WhenAll` retorna uma tarefa que é concluída quando todas as tarefas em uma coleção forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="48ad8-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="48ad8-109">Para obter mais informações `WhenAll`e um exemplo que use, consulte [Como estender o passo a passo async usando Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="48ad8-109">For more information and an example that uses `WhenAll`, see [How to extend the async walkthrough by using Task.WhenAll (C#)](./how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>
  
 <span data-ttu-id="48ad8-110">Esta seção inclui os seguintes exemplos.</span><span class="sxs-lookup"><span data-stu-id="48ad8-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="48ad8-111">[Cancele uma tarefa de sincronização ou uma lista de tarefas (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="48ad8-111">[Cancel an Async Task or a List of Tasks (C#)](./cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="48ad8-112">Cancelar tarefas de assync após um período de tempo (C#)</span><span class="sxs-lookup"><span data-stu-id="48ad8-112">Cancel Async Tasks after a Period of Time (C#)</span></span>](./cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="48ad8-113">Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)</span><span class="sxs-lookup"><span data-stu-id="48ad8-113">Cancel Remaining Async Tasks after One Is Complete (C#)</span></span>](./cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="48ad8-114">Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)</span><span class="sxs-lookup"><span data-stu-id="48ad8-114">Start Multiple Async Tasks and Process Them As They Complete (C#)</span></span>](./start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="48ad8-115">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="48ad8-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="48ad8-116">Os projetos criam uma interface do usuário que contém um botão que inicia o processo e um botão que o cancela, como mostra a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="48ad8-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="48ad8-117">Os botões são chamados `startButton` e `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="48ad8-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="48ad8-118">![Janela WPF com botão Cancelar](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Caixa de diálogo com um botão Iniciar e Parar")</span><span class="sxs-lookup"><span data-stu-id="48ad8-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="48ad8-119">É possível baixar projetos completos do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="48ad8-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48ad8-120">Confira também</span><span class="sxs-lookup"><span data-stu-id="48ad8-120">See also</span></span>

- [<span data-ttu-id="48ad8-121">Programação Assíncrona com assincronia e espera (C#)</span><span class="sxs-lookup"><span data-stu-id="48ad8-121">Asynchronous Programming with async and await (C#)</span></span>](./index.md)
