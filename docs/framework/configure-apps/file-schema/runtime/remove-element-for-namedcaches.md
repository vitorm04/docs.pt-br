---
title: Elemento <remove> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: 991ad0eb9c04c27ded4d566115107ac7b47a71e1
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252345"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="c18bf-102">\<Remover > elemento para \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="c18bf-102">\<remove> Element for \<namedCaches></span></span>
<span data-ttu-id="c18bf-103">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c18bf-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="c18bf-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c18bf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c18bf-105">&nbsp;&nbsp;[ **\<sistema. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c18bf-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="c18bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c18bf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="c18bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="c18bf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="c18bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Remover >**</span><span class="sxs-lookup"><span data-stu-id="c18bf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c18bf-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c18bf-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c18bf-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="c18bf-110">Type</span></span>  
 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c18bf-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c18bf-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c18bf-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c18bf-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c18bf-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="c18bf-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="c18bf-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c18bf-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="c18bf-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c18bf-115">Parent Elements</span></span>  
  
|<span data-ttu-id="c18bf-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="c18bf-116">Element</span></span>|<span data-ttu-id="c18bf-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="c18bf-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c18bf-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="c18bf-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="c18bf-119">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="c18bf-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c18bf-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="c18bf-120">Remarks</span></span>  
 <span data-ttu-id="c18bf-121">O `remove` elemento remove uma `namedCache` entrada da coleção de cache nomeado para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c18bf-121">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c18bf-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c18bf-122">See also</span></span>

- [<span data-ttu-id="c18bf-123">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="c18bf-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
