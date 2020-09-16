---
title: <commonParameters>
ms.date: 03/30/2017
ms.assetid: ffc20832-34d6-4622-8174-81924fd53514
ms.openlocfilehash: d4b912d003af201b19697854a67943e3d87e3734
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558479"
---
# \<commonParameters>
<span data-ttu-id="6e90d-101">Representa uma coleção de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="6e90d-101">Represents a collection of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="6e90d-102">Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="6e90d-102">This collection will typically include the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<commonParameters>**  
  
## <a name="syntax"></a><span data-ttu-id="6e90d-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="6e90d-103">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String"
         value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e90d-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6e90d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="6e90d-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6e90d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e90d-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="6e90d-106">Attributes</span></span>  
 <span data-ttu-id="6e90d-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6e90d-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e90d-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6e90d-108">Child Elements</span></span>  
  
|<span data-ttu-id="6e90d-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e90d-109">Element</span></span>|<span data-ttu-id="6e90d-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e90d-110">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-commonparameters.md)|<span data-ttu-id="6e90d-111">Adiciona um par nome-valor de parâmetros comuns usados pelos serviços para a coleção.</span><span class="sxs-lookup"><span data-stu-id="6e90d-111">Adds a name-value pair of common parameters used by services to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e90d-112">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6e90d-112">Parent Elements</span></span>  
  
|<span data-ttu-id="6e90d-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="6e90d-113">Element</span></span>|<span data-ttu-id="6e90d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="6e90d-114">Description</span></span>|  
|-------------|-----------------|  
|[\<workflowRuntime>](workflowruntime.md)|<span data-ttu-id="6e90d-115">Especifica as configurações para uma instância do <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).</span><span class="sxs-lookup"><span data-stu-id="6e90d-115">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e90d-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e90d-116">Remarks</span></span>  
 <span data-ttu-id="6e90d-117">O `<commonParameters>` elemento define todos os parâmetros que são usados globalmente em vários serviços, por exemplo, `ConnectionString` ao usar o <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="6e90d-117">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e90d-118">O serviço de controle SQL não usa consistentemente o `ConnectionString` valor se for especificado na `<commonParameters>` seção.</span><span class="sxs-lookup"><span data-stu-id="6e90d-118">SQL Tracking service does not consistently use the `ConnectionString` value if it is specified in the `<commonParameters>` section.</span></span> <span data-ttu-id="6e90d-119">Algumas de suas operações, como recuperar a `StateMachineWorkflowInstance.StateHistory` propriedade, podem falhar.</span><span class="sxs-lookup"><span data-stu-id="6e90d-119">Some of its operations such as retrieving the `StateMachineWorkflowInstance.StateHistory` property may fail.</span></span> <span data-ttu-id="6e90d-120">Para solucionar esse problema, especifique o `ConnectionString` atributo na seção de configuração para o provedor de acompanhamento, conforme indicado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="6e90d-120">To workaround this, specify the `ConnectionString` attribute in the configuration section for tracking provider, as indicated in the following example.</span></span>  

```xml  
<add
type="System.Workflow.Runtime.Tracking.SqlTrackingService, System.Workflow.Runtime, Version=3.0.00000.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35"
ConnectionString="Data Source=localhost;Initial Catalog=Partner20WFTP;Integrated Security=True;" />
```  
  
 <span data-ttu-id="6e90d-121">Para serviços que confirmam lotes de trabalho para repositórios de persistência, como <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> e <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , você pode habilitá-los para repetir sua transação usando o `EnableRetries` parâmetro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="6e90d-121">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="6e90d-122">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado na seção *CommonParameters* ) ou para serviços individuais que dão suporte `EnableRetries` (conforme mostrado na seção de *Serviços* ).</span><span class="sxs-lookup"><span data-stu-id="6e90d-122">Notice that the `EnableRetries` parameter can be set either at a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="6e90d-123">O código de exemplo a seguir mostra como alterar os parâmetros comuns programaticamente:</span><span class="sxs-lookup"><span data-stu-id="6e90d-123">The following sample code shows how to change the common parameters programmatically:</span></span>
  
```csharp  
Configuration config = WebConfigurationManager.OpenWebConfiguration("/Workflow", "Default Web Site", null, "localhost");
var wfruntime = config.GetSection("WorkflowRuntime") as WorkflowRuntimeSection;  
NameValueConfigurationCollection commonParameters = wfruntime.CommonParameters;
commonParameters["ConnectionString"].Value="another connection string";  
config.Save();  
```  
  
 <span data-ttu-id="6e90d-124">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um Windows Workflow Foundation aplicativo host, consulte [arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6e90d-124">For more information about using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e90d-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e90d-125">Example</span></span>  
  
```xml  
<commonParameters>
   <add name="ConnectionString"
        value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
   <add name="EnableRetries"
        value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="6e90d-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="6e90d-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="6e90d-127">[Arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="6e90d-127">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<add>](add-of-commonparameters.md)
