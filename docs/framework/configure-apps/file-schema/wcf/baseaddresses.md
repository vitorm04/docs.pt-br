---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850214"
---
# <a name="baseaddresses"></a><span data-ttu-id="8d8d0-101">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="8d8d0-101">\<baseAddresses></span></span>
<span data-ttu-id="8d8d0-102">Representa uma coleção de `baseAddress` elementos, que são endereços base para um host de serviço em um ambiente de hospedagem interna.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="8d8d0-103">Se um endereço base estiver presente, os pontos de extremidade poderão ser configurados com endereços relativos ao endereço base.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
<span data-ttu-id="8d8d0-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d8d0-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="8d8d0-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="8d8d0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de serviço**](service.md)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="8d8d0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do host**](host.md)</span><span class="sxs-lookup"><span data-stu-id="8d8d0-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="8d8d0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do baseAddress**</span><span class="sxs-lookup"><span data-stu-id="8d8d0-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d8d0-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d8d0-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="8d8d0-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d8d0-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d8d0-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d8d0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8d8d0-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d8d0-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d8d0-114">Attributes</span></span>  
 <span data-ttu-id="8d8d0-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d8d0-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d8d0-116">Child Elements</span></span>  
  
|<span data-ttu-id="8d8d0-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d8d0-117">Element</span></span>|<span data-ttu-id="8d8d0-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d8d0-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d8d0-119">\<add></span><span class="sxs-lookup"><span data-stu-id="8d8d0-119">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="8d8d0-120">Um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d8d0-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d8d0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8d8d0-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d8d0-122">Element</span></span>|<span data-ttu-id="8d8d0-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d8d0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d8d0-124">\<host></span><span class="sxs-lookup"><span data-stu-id="8d8d0-124">\<host></span></span>](host.md)|<span data-ttu-id="8d8d0-125">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d8d0-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d8d0-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d8d0-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="8d8d0-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="8d8d0-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
