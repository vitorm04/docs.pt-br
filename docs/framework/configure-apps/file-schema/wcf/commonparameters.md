---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 6f187e9cdcabc358ee69d65e392bc59aa38e52ca
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398175"
---
# <a name="commonparameters"></a><span data-ttu-id="4efb0-101">\<commonParameters></span><span class="sxs-lookup"><span data-stu-id="4efb0-101">\<commonParameters></span></span>
<span data-ttu-id="4efb0-102">Representa uma coleção de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="4efb0-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="4efb0-103">Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="4efb0-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="4efb0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4efb0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4efb0-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4efb0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4efb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4efb0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="4efb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4efb0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="4efb0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4efb0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="4efb0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="4efb0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="4efb0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> CommonParameters**</span><span class="sxs-lookup"><span data-stu-id="4efb0-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4efb0-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4efb0-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4efb0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4efb0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4efb0-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4efb0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4efb0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4efb0-114">Attributes</span></span>  
 <span data-ttu-id="4efb0-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4efb0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4efb0-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4efb0-116">Child Elements</span></span>  
  
|<span data-ttu-id="4efb0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="4efb0-117">Element</span></span>|<span data-ttu-id="4efb0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efb0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4efb0-119">\<add></span><span class="sxs-lookup"><span data-stu-id="4efb0-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="4efb0-120">Adiciona um par nome-valor de parâmetros comuns usados pelos serviços para a coleção.</span><span class="sxs-lookup"><span data-stu-id="4efb0-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4efb0-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4efb0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4efb0-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="4efb0-122">Element</span></span>|<span data-ttu-id="4efb0-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="4efb0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4efb0-124">\<workflowRuntime></span><span class="sxs-lookup"><span data-stu-id="4efb0-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="4efb0-125">Especifica as configurações para uma instância <xref:System.Workflow.Runtime.WorkflowRuntime> do para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).</span><span class="sxs-lookup"><span data-stu-id="4efb0-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4efb0-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="4efb0-126">Remarks</span></span>  
 <span data-ttu-id="4efb0-127">O `<commonParameters>` elemento define todos os parâmetros que são usados globalmente em vários serviços, por `ConnectionString` exemplo, ao <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>usar o.</span><span class="sxs-lookup"><span data-stu-id="4efb0-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4efb0-128">O serviço de controle SQL não usa consistentemente o `ConnectionString` valor se for especificado `<commonParameters>` na seção.</span><span class="sxs-lookup"><span data-stu-id="4efb0-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="4efb0-129">Algumas de suas operações, como recuperar a `StateMachineWorkflowInstance.StateHistory` Propriedade, podem falhar.</span><span class="sxs-lookup"><span data-stu-id="4efb0-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="4efb0-130">Para solucionar esse problema, `ConnectionString` especifique o atributo na seção de configuração para o provedor de acompanhamento, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4efb0-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  
  
 `<add`  
  
 `type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"`  
  
 `ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />`  
  
 <span data-ttu-id="4efb0-131">Para serviços que confirmam lotes de trabalho para repositórios de <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> persistência <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, como e, você pode habilitá-los para repetir `EnableRetries` sua transação usando o parâmetro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="4efb0-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="4efb0-132">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado na seção *CommonParameters* ) ou para serviços individuais que dão suporte `EnableRetries` (conforme mostrado na seção de *Serviços* ).</span><span class="sxs-lookup"><span data-stu-id="4efb0-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="4efb0-133">O código de exemplo a seguir mostra como alterar os parâmetros comuns programaticamente.</span><span class="sxs-lookup"><span data-stu-id="4efb0-133">The following sample code shows how to change the common parameters programmatically.</span></span>  
  
```  
Configuration config=WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");  
WorkflowRuntimeSection wfruntime=config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters=wfruntime.CommonParameters;  
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="4efb0-134">Para obter mais informações sobre como usar um arquivo de configuração para controlar o <xref:System.Workflow.Runtime.WorkflowRuntime> comportamento de um objeto de um Windows Workflow Foundation aplicativo host, consulte [arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4efb0-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4efb0-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4efb0-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="4efb0-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4efb0-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="4efb0-137">[Arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="4efb0-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="4efb0-138">\<add></span><span class="sxs-lookup"><span data-stu-id="4efb0-138">\<add></span></span>](add-of-commonparameters.md)
