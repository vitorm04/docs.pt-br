---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1867e307ba004af821045e7d1b5775c470d8a3e8
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266748"
---
# <a name="endtoendtracing"></a><span data-ttu-id="ad45e-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="ad45e-101">\<endToEndTracing></span></span>
<span data-ttu-id="ad45e-102">Um elemento de configuração que permite que você habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="ad45e-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="ad45e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ad45e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ad45e-104">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="ad45e-104">\<diagnostic></span></span>  
<span data-ttu-id="ad45e-105">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="ad45e-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad45e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ad45e-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ad45e-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ad45e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ad45e-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ad45e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ad45e-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="ad45e-109">Attributes</span></span>  
  
|<span data-ttu-id="ad45e-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="ad45e-110">Attribute</span></span>|<span data-ttu-id="ad45e-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad45e-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="ad45e-112">Um valor booliano que especifica se o rastreamento de atividades está habilitado.</span><span class="sxs-lookup"><span data-stu-id="ad45e-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="ad45e-113">Um valor booliano que especifica se o fluxo de mensagens de rastreamento no habilitada.</span><span class="sxs-lookup"><span data-stu-id="ad45e-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="ad45e-114">Um valor booliano que especifica se o atributo propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="ad45e-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ad45e-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ad45e-115">Child Elements</span></span>  
 <span data-ttu-id="ad45e-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ad45e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ad45e-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ad45e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ad45e-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="ad45e-118">Element</span></span>|<span data-ttu-id="ad45e-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="ad45e-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ad45e-120">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="ad45e-120">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="ad45e-121">Define as configurações do WCF para inspeção de tempo de execução e controle para o administrador.</span><span class="sxs-lookup"><span data-stu-id="ad45e-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad45e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ad45e-122">See also</span></span>
- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="ad45e-123">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="ad45e-123">End-to-End Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
