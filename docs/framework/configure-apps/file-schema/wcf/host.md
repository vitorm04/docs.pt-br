---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918717"
---
# <a name="host"></a><span data-ttu-id="b7d9c-101">\<host></span><span class="sxs-lookup"><span data-stu-id="b7d9c-101">\<host></span></span>
<span data-ttu-id="b7d9c-102">Especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="b7d9c-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="b7d9c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b7d9c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="b7d9c-104">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="b7d9c-104">\<services></span></span>  
<span data-ttu-id="b7d9c-105">\<> de serviço</span><span class="sxs-lookup"><span data-stu-id="b7d9c-105">\<service></span></span>  
<span data-ttu-id="b7d9c-106">\<host></span><span class="sxs-lookup"><span data-stu-id="b7d9c-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7d9c-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b7d9c-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="b7d9c-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="b7d9c-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7d9c-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b7d9c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b7d9c-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b7d9c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7d9c-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="b7d9c-111">Attributes</span></span>  
 <span data-ttu-id="b7d9c-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b7d9c-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7d9c-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b7d9c-113">Child Elements</span></span>  
  
|<span data-ttu-id="b7d9c-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7d9c-114">Element</span></span>|<span data-ttu-id="b7d9c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7d9c-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7d9c-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="b7d9c-116">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="b7d9c-117">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="b7d9c-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="b7d9c-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="b7d9c-118">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="b7d9c-119">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="b7d9c-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7d9c-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b7d9c-120">Parent Elements</span></span>  
  
|<span data-ttu-id="b7d9c-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="b7d9c-121">Element</span></span>|<span data-ttu-id="b7d9c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7d9c-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7d9c-123">\<service></span><span class="sxs-lookup"><span data-stu-id="b7d9c-123">\<service></span></span>](service.md)|<span data-ttu-id="b7d9c-124">Especifica as configurações para um serviço de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b7d9c-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7d9c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7d9c-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="b7d9c-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="b7d9c-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
