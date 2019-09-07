---
title: <add> de <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: d682acd7fff6bab2c66660a028f8a75b780e21d2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400674"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="d7c9a-102">\<Adicionar > de \<> CommonParameters</span><span class="sxs-lookup"><span data-stu-id="d7c9a-102">\<add> of \<commonParameters></span></span>
<span data-ttu-id="d7c9a-103">Especifica um par de nome-valor de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="d7c9a-104">Normalmente, esse parâmetro inclui a cadeia de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="d7c9a-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d7c9a-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d7c9a-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="d7c9a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="d7c9a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="d7c9a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="d7c9a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> CommonParameters**](commonparameters.md)</span><span class="sxs-lookup"><span data-stu-id="d7c9a-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)</span></span>\
<span data-ttu-id="d7c9a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="d7c9a-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7c9a-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7c9a-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7c9a-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7c9a-114">Attributes and Elements</span></span>  
 <span data-ttu-id="d7c9a-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7c9a-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7c9a-116">Attributes</span></span>  
  
|<span data-ttu-id="d7c9a-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="d7c9a-117">Attribute</span></span>|<span data-ttu-id="d7c9a-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7c9a-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d7c9a-119">name</span><span class="sxs-lookup"><span data-stu-id="d7c9a-119">name</span></span>|<span data-ttu-id="d7c9a-120">O nome do parâmetro especificado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-120">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="d7c9a-121">value</span><span class="sxs-lookup"><span data-stu-id="d7c9a-121">value</span></span>|<span data-ttu-id="d7c9a-122">O valor do parâmetro especificado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-122">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7c9a-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7c9a-123">Child Elements</span></span>  
 <span data-ttu-id="d7c9a-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7c9a-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7c9a-125">Parent Elements</span></span>  
  
|<span data-ttu-id="d7c9a-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7c9a-126">Element</span></span>|<span data-ttu-id="d7c9a-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7c9a-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7c9a-128">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="d7c9a-128">\<commonParameters></span></span>](commonparameters.md)|<span data-ttu-id="d7c9a-129">Uma coleção de parâmetros comuns usados por serviços.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-129">A collection of common parameters used by services.</span></span> <span data-ttu-id="d7c9a-130">Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-130">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7c9a-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7c9a-131">Remarks</span></span>  
 <span data-ttu-id="d7c9a-132">O `<commonParameters>` elemento define todos os parâmetros que são usados globalmente em vários serviços, por `ConnectionString` exemplo, ao <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>usar o.</span><span class="sxs-lookup"><span data-stu-id="d7c9a-132">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="d7c9a-133">Para serviços que confirmam lotes de trabalho para repositórios de <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> persistência <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, como e, você pode habilitá-los para repetir `EnableRetries` sua transação usando o parâmetro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="d7c9a-133">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
    <add type="System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
         enableRetries="False" />
  </services>
</workflowRuntime>
```  
  
 <span data-ttu-id="d7c9a-134">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado na seção *CommonParameters* ) ou para serviços individuais que dão suporte `EnableRetries` (conforme mostrado na seção de *Serviços* ).</span><span class="sxs-lookup"><span data-stu-id="d7c9a-134">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="d7c9a-135">Para obter mais informações sobre como usar um arquivo de configuração para controlar o <xref:System.Workflow.Runtime.WorkflowRuntime> comportamento de um objeto de um aplicativo host Windows Workflow Foundation, consulte [arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="d7c9a-135">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7c9a-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d7c9a-136">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="d7c9a-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7c9a-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="d7c9a-138">[Arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d7c9a-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="d7c9a-139">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="d7c9a-139">\<commonParameters></span></span>](commonparameters.md)
