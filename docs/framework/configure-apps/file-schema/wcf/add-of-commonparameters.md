---
title: <add> de <commonParameters>
ms.date: 03/30/2017
ms.assetid: 3713bf25-20c8-455f-bb85-de46b6487932
ms.openlocfilehash: 11be233d846f9025f041a26174e5b3bd2abdab55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91149186"
---
# <a name="add-of-commonparameters"></a><span data-ttu-id="c9548-102">\<add> de \<commonParameters></span><span class="sxs-lookup"><span data-stu-id="c9548-102">\<add> of \<commonParameters></span></span>

<span data-ttu-id="c9548-103">Especifica um par de nome-valor de parâmetros que são usados globalmente em vários serviços.</span><span class="sxs-lookup"><span data-stu-id="c9548-103">Specifies a name-value pair of parameters that are used globally across multiple services.</span></span> <span data-ttu-id="c9548-104">Normalmente, esse parâmetro inclui a cadeia de conexão de banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="c9548-104">Typically this parameter includes the database connection string that might be shared by durable services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<commonParameters>**](commonparameters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="c9548-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9548-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <commonParameters>
    <add name="String" value="String" />
  </commonParameters>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9548-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9548-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c9548-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9548-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9548-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9548-108">Attributes</span></span>  
  
|<span data-ttu-id="c9548-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="c9548-109">Attribute</span></span>|<span data-ttu-id="c9548-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9548-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9548-111">name</span><span class="sxs-lookup"><span data-stu-id="c9548-111">name</span></span>|<span data-ttu-id="c9548-112">O nome do parâmetro especificado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c9548-112">The name of the parameter specified for a service.</span></span>|  
|<span data-ttu-id="c9548-113">value</span><span class="sxs-lookup"><span data-stu-id="c9548-113">value</span></span>|<span data-ttu-id="c9548-114">O valor do parâmetro especificado para um serviço.</span><span class="sxs-lookup"><span data-stu-id="c9548-114">The value of the parameter specified for a service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9548-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9548-115">Child Elements</span></span>  

 <span data-ttu-id="c9548-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="c9548-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9548-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9548-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c9548-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9548-118">Element</span></span>|<span data-ttu-id="c9548-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9548-119">Description</span></span>|  
|-------------|-----------------|  
|[\<commonParameters>](commonparameters.md)|<span data-ttu-id="c9548-120">Uma coleção de parâmetros comuns usados por serviços.</span><span class="sxs-lookup"><span data-stu-id="c9548-120">A collection of common parameters used by services.</span></span> <span data-ttu-id="c9548-121">Normalmente, essa coleção inclui a cadeia de conexão do banco de dados que pode ser compartilhada por serviços duráveis.</span><span class="sxs-lookup"><span data-stu-id="c9548-121">This collection will typically include the database connection string that might be shared by durable services.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9548-122">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9548-122">Remarks</span></span>  

 <span data-ttu-id="c9548-123">O `<commonParameters>` elemento define todos os parâmetros que são usados globalmente em vários serviços, por exemplo, `ConnectionString` ao usar o <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService> .</span><span class="sxs-lookup"><span data-stu-id="c9548-123">The `<commonParameters>` element defines any parameters that are used globally across multiple services, for example `ConnectionString` when using the <xref:System.Workflow.Runtime.Hosting.SharedConnectionWorkflowCommitWorkBatchService>.</span></span>  
  
 <span data-ttu-id="c9548-124">Para serviços que confirmam lotes de trabalho para repositórios de persistência, como <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> e <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService> , você pode habilitá-los para repetir sua transação usando o `EnableRetries` parâmetro, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="c9548-124">For services that commit work batches to persistence stores, such as <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService> and <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>, you can enable them to retry their transaction by using the `EnableRetries` parameter as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="c9548-125">Observe que o `EnableRetries` parâmetro pode ser definido em um nível global (conforme mostrado na seção *CommonParameters* ) ou para serviços individuais que dão suporte `EnableRetries` (conforme mostrado na seção de *Serviços* ).</span><span class="sxs-lookup"><span data-stu-id="c9548-125">Notice that the `EnableRetries` parameter can be set at either a global level (as shown in the *CommonParameters* section) or for individual services that support `EnableRetries` (as shown in the *Services* section).</span></span>  
  
 <span data-ttu-id="c9548-126">Para obter mais informações sobre como usar um arquivo de configuração para controlar o comportamento de um <xref:System.Workflow.Runtime.WorkflowRuntime> objeto de um aplicativo host Windows Workflow Foundation, consulte [arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="c9548-126">For more information on using a configuration file to control the behavior of a <xref:System.Workflow.Runtime.WorkflowRuntime> object of a Windows Workflow Foundation host application, see [Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9548-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c9548-127">Example</span></span>  
  
```xml  
<commonParameters>
  <add name="ConnectionString"
       value="Initial Catalog=WorkflowStore;Data Source=localhost;Integrated Security=SSPI;" />
  <add name="EnableRetries"
       value="true" />
</commonParameters>
```  
  
## <a name="see-also"></a><span data-ttu-id="c9548-128">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9548-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <xref:System.Workflow.Runtime.Hosting.DefaultWorkflowCommitWorkBatchService>
- <xref:System.Workflow.Runtime.Hosting.SqlWorkflowPersistenceService>
- <span data-ttu-id="c9548-129">[Arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c9548-129">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
- [\<commonParameters>](commonparameters.md)
