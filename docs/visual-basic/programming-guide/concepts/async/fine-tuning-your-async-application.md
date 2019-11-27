---
title: Ajustando seu aplicativo Async
ms.date: 07/20/2015
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
ms.openlocfilehash: 51786993cf16cd12b39cde3d47832191b3fdca8d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345830"
---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="881ee-102">Ajuste fino do seu aplicativo assíncrono (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="881ee-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="881ee-103">É possível adicionar flexibilidade e precisão a seus aplicativos assíncronos usando os métodos e propriedades que o tipo <xref:System.Threading.Tasks.Task> disponibiliza.</span><span class="sxs-lookup"><span data-stu-id="881ee-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="881ee-104">Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken> e métodos de `Task` importantes como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="881ee-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="881ee-105">Usando `WhenAny` e `WhenAll`, é possível, com facilidade, iniciar várias tarefas e aguardar sua conclusão monitorando uma única tarefa.</span><span class="sxs-lookup"><span data-stu-id="881ee-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
- <span data-ttu-id="881ee-106">`WhenAny` retorna uma tarefa que é concluída quando qualquer tarefa em uma coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="881ee-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="881ee-107">Para obter exemplos que usam `WhenAny`, consulte [Cancelar tarefas assíncronas restantes após uma conclusão (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)e [iniciar várias tarefas assíncronas e processá-las à medida que elas forem concluídas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="881ee-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
- <span data-ttu-id="881ee-108">`WhenAll` retorna uma tarefa que é concluída quando todas as tarefas em uma coleção forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="881ee-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="881ee-109">Para obter mais informações e um exemplo que usa `WhenAll`, consulte [como: estender a explicação assíncrona usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="881ee-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="881ee-110">Esta seção inclui os seguintes exemplos.</span><span class="sxs-lookup"><span data-stu-id="881ee-110">This section includes the following examples.</span></span>  
  
- <span data-ttu-id="881ee-111">[Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="881ee-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
- [<span data-ttu-id="881ee-112">Cancelar tarefas assíncronas após um período de tempo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="881ee-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
- [<span data-ttu-id="881ee-113">Cancelar as tarefas assíncronas restantes após uma conclusão (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="881ee-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
- [<span data-ttu-id="881ee-114">Iniciar várias tarefas assíncronas e processá-las à medida que elas forem concluídas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="881ee-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
> <span data-ttu-id="881ee-115">Para executar os exemplos, você precisa ter o Visual Studio 2012 ou uma versão mais recente e o .NET Framework 4.5 ou posterior instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="881ee-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="881ee-116">Os projetos criam uma interface do usuário que contém um botão que inicia o processo e um botão que o cancela, como mostra a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="881ee-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="881ee-117">Os botões são chamados `startButton` e `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="881ee-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="881ee-118">![Janela do WPF com o botão Cancelar](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Caixa de diálogo com um botão Iniciar e parar")</span><span class="sxs-lookup"><span data-stu-id="881ee-118">![WPF window with Cancel button](./media/fine-tuning-your-async-application/cancellation-and-start-button.png "Dialog box with a Start and Stop button")</span></span>  
  
 <span data-ttu-id="881ee-119">É possível baixar projetos completos do WPF (Windows Presentation Foundation) em [Exemplo assíncrono: ajuste fino de seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span><span class="sxs-lookup"><span data-stu-id="881ee-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="881ee-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="881ee-120">See also</span></span>

- [<span data-ttu-id="881ee-121">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="881ee-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
