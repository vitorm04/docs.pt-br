---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b23728451a051f21ad3863b9a29e6290c3c837a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919008"
---
# <a name="endtoendtracing"></a><span data-ttu-id="37915-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="37915-101">\<endToEndTracing></span></span>
<span data-ttu-id="37915-102">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="37915-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
 <span data-ttu-id="37915-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="37915-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="37915-104">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="37915-104">\<diagnostic></span></span>  
<span data-ttu-id="37915-105">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="37915-105">\<endToEndTracing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37915-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37915-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37915-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="37915-107">Attributes and Elements</span></span>  
 <span data-ttu-id="37915-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="37915-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37915-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="37915-109">Attributes</span></span>  
  
|<span data-ttu-id="37915-110">Atributo</span><span class="sxs-lookup"><span data-stu-id="37915-110">Attribute</span></span>|<span data-ttu-id="37915-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="37915-111">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="37915-112">Um valor booliano que especifica se o rastreamento de atividade está habilitado.</span><span class="sxs-lookup"><span data-stu-id="37915-112">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="37915-113">Um valor booliano que especifica se o rastreamento de fluxo de mensagens está habilitado.</span><span class="sxs-lookup"><span data-stu-id="37915-113">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="37915-114">Um valor booliano que especifica se o atributo Propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="37915-114">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="37915-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="37915-115">Child Elements</span></span>  
 <span data-ttu-id="37915-116">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="37915-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37915-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="37915-117">Parent Elements</span></span>  
  
|<span data-ttu-id="37915-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="37915-118">Element</span></span>|<span data-ttu-id="37915-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="37915-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37915-120">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="37915-120">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="37915-121">Define as configurações do WCF para inspeção e controle de tempo de execução para o administrador.</span><span class="sxs-lookup"><span data-stu-id="37915-121">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37915-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37915-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="37915-123">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="37915-123">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
