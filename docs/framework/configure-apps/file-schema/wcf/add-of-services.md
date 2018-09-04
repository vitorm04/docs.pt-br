---
title: '&lt;adicionar&gt; &lt;serviços&gt;'
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 6aa903d4188d108940c76ac50eb0a706fbea8f8b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43530244"
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="fa2b0-102">&lt;adicionar&gt; &lt;serviços&gt;</span><span class="sxs-lookup"><span data-stu-id="fa2b0-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="fa2b0-103">Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar os serviços do Windows Communication Foundation (WCF) baseados em fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="fa2b0-104">Esse elemento é do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="fa2b0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fa2b0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="fa2b0-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="fa2b0-106">\<behaviors></span></span>  
<span data-ttu-id="fa2b0-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fa2b0-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="fa2b0-108">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="fa2b0-108">\<behavior></span></span>  
<span data-ttu-id="fa2b0-109">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="fa2b0-109">\<services></span></span>  
<span data-ttu-id="fa2b0-110">\<add></span><span class="sxs-lookup"><span data-stu-id="fa2b0-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa2b0-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa2b0-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa2b0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fa2b0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fa2b0-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa2b0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="fa2b0-114">Attributes</span></span>  
  
|<span data-ttu-id="fa2b0-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="fa2b0-115">Attribute</span></span>|<span data-ttu-id="fa2b0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa2b0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fa2b0-117">tipo</span><span class="sxs-lookup"><span data-stu-id="fa2b0-117">type</span></span>|<span data-ttu-id="fa2b0-118">Uma cadeia de caracteres que especifica o nome de tipo qualificado pelo assembly do serviço a ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="fa2b0-119">O serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="fa2b0-120">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa2b0-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fa2b0-121">Child Elements</span></span>  
 <span data-ttu-id="fa2b0-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa2b0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fa2b0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fa2b0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="fa2b0-124">Element</span></span>|<span data-ttu-id="fa2b0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa2b0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa2b0-126">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="fa2b0-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="fa2b0-127">Uma coleção de serviços que serão adicionados para o <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="fa2b0-128">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="fa2b0-129">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução de fluxo de trabalho e adicionados a seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="fa2b0-130">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="fa2b0-131">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa2b0-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa2b0-132">Remarks</span></span>  
 <span data-ttu-id="fa2b0-133">O serviço especificado nesse elemento será inicializado pelo mecanismo de tempo de execução de fluxo de trabalho e adicionado a seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="fa2b0-134">Portanto, o serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="fa2b0-135">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="fa2b0-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa2b0-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa2b0-136">Example</span></span>  
  
```xml  
<serviceBehaviors>  
   <behavior name="ServiceBehavior">  
      <workflowRuntime name="WorkflowServiceHostRuntime"  
                       validateOnCreate="true"  
                       enablePerformanceCounters="true">  
         <services>  
             <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common"/>  
         </services>  
      </workflowRuntime>  
   </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fa2b0-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa2b0-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 <span data-ttu-id="fa2b0-138">[Arquivos de configuração do fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fa2b0-138">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
