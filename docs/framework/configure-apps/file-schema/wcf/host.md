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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d498190e7d7c3a6e879c50324e3b973f0f8e8fa6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="lthostgt"></a><span data-ttu-id="164c1-102">&lt;host&gt;</span><span class="sxs-lookup"><span data-stu-id="164c1-102">&lt;host&gt;</span></span>
<span data-ttu-id="164c1-103">Especifica configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="164c1-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="164c1-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="164c1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="164c1-105">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="164c1-105">\<services></span></span>  
<span data-ttu-id="164c1-106">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="164c1-106">\<service></span></span>  
<span data-ttu-id="164c1-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="164c1-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="164c1-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="164c1-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="164c1-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="164c1-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="164c1-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="164c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="164c1-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="164c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="164c1-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="164c1-112">Attributes</span></span>  
 <span data-ttu-id="164c1-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="164c1-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="164c1-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="164c1-114">Child Elements</span></span>  
  
|<span data-ttu-id="164c1-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="164c1-115">Element</span></span>|<span data-ttu-id="164c1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="164c1-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="164c1-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="164c1-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="164c1-118">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="164c1-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="164c1-119">\<tempos limite ></span><span class="sxs-lookup"><span data-stu-id="164c1-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="164c1-120">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="164c1-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="164c1-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="164c1-121">Parent Elements</span></span>  
  
|<span data-ttu-id="164c1-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="164c1-122">Element</span></span>|<span data-ttu-id="164c1-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="164c1-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="164c1-124">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="164c1-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="164c1-125">Especifica as configurações para um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] serviço.</span><span class="sxs-lookup"><span data-stu-id="164c1-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="164c1-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="164c1-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="164c1-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="164c1-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
