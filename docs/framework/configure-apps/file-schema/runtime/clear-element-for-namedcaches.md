---
title: Elemento <clear> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: bcc0e23f0c47ad3a98430e36da31d39612caa3c9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252754"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="90ca6-102">Elemento \<clear> para \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="90ca6-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="90ca6-103">Limpa todas as `namedCache` entradas na `namedCaches` coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="90ca6-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="90ca6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90ca6-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="90ca6-105">Type</span><span class="sxs-lookup"><span data-stu-id="90ca6-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90ca6-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="90ca6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="90ca6-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="90ca6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90ca6-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="90ca6-108">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="90ca6-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="90ca6-109">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="90ca6-110">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="90ca6-110">Parent Elements</span></span>  
  
|<span data-ttu-id="90ca6-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="90ca6-111">Element</span></span>|<span data-ttu-id="90ca6-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="90ca6-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="90ca6-113">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="90ca6-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90ca6-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="90ca6-114">Remarks</span></span>  
 <span data-ttu-id="90ca6-115">O `clear` elemento limpa todas as `namedCache` entradas na coleção de cache nomeado para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="90ca6-115">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="90ca6-116">Você pode usar o `clear` elemento antes de usar o `add` elemento para adicionar uma nova entrada de cache nomeado a fim de ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="90ca6-116">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ca6-117">Confira também</span><span class="sxs-lookup"><span data-stu-id="90ca6-117">See also</span></span>

- [<span data-ttu-id="90ca6-118">\<namedCaches>Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="90ca6-118">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
