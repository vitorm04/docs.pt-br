---
title: '&lt;tempos limite&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 1f0638f85177d2acb6f61e3246a1a5ee9a4e2f5c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="bb668-102">&lt;tempos limite&gt;</span><span class="sxs-lookup"><span data-stu-id="bb668-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="bb668-103">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="bb668-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="bb668-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bb668-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bb668-105">\<client></span><span class="sxs-lookup"><span data-stu-id="bb668-105">\<client></span></span>  
<span data-ttu-id="bb668-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="bb668-106">\<endpoint></span></span>  
<span data-ttu-id="bb668-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="bb668-107">\<host></span></span>  
<span data-ttu-id="bb668-108">\<tempos limite ></span><span class="sxs-lookup"><span data-stu-id="bb668-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb668-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb668-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb668-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bb668-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bb668-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bb668-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb668-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="bb668-112">Attributes</span></span>  
  
|<span data-ttu-id="bb668-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="bb668-113">Attribute</span></span>|<span data-ttu-id="bb668-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb668-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="bb668-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="bb668-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="bb668-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="bb668-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bb668-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bb668-117">Child Elements</span></span>  
 <span data-ttu-id="bb668-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bb668-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bb668-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bb668-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bb668-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="bb668-120">Element</span></span>|<span data-ttu-id="bb668-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb668-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb668-122">\<host ></span><span class="sxs-lookup"><span data-stu-id="bb668-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="bb668-123">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="bb668-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb668-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb668-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="bb668-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="bb668-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
