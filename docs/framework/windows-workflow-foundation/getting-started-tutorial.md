---
title: Introdução Tutorial2
description: Este artigo inicia uma sequência de tutoriais que apresentam a programação de Windows Workflow Foundation aplicativos.
ms.date: 03/30/2017
helpviewer_keywords:
- WF [WF], getting started
- Windows Workflow Foundation [WF], getting started
ms.assetid: c2d3585f-6b1a-4d4f-9865-bd7cd31c5d42
ms.openlocfilehash: 148ba77231067bf5f8ff1d8b444b83d951ce8761
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419844"
---
# <a name="getting-started-tutorial"></a><span data-ttu-id="4f74b-103">Guia de introdução ao tutorial</span><span class="sxs-lookup"><span data-stu-id="4f74b-103">Getting Started Tutorial</span></span>
<span data-ttu-id="4f74b-104">Esta seção contém um conjunto de tópicos explicativos que apresentam a programação de aplicativos Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="4f74b-104">This section contains a set of walkthrough topics that introduce you to programming Windows Workflow Foundation (WF) applications.</span></span> <span data-ttu-id="4f74b-105">Siga os procedimentos deste tópico para criar um aplicativo que é um jogo de adivinhação de números.</span><span class="sxs-lookup"><span data-stu-id="4f74b-105">By following the procedures in these topics, you will build an application that is a number guessing game.</span></span> <span data-ttu-id="4f74b-106">O primeiro tópico no tutorial conduziu pelas etapas para criar as atividades personalizadas necessárias para o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f74b-106">The first topic in the tutorial leads you through the steps to create the custom activities required for the workflow.</span></span> <span data-ttu-id="4f74b-107">No segundo tópico, estas atividades são montadas junto com atividades internas de fluxo de trabalho em um fluxo de trabalho de fluxograma.</span><span class="sxs-lookup"><span data-stu-id="4f74b-107">In the second topic, these activities are assembled along with built-in workflow activities into a flowchart workflow.</span></span> <span data-ttu-id="4f74b-108">No terceiro tópico, o aplicativo host é configurado para executar o fluxo de trabalho e, no tópico final, é apresentada a persistência.</span><span class="sxs-lookup"><span data-stu-id="4f74b-108">In the third topic, the host application is configured to run the workflow, and in the final topic persistence is introduced.</span></span> <span data-ttu-id="4f74b-109">Cada etapa neste processo depende das etapas anteriores. Portanto, é recomendável que você as conclua na ordem.</span><span class="sxs-lookup"><span data-stu-id="4f74b-109">Each step in this process depends on the previous steps, so we recommend that you complete them in order.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f74b-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4f74b-110">In This Section</span></span>  
 [<span data-ttu-id="4f74b-111">Como criar uma atividade</span><span class="sxs-lookup"><span data-stu-id="4f74b-111">How to: Create an Activity</span></span>](how-to-create-an-activity.md)  
 <span data-ttu-id="4f74b-112">Descreve como criar uma atividade personalizada que deriva de <xref:System.Activities.NativeActivity%601>, e como compor essa atividade junto com uma atividade interna em uma atividade composta usando o designer de atividade.</span><span class="sxs-lookup"><span data-stu-id="4f74b-112">Describes how to create a custom activity that derives from <xref:System.Activities.NativeActivity%601>, and how to compose this activity along with a built-in activity into a composite activity using the activity designer.</span></span>  
  
 [<span data-ttu-id="4f74b-113">Como criar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f74b-113">How to: Create a Workflow</span></span>](how-to-create-a-workflow.md)  
 <span data-ttu-id="4f74b-114">Descreve como criar fluxos de trabalho de fluxograma, sequenciais e de máquina de estado usando atividades internas e atividades personalizadas do tutorial anterior.</span><span class="sxs-lookup"><span data-stu-id="4f74b-114">Describes how to create flowchart, sequential, and state machine workflows by using built-in activities and the custom activities from the preceding tutorial.</span></span>  
  
 [<span data-ttu-id="4f74b-115">Como executar um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="4f74b-115">How to: Run a Workflow</span></span>](how-to-run-a-workflow.md)  
 <span data-ttu-id="4f74b-116">Descreve como chamar um fluxo de trabalho de um ambiente de host, transmitir dados para dentro e para fora de um fluxo de trabalho e como retomar indicadores.</span><span class="sxs-lookup"><span data-stu-id="4f74b-116">Describes how to invoke a workflow from a host environment, pass data into and out of a workflow, and how to resume bookmarks.</span></span>  
  
 [<span data-ttu-id="4f74b-117">Como criar e executar um fluxo de trabalho de execução longa</span><span class="sxs-lookup"><span data-stu-id="4f74b-117">How to: Create and Run a Long Running Workflow</span></span>](how-to-create-and-run-a-long-running-workflow.md)  
 <span data-ttu-id="4f74b-118">Descreve como adicionar persistência a um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="4f74b-118">Describes how to add persistence to a workflow application.</span></span>  
  
 [<span data-ttu-id="4f74b-119">Como criar um participante de acompanhamento personalizado</span><span class="sxs-lookup"><span data-stu-id="4f74b-119">How to: Create a Custom Tracking Participant</span></span>](how-to-create-a-custom-tracking-participant.md)  
 <span data-ttu-id="4f74b-120">Descreve como criar um participante de rastreamento personalizado e um perfil de controle.</span><span class="sxs-lookup"><span data-stu-id="4f74b-120">Describes how to create a custom tracking participant and tracking profile.</span></span>  
  
 [<span data-ttu-id="4f74b-121">Como hospedar várias versões de um fluxo de trabalho lado a lado</span><span class="sxs-lookup"><span data-stu-id="4f74b-121">How to: Host Multiple Versions of a Workflow Side-by-Side</span></span>](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)  
 <span data-ttu-id="4f74b-122">Descreve como usar `WorkflowIdentity` para hospedar várias versões de um fluxo de trabalho lado a lado.</span><span class="sxs-lookup"><span data-stu-id="4f74b-122">Describes how to use `WorkflowIdentity` to host multiple versions of a workflow side-by-side.</span></span>  
  
 [<span data-ttu-id="4f74b-123">Como atualizar a definição de uma instância de fluxo de trabalho em execução</span><span class="sxs-lookup"><span data-stu-id="4f74b-123">How to: Update the Definition of a Running Workflow Instance</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md)  
 <span data-ttu-id="4f74b-124">Descreve como usar a atualização dinâmica para modificar instâncias de fluxo de trabalho em execução.</span><span class="sxs-lookup"><span data-stu-id="4f74b-124">Describes how to use dynamic update to modify running workflow instances.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f74b-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="4f74b-125">See also</span></span>

- [<span data-ttu-id="4f74b-126">Programação do Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="4f74b-126">Windows Workflow Foundation Programming</span></span>](programming.md)
