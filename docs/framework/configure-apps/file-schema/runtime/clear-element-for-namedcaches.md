---
title: Elemento <clear> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252754"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="0bc22-102">\<limpar > elemento para \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="0bc22-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="0bc22-103">Limpa todas `namedCache` as entradas `namedCaches` na coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="0bc22-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
<span data-ttu-id="0bc22-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0bc22-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0bc22-105">&nbsp;&nbsp;[ **\<sistema. Runtime. Caching >** ](system-runtime-caching-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0bc22-105">&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)</span></span>\
<span data-ttu-id="0bc22-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> memoryCache**](memorycache-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0bc22-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)</span></span>\
<span data-ttu-id="0bc22-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> namedCaches**](namedcaches-element-cache-settings.md)</span><span class="sxs-lookup"><span data-stu-id="0bc22-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)</span></span>\
<span data-ttu-id="0bc22-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<limpar >**</span><span class="sxs-lookup"><span data-stu-id="0bc22-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc22-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0bc22-109">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="0bc22-110">Tipo</span><span class="sxs-lookup"><span data-stu-id="0bc22-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0bc22-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0bc22-111">Attributes and Elements</span></span>  
 <span data-ttu-id="0bc22-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0bc22-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0bc22-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="0bc22-113">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="0bc22-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0bc22-114">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="0bc22-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0bc22-115">Parent Elements</span></span>  
  
|<span data-ttu-id="0bc22-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="0bc22-116">Element</span></span>|<span data-ttu-id="0bc22-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0bc22-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0bc22-118">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="0bc22-118">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="0bc22-119">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="0bc22-119">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bc22-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="0bc22-120">Remarks</span></span>  
 <span data-ttu-id="0bc22-121">O `clear` elemento limpa todas `namedCache` as entradas na coleção de cache nomeado para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="0bc22-121">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="0bc22-122">Você pode usar o `clear` elemento antes de usar o `add` elemento para adicionar uma nova entrada de cache nomeado a fim de ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="0bc22-122">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc22-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0bc22-123">See also</span></span>

- [<span data-ttu-id="0bc22-124">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="0bc22-124">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
