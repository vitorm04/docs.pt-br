---
title: Criando e executando uma instância de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: f2bdfce0b311da6dd20aac5e0fe4f5fbcd14f68a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005297"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="d25cf-102">Criando e executando uma instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d25cf-102">Creating and Running a Workflow Instance</span></span>
<span data-ttu-id="d25cf-103">Este exemplo mostra como executar uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d25cf-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="d25cf-104">Mostra como executar forma síncrona e de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="d25cf-104">It shows how to execute it synchronously and asynchronously.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="d25cf-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="d25cf-105">Demonstrates</span></span>  
 <span data-ttu-id="d25cf-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="d25cf-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="d25cf-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="d25cf-107">Discussion</span></span>  
 <span data-ttu-id="d25cf-108">A primeira parte do exemplo usa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="d25cf-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="d25cf-109">Esta é a maneira mais básica de executar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d25cf-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="d25cf-110">Fluxos de trabalho executados com <xref:System.Activities.WorkflowInvoker.Invoke%2A> são executados synchronously.</span><span class="sxs-lookup"><span data-stu-id="d25cf-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>  
  
 <span data-ttu-id="d25cf-111">A segunda parte do exemplo usa a classe de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="d25cf-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="d25cf-112"><xref:System.Activities.WorkflowApplication> permite que você ter mais controle sobre cada instância, incluindo a capacidade de interagir com o fluxo de trabalho em execução e executar de forma assíncrona o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d25cf-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d25cf-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d25cf-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d25cf-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d25cf-114">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d25cf-115">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d25cf-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d25cf-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d25cf-116">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`  
  
## <a name="see-also"></a><span data-ttu-id="d25cf-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d25cf-117">See also</span></span>

- [<span data-ttu-id="d25cf-118">Usando WorkflowInvoker e WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="d25cf-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
