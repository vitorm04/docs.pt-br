---
title: "Criando e executando uma instância de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b25acebfaf6df68ac3163a5ef4bcb235077139cc
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="9848d-102">Criando e executando uma instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="9848d-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="9848d-103">Este exemplo mostra como executar uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9848d-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="9848d-104">Mostra como executar forma síncrona e de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="9848d-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="9848d-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="9848d-105">Demonstrates</span></span>  
 <span data-ttu-id="9848d-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="9848d-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="9848d-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="9848d-107">Discussion</span></span>  
 <span data-ttu-id="9848d-108">A primeira parte do exemplo usa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="9848d-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="9848d-109">Esta é a maneira mais básica de executar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9848d-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="9848d-110">Fluxos de trabalho executados com <xref:System.Activities.WorkflowInvoker.Invoke%2A> são executados synchronously.</span><span class="sxs-lookup"><span data-stu-id="9848d-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="9848d-111">A segunda parte do exemplo usa a classe de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="9848d-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="9848d-112"><xref:System.Activities.WorkflowApplication> permite que você ter mais controle sobre cada instância, incluindo a capacidade de interagir com o fluxo de trabalho em execução e executar de forma assíncrona o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="9848d-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9848d-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9848d-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9848d-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9848d-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9848d-115">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9848d-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9848d-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9848d-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="9848d-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9848d-117">See Also</span></span>  
 [<span data-ttu-id="9848d-118">Usando WorkflowInvoker e WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="9848d-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
