---
title: '&lt;Limpar&gt; elemento para &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cdd6e4a4849a031dc6bcad909509498406fcb129
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="c9889-102">&lt;Limpar&gt; elemento para &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="c9889-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="c9889-103">Limpa todos os `namedCache` entradas na `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c9889-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="c9889-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="c9889-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="c9889-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="c9889-105">\<memoryCache></span></span>  
<span data-ttu-id="c9889-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="c9889-106">\<namedCaches></span></span>  
<span data-ttu-id="c9889-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c9889-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9889-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9889-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="c9889-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="c9889-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9889-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c9889-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c9889-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c9889-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9889-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c9889-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="c9889-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c9889-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="c9889-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c9889-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c9889-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="c9889-115">Element</span></span>|<span data-ttu-id="c9889-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9889-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9889-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="c9889-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="c9889-118">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="c9889-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9889-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9889-119">Remarks</span></span>  
 <span data-ttu-id="c9889-120">O `clear` elemento limpa todos os `namedCache` entradas na coleção de cache nomeado de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="c9889-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="c9889-121">Você pode usar o `clear` elemento antes de usar o `add` elemento para adicionar uma nova entrada de cache nomeado para ter certeza de que não há nenhum outro denominado caches na coleção.</span><span class="sxs-lookup"><span data-stu-id="c9889-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9889-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9889-122">See Also</span></span>  
 [<span data-ttu-id="c9889-123">\<namedCaches > elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="c9889-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
