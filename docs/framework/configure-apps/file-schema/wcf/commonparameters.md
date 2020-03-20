---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: 73d8549f68e8ca77115619431c857c4a2aac3fdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153016"
---
# <a name="commonparameters"></a><span data-ttu-id="58416-101">\<parâmetros comuns></span><span class="sxs-lookup"><span data-stu-id="58416-101">\<commonParameters></span></span>
<span data-ttu-id="58416-102">Representa uma coleção de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="58416-102">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="58416-103">Essa coleção normalmente incluirá a seqüência de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="58416-103">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
<span data-ttu-id="58416-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="58416-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="58416-105">&nbsp;&nbsp;[**\<system.serviceModelo>**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="58416-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="58416-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamentos>**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="58416-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="58416-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviçocomportamentos>**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="58416-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="58416-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comportamento>**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="58416-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="58416-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<fluxo de trabalho>detempo de execução**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="58416-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="58416-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<parâmetros comuns>**</span><span class="sxs-lookup"><span data-stu-id="58416-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58416-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="58416-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58416-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="58416-112">Attributes and Elements</span></span>  
 <span data-ttu-id="58416-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="58416-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58416-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="58416-114">Attributes</span></span>  
 <span data-ttu-id="58416-115">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="58416-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58416-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="58416-116">Child Elements</span></span>  
  
|<span data-ttu-id="58416-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="58416-117">Element</span></span>|<span data-ttu-id="58416-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="58416-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58416-119">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="58416-119">\<add></span></span>](add-of-commonparameters.md)|<span data-ttu-id="58416-120">Adiciona um par de parâmetros comuns usados pelos serviços à coleção.</span><span class="sxs-lookup"><span data-stu-id="58416-120">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58416-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="58416-121">Parent Elements</span></span>  
  
|<span data-ttu-id="58416-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="58416-122">Element</span></span>|<span data-ttu-id="58416-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="58416-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58416-124">\<fluxo de trabalho>detempo de execução</span><span class="sxs-lookup"><span data-stu-id="58416-124">\<workflowRuntime></span></span>](workflowruntime.md)|<span data-ttu-id="58416-125">Especifica configurações para uma <xref:System.Workflow.Runtime.WorkflowRuntime> instância de hospedagem de serviços wcf baseados em fluxo de trabalho baseados no Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="58416-125">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58416-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="58416-126">Remarks</span></span>  
 <span data-ttu-id="58416-127">O `<commonParameters>` elemento define quaisquer parâmetros que são usados `ConnectionString` globalmente <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>em vários serviços, por exemplo, ao usar o .</span><span class="sxs-lookup"><span data-stu-id="58416-127">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="58416-128">O serviço sql tracking não `ConnectionString` usa consistentemente o `<commonParameters>` valor se for especificado na seção.</span><span class="sxs-lookup"><span data-stu-id="58416-128">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="58416-129">Algumas de suas operações, `StateMachineWorkflowInstance.StateHistory` como recuperar a propriedade, podem falhar.</span><span class="sxs-lookup"><span data-stu-id="58416-129">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="58416-130">Para contornar isso, `ConnectionString` especifique o atributo na seção de configuração para o provedor de rastreamento, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="58416-130">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="58416-131">Para serviços que comprometem lotes de <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> trabalho <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>em lojas de persistência, como e `EnableRetries` , você pode permitir que eles tritimem novamente sua transação usando o parâmetro como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="58416-131">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="58416-132">Observe que `EnableRetries` o parâmetro pode ser definido em nível global (como mostrado na seção *CommonParameters)* ou para serviços individuais que suportam `EnableRetries` (como mostrado na seção *Serviços).*</span><span class="sxs-lookup"><span data-stu-id="58416-132">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="58416-133">O código de amostra a seguir mostra como alterar os parâmetros comuns de forma programática:</span><span class="sxs-lookup"><span data-stu-id="58416-133">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="58416-134">Para obter mais informações sobre o uso <xref:System.Workflow.Runtime.WorkflowRuntime> de um arquivo de configuração para controlar o comportamento de um objeto de um aplicativo de host do Windows Workflow Foundation, consulte [Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="58416-134">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="58416-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58416-135">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="58416-136">Confira também</span><span class="sxs-lookup"><span data-stu-id="58416-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="58416-137">[Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="58416-137">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [<span data-ttu-id="58416-138">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="58416-138">\<add></span></span>](add-of-commonparameters.md)
