---
title: '&lt;adicionar&gt; &lt;baseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: ce476c2d40758cf52eada813873d061d0e441bce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149079"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="a6a01-102">&lt;adicionar&gt; &lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="a6a01-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="a6a01-103">Representa um elemento de configuração que especifica os endereços base usados pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="a6a01-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="a6a01-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a6a01-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a6a01-105">\<client></span><span class="sxs-lookup"><span data-stu-id="a6a01-105">\<client></span></span>  
<span data-ttu-id="a6a01-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="a6a01-106">\<endpoint></span></span>  
<span data-ttu-id="a6a01-107">\<host ></span><span class="sxs-lookup"><span data-stu-id="a6a01-107">\<host></span></span>  
<span data-ttu-id="a6a01-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="a6a01-108">\<baseAddresses></span></span>  
<span data-ttu-id="a6a01-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="a6a01-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a01-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6a01-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="a6a01-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="a6a01-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a6a01-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a6a01-112">Attributes and Elements</span></span>  
 <span data-ttu-id="a6a01-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a6a01-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a6a01-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="a6a01-114">Attributes</span></span>  
  
|<span data-ttu-id="a6a01-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="a6a01-115">Attribute</span></span>|<span data-ttu-id="a6a01-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6a01-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="a6a01-117">Uma cadeia de caracteres que especifica um endereço base usado pelo host de serviço.</span><span class="sxs-lookup"><span data-stu-id="a6a01-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a6a01-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a6a01-118">Child Elements</span></span>  
 <span data-ttu-id="a6a01-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a6a01-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a6a01-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a6a01-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a6a01-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="a6a01-121">Element</span></span>|<span data-ttu-id="a6a01-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6a01-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a6a01-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="a6a01-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="a6a01-124">Uma coleção de elementos `baseAddress`.</span><span class="sxs-lookup"><span data-stu-id="a6a01-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6a01-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a6a01-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="a6a01-126">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="a6a01-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
