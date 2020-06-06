---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850214"
---
# \<baseAddresses>
<span data-ttu-id="df547-101">Representa uma coleção de `baseAddress` elementos, que são endereços base para um host de serviço em um ambiente de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="df547-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="df547-102">Se um endereço base estiver presente, os pontos de extremidade poderão ser configurados com endereços relativos ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="df547-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="df547-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df547-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="df547-104">Type</span><span class="sxs-lookup"><span data-stu-id="df547-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df547-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df547-105">Attributes and Elements</span></span>  
 <span data-ttu-id="df547-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df547-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df547-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="df547-107">Attributes</span></span>  
 <span data-ttu-id="df547-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="df547-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="df547-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df547-109">Child Elements</span></span>  
  
|<span data-ttu-id="df547-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="df547-110">Element</span></span>|<span data-ttu-id="df547-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="df547-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="df547-112">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="df547-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="df547-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df547-113">Parent Elements</span></span>  
  
|<span data-ttu-id="df547-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="df547-114">Element</span></span>|<span data-ttu-id="df547-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="df547-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="df547-116">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="df547-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df547-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="df547-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="df547-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="df547-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
