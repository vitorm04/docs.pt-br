---
title: '&lt;Limpar&gt; elemento para &lt;namedCaches&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 0819141b2135a2de99a2801a1888f7b0e1cd19fc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltcleargt-element-for-ltnamedcachesgt"></a><span data-ttu-id="5d56e-102">&lt;Limpar&gt; elemento para &lt;namedCaches&gt;</span><span class="sxs-lookup"><span data-stu-id="5d56e-102">&lt;clear&gt; Element for &lt;namedCaches&gt;</span></span>
<span data-ttu-id="5d56e-103">Limpa todos os `namedCache` entradas na `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="5d56e-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="5d56e-104">\<System.Runtime.Caching ></span><span class="sxs-lookup"><span data-stu-id="5d56e-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="5d56e-105">\<memoryCache ></span><span class="sxs-lookup"><span data-stu-id="5d56e-105">\<memoryCache></span></span>  
<span data-ttu-id="5d56e-106">\<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="5d56e-106">\<namedCaches></span></span>  
<span data-ttu-id="5d56e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="5d56e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d56e-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5d56e-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="5d56e-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="5d56e-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5d56e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5d56e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5d56e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5d56e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5d56e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="5d56e-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="5d56e-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5d56e-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="5d56e-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5d56e-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5d56e-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="5d56e-115">Element</span></span>|<span data-ttu-id="5d56e-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="5d56e-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5d56e-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="5d56e-117">\<namedCaches></span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|<span data-ttu-id="5d56e-118">Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.</span><span class="sxs-lookup"><span data-stu-id="5d56e-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d56e-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="5d56e-119">Remarks</span></span>  
 <span data-ttu-id="5d56e-120">O `clear` elemento limpa todos os `namedCache` entradas na coleção de cache nomeado de um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="5d56e-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="5d56e-121">Você pode usar o `clear` elemento antes de usar o `add` elemento para adicionar uma nova entrada de cache nomeado para ter certeza de que não há nenhum outro denominado caches na coleção.</span><span class="sxs-lookup"><span data-stu-id="5d56e-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d56e-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5d56e-122">See Also</span></span>  
 [<span data-ttu-id="5d56e-123">\<namedCaches > elemento (configurações de Cache)</span><span class="sxs-lookup"><span data-stu-id="5d56e-123">\<namedCaches> Element (Cache Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
