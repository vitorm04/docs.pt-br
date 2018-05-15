---
title: Guia de Introdução Tutorial2
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 7e1bfdc79eda8095d5d391afd61abb8473d8e7ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="25a8c-102">Guia de introdução ao tutorial</span><span class="sxs-lookup"><span data-stu-id="25a8c-102">Getting Started Tutorial</span></span>
<span data-ttu-id="25a8c-103">Esta seção contém um conjunto de tópicos de instruções passo a passo que apresentam para programação de aplicativos do Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="25a8c-103">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="25a8c-104">Siga os procedimentos deste tópico para criar um aplicativo que é um jogo de adivinhação de números.</span><span class="sxs-lookup"><span data-stu-id="25a8c-104">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="25a8c-105">O primeiro tópico no tutorial conduziu pelas etapas para criar as atividades personalizadas necessárias para o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="25a8c-105">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="25a8c-106">No segundo tópico, estas atividades são montadas junto com atividades internas de fluxo de trabalho em um fluxo de trabalho de fluxograma.</span><span class="sxs-lookup"><span data-stu-id="25a8c-106">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="25a8c-107">No terceiro tópico, o aplicativo host é configurado para executar o fluxo de trabalho e, no tópico final, é apresentada a persistência.</span><span class="sxs-lookup"><span data-stu-id="25a8c-107">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="25a8c-108">Cada etapa neste processo depende das etapas anteriores. Portanto, é recomendável que você as conclua na ordem.</span><span class="sxs-lookup"><span data-stu-id="25a8c-108">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="25a8c-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="25a8c-109">In This Section</span></span>  
 [<span data-ttu-id="25a8c-110">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="25a8c-110">How to: Create an Activity</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)  
 <span data-ttu-id="25a8c-111">Descreve como criar uma atividade personalizada que deriva de <xref:System.Activities.NativeActivity%601>, e como compor essa atividade junto com uma atividade interna em uma atividade composta usando o designer de atividade.</span><span class="sxs-lookup"><span data-stu-id="25a8c-111">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="25a8c-112">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="25a8c-112">How to: Create a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow.md)  
 <span data-ttu-id="25a8c-113">Descreve como criar fluxos de trabalho de fluxograma, sequenciais e de máquina de estado usando atividades internas e atividades personalizadas do tutorial anterior.</span><span class="sxs-lookup"><span data-stu-id="25a8c-113">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="25a8c-114">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="25a8c-114">How to: Run a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-run-a-workflow.md)  
 <span data-ttu-id="25a8c-115">Descreve como chamar um fluxo de trabalho de um ambiente de host, transmitir dados para dentro e para fora de um fluxo de trabalho e como retomar indicadores.</span><span class="sxs-lookup"><span data-stu-id="25a8c-115">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="25a8c-116">Como criar e executar um fluxo de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="25a8c-116">How to: Create and Run a Long Running Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="25a8c-117">Descreve como adicionar persistência a um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="25a8c-117">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="25a8c-118">Como criar um participante de acompanhamento personalizado</span><span class="sxs-lookup"><span data-stu-id="25a8c-118">How to: Create a Custom Tracking Participant</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="25a8c-119">Descreve como criar um participante de rastreamento personalizado e um perfil de controle.</span><span class="sxs-lookup"><span data-stu-id="25a8c-119">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="25a8c-120">Como hospedar várias versões de um fluxo de trabalho lado a lado</span><span class="sxs-lookup"><span data-stu-id="25a8c-120">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="25a8c-121">Descreve como usar `WorkflowIdentity` para hospedar várias versões de um fluxo de trabalho lado a lado.</span><span class="sxs-lookup"><span data-stu-id="25a8c-121">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="25a8c-122">Como atualizar a definição de uma instância de fluxo de trabalho em execução</span><span class="sxs-lookup"><span data-stu-id="25a8c-122">How to: Update the Definition of a Running Workflow Instance</span></span>](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="25a8c-123">Descreve como usar a atualização dinâmica para modificar instâncias de fluxo de trabalho em execução.</span><span class="sxs-lookup"><span data-stu-id="25a8c-123">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a8c-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25a8c-124">See Also</span></span>  
 [<span data-ttu-id="25a8c-125">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="25a8c-125">Windows Workflow Foundation Programming</span></span>](../../../docs/framework/windows-workflow-foundation/programming.md)
