---
title: '&lt;Remova&gt; elemento para &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d31caf88e1376025484ed6d65d5277c015e70b5e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613733"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="6fe1a-102">&lt;Remova&gt; elemento para &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="6fe1a-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="6fe1a-103">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="6fe1a-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="6fe1a-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="6fe1a-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="6fe1a-105">\<memoryCache></span></span>  
<span data-ttu-id="6fe1a-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="6fe1a-106">\<namedCaches></span></span>  
<span data-ttu-id="6fe1a-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="6fe1a-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fe1a-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fe1a-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="6fe1a-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="6fe1a-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6fe1a-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6fe1a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6fe1a-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6fe1a-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="6fe1a-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="6fe1a-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6fe1a-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="6fe1a-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6fe1a-114">Parent Elements</span></span>  
  
|<span data-ttu-id="6fe1a-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="6fe1a-115">Element</span></span>|<span data-ttu-id="6fe1a-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6fe1a-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6fe1a-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="6fe1a-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="6fe1a-118">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6fe1a-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fe1a-119">Remarks</span></span>  
 <span data-ttu-id="6fe1a-120">O `remove` elemento remove uma `namedCache` entrada da coleção para um cache de memória cache nomeado.</span><span class="sxs-lookup"><span data-stu-id="6fe1a-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fe1a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6fe1a-121">See Also</span></span>  
- [<span data-ttu-id="6fe1a-122">\<namedCaches > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="6fe1a-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
