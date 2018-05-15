---
title: Criando e executando uma instância de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: 3bfcde3dd635820fa66d639134a43e5e43186c17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="1231b-102">Criando e executando uma instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1231b-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="1231b-103">Este exemplo mostra como executar uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1231b-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="1231b-104">Mostra como executar forma síncrona e de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="1231b-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="1231b-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="1231b-105">Demonstrates</span></span>  
 <span data-ttu-id="1231b-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="1231b-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="1231b-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="1231b-107">Discussion</span></span>  
 <span data-ttu-id="1231b-108">A primeira parte do exemplo usa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="1231b-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="1231b-109">Esta é a maneira mais básica de executar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1231b-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="1231b-110">Fluxos de trabalho executados com <xref:System.Activities.WorkflowInvoker.Invoke%2A> são executados synchronously.</span><span class="sxs-lookup"><span data-stu-id="1231b-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="1231b-111">A segunda parte do exemplo usa a classe de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="1231b-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="1231b-112"><xref:System.Activities.WorkflowApplication> permite que você ter mais controle sobre cada instância, incluindo a capacidade de interagir com o fluxo de trabalho em execução e executar de forma assíncrona o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1231b-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="1231b-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1231b-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1231b-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1231b-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="1231b-115">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="1231b-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1231b-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1231b-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="1231b-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1231b-117">See Also</span></span>  
 [<span data-ttu-id="1231b-118">Usando WorkflowInvoker e WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="1231b-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md)
