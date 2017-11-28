---
title: '&lt;host&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a><span data-ttu-id="af800-102">&lt;host&gt;</span><span class="sxs-lookup"><span data-stu-id="af800-102">&lt;host&gt;</span></span>
<span data-ttu-id="af800-103">Especifica configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="af800-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="af800-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="af800-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="af800-105">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="af800-105">\<services></span></span>  
<span data-ttu-id="af800-106">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="af800-106">\<service></span></span>  
<span data-ttu-id="af800-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="af800-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af800-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="af800-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="af800-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="af800-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="af800-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="af800-110">Attributes and Elements</span></span>  
 <span data-ttu-id="af800-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="af800-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="af800-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="af800-112">Attributes</span></span>  
 <span data-ttu-id="af800-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="af800-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="af800-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="af800-114">Child Elements</span></span>  
  
|<span data-ttu-id="af800-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="af800-115">Element</span></span>|<span data-ttu-id="af800-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="af800-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af800-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="af800-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="af800-118">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="af800-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="af800-119">\<tempos limite ></span><span class="sxs-lookup"><span data-stu-id="af800-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="af800-120">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="af800-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="af800-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="af800-121">Parent Elements</span></span>  
  
|<span data-ttu-id="af800-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="af800-122">Element</span></span>|<span data-ttu-id="af800-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="af800-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="af800-124">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="af800-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="af800-125">Especifica as configurações para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="af800-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="af800-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="af800-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="af800-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="af800-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
