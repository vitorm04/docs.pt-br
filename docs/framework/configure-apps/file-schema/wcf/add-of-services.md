---
title: <add> de <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: dc769097a3aede2522c1fa7a4cf8e36c2d8fdfe8
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398286"
---
# <a name="add-of-services"></a><span data-ttu-id="c1f8f-102">\<Adicionar > de \<serviços ></span><span class="sxs-lookup"><span data-stu-id="c1f8f-102">\<add> of \<services></span></span>
<span data-ttu-id="c1f8f-103">Especifica as configurações para uma instância <xref:System.Workflow.Runtime.WorkflowRuntime> do para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).</span><span class="sxs-lookup"><span data-stu-id="c1f8f-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="c1f8f-104">Esse elemento é do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
<span data-ttu-id="c1f8f-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1f8f-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c1f8f-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c1f8f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c1f8f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c1f8f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de workflowRuntime**](workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)</span></span>\
<span data-ttu-id="c1f8f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services-of-workflowruntime.md)</span><span class="sxs-lookup"><span data-stu-id="c1f8f-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)</span></span>\
<span data-ttu-id="c1f8f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Adicionar >**</span><span class="sxs-lookup"><span data-stu-id="c1f8f-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1f8f-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c1f8f-113">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1f8f-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c1f8f-114">Attributes and Elements</span></span>  
 <span data-ttu-id="c1f8f-115">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1f8f-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="c1f8f-116">Attributes</span></span>  
  
|<span data-ttu-id="c1f8f-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="c1f8f-117">Attribute</span></span>|<span data-ttu-id="c1f8f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1f8f-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1f8f-119">tipo</span><span class="sxs-lookup"><span data-stu-id="c1f8f-119">type</span></span>|<span data-ttu-id="c1f8f-120">Uma cadeia de caracteres que especifica o nome do tipo qualificado por assembly do serviço a ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-120">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="c1f8f-121">O serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-121">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c1f8f-122">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-122">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1f8f-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c1f8f-123">Child Elements</span></span>  
 <span data-ttu-id="c1f8f-124">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1f8f-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c1f8f-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c1f8f-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="c1f8f-126">Element</span></span>|<span data-ttu-id="c1f8f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1f8f-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1f8f-128">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="c1f8f-128">\<services></span></span>](services-of-workflowruntime.md)|<span data-ttu-id="c1f8f-129">Uma coleção de serviços que serão adicionados ao <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-129">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="c1f8f-130">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-130">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="c1f8f-131">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução do fluxo de trabalho e adicionados aos seus <xref:System.Workflow.Runtime.WorkflowRuntime> serviços quando o construtor apropriado for chamado.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-131">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="c1f8f-132">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-132">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c1f8f-133">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-133">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1f8f-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="c1f8f-134">Remarks</span></span>  
 <span data-ttu-id="c1f8f-135">O serviço especificado neste elemento será inicializado pelo mecanismo de tempo de execução do fluxo de trabalho e adicionado aos seus <xref:System.Workflow.Runtime.WorkflowRuntime> serviços quando o construtor apropriado for chamado.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-135">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="c1f8f-136">Portanto, o serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-136">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="c1f8f-137">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="c1f8f-137">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1f8f-138">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c1f8f-138">Example</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="ServiceBehavior">
    <workflowRuntime name="WorkflowServiceHostRuntime"
                     validateOnCreate="true"
                     enablePerformanceCounters="true">
      <services>
        <add type="NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common.TestPersistenceService.FilePersistenceService, NetFx.Checkin.Scenario.WorkflowServices.WorkflowBasedServices.Common" />
      </services>
    </workflowRuntime>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="c1f8f-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1f8f-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="c1f8f-140">[Arquivos de configuração de fluxo de trabalho](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c1f8f-140">[Workflow Configuration Files](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
