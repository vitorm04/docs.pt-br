---
title: '&lt;Remova&gt; elemento para &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7e183a624b95e207d34697c906cc3f278c967ae9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499753"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a><span data-ttu-id="bb459-102">&lt;Remova&gt; elemento para &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="bb459-102">&lt;remove&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="bb459-103">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="bb459-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="bb459-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="bb459-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="bb459-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="bb459-105">\<memoryCache></span></span>  
<span data-ttu-id="bb459-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="bb459-106">\<namedCaches></span></span>  
<span data-ttu-id="bb459-107">\<remove></span><span class="sxs-lookup"><span data-stu-id="bb459-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb459-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb459-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="bb459-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="bb459-109">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bb459-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bb459-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bb459-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="bb459-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bb459-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="bb459-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="bb459-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bb459-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="bb459-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bb459-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bb459-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="bb459-115">Element</span></span>|<span data-ttu-id="bb459-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb459-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bb459-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="bb459-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="bb459-118">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="bb459-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb459-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb459-119">Remarks</span></span>  
 <span data-ttu-id="bb459-120">O `remove` elemento remove uma `namedCache` entrada da coleção para um cache de memória cache nomeado.</span><span class="sxs-lookup"><span data-stu-id="bb459-120">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb459-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb459-121">See also</span></span>
- [<span data-ttu-id="bb459-122">\<namedCaches > (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="bb459-122">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
