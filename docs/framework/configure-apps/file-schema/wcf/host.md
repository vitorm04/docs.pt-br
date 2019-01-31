---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 8a8f9db96281d8d775ff5c2923018228b3a9c1e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269023"
---
# <a name="host"></a><span data-ttu-id="5e0e7-101">\<host></span><span class="sxs-lookup"><span data-stu-id="5e0e7-101">\<host></span></span>
<span data-ttu-id="5e0e7-102">Especifica configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="5e0e7-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="5e0e7-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5e0e7-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="5e0e7-104">\<services></span><span class="sxs-lookup"><span data-stu-id="5e0e7-104">\<services></span></span>  
<span data-ttu-id="5e0e7-105">\<service></span><span class="sxs-lookup"><span data-stu-id="5e0e7-105">\<service></span></span>  
<span data-ttu-id="5e0e7-106">\<host></span><span class="sxs-lookup"><span data-stu-id="5e0e7-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e0e7-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e0e7-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="5e0e7-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="5e0e7-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e0e7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5e0e7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5e0e7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5e0e7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e0e7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="5e0e7-111">Attributes</span></span>  
 <span data-ttu-id="5e0e7-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5e0e7-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5e0e7-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5e0e7-113">Child Elements</span></span>  
  
|<span data-ttu-id="5e0e7-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e0e7-114">Element</span></span>|<span data-ttu-id="5e0e7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e0e7-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e0e7-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="5e0e7-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="5e0e7-117">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="5e0e7-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="5e0e7-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="5e0e7-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="5e0e7-119">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="5e0e7-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e0e7-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5e0e7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5e0e7-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="5e0e7-121">Element</span></span>|<span data-ttu-id="5e0e7-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="5e0e7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5e0e7-123">\<service></span><span class="sxs-lookup"><span data-stu-id="5e0e7-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="5e0e7-124">Especifica as configurações para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5e0e7-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5e0e7-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e0e7-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="5e0e7-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="5e0e7-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
