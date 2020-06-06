---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855217"
---
# \<host>
<span data-ttu-id="850fb-101">Especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="850fb-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="850fb-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="850fb-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="850fb-103">Type</span><span class="sxs-lookup"><span data-stu-id="850fb-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="850fb-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="850fb-104">Attributes and Elements</span></span>  
 <span data-ttu-id="850fb-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="850fb-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="850fb-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="850fb-106">Attributes</span></span>  
 <span data-ttu-id="850fb-107">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="850fb-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="850fb-108">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="850fb-108">Child Elements</span></span>  
  
|<span data-ttu-id="850fb-109">Elemento</span><span class="sxs-lookup"><span data-stu-id="850fb-109">Element</span></span>|<span data-ttu-id="850fb-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="850fb-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="850fb-111">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="850fb-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="850fb-112">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="850fb-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="850fb-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="850fb-113">Parent Elements</span></span>  
  
|<span data-ttu-id="850fb-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="850fb-114">Element</span></span>|<span data-ttu-id="850fb-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="850fb-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="850fb-116">Especifica as configurações para um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="850fb-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="850fb-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="850fb-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="850fb-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="850fb-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
