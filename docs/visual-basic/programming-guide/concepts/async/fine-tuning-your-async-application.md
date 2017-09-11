---
title: Ajustando seu aplicativo Async (Visual Basic) | Documentos do Microsoft
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 4c3e7997-a95f-4fbe-a6ac-60ba042d30b9
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e031c2e23430a62629424ee57a140a7d8da41777
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="fine-tuning-your-async-application-visual-basic"></a><span data-ttu-id="e40d5-102">Ajustando seu aplicativo Async (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e40d5-102">Fine-Tuning Your Async Application (Visual Basic)</span></span>
<span data-ttu-id="e40d5-103">Você pode adicionar flexibilidade e precisão aos seus aplicativos assíncronos usando os métodos e propriedades que o <xref:System.Threading.Tasks.Task>tipo disponibiliza.</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="e40d5-103">You can add precision and flexibility to your async applications by using the methods and properties that the <xref:System.Threading.Tasks.Task> type makes available.</span></span> <span data-ttu-id="e40d5-104">Os tópicos nesta seção mostram exemplos que usam <xref:System.Threading.CancellationToken>e importante `Task` métodos como <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName>e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName> </xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> </xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="e40d5-104">The topics in this section show examples that use <xref:System.Threading.CancellationToken> and important `Task` methods such as <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="e40d5-105">Usando `WhenAny` e `WhenAll`, você pode iniciar várias tarefas e aguardar sua conclusão por uma única tarefa de monitoramento mais facilmente.</span><span class="sxs-lookup"><span data-stu-id="e40d5-105">By using `WhenAny` and `WhenAll`, you can more easily start multiple tasks and await their completion by monitoring a single task.</span></span>  
  
-   <span data-ttu-id="e40d5-106">`WhenAny`Retorna uma tarefa concluída quando qualquer tarefa em uma coleção for concluída.</span><span class="sxs-lookup"><span data-stu-id="e40d5-106">`WhenAny` returns a task that completes when any task in a collection is complete.</span></span>  
  
     <span data-ttu-id="e40d5-107">Para obter exemplos que usam `WhenAny`, consulte [Cancelar tarefas de Async restantes após um é concluído (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)e [iniciar várias tarefas assíncronas e processo-los como eles completo (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="e40d5-107">For examples that use `WhenAny`, see  [Cancel Remaining Async Tasks after One Is Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)and [Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>  
  
-   <span data-ttu-id="e40d5-108">`WhenAll`Retorna uma tarefa concluída quando todas as tarefas em uma coleção forem concluídas.</span><span class="sxs-lookup"><span data-stu-id="e40d5-108">`WhenAll` returns a task that completes when all tasks in a collection are complete.</span></span>  
  
     <span data-ttu-id="e40d5-109">Para obter mais informações e um exemplo que usa `WhenAll`, consulte [como: estender o Async Walkthrough por usando Task. WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span><span class="sxs-lookup"><span data-stu-id="e40d5-109">For more information and an example that uses `WhenAll`, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="e40d5-110">Esta seção inclui os exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="e40d5-110">This section includes the following examples.</span></span>  
  
-   <span data-ttu-id="e40d5-111">[Cancelar uma tarefa assíncrona ou uma lista de tarefas (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span><span class="sxs-lookup"><span data-stu-id="e40d5-111">[Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md).</span></span>  
  
-   [<span data-ttu-id="e40d5-112">Cancelar tarefas assíncronas após um período de tempo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e40d5-112">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)  
  
-   [<span data-ttu-id="e40d5-113">Cancelar as demais tarefas assíncronas após um completo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e40d5-113">Cancel Remaining Async Tasks after One Is Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)  
  
-   [<span data-ttu-id="e40d5-114">Iniciar várias tarefas assíncronas e processá-las assim que são concluídas (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e40d5-114">Start Multiple Async Tasks and Process Them As They Complete (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)  
  
> [!NOTE]
>  <span data-ttu-id="e40d5-115">Para executar os exemplos, você deve ter o Visual Studio 2012 ou mais recente e o .NET Framework 4.5 ou posterior esteja instalado no computador.</span><span class="sxs-lookup"><span data-stu-id="e40d5-115">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
 <span data-ttu-id="e40d5-116">Os projetos de criar uma interface do usuário que contém um botão que inicia o processo e um botão cancela, como mostra a imagem a seguir.</span><span class="sxs-lookup"><span data-stu-id="e40d5-116">The projects create a UI that contains a button that starts the process and a button that cancels it, as the following image shows.</span></span> <span data-ttu-id="e40d5-117">Os botões são nomeados `startButton` e `cancelButton`.</span><span class="sxs-lookup"><span data-stu-id="e40d5-117">The buttons are named `startButton` and `cancelButton`.</span></span>  
  
 <span data-ttu-id="e40d5-118">![Janela WPF com o botão Cancelar](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "cancelamento")</span><span class="sxs-lookup"><span data-stu-id="e40d5-118">![WPF window with Cancel button](../../../../csharp/programming-guide/concepts/async/media/cancellation.png "Cancellation")</span></span>  
  
 <span data-ttu-id="e40d5-119">Você pode baixar os projetos Windows Presentation Foundation (WPF) completa de [exemplo de assincronia: bem ajustando seu aplicativo](http://go.microsoft.com/fwlink/?LinkId=255046).</span><span class="sxs-lookup"><span data-stu-id="e40d5-119">You can download the complete Windows Presentation Foundation (WPF) projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e40d5-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e40d5-120">See Also</span></span>  
 [<span data-ttu-id="e40d5-121">Programação assíncrona com Async e Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e40d5-121">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
