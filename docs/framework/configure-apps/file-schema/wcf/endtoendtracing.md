---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855288"
---
# <a name="endtoendtracing"></a><span data-ttu-id="5a723-101">\<endToEndTracing></span><span class="sxs-lookup"><span data-stu-id="5a723-101">\<endToEndTracing></span></span>
<span data-ttu-id="5a723-102">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="5a723-102">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
<span data-ttu-id="5a723-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a723-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a723-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a723-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a723-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de diagnóstico**](diagnostics.md)</span><span class="sxs-lookup"><span data-stu-id="5a723-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)</span></span>\
<span data-ttu-id="5a723-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> endToEndTracing**</span><span class="sxs-lookup"><span data-stu-id="5a723-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a723-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5a723-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a723-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5a723-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5a723-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5a723-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a723-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="5a723-110">Attributes</span></span>  
  
|<span data-ttu-id="5a723-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="5a723-111">Attribute</span></span>|<span data-ttu-id="5a723-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a723-112">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="5a723-113">Um valor booliano que especifica se o rastreamento de atividade está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5a723-113">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="5a723-114">Um valor booliano que especifica se o rastreamento de fluxo de mensagens está habilitado.</span><span class="sxs-lookup"><span data-stu-id="5a723-114">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="5a723-115">Um valor booliano que especifica se o atributo Propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="5a723-115">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a723-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5a723-116">Child Elements</span></span>  
 <span data-ttu-id="5a723-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5a723-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a723-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5a723-118">Parent Elements</span></span>  
  
|<span data-ttu-id="5a723-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="5a723-119">Element</span></span>|<span data-ttu-id="5a723-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="5a723-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a723-121">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="5a723-121">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="5a723-122">Define as configurações do WCF para inspeção e controle de tempo de execução para o administrador.</span><span class="sxs-lookup"><span data-stu-id="5a723-122">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a723-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5a723-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="5a723-124">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="5a723-124">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
