---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855217"
---
# <a name="host"></a><span data-ttu-id="1e9ed-101">\<host></span><span class="sxs-lookup"><span data-stu-id="1e9ed-101">\<host></span></span>
<span data-ttu-id="1e9ed-102">Especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="1e9ed-102">Specifies settings for a service host.</span></span>  
  
<span data-ttu-id="1e9ed-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e9ed-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e9ed-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1e9ed-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1e9ed-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="1e9ed-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="1e9ed-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de serviço**](service.md)</span><span class="sxs-lookup"><span data-stu-id="1e9ed-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="1e9ed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do host**</span><span class="sxs-lookup"><span data-stu-id="1e9ed-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e9ed-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e9ed-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="1e9ed-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="1e9ed-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e9ed-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e9ed-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1e9ed-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1e9ed-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e9ed-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e9ed-112">Attributes</span></span>  
 <span data-ttu-id="1e9ed-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1e9ed-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1e9ed-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e9ed-114">Child Elements</span></span>  
  
|<span data-ttu-id="1e9ed-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e9ed-115">Element</span></span>|<span data-ttu-id="1e9ed-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e9ed-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e9ed-117">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="1e9ed-117">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="1e9ed-118">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="1e9ed-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="1e9ed-119">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="1e9ed-119">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="1e9ed-120">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="1e9ed-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e9ed-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e9ed-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1e9ed-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e9ed-122">Element</span></span>|<span data-ttu-id="1e9ed-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e9ed-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e9ed-124">\<service></span><span class="sxs-lookup"><span data-stu-id="1e9ed-124">\<service></span></span>](service.md)|<span data-ttu-id="1e9ed-125">Especifica as configurações para um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1e9ed-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1e9ed-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e9ed-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="1e9ed-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="1e9ed-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
