---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: b9ab4e8ca5a71d54a80d17322b61c83d41af2b40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673583"
---
# <a name="commonparameters"></a><span data-ttu-id="69acd-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="69acd-101">\<commonParameters></span></span>
<span data-ttu-id="69acd-102">Representa uma coleção de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="69acd-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="69acd-103">Esta coleção normalmente incluirão a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="69acd-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="69acd-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69acd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69acd-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="69acd-105">\<behaviors></span></span>  
<span data-ttu-id="69acd-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="69acd-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="69acd-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="69acd-107">\<behavior></span></span>  
<span data-ttu-id="69acd-108">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="69acd-108">\<workflowRuntime></span></span>  
<span data-ttu-id="69acd-109">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="69acd-109">\<commonParameters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69acd-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="69acd-110">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69acd-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="69acd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="69acd-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="69acd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69acd-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="69acd-113">Attributes</span></span>  
 <span data-ttu-id="69acd-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="69acd-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="69acd-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="69acd-115">Child Elements</span></span>  
  
|<span data-ttu-id="69acd-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="69acd-116">Element</span></span>|<span data-ttu-id="69acd-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="69acd-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69acd-118">\<add></span><span class="sxs-lookup"><span data-stu-id="69acd-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)|<span data-ttu-id="69acd-119">Adiciona um par nome-valor de parâmetros comuns usados pelos serviços à coleção.</span><span class="sxs-lookup"><span data-stu-id="69acd-119">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="69acd-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="69acd-120">Parent Elements</span></span>  
  
|<span data-ttu-id="69acd-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="69acd-121">Element</span></span>|<span data-ttu-id="69acd-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="69acd-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69acd-123">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="69acd-123">\<workflowRuntime></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowruntime.md)|<span data-ttu-id="69acd-124">Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar os serviços do Windows Communication Foundation (WCF) baseados em fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="69acd-124">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69acd-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="69acd-125">Remarks</span></span>  
 <span data-ttu-id="69acd-126">O `<commonParameters>` elemento define todos os parâmetros que são usados globalmente em vários serviços, por exemplo `ConnectionString` ao usar o <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="69acd-126">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69acd-127">Serviço de controle do SQL não usar consistentemente a `ConnectionString` valor se ele é especificado no `<commonParameters>` seção.</span><span class="sxs-lookup"><span data-stu-id="69acd-127">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="69acd-128">Algumas de suas operações, como recuperar o `StateMachineWorkflowInstance.StateHistory` propriedade pode falhar.</span><span class="sxs-lookup"><span data-stu-id="69acd-128">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="69acd-129">Solução alternativa para isso, especifique o `ConnectionString` de atributo na seção de configuração para provedor de rastreamento, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="69acd-129">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="69acd-130">Para os serviços que o trabalho de confirmação de lotes a armazenamentos de persistência, tais como <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> e <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, você poderá habilitá-las repetir a transação usando o `EnableRetries` parâmetro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="69acd-130">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
```xml  
<workflowRuntime name="SampleApplication"
                 unloadOnIdle="false">
  <commonParameters>
    <add name="ConnectionString"
         value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
    <add name="EnableRetries"
         value="True" />
  </commonParameters>
  <services>
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime,
               Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="69acd-131">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado na *CommonParameters* seção) ou para individuais dos serviços que dão suporte ao `EnableRetries` (conforme mostrado no *serviços*seção).</span><span class="sxs-lookup"><span data-stu-id="69acd-131">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="69acd-132">O código de exemplo a seguir mostra como alterar os parâmetros comuns de forma programática.</span><span class="sxs-lookup"><span data-stu-id="69acd-132">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="69acd-133">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo de host do Windows Workflow Foundation, consulte [arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="69acd-133">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69acd-134">Exemplo</span><span class="sxs-lookup"><span data-stu-id="69acd-134">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="69acd-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="69acd-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="69acd-136">[Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="69acd-136">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="69acd-137">\<add></span><span class="sxs-lookup"><span data-stu-id="69acd-137">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-commonparameters.md)
