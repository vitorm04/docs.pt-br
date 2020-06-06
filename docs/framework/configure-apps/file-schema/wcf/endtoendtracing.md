---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 1a274f15800c6a132994a2437943c83982de9de0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855288"
---
# \<endToEndTracing>
<span data-ttu-id="91038-101">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="91038-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="91038-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="91038-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91038-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="91038-103">Attributes and Elements</span></span>  
 <span data-ttu-id="91038-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="91038-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91038-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="91038-105">Attributes</span></span>  
  
|<span data-ttu-id="91038-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="91038-106">Attribute</span></span>|<span data-ttu-id="91038-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="91038-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="91038-108">Um valor booliano que especifica se o rastreamento de atividade está habilitado.</span><span class="sxs-lookup"><span data-stu-id="91038-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="91038-109">Um valor booliano que especifica se o rastreamento de fluxo de mensagens está habilitado.</span><span class="sxs-lookup"><span data-stu-id="91038-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="91038-110">Um valor booliano que especifica se o atributo Propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="91038-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="91038-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="91038-111">Child Elements</span></span>  
 <span data-ttu-id="91038-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="91038-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="91038-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="91038-113">Parent Elements</span></span>  
  
|<span data-ttu-id="91038-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="91038-114">Element</span></span>|<span data-ttu-id="91038-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="91038-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="91038-116">Define as configurações do WCF para inspeção e controle de tempo de execução para o administrador.</span><span class="sxs-lookup"><span data-stu-id="91038-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91038-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="91038-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="91038-118">Rastreamento de ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="91038-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
