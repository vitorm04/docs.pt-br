---
title: '&lt;Host&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: ec53568e9d1df9ebb04bc299f491e80674950c63
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/17/2018
---
# <a name="lthostgt"></a><span data-ttu-id="8d908-102">&lt;Host&gt;</span><span class="sxs-lookup"><span data-stu-id="8d908-102">&lt;host&gt;</span></span>
<span data-ttu-id="8d908-103">Especifica configurações para um host de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d908-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="8d908-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8d908-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8d908-105">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="8d908-105">\<services></span></span>  
<span data-ttu-id="8d908-106">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="8d908-106">\<service></span></span>  
<span data-ttu-id="8d908-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="8d908-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d908-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8d908-108">Syntax</span></span>  
  
```xml  
<host>
    <baseAddresses>  
        <add baseAddress="string" />  
    </baseAddresses>  
    <timeOuts closeTimeout="TimeSpan" openTimeout="TimeSpan">  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="8d908-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="8d908-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d908-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8d908-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8d908-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8d908-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d908-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8d908-112">Attributes</span></span>  
 <span data-ttu-id="8d908-113">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8d908-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d908-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8d908-114">Child Elements</span></span>  
  
|<span data-ttu-id="8d908-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d908-115">Element</span></span>|<span data-ttu-id="8d908-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d908-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d908-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="8d908-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="8d908-118">Uma coleção de `baseAddress` elementos que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="8d908-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="8d908-119">\<tempos limite ></span><span class="sxs-lookup"><span data-stu-id="8d908-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="8d908-120">Um elemento de configuração que especifica o intervalo de tempo permitido para o host de serviço abrir ou fechar.</span><span class="sxs-lookup"><span data-stu-id="8d908-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8d908-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8d908-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8d908-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="8d908-122">Element</span></span>|<span data-ttu-id="8d908-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="8d908-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8d908-124">\<service></span><span class="sxs-lookup"><span data-stu-id="8d908-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="8d908-125">Especifica as configurações para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="8d908-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d908-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d908-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="8d908-127">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="8d908-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
