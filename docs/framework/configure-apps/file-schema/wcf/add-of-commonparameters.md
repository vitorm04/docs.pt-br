---
title: '&lt;adicionar&gt; &lt;commonParameters&gt;'
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 93e82aa3bd44a747d1e85986c51c21522d709bd0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192906"
---
# <a name="ltaddgt-of-ltcommonparametersgt"></a><span data-ttu-id="16b54-102">&lt;adicionar&gt; &lt;commonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="16b54-102">&lt;add&gt; of &lt;commonParameters&gt;</span></span>
<span data-ttu-id="16b54-103">Especifica um par nome-valor de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="16b54-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="16b54-104">Normalmente, esse parâmetro inclui a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="16b54-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
 <span data-ttu-id="16b54-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="16b54-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="16b54-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="16b54-106">\<behaviors></span></span>  
<span data-ttu-id="16b54-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="16b54-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="16b54-108">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="16b54-108">\<behavior></span></span>  
<span data-ttu-id="16b54-109">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="16b54-109">\<workflowRuntime></span></span>  
<span data-ttu-id="16b54-110">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="16b54-110">\<commonParameters></span></span>  
<span data-ttu-id="16b54-111">\<add></span><span class="sxs-lookup"><span data-stu-id="16b54-111">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b54-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="16b54-112">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <commonParameters>  
      <add name="String" value="String" />  
   </commonParameters>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16b54-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="16b54-113">Attributes and Elements</span></span>  
 <span data-ttu-id="16b54-114">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="16b54-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16b54-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="16b54-115">Attributes</span></span>  
  
|<span data-ttu-id="16b54-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="16b54-116">Attribute</span></span>|<span data-ttu-id="16b54-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="16b54-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="16b54-118">name</span><span class="sxs-lookup"><span data-stu-id="16b54-118">name</span></span>|<span data-ttu-id="16b54-119">O nome do parâmetro especificado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="16b54-119">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="16b54-120">Valor </span><span class="sxs-lookup"><span data-stu-id="16b54-120">value</span></span>|<span data-ttu-id="16b54-121">O valor do parâmetro especificado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="16b54-121">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16b54-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="16b54-122">Child Elements</span></span>  
 <span data-ttu-id="16b54-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="16b54-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16b54-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="16b54-124">Parent Elements</span></span>  
  
|<span data-ttu-id="16b54-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="16b54-125">Element</span></span>|<span data-ttu-id="16b54-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="16b54-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="16b54-127">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="16b54-127">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)|<span data-ttu-id="16b54-128">Uma coleção de parâmetros comuns usados pelos serviços.</span><span class="sxs-lookup"><span data-stu-id="16b54-128">A collection of common parameters used by services.</span></span> <span data-ttu-id="16b54-129">Esta coleção normalmente incluirão a cadeia de caracteres de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="16b54-129">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="16b54-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="16b54-130">Remarks</span></span>  
 <span data-ttu-id="16b54-131">O `<commonParameters>` elemento define todos os parâmetros que são usados globalmente em vários serviços, por exemplo `ConnectionString` ao usar o <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span><span class="sxs-lookup"><span data-stu-id="16b54-131">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="16b54-132">Para os serviços que o trabalho de confirmação de lotes a armazenamentos de persistência, tais como <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> e <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, você poderá habilitá-las repetir a transação usando o `EnableRetries` parâmetro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="16b54-132">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="16b54-133">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado na *CommonParameters* seção) ou para individuais dos serviços que dão suporte ao `EnableRetries` (conforme mostrado no *serviços*seção).</span><span class="sxs-lookup"><span data-stu-id="16b54-133">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="16b54-134">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo de host do Windows Workflow Foundation, consulte [arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="16b54-134">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="16b54-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="16b54-135">Example</span></span>  
  
```xml  
<commonParameters>  
   <add name="ConnectionString" value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;"/>  
   <add name="EnableRetries" value="true"/>  
</commonParameters>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16b54-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="16b54-136">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>  
 <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>  
 <span data-ttu-id="16b54-137">[Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="16b54-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>  
 [<span data-ttu-id="16b54-138">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="16b54-138">\<commonParameters></span></span>](https://msdn.microsoft.com/library/d0e1e6fc-985a-4713-b7da-194e30dfab4c)
