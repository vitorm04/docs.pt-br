---
title: Criando e executando uma instância de fluxo de trabalho
ms.date: 03/30/2017
ms.assetid: 19d27f47-0491-4569-8f53-51bc1d940e80
ms.openlocfilehash: d895cfa9e924ecf4d1571cf67f1c1e7069e25da5
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715198"
---
# <a name="creating-and-running-a-workflow-instance"></a><span data-ttu-id="1bff8-102">Criando e executando uma instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="1bff8-102">Creating and Running a Workflow Instance</span></span>

<span data-ttu-id="1bff8-103">Este exemplo mostra como executar uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1bff8-103">This sample shows how to run a workflow instance.</span></span> <span data-ttu-id="1bff8-104">Mostra como executar forma síncrona e de forma assíncrona.</span><span class="sxs-lookup"><span data-stu-id="1bff8-104">It shows how to execute it synchronously and asynchronously.</span></span>

## <a name="demonstrates"></a><span data-ttu-id="1bff8-105">Demonstra</span><span class="sxs-lookup"><span data-stu-id="1bff8-105">Demonstrates</span></span>

<span data-ttu-id="1bff8-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="1bff8-106"><xref:System.Activities.WorkflowInvoker>, <xref:System.Activities.WorkflowApplication>.</span></span>

## <a name="discussion"></a><span data-ttu-id="1bff8-107">Discussão</span><span class="sxs-lookup"><span data-stu-id="1bff8-107">Discussion</span></span>

<span data-ttu-id="1bff8-108">A primeira parte do exemplo usa <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span><span class="sxs-lookup"><span data-stu-id="1bff8-108">The first part of the sample uses <xref:System.Activities.WorkflowInvoker.Invoke%2A>.</span></span> <span data-ttu-id="1bff8-109">Esta é a maneira mais básica de executar um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1bff8-109">This is the most basic way to execute a workflow.</span></span> <span data-ttu-id="1bff8-110">Fluxos de trabalho executados com <xref:System.Activities.WorkflowInvoker.Invoke%2A> são executados synchronously.</span><span class="sxs-lookup"><span data-stu-id="1bff8-110">Workflows executed with <xref:System.Activities.WorkflowInvoker.Invoke%2A> are executed synchronously.</span></span>

<span data-ttu-id="1bff8-111">A segunda parte do exemplo usa a classe de <xref:System.Activities.WorkflowApplication> .</span><span class="sxs-lookup"><span data-stu-id="1bff8-111">The second part of the sample uses the <xref:System.Activities.WorkflowApplication> class.</span></span> <span data-ttu-id="1bff8-112"><xref:System.Activities.WorkflowApplication> permite que você ter mais controle sobre cada instância, incluindo a capacidade de interagir com o fluxo de trabalho em execução e executar de forma assíncrona o fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="1bff8-112"><xref:System.Activities.WorkflowApplication> enables you to have more control over each instance, including the ability to interact with the running workflow and to run the workflow asynchronously.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bff8-113">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="1bff8-113">The samples may already be installed on your machine.</span></span> <span data-ttu-id="1bff8-114">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="1bff8-114">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="1bff8-115">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="1bff8-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="1bff8-116">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="1bff8-116">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\CreatingWorkflowInstances`

## <a name="see-also"></a><span data-ttu-id="1bff8-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bff8-117">See also</span></span>

- [<span data-ttu-id="1bff8-118">Usando WorkflowInvoker e WorkflowApplication</span><span class="sxs-lookup"><span data-stu-id="1bff8-118">Using WorkflowInvoker and WorkflowApplication</span></span>](../using-workflowinvoker-and-workflowapplication.md)
