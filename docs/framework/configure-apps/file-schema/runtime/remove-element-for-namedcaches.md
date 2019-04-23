---
title: Elemento <remove> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 053e2776153489dfdd61547fdc039980646ae697
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229765"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="684bc-102">\<Remover > elemento para \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="684bc-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="684bc-103">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="684bc-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="684bc-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="684bc-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="684bc-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="684bc-105">\<memoryCache></span></span>  
<span data-ttu-id="684bc-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="684bc-106">\<namedCaches></span></span>  
<span data-ttu-id="684bc-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="684bc-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="684bc-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="684bc-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="684bc-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="684bc-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="684bc-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="684bc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="684bc-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="684bc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="684bc-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="684bc-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="684bc-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="684bc-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="684bc-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="684bc-114">Parent Elements</span></span>  
  
|<span data-ttu-id="684bc-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="684bc-115">Element</span></span>|<span data-ttu-id="684bc-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="684bc-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="684bc-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="684bc-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="684bc-118">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="684bc-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="684bc-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="684bc-119">Remarks</span></span>  
 <span data-ttu-id="684bc-120">O `remove` elemento remove uma `namedCache` entrada da coleção para um cache de memória cache nomeado.</span><span class="sxs-lookup"><span data-stu-id="684bc-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="684bc-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="684bc-121">See also</span></span>

- [<span data-ttu-id="684bc-122">\<namedCaches > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="684bc-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
