---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 3d1f7774f61060880a5c3b0327bdd6c2cc4dd74e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61746686"
---
# <a name="host"></a><span data-ttu-id="23a5b-101">\<host></span><span class="sxs-lookup"><span data-stu-id="23a5b-101">\<host></span></span>
<span data-ttu-id="23a5b-102">Especifica configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="23a5b-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="23a5b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="23a5b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="23a5b-104">\<services></span><span class="sxs-lookup"><span data-stu-id="23a5b-104">\<services></span></span>  
<span data-ttu-id="23a5b-105">\<service></span><span class="sxs-lookup"><span data-stu-id="23a5b-105">\<service></span></span>  
<span data-ttu-id="23a5b-106">\<host></span><span class="sxs-lookup"><span data-stu-id="23a5b-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23a5b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="23a5b-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="23a5b-108">Tipo</span><span class="sxs-lookup"><span data-stu-id="23a5b-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="23a5b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="23a5b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="23a5b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="23a5b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="23a5b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="23a5b-111">Attributes</span></span>  
 <span data-ttu-id="23a5b-112">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="23a5b-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="23a5b-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="23a5b-113">Child Elements</span></span>  
  
|<span data-ttu-id="23a5b-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="23a5b-114">Element</span></span>|<span data-ttu-id="23a5b-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="23a5b-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23a5b-116">\<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="23a5b-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="23a5b-117">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="23a5b-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="23a5b-118">\<timeOuts></span><span class="sxs-lookup"><span data-stu-id="23a5b-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="23a5b-119">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="23a5b-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="23a5b-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="23a5b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="23a5b-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="23a5b-121">Element</span></span>|<span data-ttu-id="23a5b-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="23a5b-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="23a5b-123">\<service></span><span class="sxs-lookup"><span data-stu-id="23a5b-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="23a5b-124">Especifica as configurações para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="23a5b-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="23a5b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23a5b-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="23a5b-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="23a5b-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
