---
title: '&lt;timeOuts&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 42f4db1d954834cbfa3c526328cca45443751506
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629651"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="4d772-102">&lt;timeOuts&gt;</span><span class="sxs-lookup"><span data-stu-id="4d772-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="4d772-103">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="4d772-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="4d772-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4d772-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4d772-105">\<client></span><span class="sxs-lookup"><span data-stu-id="4d772-105">\<client></span></span>  
<span data-ttu-id="4d772-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="4d772-106">\<endpoint></span></span>  
<span data-ttu-id="4d772-107">\<host></span><span class="sxs-lookup"><span data-stu-id="4d772-107">\<host></span></span>  
<span data-ttu-id="4d772-108">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="4d772-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d772-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d772-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d772-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4d772-110">Attributes and Elements</span></span>  
 <span data-ttu-id="4d772-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4d772-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d772-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="4d772-112">Attributes</span></span>  
  
|<span data-ttu-id="4d772-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="4d772-113">Attribute</span></span>|<span data-ttu-id="4d772-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d772-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="4d772-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="4d772-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="4d772-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="4d772-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d772-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4d772-117">Child Elements</span></span>  
 <span data-ttu-id="4d772-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4d772-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d772-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4d772-119">Parent Elements</span></span>  
  
|<span data-ttu-id="4d772-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="4d772-120">Element</span></span>|<span data-ttu-id="4d772-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="4d772-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d772-122">\<host></span><span class="sxs-lookup"><span data-stu-id="4d772-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="4d772-123">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="4d772-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d772-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d772-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="4d772-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="4d772-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
