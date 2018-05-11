---
title: '&lt;adicionar&gt; &lt;serviços&gt;'
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 709636f0b9667a431838b463c05cfd00f6521f6b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="d0612-102">&lt;adicionar&gt; &lt;serviços&gt;</span><span class="sxs-lookup"><span data-stu-id="d0612-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="d0612-103">Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar os serviços do Windows Communication Foundation (WCF) baseados em fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="d0612-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="d0612-104">Esse elemento é do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d0612-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="d0612-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d0612-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d0612-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d0612-106">\<behaviors></span></span>  
<span data-ttu-id="d0612-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d0612-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="d0612-108">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="d0612-108">\<behavior></span></span>  
<span data-ttu-id="d0612-109">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="d0612-109">\<services></span></span>  
<span data-ttu-id="d0612-110">\<add></span><span class="sxs-lookup"><span data-stu-id="d0612-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0612-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0612-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d0612-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d0612-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d0612-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d0612-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d0612-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="d0612-114">Attributes</span></span>  
  
|<span data-ttu-id="d0612-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="d0612-115">Attribute</span></span>|<span data-ttu-id="d0612-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0612-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d0612-117">tipo</span><span class="sxs-lookup"><span data-stu-id="d0612-117">type</span></span>|<span data-ttu-id="d0612-118">Uma cadeia de caracteres que especifica o nome de tipo qualificado por assembly do serviço a ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="d0612-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="d0612-119">O serviço especificado deve seguir determinadas regras sobre as assinaturas dos seus construtores.</span><span class="sxs-lookup"><span data-stu-id="d0612-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d0612-120">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="d0612-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d0612-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d0612-121">Child Elements</span></span>  
 <span data-ttu-id="d0612-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d0612-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d0612-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d0612-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d0612-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="d0612-124">Element</span></span>|<span data-ttu-id="d0612-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="d0612-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d0612-126">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="d0612-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="d0612-127">Uma coleção de serviços que serão adicionados para o <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="d0612-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="d0612-128">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="d0612-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="d0612-129">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução de fluxo de trabalho e adicionados para seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="d0612-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d0612-130">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas dos seus construtores.</span><span class="sxs-lookup"><span data-stu-id="d0612-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d0612-131">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="d0612-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0612-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0612-132">Remarks</span></span>  
 <span data-ttu-id="d0612-133">O serviço especificado nesse elemento será inicializado pelo mecanismo de tempo de execução de fluxo de trabalho e adicionado para seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="d0612-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="d0612-134">Portanto, o serviço especificado deve seguir determinadas regras sobre as assinaturas dos seus construtores.</span><span class="sxs-lookup"><span data-stu-id="d0612-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="d0612-135">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="d0612-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0612-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0612-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d0612-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0612-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="d0612-138">Arquivos de configuração do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="d0612-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
