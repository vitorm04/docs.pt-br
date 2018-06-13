---
title: '&lt;endToEndTracing&gt;'
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 855f579241dfd495e7f8603ce3bd57aa2556ca2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753463"
---
# <a name="ltendtoendtracinggt"></a><span data-ttu-id="555be-102">&lt;endToEndTracing&gt;</span><span class="sxs-lookup"><span data-stu-id="555be-102">&lt;endToEndTracing&gt;</span></span>
<span data-ttu-id="555be-103">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="555be-103">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="555be-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="555be-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="555be-105">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="555be-105">\<diagnostic></span></span>  
<span data-ttu-id="555be-106">\<endToEndTracing ></span><span class="sxs-lookup"><span data-stu-id="555be-106">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="555be-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="555be-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="555be-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="555be-108">Attributes and Elements</span></span>  
 <span data-ttu-id="555be-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="555be-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="555be-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="555be-110">Attributes</span></span>  
  
|<span data-ttu-id="555be-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="555be-111">Attribute</span></span>|<span data-ttu-id="555be-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="555be-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="555be-113">Um valor booleano que especifica se o rastreamento de atividades está habilitado.</span><span class="sxs-lookup"><span data-stu-id="555be-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="555be-114">Um valor booleano que especifica se o fluxo de mensagens de rastreamento no habilitado.</span><span class="sxs-lookup"><span data-stu-id="555be-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="555be-115">Um valor booleano que especifica se o atributo propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="555be-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="555be-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="555be-116">Child Elements</span></span>  
 <span data-ttu-id="555be-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="555be-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="555be-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="555be-118">Parent Elements</span></span>  
  
|<span data-ttu-id="555be-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="555be-119">Element</span></span>|<span data-ttu-id="555be-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="555be-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="555be-121">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="555be-121">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="555be-122">Define as configurações de WCF para inspeção de tempo de execução e o controle para o administrador.</span><span class="sxs-lookup"><span data-stu-id="555be-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="555be-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="555be-123">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [<span data-ttu-id="555be-124">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="555be-124">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
