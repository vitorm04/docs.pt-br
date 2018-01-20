---
title: "&lt;adicionar&gt; &lt;serviços&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 040db3b350ebacfc3aff76d90e87e65206701069
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt-of-ltservicesgt"></a><span data-ttu-id="91808-102">&lt;adicionar&gt; &lt;serviços&gt;</span><span class="sxs-lookup"><span data-stu-id="91808-102">&lt;add&gt; of &lt;services&gt;</span></span>
<span data-ttu-id="91808-103">Especifica configurações para uma instância de <xref:System.Workflow.Runtime.WorkflowRuntime> para a hospedagem com base em fluxo de trabalho [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviços.</span><span class="sxs-lookup"><span data-stu-id="91808-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] services.</span></span> <span data-ttu-id="91808-104">Esse elemento é do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="91808-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
 <span data-ttu-id="91808-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="91808-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="91808-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="91808-106">\<behaviors></span></span>  
<span data-ttu-id="91808-107">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="91808-107">\<serviceBehaviors></span></span>  
<span data-ttu-id="91808-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="91808-108">\<behavior></span></span>  
<span data-ttu-id="91808-109">\<services></span><span class="sxs-lookup"><span data-stu-id="91808-109">\<services></span></span>  
<span data-ttu-id="91808-110">\<add></span><span class="sxs-lookup"><span data-stu-id="91808-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91808-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91808-111">Syntax</span></span>  
  
```xml  
<workflowRuntime>  
   <services>  
      <add type="String"/>  
   </services>  
</workflowRuntime>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91808-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="91808-112">Attributes and Elements</span></span>  
 <span data-ttu-id="91808-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="91808-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91808-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="91808-114">Attributes</span></span>  
  
|<span data-ttu-id="91808-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="91808-115">Attribute</span></span>|<span data-ttu-id="91808-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="91808-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="91808-117">tipo</span><span class="sxs-lookup"><span data-stu-id="91808-117">type</span></span>|<span data-ttu-id="91808-118">Uma cadeia de caracteres que especifica o nome de tipo qualificado por assembly do serviço a ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="91808-118">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="91808-119">O serviço especificado deve seguir determinadas regras sobre as assinaturas dos seus construtores.</span><span class="sxs-lookup"><span data-stu-id="91808-119">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="91808-120">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="91808-120">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91808-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="91808-121">Child Elements</span></span>  
 <span data-ttu-id="91808-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="91808-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91808-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="91808-123">Parent Elements</span></span>  
  
|<span data-ttu-id="91808-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="91808-124">Element</span></span>|<span data-ttu-id="91808-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="91808-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91808-126">\<services></span><span class="sxs-lookup"><span data-stu-id="91808-126">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services-of-workflowruntime.md)|<span data-ttu-id="91808-127">Uma coleção de serviços que serão adicionados para o <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="91808-127">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="91808-128">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="91808-128">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="91808-129">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução de fluxo de trabalho e adicionados para seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="91808-129">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="91808-130">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas dos seus construtores.</span><span class="sxs-lookup"><span data-stu-id="91808-130">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="91808-131">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="91808-131">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91808-132">Comentários</span><span class="sxs-lookup"><span data-stu-id="91808-132">Remarks</span></span>  
 <span data-ttu-id="91808-133">O serviço especificado nesse elemento será inicializado pelo mecanismo de tempo de execução de fluxo de trabalho e adicionado para seus serviços quando apropriado <xref:System.Workflow.Runtime.WorkflowRuntime> construtor seja chamado.</span><span class="sxs-lookup"><span data-stu-id="91808-133">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="91808-134">Portanto, o serviço especificado deve seguir determinadas regras sobre as assinaturas dos seus construtores.</span><span class="sxs-lookup"><span data-stu-id="91808-134">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="91808-135">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="91808-135">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91808-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="91808-136">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="91808-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="91808-137">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>  
 <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>  
 <xref:System.Workflow.Runtime.WorkflowRuntime>  
 [<span data-ttu-id="91808-138">Arquivos de configuração do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="91808-138">Workflow Configuration Files</span></span>](http://msdn.microsoft.com/library/ada4bb90-6c9d-4f3d-a9d0-b559bb0f9909)
