---
title: Ajustando seu aplicativo Async (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 6e919d3998719186d0355b9bd187782fcb0e5332
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696670"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="d232d-102">Ajustando seu aplicativo Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d232d-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="d232d-103">É possível adicionar flexibilidade e precisão a seus aplicativos assíncronos usando os métodos e propriedades que o tipo <xref:System.Threading.Tasks.Task> disponibiliza.</span><span class="sxs-lookup"><span data-stu-id="d232d-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="d232d-104">Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken> e métodos de `Task` importantes como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d232d-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d232d-105">Usando `WhenAny` e `WhenAll`, é possível, com facilidade, iniciar várias tarefas e aguardar sua conclusão monitorando uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="d232d-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="d232d-106">`WhenAny` retorna uma tarefa que é concluída quando qualquer tarefa em uma coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="d232d-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="d232d-107">Para obter exemplos que usam `WhenAny`, consulte [Cancelar assíncrono as tarefas restantes após uma for concluída (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)e [iniciar várias tarefas assíncronas e processo-los como eles completo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="d232d-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="d232d-108">`WhenAll` retorna uma tarefa que é concluída quando todas as tarefas em uma coleção forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="d232d-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="d232d-109">Para obter mais informações e um exemplo que usa `WhenAll`, consulte [como: estender a Async Walkthrough por usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="d232d-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="d232d-110">Esta seção inclui os seguintes exemplos.</span><span class="sxs-lookup"><span data-stu-id="d232d-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="d232d-111">[Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="d232d-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="d232d-112">Cancelar tarefas assíncronas após um período de tempo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d232d-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="d232d-113">Cancelar as demais tarefas assíncronas após um completo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d232d-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="d232d-114">Iniciar várias tarefas assíncronas e processá-las na conclusão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d232d-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="d232d-115">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="d232d-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="d232d-116">Os projetos criam uma interface do usuário que contém um botão que inicia o processo e um botão que o cancela, como mostra a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="d232d-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="d232d-117">Os botões são chamados `startButton` e `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="d232d-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="d232d-118">![Janela do WPF com o botão Cancelar](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancelamento")</span><span class="sxs-lookup"><span data-stu-id="d232d-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="d232d-119">É possível baixar projetos completos do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="d232d-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d232d-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d232d-120">See Also</span></span>  
 [<span data-ttu-id="d232d-121">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d232d-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
