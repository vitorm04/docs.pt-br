---
title: 'Como: Criar um fluxo de trabalho'
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: e54dcc240a12100650bacbc355895a043c68c117
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415657"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="cfdd8-102">Como: Criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="cfdd8-102">How to: Create a Workflow</span></span>
<span data-ttu-id="cfdd8-103">Os fluxos de trabalho podem ser construídos a partir de atividades internas assim como as atividades personalizadas.</span><span class="sxs-lookup"><span data-stu-id="cfdd8-103">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="cfdd8-104">Os tópicos nesta seção passa pela criação de um fluxo de trabalho usa atividades internas, como o <xref:System.Activities.Statements.Flowchart> atividade e atividades personalizadas do anterior [como: Criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) tópico.</span><span class="sxs-lookup"><span data-stu-id="cfdd8-104">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="cfdd8-105">O fluxo de trabalho modela um jogo de palpite de número.</span><span class="sxs-lookup"><span data-stu-id="cfdd8-105">The workflow models a number guessing game.</span></span> <span data-ttu-id="cfdd8-106">Somente um dos tópicos nesta seção é necessário para concluir o tutorial; você deve escolher o estilo que os interesses você e seguem essa etapa.</span><span class="sxs-lookup"><span data-stu-id="cfdd8-106">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="cfdd8-107">No entanto, você pode concluir todos os tópicos se desejado.</span><span class="sxs-lookup"><span data-stu-id="cfdd8-107">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfdd8-108">Cada tópico do tutorial de Introdução depende dos tópicos anteriores.</span><span class="sxs-lookup"><span data-stu-id="cfdd8-108">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="cfdd8-109">Para concluir este tópico, você deve primeiro concluir [como: Criar uma atividade](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span><span class="sxs-lookup"><span data-stu-id="cfdd8-109">To complete this topic, you must first complete [How to: Create an Activity](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cfdd8-110">Para baixar uma versão completa do tutorial, consulte [Windows Workflow Foundation (WF45) - Tutorial de Introdução](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="cfdd8-110">To download a completed version of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfdd8-111">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cfdd8-111">In This Section</span></span>  
 [<span data-ttu-id="cfdd8-112">Como: Criar um fluxo de trabalho sequencial</span><span class="sxs-lookup"><span data-stu-id="cfdd8-112">How to: Create a Sequential Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="cfdd8-113">Descreve como criar um fluxo de trabalho sequencial usando a atividade de <xref:System.Activities.Statements.Sequence> .</span><span class="sxs-lookup"><span data-stu-id="cfdd8-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="cfdd8-114">Como: Criar um fluxo de trabalho de fluxograma</span><span class="sxs-lookup"><span data-stu-id="cfdd8-114">How to: Create a Flowchart Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="cfdd8-115">Descreve como criar um fluxo de trabalho do fluxograma usando a atividade de <xref:System.Activities.Statements.Flowchart> .</span><span class="sxs-lookup"><span data-stu-id="cfdd8-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="cfdd8-116">Como: Criar um fluxo de trabalho de máquina de estado</span><span class="sxs-lookup"><span data-stu-id="cfdd8-116">How to: Create a State Machine Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="cfdd8-117">Descreve como criar um fluxo de trabalho do computador de estado usando a atividade de <xref:System.Activities.Statements.StateMachine> .</span><span class="sxs-lookup"><span data-stu-id="cfdd8-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfdd8-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cfdd8-118">See Also</span></span>  
 [<span data-ttu-id="cfdd8-119">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="cfdd8-119">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
