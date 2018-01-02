---
title: '&lt;commonParameters&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: efd4f37adb19940e81109924c3ec313d71bf6e7f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltcommonparametersgt"></a><span data-ttu-id="ddbfc-102">&lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ddbfc-102">&lt;commonParameters&gt;</span></span>
<span data-ttu-id="ddbfc-103">Representa uma coleção de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-103">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="ddbfc-104">Normalmente, essa coleção incluirá a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada com serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-104">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="ddbfc-105">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ddbfc-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-106">\<behaviors></span></span>  
<span data-ttu-id="ddbfc-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="ddbfc-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-108">\<behavior></span></span>  
<span data-ttu-id="ddbfc-109">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-109">\<workflowRuntime></span></span>  
<span data-ttu-id="ddbfc-110">\<commonParameters ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-110">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddbfc-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ddbfc-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ddbfc-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ddbfc-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ddbfc-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ddbfc-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="ddbfc-114">Attributes</span></span>  
 <span data-ttu-id="ddbfc-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ddbfc-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ddbfc-116">Child Elements</span></span>  
  
|<span data-ttu-id="ddbfc-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddbfc-117">Element</span></span>|<span data-ttu-id="ddbfc-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddbfc-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddbfc-119">\<add></span><span class="sxs-lookup"><span data-stu-id="ddbfc-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="ddbfc-120">Adiciona um par nome-valor dos parâmetros comuns usados pelos serviços à coleção.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ddbfc-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ddbfc-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ddbfc-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="ddbfc-122">Element</span></span>|<span data-ttu-id="ddbfc-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddbfc-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ddbfc-124">\<workflowRuntime ></span><span class="sxs-lookup"><span data-stu-id="ddbfc-124">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="ddbfc-125">Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para a hospedagem com base em fluxo de trabalho [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddbfc-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="ddbfc-126">Remarks</span></span>  
 <span data-ttu-id="ddbfc-127">O `<commonParameters>` elemento define os parâmetros que são usados globalmente em vários serviços, por exemplo `ConnectionString` ao usar o <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddbfc-128">O serviço de rastreamento do SQL não usar consistentemente o `ConnectionString` valor se for especificado no `<commonParameters>` seção.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="ddbfc-129">Algumas das suas operações, como recuperar o `StateMachineWorkflowInstance.StateHistory` propriedade pode falhar.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="ddbfc-130">Para solucionar isso, especifique o `ConnectionString` atributo na seção de configuração para o provedor de rastreamento, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="ddbfc-131">Para serviços que confirme o trabalho processa em lotes em repositórios de persistência, como <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> e <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, você poderá habilitá-los repetir a transação usando o `EnableRetries` parâmetro conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="ddbfc-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<WorkflowRuntime Name="SampleApplication" UnloadOnIdle="false">  
    <commonParameters>  
        <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />  
        <add name="EnableRetries" value="True" />  
    </commonParameters>  
    <Services>  
        <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" EnableRetries="False" />   
     </Services>  
</WorkflowRuntime>  
```  
  
 <span data-ttu-id="ddbfc-132">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado no *CommonParameters* seção) ou para individuais dos serviços que oferecem suporte a `EnableRetries` (conforme mostrado no *serviços*seção).</span><span class="sxs-lookup"><span data-stu-id="ddbfc-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="ddbfc-133">O código de exemplo a seguir mostra como alterar os parâmetros comuns de forma programática.</span><span class="sxs-lookup"><span data-stu-id="ddbfc-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="ddbfc-134">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo de host do Windows Workflow Foundation, consulte [arquivos de configuração do fluxo de trabalho](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span><span class="sxs-lookup"><span data-stu-id="ddbfc-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddbfc-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ddbfc-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ddbfc-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ddbfc-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 [<span data-ttu-id="ddbfc-137">Arquivos de configuração do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="ddbfc-137">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/en-us/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)  
 [<span data-ttu-id="ddbfc-138">\<add></span><span class="sxs-lookup"><span data-stu-id="ddbfc-138">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
