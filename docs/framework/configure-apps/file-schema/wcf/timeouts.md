---
title: '&lt;tempos limite&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="73ca4-102">&lt;tempos limite&gt;</span><span class="sxs-lookup"><span data-stu-id="73ca4-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="73ca4-103">Representa um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="73ca4-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="73ca4-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="73ca4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="73ca4-105">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="73ca4-105">\<client></span></span>  
<span data-ttu-id="73ca4-106">\<ponto de extremidade ></span><span class="sxs-lookup"><span data-stu-id="73ca4-106">\<endpoint></span></span>  
<span data-ttu-id="73ca4-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="73ca4-107">\<host></span></span>  
<span data-ttu-id="73ca4-108">\<tempos limite ></span><span class="sxs-lookup"><span data-stu-id="73ca4-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73ca4-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="73ca4-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73ca4-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="73ca4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="73ca4-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="73ca4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73ca4-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="73ca4-112">Attributes</span></span>  
  
|<span data-ttu-id="73ca4-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="73ca4-113">Attribute</span></span>|<span data-ttu-id="73ca4-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="73ca4-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="73ca4-115">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço fechar.</span><span class="sxs-lookup"><span data-stu-id="73ca4-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="73ca4-116">Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo permitido para o host de serviço abrir.</span><span class="sxs-lookup"><span data-stu-id="73ca4-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73ca4-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="73ca4-117">Child Elements</span></span>  
 <span data-ttu-id="73ca4-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="73ca4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73ca4-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="73ca4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="73ca4-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="73ca4-120">Element</span></span>|<span data-ttu-id="73ca4-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="73ca4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73ca4-122">\<host ></span><span class="sxs-lookup"><span data-stu-id="73ca4-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="73ca4-123">Um elemento de configuração que especifica as configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="73ca4-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="73ca4-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73ca4-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="73ca4-125">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="73ca4-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
