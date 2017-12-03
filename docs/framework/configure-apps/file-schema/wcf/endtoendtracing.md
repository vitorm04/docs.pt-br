---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bb187302000291fd6b540b562ed7aebf1db7add2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="d7bc7-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="d7bc7-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="d7bc7-103">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="d7bc7-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d7bc7-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7bc7-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="d7bc7-105">\<diagnostic></span></span>  
<span data-ttu-id="d7bc7-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="d7bc7-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7bc7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d7bc7-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7bc7-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d7bc7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d7bc7-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7bc7-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="d7bc7-110">Attributes</span></span>  
  
|<span data-ttu-id="d7bc7-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="d7bc7-111">Attribute</span></span>|<span data-ttu-id="d7bc7-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7bc7-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="d7bc7-113">Um valor booleano que especifica se o rastreamento de atividades está habilitado.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="d7bc7-114">Um valor booleano que especifica se o fluxo de mensagens de rastreamento no habilitado.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="d7bc7-115">Um valor booleano que especifica se o atributo propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d7bc7-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d7bc7-116">Child Elements</span></span>  
 <span data-ttu-id="d7bc7-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d7bc7-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d7bc7-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d7bc7-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="d7bc7-119">Element</span></span>|<span data-ttu-id="d7bc7-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7bc7-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7bc7-121">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="d7bc7-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="d7bc7-122">Define as configurações de WCF para inspeção de tempo de execução e o controle para o administrador.</span><span class="sxs-lookup"><span data-stu-id="d7bc7-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7bc7-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7bc7-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="d7bc7-124">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="d7bc7-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
