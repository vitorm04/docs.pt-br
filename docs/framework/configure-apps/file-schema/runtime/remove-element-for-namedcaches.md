---
title: '&lt;remover&gt; elemento para &lt;namedCaches&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: "10"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 4b360b206586b263627ab6f6b7e0309f3055f38a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="07acb-102">&lt;remover&gt; elemento para &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="07acb-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="07acb-103">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="07acb-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="07acb-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="07acb-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="07acb-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="07acb-105">\<memoryCache></span></span>  
<span data-ttu-id="07acb-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="07acb-106">\<namedCaches></span></span>  
<span data-ttu-id="07acb-107">\<Remover ></span><span class="sxs-lookup"><span data-stu-id="07acb-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07acb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="07acb-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="07acb-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="07acb-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="07acb-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="07acb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="07acb-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="07acb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="07acb-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="07acb-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="07acb-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="07acb-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="07acb-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="07acb-114">Parent Elements</span></span>  
  
|<span data-ttu-id="07acb-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="07acb-115">Element</span></span>|<span data-ttu-id="07acb-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="07acb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="07acb-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="07acb-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="07acb-118">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="07acb-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07acb-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="07acb-119">Remarks</span></span>  
 <span data-ttu-id="07acb-120">O `remove` elemento remove um `namedCache` entrada da coleção de cache nomeado para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="07acb-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07acb-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="07acb-121">See Also</span></span>  
 [<span data-ttu-id="07acb-122">\<namedCaches > elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="07acb-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
