---
title: Obter WorkflowInstanceId
ms.date: 03/30/2017
ms.assetid: bd7eea3b-1c28-4b84-9a67-003bc553aa81
ms.openlocfilehash: 6725ed92bf785e5b7f7d61332944fcce8427388a
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47112251"
---
# <a name="get-workflowinstanceid"></a><span data-ttu-id="c44bb-102">Obter WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="c44bb-102">Get WorkflowInstanceId</span></span>
<span data-ttu-id="c44bb-103">Este exemplo demonstra como usar a atividade personalizado, `GetWorkflowInstanceId` para retornar a identificação de instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c44bb-103">This sample demonstrates how to use the custom activity, `GetWorkflowInstanceId` to return the workflow instance ID.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="c44bb-104">Demonstra</span><span class="sxs-lookup"><span data-stu-id="c44bb-104">Demonstrates</span></span>  
 <span data-ttu-id="c44bb-105">Desenvolvimento personalizado de atividade, como acessar a instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c44bb-105">Custom activity development, how to access the workflow instance.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="c44bb-106">Discussão</span><span class="sxs-lookup"><span data-stu-id="c44bb-106">Discussion</span></span>  
 <span data-ttu-id="c44bb-107">Obter o ID de instância de um fluxo de trabalho em execução exige a escrever código.</span><span class="sxs-lookup"><span data-stu-id="c44bb-107">Getting the instance ID of a running workflow requires writing code.</span></span> <span data-ttu-id="c44bb-108">Se você deseja gravar um fluxo de trabalho totalmente declarativo, você precisa de uma atividade que pode retornar a ID da instância de fluxo de trabalho de forma que a atividade pode ser referenciada no fluxo de trabalho para fornecer uma experiência totalmente declarativa de criação de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c44bb-108">If you want to write a fully-declarative workflow, then you need an activity that can return the workflow instance ID so that the activity can be referenced in the workflow to provide a fully-declarative workflow authoring experience.</span></span> <span data-ttu-id="c44bb-109">Muitos cenários requerem acesso a identificação da instância: alguns exemplos são de log ou auditando fins ou fazendo correlação de nível fornecendo o ID de instância de volta para um cliente para a associação futura (por exemplo, usando esta atividade dentro de uma atividade de SendReply).</span><span class="sxs-lookup"><span data-stu-id="c44bb-109">Many scenarios require access to the instance ID: a few examples are for logging or auditing purposes or for doing application-level correlation by providing the instance ID back to a client for future association (for example, by using this activity inside a SendReply activity).</span></span>  
  
 <span data-ttu-id="c44bb-110">`GetWorkflowInstanceId` é implementado como <xref:System.Activities.CodeActivity%601> porque ele deve retornar um valor do tipo <xref:System.Guid>, e deve ter acesso a <xref:System.Activities.CodeActivityContext> para obter a identificação de instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c44bb-110">`GetWorkflowInstanceId` is implemented as a <xref:System.Activities.CodeActivity%601> because it must return a value of type <xref:System.Guid>, and it must have access to the <xref:System.Activities.CodeActivityContext> for getting the workflow’s instance ID.</span></span> <span data-ttu-id="c44bb-111">A implementação é bastante básica.</span><span class="sxs-lookup"><span data-stu-id="c44bb-111">Its implementation is fairly basic.</span></span>  
  
```  
public sealed class GetWorkflowInstanceId : CodeActivity<Guid>  
{  
protected override Guid Execute(CodeActivityContext context)  
        {  
            return context.WorkflowInstanceId;  
        }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="c44bb-112">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="c44bb-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c44bb-113">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="c44bb-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c44bb-114">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="c44bb-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c44bb-115">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="c44bb-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\GetWorkflowInstanceId`
