---
title: <endToEndTracing>
ms.date: 03/30/2017
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
ms.openlocfilehash: 6b50c0c3db644787fe41ee58ced7eb640e7295f1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190014"
---
# \<endToEndTracing>

<span data-ttu-id="44281-101">Um elemento de configuração que permite habilitar e desabilitar diferentes aspectos de rastreamento de ponta a ponta durante a execução de um aplicativo de serviço.</span><span class="sxs-lookup"><span data-stu-id="44281-101">A configuration element that allows you to enable and disable different aspects of end-to-end tracing during the running of a service application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<diagnostics>**](diagnostics.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endToEndTracing>**  
  
## <a name="syntax"></a><span data-ttu-id="44281-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44281-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <diagnostics>
    <endToEndTracing activityTracing="Boolean"
                     messageFlowTracing="Boolean"
                     propagateActivity="Boolean" />
  </diagnostics>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44281-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44281-103">Attributes and Elements</span></span>  

 <span data-ttu-id="44281-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44281-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44281-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="44281-105">Attributes</span></span>  
  
|<span data-ttu-id="44281-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="44281-106">Attribute</span></span>|<span data-ttu-id="44281-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="44281-107">Description</span></span>|  
|---------------|-----------------|  
|`activityTracing`|<span data-ttu-id="44281-108">Um valor booliano que especifica se o rastreamento de atividade está habilitado.</span><span class="sxs-lookup"><span data-stu-id="44281-108">A Boolean value that specifies whether activity tracing is enabled.</span></span>|  
|`messageFlowTracing`|<span data-ttu-id="44281-109">Um valor booliano que especifica se o rastreamento de fluxo de mensagens está habilitado.</span><span class="sxs-lookup"><span data-stu-id="44281-109">A Boolean value that specifies whether message flow tracing in enabled.</span></span>|  
|`propagateActivity`|<span data-ttu-id="44281-110">Um valor booliano que especifica se o atributo Propagate é definido como true.</span><span class="sxs-lookup"><span data-stu-id="44281-110">A Boolean value that specifies whether the propagate attribute is set to true.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44281-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44281-111">Child Elements</span></span>  

 <span data-ttu-id="44281-112">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="44281-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44281-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44281-113">Parent Elements</span></span>  
  
|<span data-ttu-id="44281-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="44281-114">Element</span></span>|<span data-ttu-id="44281-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="44281-115">Description</span></span>|  
|-------------|-----------------|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="44281-116">Define as configurações do WCF para inspeção e controle de tempo de execução para o administrador.</span><span class="sxs-lookup"><span data-stu-id="44281-116">Defines WCF settings for runtime inspection and control for the administrator.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="44281-117">Veja também</span><span class="sxs-lookup"><span data-stu-id="44281-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.DiagnosticSection>
- <xref:System.ServiceModel.Diagnostics>
- <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>
- <xref:System.ServiceModel.Configuration.EndToEndTracingElement>
- [<span data-ttu-id="44281-118">Rastreamento ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="44281-118">End-to-End Tracing</span></span>](../../../wcf/diagnostics/tracing/end-to-end-tracing.md)
