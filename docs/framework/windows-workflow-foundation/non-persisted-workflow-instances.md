---
title: "Instâncias são persistentes de fluxo de trabalho"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5e01af77-6b14-4964-91a5-7dfd143449c0
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54ed92ee666a55b52db22abbbe46922189b3f8fb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="non-persisted-workflow-instances"></a><span data-ttu-id="41fb2-102">Instâncias são persistentes de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="41fb2-102">Non-Persisted Workflow Instances</span></span>
<span data-ttu-id="41fb2-103">Quando uma nova instância de um fluxo de trabalho é criada que persiste seu estado em <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, o host serviço cria uma entrada para o serviço no armazenamento de instância.</span><span class="sxs-lookup"><span data-stu-id="41fb2-103">When a new instance of a workflow is created that persists its state in the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>, the service host creates an entry for that service in the instance store.</span></span> <span data-ttu-id="41fb2-104">Posteriormente, quando a instância do fluxo de trabalho é mantida pela primeira vez, <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> armazena o estado atual da instância.</span><span class="sxs-lookup"><span data-stu-id="41fb2-104">Subsequently, when the workflow instance is persisted for the first time, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> stores the current instance state.</span></span> <span data-ttu-id="41fb2-105">Se o fluxo de trabalho é hospedado no serviço de ativação de processo do Windows, os dados de implantação de serviço são gravados também para o armazenamento de instância quando a instância é mantida pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="41fb2-105">If the workflow is hosted in the Windows Process Activation Service, the service deployment data is also written to the instance store when the instance is persisted for the first time.</span></span>  
  
 <span data-ttu-id="41fb2-106">Como a instância de fluxo de trabalho não foi mantida, ele está em um **persistentes** estado.</span><span class="sxs-lookup"><span data-stu-id="41fb2-106">As long as the workflow instance has not been persisted, it is in a **non-persisted** state.</span></span> <span data-ttu-id="41fb2-107">Quando nesse estado, a instância de fluxo de trabalho não pode ser recuperada após um domínio de aplicativo se recicla, falha do host, ou falha do computador.</span><span class="sxs-lookup"><span data-stu-id="41fb2-107">While in this state, the workflow instance cannot be recovered after an application domain recycle, host failure, or computer failure.</span></span>  
  
## <a name="the-non-persisted-state"></a><span data-ttu-id="41fb2-108">O estado não persistente</span><span class="sxs-lookup"><span data-stu-id="41fb2-108">The Non-Persisted State</span></span>  
 <span data-ttu-id="41fb2-109">As instâncias duráveis de fluxo de trabalho que não foram persistentes permanecem em um estado não mantido nos seguintes casos:</span><span class="sxs-lookup"><span data-stu-id="41fb2-109">Durable workflow instances that have not been persisted remain in a non-persisted state in the following cases:</span></span>  
  
-   <span data-ttu-id="41fb2-110">Falhas de host serviço antes de instância de fluxo de trabalho são mantidas pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="41fb2-110">The service host crashes before the workflow instance is persisted for the first time.</span></span> <span data-ttu-id="41fb2-111">O de instância de fluxo de trabalho na instância armazenam e não são recuperadas.</span><span class="sxs-lookup"><span data-stu-id="41fb2-111">The workflow instance remains in the instance store and is not recovered.</span></span> <span data-ttu-id="41fb2-112">Se uma mensagem correlacionada chega, a instância de fluxo de trabalho se torna ativa novamente.</span><span class="sxs-lookup"><span data-stu-id="41fb2-112">If a correlated message arrives, the workflow instance becomes active again.</span></span>  
  
-   <span data-ttu-id="41fb2-113">A instância de fluxo de trabalho apresenta uma exceção antes de ser mantidas pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="41fb2-113">The workflow instance experiences an exception before it is persisted for the first time.</span></span> <span data-ttu-id="41fb2-114">Como <xref:System.Activities.UnhandledExceptionAction> retornado, os seguintes cenários ocorrem:</span><span class="sxs-lookup"><span data-stu-id="41fb2-114">Depending on the <xref:System.Activities.UnhandledExceptionAction> returned, the following scenarios occur:</span></span>  
  
    -   <span data-ttu-id="41fb2-115"><xref:System.Activities.UnhandledExceptionAction> é definido como <xref:System.Activities.UnhandledExceptionAction.Abort>: Quando ocorre uma exceção, informações de implantação de serviço é escrita para o armazenamento de instância, e a instância de fluxo de trabalho é descarregada de memória.</span><span class="sxs-lookup"><span data-stu-id="41fb2-115"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Abort>: When an exception occurs, service deployment information is written to the instance store, and the workflow instance is unloaded from memory.</span></span> <span data-ttu-id="41fb2-116">O de instância de fluxo de trabalho em um estado não persistido e não podem ser recarregadas.</span><span class="sxs-lookup"><span data-stu-id="41fb2-116">The workflow instance remains in a non-persisted state and cannot be reloaded.</span></span>  
  
    -   <span data-ttu-id="41fb2-117"><xref:System.Activities.UnhandledExceptionAction> é definido como <xref:System.Activities.UnhandledExceptionAction.Cancel> ou a <xref:System.Activities.UnhandledExceptionAction.Terminate>: Quando ocorre uma exceção, informações de implantação de serviço é escrita para o armazenamento de instância, e o estado da instância da atividade é definido como <xref:System.Activities.ActivityInstanceState.Closed>.</span><span class="sxs-lookup"><span data-stu-id="41fb2-117"><xref:System.Activities.UnhandledExceptionAction> is set to <xref:System.Activities.UnhandledExceptionAction.Cancel> or <xref:System.Activities.UnhandledExceptionAction.Terminate>: When an exception occurs, service deployment information is written to the instance store, and the activity instance state is set to <xref:System.Activities.ActivityInstanceState.Closed>.</span></span>  
  
 <span data-ttu-id="41fb2-118">Para minimizar o risco de localizar instâncias são persistentes descarregadas de fluxo de trabalho, recomendamos persistir o fluxo de trabalho no início em seu ciclo de vida.</span><span class="sxs-lookup"><span data-stu-id="41fb2-118">To minimize the risk of encountering unloaded non-persisted workflow instances, we recommend persisting the workflow early in its life cycle.</span></span>  
  
## <a name="detection-and-removal-of-non-persisted-instances"></a><span data-ttu-id="41fb2-119">Detecção e remoção de instâncias são persistentes</span><span class="sxs-lookup"><span data-stu-id="41fb2-119">Detection and Removal of Non-Persisted Instances</span></span>  
 <span data-ttu-id="41fb2-120"><xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> não remove quaisquer instâncias são mantidas de fluxo de trabalho da instância.</span><span class="sxs-lookup"><span data-stu-id="41fb2-120">The <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> does not remove any non-persisted workflow instances from the instance store.</span></span> <span data-ttu-id="41fb2-121">Também não remove quaisquer proprietários expiradas de bloqueio que não persistiram as instâncias de fluxo de trabalho associados com eles.</span><span class="sxs-lookup"><span data-stu-id="41fb2-121">It also does not remove any expired lock owners that have non-persisted workflow instances associated with them.</span></span>  
  
 <span data-ttu-id="41fb2-122">Recomendamos que o administrador verifica periodicamente o armazenamento de instância para instâncias são persistentes.</span><span class="sxs-lookup"><span data-stu-id="41fb2-122">We recommend that the administrator periodically checks the instance store for non-persisted instances.</span></span> <span data-ttu-id="41fb2-123">Os administradores podem remover essas instâncias da instância como sabem que esse fluxo de trabalho não receberá mensagens correlacionadas.</span><span class="sxs-lookup"><span data-stu-id="41fb2-123">Administrators can remove those instances from the instance store as long as they know that this workflow will not receive correlated messages.</span></span> <span data-ttu-id="41fb2-124">Por exemplo, se a instância foi na base de dados por vários meses e se souber que o fluxo de trabalho normalmente tem um tempo de vida de vários dias, seria seguro suponha que isso foi inicializada uma instância que falhasse.</span><span class="sxs-lookup"><span data-stu-id="41fb2-124">For example, if the instance has been in the database for several months and it is known that the workflow typically has a lifetime of several days, it would be safe to assume that this was an initialized instance that had crashed.</span></span>  
  
 <span data-ttu-id="41fb2-125">Para localizar ocorrências são mantidas na instância Store de fluxo de trabalho do SQL você pode usar as seguintes consultas SQL:</span><span class="sxs-lookup"><span data-stu-id="41fb2-125">To find non-persisted instances in the SQL Workflow Instance Store you can use the following SQL queries:</span></span>  
  
-   <span data-ttu-id="41fb2-126">Esta consulta localiza todas as instâncias que não foram persistentes, e retorna a hora de identificação e de criação (armazenados na hora UTC) para eles.</span><span class="sxs-lookup"><span data-stu-id="41fb2-126">This query finds all instances that have not been persisted, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0  
    ```  
  
-   <span data-ttu-id="41fb2-127">Esta consulta localiza todas as instâncias que não foram persistentes, e não é carregado, e retorna a hora de identificação e de criação (armazenados na hora UTC) para eles.</span><span class="sxs-lookup"><span data-stu-id="41fb2-127">This query finds all instances that have not been persisted, and that are not loaded, and returns the ID and creation time (stored in UTC time) for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and CurrentMachine is NULL  
    ```  
  
-   <span data-ttu-id="41fb2-128">Esta consulta localiza todas as instâncias suspensas que não foram persistentes, e retorna a identificação, o tempo de criação (armazenados na hora UTC), a razão de suspensão, e o nome da exceção para eles.</span><span class="sxs-lookup"><span data-stu-id="41fb2-128">This query finds all suspended instances that have not been persisted, and returns the ID, creation time (stored in UTC time), suspension reason, and exception name for them.</span></span>  
  
    ```sql  
    select InstanceId, CreationTime, SuspensionReason, SuspensionExceptionName   
        from [System.Activities.DurableInstancing].[Instances]   
        where IsInitialized = 0   
            and IsSuspended = 1  
    ```  
  
 <span data-ttu-id="41fb2-129">Use cuidado quando você estiver excluindo instâncias são persistentes.</span><span class="sxs-lookup"><span data-stu-id="41fb2-129">Use care when you are deleting non-persisted instances.</span></span> <span data-ttu-id="41fb2-130">Geralmente, é seguro remover instâncias são persistentes criadas por <xref:System.ServiceModel.Activities.WorkflowServiceHost> que são suspensas ou não carregadas.</span><span class="sxs-lookup"><span data-stu-id="41fb2-130">In general, it is safe to remove non-persisted instances created by <xref:System.ServiceModel.Activities.WorkflowServiceHost> that are suspended or are not loaded.</span></span> <span data-ttu-id="41fb2-131">Essas instâncias específicas podem ser excluídas de armazenamento excluindo os do modo de `[System.Activities.DurableInstancing].[Instances]` usando o seguinte comando SQL, substituindo a identificação correta de instância</span><span class="sxs-lookup"><span data-stu-id="41fb2-131">Those specific instances can be deleted from the store by deleting them from the `[System.Activities.DurableInstancing].[Instances]` view by using the following SQL command, substituting the correct instance ID.</span></span>  
  
```sql  
delete [System.Activities.DurableInstancing].[Instances]   
    where InstanceId=’078a9bc4-ada5-4f9e-8cce-b0eb0009995f’  
```  
  
> [!WARNING]
>  <span data-ttu-id="41fb2-132">Não recomendamos remover todas as instâncias são persistentes porque isso inclui instâncias que foram criados e apenas para ter sido persistente ainda não.</span><span class="sxs-lookup"><span data-stu-id="41fb2-132">We do not recommend removing all non-persisted instances because this includes instances that have just been created and have not yet been persisted.</span></span>
