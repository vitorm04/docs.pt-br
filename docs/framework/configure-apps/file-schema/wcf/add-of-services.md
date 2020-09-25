---
title: <add> de <services>
ms.date: 03/30/2017
ms.assetid: 6bdc4590-aa9c-4ec8-9345-879d780cd141
ms.openlocfilehash: 31a4d2a5a3baf3d53cf18ab6e37edfaf7acb8540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204977"
---
# <a name="add-of-services"></a><span data-ttu-id="3a0f6-102">\<add> de \<services></span><span class="sxs-lookup"><span data-stu-id="3a0f6-102">\<add> of \<services></span></span>

<span data-ttu-id="3a0f6-103">Especifica as configurações para uma instância do <xref:System.Workflow.Runtime.WorkflowRuntime> para hospedar serviços de Windows Communication Foundation baseado em fluxo de trabalho (WCF).</span><span class="sxs-lookup"><span data-stu-id="3a0f6-103">Specifies settings for an instance of <xref:System.Workflow.Runtime.WorkflowRuntime> for hosting workflow-based Windows Communication Foundation (WCF) services.</span></span> <span data-ttu-id="3a0f6-104">Esse elemento é do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3a0f6-104">This element is of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<workflowRuntime>**](workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services-of-workflowruntime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="3a0f6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a0f6-105">Syntax</span></span>  
  
```xml  
<workflowRuntime>
  <services>
    <add type="String" />
  </services>
</workflowRuntime>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a0f6-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a0f6-106">Attributes and Elements</span></span>  

 <span data-ttu-id="3a0f6-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a0f6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a0f6-108">Attributes</span></span>  
  
|<span data-ttu-id="3a0f6-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="3a0f6-109">Attribute</span></span>|<span data-ttu-id="3a0f6-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0f6-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3a0f6-111">type</span><span class="sxs-lookup"><span data-stu-id="3a0f6-111">type</span></span>|<span data-ttu-id="3a0f6-112">Uma cadeia de caracteres que especifica o nome do tipo qualificado por assembly do serviço a ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-112">A string that specifies the assembly-qualified type name of the service to be initialized.</span></span> <span data-ttu-id="3a0f6-113">O serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-113">The service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="3a0f6-114">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-114">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3a0f6-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a0f6-115">Child Elements</span></span>  

 <span data-ttu-id="3a0f6-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3a0f6-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a0f6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3a0f6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a0f6-118">Element</span></span>|<span data-ttu-id="3a0f6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a0f6-119">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services-of-workflowruntime.md)|<span data-ttu-id="3a0f6-120">Uma coleção de serviços que serão adicionados ao <xref:System.Workflow.Runtime.WorkflowRuntime> mecanismo.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-120">A collection of services that will be added to the <xref:System.Workflow.Runtime.WorkflowRuntime> engine.</span></span> <span data-ttu-id="3a0f6-121">Os elementos são do tipo <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> .</span><span class="sxs-lookup"><span data-stu-id="3a0f6-121">The elements are of type <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>.</span></span>  <span data-ttu-id="3a0f6-122">Os serviços especificados na coleção serão inicializados pelo mecanismo de tempo de execução do fluxo de trabalho e adicionados aos seus serviços quando o <xref:System.Workflow.Runtime.WorkflowRuntime> construtor apropriado for chamado.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-122">The services specified in the collection will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="3a0f6-123">Portanto, os serviços especificados na coleção devem seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-123">Therefore, the services specified in the collection must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="3a0f6-124">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-124">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a0f6-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a0f6-125">Remarks</span></span>  

 <span data-ttu-id="3a0f6-126">O serviço especificado neste elemento será inicializado pelo mecanismo de tempo de execução do fluxo de trabalho e adicionado aos seus serviços quando o <xref:System.Workflow.Runtime.WorkflowRuntime> construtor apropriado for chamado.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-126">The service specified in this element will be initialized by the workflow runtime engine and added to its services when the appropriate <xref:System.Workflow.Runtime.WorkflowRuntime> constructor is called.</span></span> <span data-ttu-id="3a0f6-127">Portanto, o serviço especificado deve seguir determinadas regras sobre as assinaturas de seus construtores.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-127">Therefore, the service specified must follow certain rules about the signatures of their constructors.</span></span> <span data-ttu-id="3a0f6-128">Consulte <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="3a0f6-128">See <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement> for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a0f6-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a0f6-129">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a0f6-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="3a0f6-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.WorkflowRuntimeElement>
- <xref:System.Workflow.Runtime.Configuration.WorkflowRuntimeServiceElement>
- <xref:System.Workflow.Runtime.WorkflowRuntime>
- <span data-ttu-id="3a0f6-131">[Arquivos de configuração de fluxo de trabalho](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3a0f6-131">[Workflow Configuration Files](/previous-versions/dotnet/netframework-3.5/ms732240(v=vs.90))</span></span>
