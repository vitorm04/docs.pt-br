---
title: Elemento <clear> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- <clear> element for <namedCaches>
- clear element for <namedCaches>
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
ms.openlocfilehash: a90970e468359714bbbb858f3f300c26b5757a4d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658854"
---
# <a name="clear-element-for-namedcaches"></a><span data-ttu-id="a97e7-102">\<limpar > elemento para \<namedCaches ></span><span class="sxs-lookup"><span data-stu-id="a97e7-102">\<clear> Element for \<namedCaches></span></span>
<span data-ttu-id="a97e7-103">Limpa todas `namedCache` as entradas `namedCaches` na coleção para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="a97e7-103">Clears all `namedCache` entries in the `namedCaches` collection for a memory cache.</span></span>  
  
 <span data-ttu-id="a97e7-104">\<system.runtime.caching></span><span class="sxs-lookup"><span data-stu-id="a97e7-104">\<system.runtime.caching></span></span>  
<span data-ttu-id="a97e7-105">\<memoryCache></span><span class="sxs-lookup"><span data-stu-id="a97e7-105">\<memoryCache></span></span>  
<span data-ttu-id="a97e7-106">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="a97e7-106">\<namedCaches></span></span>  
<span data-ttu-id="a97e7-107">\<add></span><span class="sxs-lookup"><span data-stu-id="a97e7-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a97e7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a97e7-108">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <clear name="Default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="a97e7-109">Tipo</span><span class="sxs-lookup"><span data-stu-id="a97e7-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a97e7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a97e7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a97e7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="a97e7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a97e7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="a97e7-112">Attributes</span></span>  
 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="a97e7-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a97e7-113">Child Elements</span></span>  
 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="a97e7-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a97e7-114">Parent Elements</span></span>  
  
|<span data-ttu-id="a97e7-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="a97e7-115">Element</span></span>|<span data-ttu-id="a97e7-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="a97e7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a97e7-117">\<namedCaches></span><span class="sxs-lookup"><span data-stu-id="a97e7-117">\<namedCaches></span></span>](namedcaches-element-cache-settings.md)|<span data-ttu-id="a97e7-118">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="a97e7-118">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a97e7-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="a97e7-119">Remarks</span></span>  
 <span data-ttu-id="a97e7-120">O `clear` elemento limpa todas `namedCache` as entradas na coleção de cache nomeado para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="a97e7-120">The `clear` element clears all `namedCache` entries in the named cache collection for a memory cache.</span></span> <span data-ttu-id="a97e7-121">Você pode usar o `clear` elemento antes de usar o `add` elemento para adicionar uma nova entrada de cache nomeado a fim de ter certeza de que não há outros caches nomeados na coleção.</span><span class="sxs-lookup"><span data-stu-id="a97e7-121">You can use the `clear` element before you use the `add` element to add a new named cache entry in order to be certain there are no other named caches in the collection.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a97e7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a97e7-122">See also</span></span>

- [<span data-ttu-id="a97e7-123">\<Elemento de > namedCaches (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="a97e7-123">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
