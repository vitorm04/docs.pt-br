---
title: "Usando WorkflowIdentity e controle de versão"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8451735-8046-478f-912b-40870a6c0c3a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7378609d056ded8602df827254248cf8a0476e59
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="using-workflowidentity-and-versioning"></a><span data-ttu-id="af5a0-102">Usando WorkflowIdentity e controle de versão</span><span class="sxs-lookup"><span data-stu-id="af5a0-102">Using WorkflowIdentity and Versioning</span></span>
<span data-ttu-id="af5a0-103">O <xref:System.Activities.WorkflowIdentity> fornece uma maneira para que os desenvolvedores de aplicativos de fluxo de trabalho associem um nome e uma <xref:System.Version> com uma definição de fluxo de trabalho, e para que essas informações sejam associadas a uma instância de fluxo de trabalho persistida.</span><span class="sxs-lookup"><span data-stu-id="af5a0-103"><xref:System.Activities.WorkflowIdentity> provides a way for workflow application developers to associate a name and a <xref:System.Version> with a workflow definition, and for this information to be associated with a persisted workflow instance.</span></span> <span data-ttu-id="af5a0-104">Essas informações de identidade podem ser usadas por desenvolvedores de aplicativos de fluxo de trabalho para habilitar cenários como execução lado a lado de várias versões de uma definição de fluxo de trabalho, e fornece o pilar para outra funcionalidade como a atualização dinâmica.</span><span class="sxs-lookup"><span data-stu-id="af5a0-104">This identity information can be used by workflow application developers to enable scenarios such as side-by-side execution of multiple versions of a workflow definition, and provides the cornerstone for other functionality such as dynamic update.</span></span> <span data-ttu-id="af5a0-105">Este tópico fornece uma visão geral de como usar o <xref:System.Activities.WorkflowIdentity> com hospedagem <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="af5a0-105">This topic provides as overview of using <xref:System.Activities.WorkflowIdentity> with <xref:System.Activities.WorkflowApplication> hosting.</span></span> <span data-ttu-id="af5a0-106">Para obter informações sobre a execução lado a lado das definições de fluxo de trabalho em um serviço de fluxo de trabalho, consulte [controle de versão lado a lado no WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span><span class="sxs-lookup"><span data-stu-id="af5a0-106">For information on side-by-side execution of workflow definitions in a workflow service, see [Side by Side Versioning in WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).</span></span> <span data-ttu-id="af5a0-107">Para obter informações sobre a atualização dinâmica, consulte [atualização dinâmica](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span><span class="sxs-lookup"><span data-stu-id="af5a0-107">For information on dynamic update, see [Dynamic Update](../../../docs/framework/windows-workflow-foundation/dynamic-update.md).</span></span>  
  
## <a name="in-this-topic"></a><span data-ttu-id="af5a0-108">Neste tópico</span><span class="sxs-lookup"><span data-stu-id="af5a0-108">In this topic</span></span>  
  
-   [<span data-ttu-id="af5a0-109">Usando WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="af5a0-109">Using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UsingWorkflowIdentity)  
  
    -   [<span data-ttu-id="af5a0-110">Execução lado a lado usando WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="af5a0-110">Side-by-side Execution using WorkflowIdentity</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#SxS)  
  
-   [<span data-ttu-id="af5a0-111">Atualizando bancos de dados do .NET Framework 4 persistência para dar suporte a controle de versão de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="af5a0-111">Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases)  
  
    -   [<span data-ttu-id="af5a0-112">Para atualizar o esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="af5a0-112">To upgrade the database schema</span></span>](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#ToUpgrade)  
  
##  <span data-ttu-id="af5a0-113"><a name="UsingWorkflowIdentity"></a>Usando WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="af5a0-113"><a name="UsingWorkflowIdentity"></a> Using WorkflowIdentity</span></span>  
 <span data-ttu-id="af5a0-114">Para usar <xref:System.Activities.WorkflowIdentity>, crie uma instância, configure-a e associe-a a uma instância <xref:System.Activities.WorkflowApplication>.</span><span class="sxs-lookup"><span data-stu-id="af5a0-114">To use <xref:System.Activities.WorkflowIdentity>, create an instance, configure it, and associate it with a <xref:System.Activities.WorkflowApplication> instance.</span></span> <span data-ttu-id="af5a0-115">Uma instância <xref:System.Activities.WorkflowIdentity> contém três informações de identificação.</span><span class="sxs-lookup"><span data-stu-id="af5a0-115">A <xref:System.Activities.WorkflowIdentity> instance contains three identifying pieces of information.</span></span> <span data-ttu-id="af5a0-116"><xref:System.Activities.WorkflowIdentity.Name%2A> e <xref:System.Activities.WorkflowIdentity.Version%2A> contêm um nome e um <xref:System.Version> e são necessários, e <xref:System.Activities.WorkflowIdentity.Package%2A> é opcional e pode ser usado para especificar uma cadeia de caracteres adicional que contém informações como o nome do assembly ou outras informações desejadas.</span><span class="sxs-lookup"><span data-stu-id="af5a0-116"><xref:System.Activities.WorkflowIdentity.Name%2A> and <xref:System.Activities.WorkflowIdentity.Version%2A> contain a name and a <xref:System.Version> and are required, and <xref:System.Activities.WorkflowIdentity.Package%2A> is optional and can be used to specify an additional string containing information such as assembly name or other desired information.</span></span> <span data-ttu-id="af5a0-117">Um <xref:System.Activities.WorkflowIdentity> é exclusivo se qualquer uma de suas três propriedades for diferente da outra <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="af5a0-117">A <xref:System.Activities.WorkflowIdentity> is unique if any of its three properties are different from another <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af5a0-118">Um <xref:System.Activities.WorkflowIdentity> não deve conter informações pessoalmente identificáveis (PII).</span><span class="sxs-lookup"><span data-stu-id="af5a0-118">A <xref:System.Activities.WorkflowIdentity> should not contain any personally identifiable information (PII).</span></span> <span data-ttu-id="af5a0-119">As informações sobre o <xref:System.Activities.WorkflowIdentity> usadas para criar uma instância são emitidas para todos os serviços de rastreamento configurados em vários pontos diferentes do ciclo de vida da atividade em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="af5a0-119">Information about the <xref:System.Activities.WorkflowIdentity> used to create an instance is emitted to any configured tracking services at several different points of the activity life-cycle by the runtime.</span></span> <span data-ttu-id="af5a0-120">O Rastreamento WF não tem nenhum mecanismo para ocultar o PII (dados de usuário confidenciais).</span><span class="sxs-lookup"><span data-stu-id="af5a0-120">WF Tracking does not have any mechanism to hide PII (sensitive user data).</span></span> <span data-ttu-id="af5a0-121">Portanto, uma instância <xref:System.Activities.WorkflowIdentity> não deve conter nenhum dado de PII porque será emitido pelo tempo de execução em registros de rastreamento e pode estar visível para qualquer um com acesso para exibir os registros de rastreamento.</span><span class="sxs-lookup"><span data-stu-id="af5a0-121">Therefore, a <xref:System.Activities.WorkflowIdentity> instance should not contain any PII data as it will be emitted by the runtime in tracking records and may be visible to anyone with access to view the tracking records.</span></span>  
  
 <span data-ttu-id="af5a0-122">No exemplo a seguir, <xref:System.Activities.WorkflowIdentity> é criado e associado a uma instância de um trabalho criada usando uma definição de trabalho `MortgageWorkflow`.</span><span class="sxs-lookup"><span data-stu-id="af5a0-122">In the following example, a <xref:System.Activities.WorkflowIdentity> is created and associated with an instance of a workflow created using a `MortgageWorkflow` workflow definition.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="af5a0-123">Para recarregar e retomar um fluxo de trabalho, um <xref:System.Activities.WorkflowIdentity> que está configurado para corresponder o <xref:System.Activities.WorkflowIdentity> da instância do fluxo de trabalho persistida deve ser usado.</span><span class="sxs-lookup"><span data-stu-id="af5a0-123">When reloading and resuming a workflow, a <xref:System.Activities.WorkflowIdentity> that is configured to match the <xref:System.Activities.WorkflowIdentity> of the persisted workflow instance must be used.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the workflow.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="af5a0-124">Se o <xref:System.Activities.WorkflowIdentity> usado ao recarregar a instância de fluxo de trabalho não corresponder ao <xref:System.Activities.WorkflowIdentity> persistido, uma <xref:System.Activities.VersionMismatchException> é gerada.</span><span class="sxs-lookup"><span data-stu-id="af5a0-124">If the <xref:System.Activities.WorkflowIdentity> used when reloading the workflow instance does not match the persisted <xref:System.Activities.WorkflowIdentity>, a <xref:System.Activities.VersionMismatchException> is thrown.</span></span> <span data-ttu-id="af5a0-125">No exemplo a seguir, uma tentativa de carregamento é feita na instância `MortgageWorkflow` que foi persistida no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="af5a0-125">In the following example a load attempt is made on the `MortgageWorkflow` instance that was persisted in the previous example.</span></span> <span data-ttu-id="af5a0-126">Essa tentativa de carregamento é feita usando um <xref:System.Activities.WorkflowIdentity> configurado para uma versão mais nova do fluxo de trabalho de hipoteca que não corresponde à instância persistida.</span><span class="sxs-lookup"><span data-stu-id="af5a0-126">This load attempt is made using a <xref:System.Activities.WorkflowIdentity> configured for a newer version of the mortgage workflow that does not match the persisted instance.</span></span>  
  
```csharp  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow_v2(), identityV2);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Attempt to load the workflow instance.  
wfApp.Load(instanceId);  
  
// Resume the workflow...  
```  
  
 <span data-ttu-id="af5a0-127">Quando o código anterior for executado, o <xref:System.Activities.VersionMismatchException> a seguir será gerado.</span><span class="sxs-lookup"><span data-stu-id="af5a0-127">When the previous code is executed, the following <xref:System.Activities.VersionMismatchException> is thrown.</span></span>  
  
 <span data-ttu-id="af5a0-128">**A WorkflowIdentity ('MortgageWorkflow v1; Versão = 1.0.0.0') da instância carregada não corresponde a WorkflowIdentity ('MortgageWorkflow v2; Versão = 2.0.0.0') da definição de fluxo de trabalho fornecida. A instância pode ser carregada com o uso de uma definição diferente ou atualizada com a atualização dinâmica.**</span><span class="sxs-lookup"><span data-stu-id="af5a0-128">**The WorkflowIdentity ('MortgageWorkflow v1; Version=1.0.0.0') of the loaded instance does not match the WorkflowIdentity ('MortgageWorkflow v2; Version=2.0.0.0') of the provided workflow definition. The instance can be loaded using a different definition, or updated using Dynamic Update.**</span></span>  
###  <span data-ttu-id="af5a0-129"><a name="SxS"></a>Execução lado a lado usando WorkflowIdentity</span><span class="sxs-lookup"><span data-stu-id="af5a0-129"><a name="SxS"></a> Side-by-side Execution using WorkflowIdentity</span></span>  
 <span data-ttu-id="af5a0-130">O <xref:System.Activities.WorkflowIdentity> pode ser usado para facilitar a execução de várias versões de um fluxo de trabalho lado a lado.</span><span class="sxs-lookup"><span data-stu-id="af5a0-130"><xref:System.Activities.WorkflowIdentity> can be used to facilitate the execution of multiple versions of a workflow side-by-side.</span></span> <span data-ttu-id="af5a0-131">Um cenário comum é a mudança de requisitos comerciais em um fluxo de trabalho de execução longa.</span><span class="sxs-lookup"><span data-stu-id="af5a0-131">One common scenario is changing business requirements on a long-running workflow.</span></span> <span data-ttu-id="af5a0-132">Muitas instâncias de um fluxo de trabalho podem ser executadas quando uma versão atualizada é implantada.</span><span class="sxs-lookup"><span data-stu-id="af5a0-132">Many instances of a workflow could be running when an updated version is deployed.</span></span> <span data-ttu-id="af5a0-133">O aplicativo de host pode ser configurado para usar a definição atualizada do fluxo de trabalho ao iniciar novas instâncias e é responsabilidade do aplicativo host fornecer a definição correta do fluxo de trabalho ao retomar instâncias.</span><span class="sxs-lookup"><span data-stu-id="af5a0-133">The host application can be configured to use the updated workflow definition when starting new instances, and it is the responsibility of the host application to provide the correct workflow definition when resuming instances.</span></span> <span data-ttu-id="af5a0-134">O <xref:System.Activities.WorkflowIdentity> pode ser usado para identificar e fornecer a definição de fluxo de trabalho correspondente ao retomar instâncias de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af5a0-134"><xref:System.Activities.WorkflowIdentity> can be used to identify and supply the matching workflow definition when resuming workflow instances.</span></span>  
  
 <span data-ttu-id="af5a0-135">Para recuperar o <xref:System.Activities.WorkflowIdentity> de uma instância do fluxo de trabalho persistida, o método <xref:System.Activities.WorkflowApplication.GetInstance%2A> é usado.</span><span class="sxs-lookup"><span data-stu-id="af5a0-135">To retrieve the <xref:System.Activities.WorkflowIdentity> of a persisted workflow instance, the <xref:System.Activities.WorkflowApplication.GetInstance%2A> method is used.</span></span> <span data-ttu-id="af5a0-136">O método <xref:System.Activities.WorkflowApplication.GetInstance%2A> usa a <xref:System.Activities.WorkflowApplication.Id%2A> da instância do fluxo de trabalho persistida e o <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que contém a instância persistida e retorna um <xref:System.Activities.WorkflowApplicationInstance>.</span><span class="sxs-lookup"><span data-stu-id="af5a0-136">The <xref:System.Activities.WorkflowApplication.GetInstance%2A> method takes the <xref:System.Activities.WorkflowApplication.Id%2A> of the persisted workflow instance and the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that contains the persisted instance and returns a <xref:System.Activities.WorkflowApplicationInstance>.</span></span> <span data-ttu-id="af5a0-137">Um <xref:System.Activities.WorkflowApplicationInstance> contém informações sobre uma instância do fluxo de trabalho persistida, incluindo o <xref:System.Activities.WorkflowIdentity> associado.</span><span class="sxs-lookup"><span data-stu-id="af5a0-137">A <xref:System.Activities.WorkflowApplicationInstance> contains information about a persisted workflow instance, including its associated <xref:System.Activities.WorkflowIdentity>.</span></span> <span data-ttu-id="af5a0-138">Esse <xref:System.Activities.WorkflowIdentity> associado pode ser usado pelo host para fornecer a definição correta de fluxo de trabalho ao carregar e retomar a instância de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af5a0-138">This associated <xref:System.Activities.WorkflowIdentity> can be used by the host to supply the correct workflow definition when loading and resuming the workflow instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af5a0-139">Um <xref:System.Activities.WorkflowIdentity> nulo é válido e pode ser usado pelo host para mapear as instâncias que foram persistidas sem <xref:System.Activities.WorkflowIdentity> associado para a definição adequada de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="af5a0-139">A null <xref:System.Activities.WorkflowIdentity> is valid, and can be used by the host to map instances that were persisted with no associated <xref:System.Activities.WorkflowIdentity> to the proper workflow definition.</span></span> <span data-ttu-id="af5a0-140">Este cenário poderá ocorrer quando um aplicativo de fluxo de trabalho não tiver sido inicialmente escrito com controle de versão de fluxo de trabalho ou quando um aplicativo for atualizado do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af5a0-140">This scenario can occur when a workflow application was not initially written with workflow versioning, or when an application is upgraded from [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span></span> [!INCLUDE[crdefault](../../../includes/crdefault-md.md)]<span data-ttu-id="af5a0-141">[Atualizando bancos de dados do .NET Framework 4 persistência para dar suporte a controle de versão de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span><span class="sxs-lookup"><span data-stu-id="af5a0-141"> [Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).</span></span>  
  
 <span data-ttu-id="af5a0-142">No exemplo a seguir um `Dictionary<WorkflowIdentity, Activity>` é usada para associar <xref:System.Activities.WorkflowIdentity> instâncias com suas definições de fluxo de trabalho correspondente e um fluxo de trabalho é iniciado usando o `MortgageWorkflow` definição de fluxo de trabalho, que está associada a `identityV1` <xref:System.Activities.WorkflowIdentity>.</span><span class="sxs-lookup"><span data-stu-id="af5a0-142">In the following example a `Dictionary<WorkflowIdentity, Activity>` is used to associate <xref:System.Activities.WorkflowIdentity> instances with their matching workflow definitions, and a workflow is started using the `MortgageWorkflow` workflow definition, which is associated with the `identityV1` <xref:System.Activities.WorkflowIdentity>.</span></span>  
  
```csharp  
WorkflowIdentity identityV1 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v1",  
    Version = new Version(1, 0, 0, 0)  
};  
  
WorkflowIdentity identityV2 = new WorkflowIdentity  
{  
    Name = "MortgageWorkflow v2",  
    Version = new Version(2, 0, 0, 0)  
};  
  
Dictionary<WorkflowIdentity, Activity> WorkflowVersionMap = new Dictionary<WorkflowIdentity, Activity>();  
WorkflowVersionMap.Add(identityV1, new MortgageWorkflow());  
WorkflowVersionMap.Add(identityV2, new MortgageWorkflow_v2());  
  
WorkflowApplication wfApp = new WorkflowApplication(new MortgageWorkflow(), identityV1);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Run the workflow.  
wfApp.Run();  
```  
  
 <span data-ttu-id="af5a0-143">No exemplo a seguir, as informações sobre a instância do fluxo de trabalho persistida do exemplo anterior são recuperadas chamando <xref:System.Activities.WorkflowApplication.GetInstance%2A>, e as informações persistidas do <xref:System.Activities.WorkflowIdentity> são usadas para recuperar a definição de fluxo de trabalho correspondente.</span><span class="sxs-lookup"><span data-stu-id="af5a0-143">In the following example, information about the persisted workflow instance from the previous example is retrieved by calling <xref:System.Activities.WorkflowApplication.GetInstance%2A>, and the persisted <xref:System.Activities.WorkflowIdentity> information is used to retrieve the matching workflow definition.</span></span> <span data-ttu-id="af5a0-144">Essas informações são usadas para configurar o <xref:System.Activities.WorkflowApplication> e, em seguida, o fluxo de trabalho é carregado.</span><span class="sxs-lookup"><span data-stu-id="af5a0-144">This information is used to configure the <xref:System.Activities.WorkflowApplication>, and then the workflow is loaded.</span></span> <span data-ttu-id="af5a0-145">Observe que, como a sobrecarga do <xref:System.Activities.WorkflowApplication.Load%2A> que usa o <xref:System.Activities.WorkflowApplicationInstance> é usada, o <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> que foi configurado no <xref:System.Activities.WorkflowApplicationInstance> é usado pelo <xref:System.Activities.WorkflowApplication> e, portanto, a propriedade de <xref:System.Activities.WorkflowApplication.InstanceStore%2A> não precisa ser configurada.</span><span class="sxs-lookup"><span data-stu-id="af5a0-145">Note that because the <xref:System.Activities.WorkflowApplication.Load%2A> overload that takes the <xref:System.Activities.WorkflowApplicationInstance> is used, the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> that was configured on the <xref:System.Activities.WorkflowApplicationInstance> is used by the <xref:System.Activities.WorkflowApplication> and therefore its <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property does not need to be configured.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af5a0-146">Se a propriedade <xref:System.Activities.WorkflowApplication.InstanceStore%2A> for definida, ela deverá ser definida com a mesma instância <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> usada pelo <xref:System.Activities.WorkflowApplicationInstance> ou um <xref:System.ArgumentException> será gerado com a seguinte mensagem: `The instance is configured with a different InstanceStore than this WorkflowApplication.`</span><span class="sxs-lookup"><span data-stu-id="af5a0-146">If the <xref:System.Activities.WorkflowApplication.InstanceStore%2A> property is set, it must be set with the same <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> instance used by the <xref:System.Activities.WorkflowApplicationInstance> or else an <xref:System.ArgumentException> will be thrown with the following message: `The instance is configured with a different InstanceStore than this WorkflowApplication.`.</span></span>  
  
```csharp  
// Get the WorkflowApplicationInstance of the desired workflow from the specified  
// SqlWorkflowInstanceStore.  
WorkflowApplicationInstance instance = WorkflowApplication.GetInstance(instanceId, store);  
  
// Use the persisted WorkflowIdentity to retrieve the correct workflow  
// definition from the dictionary.  
Activity definition = WorkflowVersionMap[instance.DefinitionIdentity];  
  
WorkflowApplication wfApp = new WorkflowApplication(definition, instance.DefinitionIdentity);  
  
// Configure the WorkflowApplication with persistence and desired workflow event handlers.  
ConfigureWorkflowApplication(wfApp);  
  
// Load the persisted workflow instance.  
wfApp.Load(instance);  
  
// Resume the workflow...  
```  
  
##  <span data-ttu-id="af5a0-147"><a name="UpdatingWF4PersistenceDatabases"></a>Atualizando bancos de dados do .NET Framework 4 persistência para dar suporte a controle de versão de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="af5a0-147"><a name="UpdatingWF4PersistenceDatabases"></a> Upgrading .NET Framework 4 Persistence Databases to Support Workflow Versioning</span></span>  
 <span data-ttu-id="af5a0-148">Um script de banco de dados SqlWorkflowInstanceStoreSchemaUpgrade.sql é fornecido para atualizar bancos de dados de persistência criados usando os scripts de banco de dados do [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af5a0-148">A SqlWorkflowInstanceStoreSchemaUpgrade.sql database script is provided to upgrade persistence databases created using the [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] database scripts.</span></span> <span data-ttu-id="af5a0-149">Esse script atualiza os bancos de dados para dar suporte aos novos recursos de controle de versão introduzidos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span><span class="sxs-lookup"><span data-stu-id="af5a0-149">This script updates the databases to support the new versioning capabilities introduced in [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="af5a0-150">As instâncias de fluxo de trabalho persistidas nos bancos de dados recebem valores padrão do controle de versão e podem participar da execução lado a lado e da atualização dinâmica.</span><span class="sxs-lookup"><span data-stu-id="af5a0-150">Any persisted workflow instances in the databases are given default versioning values, and can then participate in side-by-side execution and dynamic update.</span></span>  
  
 <span data-ttu-id="af5a0-151">Se um aplicativo de fluxo de trabalho do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] tentar qualquer operação de persistência que use os novos recursos de controle de versão em um banco de dados de persistência que não seja atualizado usando o script fornecido, o <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> será gerado com uma mensagem semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="af5a0-151">If a [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] workflow application attempts any persistence operations that use the new versioning features on a persistence database which has not been upgraded using the provided script, an <xref:System.Runtime.DurableInstancing.InstancePersistenceCommandException> is thrown with a message similar to the following message.</span></span>  
  
 <span data-ttu-id="af5a0-152">**O SqlWorkflowInstanceStore tem uma versão de banco de dados do '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' não pode ser executado nesta versão do banco de dados.  Atualize o banco de dados '4.5.0.0'.**</span><span class="sxs-lookup"><span data-stu-id="af5a0-152">**The SqlWorkflowInstanceStore has a database version of '4.0.0.0'. InstancePersistenceCommand 'System.Activities.DurableInstancing.CreateWorkflowOwnerWithIdentityCommand' cannot be run against this database version.  Please upgrade the database to '4.5.0.0'.**</span></span>  
###  <span data-ttu-id="af5a0-153"><a name="ToUpgrade"></a>Para atualizar o esquema de banco de dados</span><span class="sxs-lookup"><span data-stu-id="af5a0-153"><a name="ToUpgrade"></a> To upgrade the database schema</span></span>  
  
1.  <span data-ttu-id="af5a0-154">Abra o SQL Server Management Studio e conecte-se ao servidor de banco de dados de persistência, por exemplo **. \SQLEXPRESS**.</span><span class="sxs-lookup"><span data-stu-id="af5a0-154">Open SQL Server Management Studio and connect to the persistence database server, for example **.\SQLEXPRESS**.</span></span>  
  
2.  <span data-ttu-id="af5a0-155">Escolha **abrir**, **arquivo** do **arquivo** menu.</span><span class="sxs-lookup"><span data-stu-id="af5a0-155">Choose **Open**, **File** from the **File** menu.</span></span> <span data-ttu-id="af5a0-156">Navegue até a pasta a seguir:`C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span><span class="sxs-lookup"><span data-stu-id="af5a0-156">Browse to the following folder: `C:\Windows\Microsoft.NET\Framework\4.0.30319\sql\en`</span></span>  
  
3.  <span data-ttu-id="af5a0-157">Selecione **SqlWorkflowInstanceStoreSchemaUpgrade.sql** e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="af5a0-157">Select **SqlWorkflowInstanceStoreSchemaUpgrade.sql** and click **Open**.</span></span>  
  
4.  <span data-ttu-id="af5a0-158">Selecione o nome do banco de dados de persistência no **bancos de dados disponíveis** lista suspensa.</span><span class="sxs-lookup"><span data-stu-id="af5a0-158">Select the name of the persistence database in the **Available Databases** drop-down.</span></span>  
  
5.  <span data-ttu-id="af5a0-159">Escolha **Execute** do **consulta** menu.</span><span class="sxs-lookup"><span data-stu-id="af5a0-159">Choose **Execute** from the **Query** menu.</span></span>  
  
 <span data-ttu-id="af5a0-160">Quando a consulta tiver sido concluída, o esquema de banco de dados é atualizado e, se desejar, você poderá exibir a identidade padrão de fluxo de trabalho que foi atribuída a instâncias de fluxo de trabalho persistidas.</span><span class="sxs-lookup"><span data-stu-id="af5a0-160">When the query completes, the database schema is upgraded, and if desired, you can view the default workflow identity that was assigned to the persisted workflow instances.</span></span> <span data-ttu-id="af5a0-161">Expanda o banco de dados de persistência no **bancos de dados** nó do **Pesquisador de objetos**e, em seguida, expanda o **exibições** nó.</span><span class="sxs-lookup"><span data-stu-id="af5a0-161">Expand your persistence database in the **Databases** node of the **Object Explorer**, and then expand the **Views** node.</span></span> <span data-ttu-id="af5a0-162">Clique com botão direito **System.Activities.DurableInstancing.Instances** e escolha **selecionar 1000 linhas superiores**.</span><span class="sxs-lookup"><span data-stu-id="af5a0-162">Right-click **System.Activities.DurableInstancing.Instances** and choose **Select Top 1000 Rows**.</span></span> <span data-ttu-id="af5a0-163">Role até o final das colunas e observe que há seis colunas adicionais adicionadas à exibição: **IdentityName**, **IdentityPackage**, **criar**, **principais** , **Secundária**, e **revisão**.</span><span class="sxs-lookup"><span data-stu-id="af5a0-163">Scroll to end of the columns and note that there are six additional columns added to the view: **IdentityName**, **IdentityPackage**, **Build**, **Major**, **Minor**, and **Revision**.</span></span> <span data-ttu-id="af5a0-164">Nenhum fluxo de trabalho persistentes terá um valor de **nulo** para esses campos, que representa uma identidade de fluxo de trabalho nulos.</span><span class="sxs-lookup"><span data-stu-id="af5a0-164">Any persisted workflows will have a value of **NULL** for these fields, representing a null workflow identity.</span></span>
