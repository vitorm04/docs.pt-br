---
title: Biblioteca de Atividades
ms.date: 03/30/2017
ms.assetid: 5323e9d4-71d6-47eb-bfa6-31feac62044d
ms.openlocfilehash: fae2a94b5e5e776625aa7f26700980640b66afd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142895"
---
# <a name="activity-library"></a><span data-ttu-id="3d6c0-102">Biblioteca de Atividades</span><span class="sxs-lookup"><span data-stu-id="3d6c0-102">Activity Library</span></span>
<span data-ttu-id="3d6c0-103">Esta seção contém amostras que demonstram atividades personalizadas avançadas no Windows Workflow Foundation (WF).</span><span class="sxs-lookup"><span data-stu-id="3d6c0-103">This section contains samples that demonstrate advanced custom activities in Windows Workflow Foundation (WF).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3d6c0-104">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3d6c0-104">In This Section</span></span>

 [<span data-ttu-id="3d6c0-105">Atividade personalizado de SendMail</span><span class="sxs-lookup"><span data-stu-id="3d6c0-105">SendMail Custom Activity</span></span>](sendmail-custom-activity.md)  
 <span data-ttu-id="3d6c0-106">Demonstra como criar uma atividade personalizada que derive de <xref:System.Activities.AsyncCodeActivity> para enviar email SMTP usando para uso em um aplicativo de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3d6c0-106">Demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span>  
  
 [<span data-ttu-id="3d6c0-107">Paralelo estrangulado ForEach</span><span class="sxs-lookup"><span data-stu-id="3d6c0-107">Throttled Parallel ForEach</span></span>](throttled-parallel-foreach.md)  
 <span data-ttu-id="3d6c0-108">Demonstra como atividade de `ThrottleParallelForEach` é semelhante à atividade de <xref:System.Activities.Statements.ParallelForEach%601> com uma exceção que permite que define um fator de simultaneidade para restringir o número de ramificações simultâneas para executar.</span><span class="sxs-lookup"><span data-stu-id="3d6c0-108">Demonstrates how the `ThrottleParallelForEach` activity is similar to the <xref:System.Activities.Statements.ParallelForEach%601> activity with the one exception that it allows setting a concurrency factor to restrict the number of simultaneous branches to execute.</span></span>
  
 [<span data-ttu-id="3d6c0-109">Atividades de acesso de banco de dados</span><span class="sxs-lookup"><span data-stu-id="3d6c0-109">Database Access Activities</span></span>](database-access-activities.md)  
 <span data-ttu-id="3d6c0-110">Demonstra como criar atividades que permitam acessar bancos de dados para recuperar ou modificar informações e usar [ADO.NET](../../data/adonet/index.md) para acessar o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="3d6c0-110">Demonstrates how to create activities that allow accessing databases to retrieve or modify information and use [ADO.NET](../../data/adonet/index.md) to access the database.</span></span>  
  
 [<span data-ttu-id="3d6c0-111">Atividade de política exteriorizada no .NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="3d6c0-111">Externalized Policy Activity in .NET Framework 4.5</span></span>](externalized-policy-activity-in-net-framework-4-5.md)  
 <span data-ttu-id="3d6c0-112">Demonstra como a atividade ExternalizedPolicy4 permite executar o Windows Workflow Foundation existente em <xref:System.Workflow.Activities.Rules.RuleSet> objetos .NET Framework [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 3.5 (WF 3.5) no Windows Workflow Foundation em (WF 4.5) diretamente usando o mecanismo de regras que é enviado no WF 3.5.</span><span class="sxs-lookup"><span data-stu-id="3d6c0-112">Demonstrates how the ExternalizedPolicy4 activity allows executing existing Windows Workflow Foundation in .NET Framework 3.5 (WF 3.5) <xref:System.Workflow.Activities.Rules.RuleSet> objects in Windows Workflow Foundation in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] (WF 4.5) directly by using the rules engine that is shipped in WF 3.5.</span></span>
  
 [<span data-ttu-id="3d6c0-113">ForEach não genérico</span><span class="sxs-lookup"><span data-stu-id="3d6c0-113">Non-Generic ForEach</span></span>](non-generic-foreach.md)  
 <span data-ttu-id="3d6c0-114">Demonstra como criar uma versão não genérico de atividade de <xref:System.Activities.Statements.ForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="3d6c0-114">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3d6c0-115">ParallelForEach não genérico</span><span class="sxs-lookup"><span data-stu-id="3d6c0-115">Non-Generic ParallelForEach</span></span>](non-generic-parallelforeach.md)  
 <span data-ttu-id="3d6c0-116">Demonstra como criar uma versão não genérico de atividade de <xref:System.Activities.Statements.ParallelForEach%601> .</span><span class="sxs-lookup"><span data-stu-id="3d6c0-116">Demonstrates how to create a non-generic version of the <xref:System.Activities.Statements.ParallelForEach%601> activity.</span></span>  
  
 [<span data-ttu-id="3d6c0-117">Obter WorkflowInstanceId</span><span class="sxs-lookup"><span data-stu-id="3d6c0-117">Get WorkflowInstanceId</span></span>](get-workflowinstanceid.md)  
 <span data-ttu-id="3d6c0-118">Demonstra como usar a atividade personalizado, `GetWorkflowInstanceId`, para retornar a identificação de instância de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="3d6c0-118">Demonstrates how to use the custom activity, `GetWorkflowInstanceId`, to return the workflow instance ID.</span></span>
