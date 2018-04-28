---
title: Persistência de fluxo de trabalho
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d2278762895978f90d80977f9e538b0e10a4f3f8
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="workflow-persistence"></a><span data-ttu-id="d156a-102">Persistência de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d156a-102">Workflow Persistence</span></span>
<span data-ttu-id="d156a-103">Persistência de fluxo de trabalho é a captura durável do estado de uma instância de fluxo de trabalho, independente de processo ou de informações do computador.</span><span class="sxs-lookup"><span data-stu-id="d156a-103">Workflow persistence is the durable capture of a workflow instance's state, independent of process or computer information.</span></span> <span data-ttu-id="d156a-104">Isso é feito para fornecer um ponto conhecido de recuperação para a instância de fluxo de trabalho no caso de falha do sistema, ou para preservar a memória descarregando as instâncias de fluxo de trabalho que não estão fazendo ativamente o trabalho, ou para mover o estado da instância de fluxo de trabalho de um nó para outro nó em um farm de servidores.</span><span class="sxs-lookup"><span data-stu-id="d156a-104">This is done to provide a well-known point of recovery for the workflow instance in the event of system failure, or to preserve memory by unloading workflow instances that are not actively doing work, or to move the state of the workflow instance from one node to another node in a server farm.</span></span>  
  
 <span data-ttu-id="d156a-105">Persistência permite a agilidade do processo, a escalabilidade, a recuperação face falhar, e a capacidade gerenciar mais eficientemente a memória.</span><span class="sxs-lookup"><span data-stu-id="d156a-105">Persistence enables process agility, scalability, recovery in the face of failure, and the ability to manage memory more efficiently.</span></span> <span data-ttu-id="d156a-106">O processo de persistência inclui a identificação de um ponto de persistência, a coleta de dados a ser salvos, e finalmente a delegação de armazenamento real de dados a um provedor de persistência.</span><span class="sxs-lookup"><span data-stu-id="d156a-106">The persistence process includes the identification of a persistence point, the gathering of the data to be saved, and finally the delegation of the actual storage of the data to a persistence provider.</span></span>  
  
 <span data-ttu-id="d156a-107">Para habilitar a persistência de um fluxo de trabalho, você precisa associar a um repositório de instâncias com o **WorkflowApplication** ou **WorkflowServiceHost** conforme mencionado em [como: Ativar persistência para Fluxos de trabalho e serviços de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span><span class="sxs-lookup"><span data-stu-id="d156a-107">To enable persistence for a workflow, you need to associate an instance store with the **WorkflowApplication** or **WorkflowServiceHost** as mentioned in [How to: Enable Persistence for Workflows and Workflow Services](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).</span></span> <span data-ttu-id="d156a-108">O **WorkflowApplication** e **WorkflowServiceHost** usar o armazenamento de instância associado a eles para habilitar instâncias de fluxo de trabalho persistentes em um repositório de persistência e carregamento de instâncias de fluxo de trabalho em memória com base nos dados de instância de fluxo de trabalho armazenados no repositório de persistência.</span><span class="sxs-lookup"><span data-stu-id="d156a-108">The **WorkflowApplication** and **WorkflowServiceHost** use the instance store associated with them to enable persisting workflow instances into a persistence store and loading workflow instances into memory based on the workflow instance data stored in the persistence store.</span></span>  
  
 <span data-ttu-id="d156a-109">O [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] acompanha o **SqlWorkflowInstanceStore** classe, que permite a persistência de dados e metadados sobre instâncias de fluxo de trabalho em um banco de dados do SQL Server 2005 ou SQL Server 2008.</span><span class="sxs-lookup"><span data-stu-id="d156a-109">The [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] ships with the **SqlWorkflowInstanceStore** class, which allows persistence of data and metadata about workflow instances into a SQL Server 2005 or SQL Server 2008 database.</span></span> <span data-ttu-id="d156a-110">Consulte [armazenamento de instância de fluxo de trabalho do SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) para obter mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="d156a-110">See [SQL Workflow Instance Store](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) for more details.</span></span>  
  
 <span data-ttu-id="d156a-111">Para armazenar e carregar os dados específicos do aplicativo junto com informações relacionadas instância de fluxo de trabalho, você pode criar os participantes de persistência que estendem a classe de <xref:System.Activities.Persistence.PersistenceParticipant> .</span><span class="sxs-lookup"><span data-stu-id="d156a-111">To store and load your application-specific data along with the workflow instance-related information, you can create persistence participants that extend the <xref:System.Activities.Persistence.PersistenceParticipant> class.</span></span> <span data-ttu-id="d156a-112">Um participante de persistência participa no processo de persistência para salvar dados serializados personalizados no armazenamento de persistência, para carregar os dados da instância na memória, e executar qualquer lógica adicional em uma transação de persistência.</span><span class="sxs-lookup"><span data-stu-id="d156a-112">A persistence participant participates in the persistence process to save custom serializable data into the persistence store, to load the data from the instance store into memory, and to perform any additional logic under a persistence transaction.</span></span> <span data-ttu-id="d156a-113">Para obter mais informações, consulte [participantes de persistência](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span><span class="sxs-lookup"><span data-stu-id="d156a-113">For more information, see [Persistence Participants](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).</span></span>  
  
 <span data-ttu-id="d156a-114">A tela de aplicativo Windows Server simplifica o processo de configurar a persistência.</span><span class="sxs-lookup"><span data-stu-id="d156a-114">Windows Server App Fabric simplifies the process of configuring persistence.</span></span> <span data-ttu-id="d156a-115">Para obter mais informações, consulte [conceitos de persistência com Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span><span class="sxs-lookup"><span data-stu-id="d156a-115">For more information, see [Persistence Concepts with Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)</span></span>  
  
## <a name="implicit-persistence-points"></a><span data-ttu-id="d156a-116">Pontos implícitos de persistência</span><span class="sxs-lookup"><span data-stu-id="d156a-116">Implicit Persistence Points</span></span>  
 <span data-ttu-id="d156a-117">A lista a seguir contém exemplos das circunstâncias na qual um fluxo de trabalho é mantido quando um armazenamento de instância é associado com um fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d156a-117">The following list contains examples of the conditions upon which a workflow is persisted when an instance store is associated with a workflow.</span></span>  
  
-   <span data-ttu-id="d156a-118">Quando um **TransactionScope** conclusão da atividade ou um **TransactedReceiveScope** conclusão da atividade.</span><span class="sxs-lookup"><span data-stu-id="d156a-118">When a **TransactionScope** activity completes or a **TransactedReceiveScope** activity completes.</span></span>  
  
-   <span data-ttu-id="d156a-119">Quando uma instância de fluxo de trabalho se torna ociosa e o **WorkflowIdleBehavior** é definido no host de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d156a-119">When a workflow instance becomes idle and the **WorkflowIdleBehavior** is set on workflow host.</span></span> <span data-ttu-id="d156a-120">Isso ocorre, por exemplo, quando você usar atividades de mensagens ou um **atraso** atividade.</span><span class="sxs-lookup"><span data-stu-id="d156a-120">This occurs, for example, when you use messaging activities or a **Delay** activity.</span></span>  
  
-   <span data-ttu-id="d156a-121">Quando um WorkflowApplication fica ocioso e o **PersistableIdle** do aplicativo é definida como **PersistableIdleAction.Persist**.</span><span class="sxs-lookup"><span data-stu-id="d156a-121">When a WorkflowApplication becomes idle and the **PersistableIdle** property of the application is set to **PersistableIdleAction.Persist**.</span></span>  
  
-   <span data-ttu-id="d156a-122">Quando um aplicativo host seja instruído para persistir ou descarregar uma instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d156a-122">When a host application is instructed to persist or unload a workflow instance.</span></span>  
  
-   <span data-ttu-id="d156a-123">Quando uma instância de fluxo de trabalho seja finalizada ou termina.</span><span class="sxs-lookup"><span data-stu-id="d156a-123">When a workflow instance is terminated or finishes.</span></span>  
  
-   <span data-ttu-id="d156a-124">Quando um **Persist** atividade é executada.</span><span class="sxs-lookup"><span data-stu-id="d156a-124">When a **Persist** activity executes.</span></span>  
  
-   <span data-ttu-id="d156a-125">Quando uma instância de um fluxo de trabalho desenvolvido usando uma versão anterior do Windows Workflow Foundation localizar um ponto de persistência durante a execução interoperável.</span><span class="sxs-lookup"><span data-stu-id="d156a-125">When an instance of a workflow developed using a previous version of Windows Workflow Foundation encounters a persistence point during interoperable execution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d156a-126">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d156a-126">In This Section</span></span>  
  
-   [<span data-ttu-id="d156a-127">Repositório de instâncias de fluxo de trabalho do SQL</span><span class="sxs-lookup"><span data-stu-id="d156a-127">SQL Workflow Instance Store</span></span>](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [<span data-ttu-id="d156a-128">Armazenamentos de instância</span><span class="sxs-lookup"><span data-stu-id="d156a-128">Instance Stores</span></span>](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [<span data-ttu-id="d156a-129">Participantes da persistência</span><span class="sxs-lookup"><span data-stu-id="d156a-129">Persistence Participants</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [<span data-ttu-id="d156a-130">Práticas recomendadas de persistência</span><span class="sxs-lookup"><span data-stu-id="d156a-130">Persistence Best Practices</span></span>](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [<span data-ttu-id="d156a-131">Instâncias de fluxo de trabalho não persistentes</span><span class="sxs-lookup"><span data-stu-id="d156a-131">Non-Persisted Workflow Instances</span></span>](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [<span data-ttu-id="d156a-132">Pausando e continuando um fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d156a-132">Pausing and Resuming a Workflow</span></span>](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
