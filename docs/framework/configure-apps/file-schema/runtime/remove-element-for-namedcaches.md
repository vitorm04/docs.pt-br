---
title: Elemento <remove> para <namedCaches>
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
ms.openlocfilehash: c8ad5a0ce6d7a3059943b3962b9255385cea6e15
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183982"
---
# <a name="remove-element-for-namedcaches"></a><span data-ttu-id="cd7a4-102">Elemento \<remove> para \<namedCaches></span><span class="sxs-lookup"><span data-stu-id="cd7a4-102">\<remove> Element for \<namedCaches></span></span>

<span data-ttu-id="cd7a4-103">Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="cd7a4-103">Removes a named cache entry from the `namedCaches` collection for a memory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a><span data-ttu-id="cd7a4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cd7a4-104">Syntax</span></span>  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a><span data-ttu-id="cd7a4-105">Tipo</span><span class="sxs-lookup"><span data-stu-id="cd7a4-105">Type</span></span>  

 `None`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd7a4-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="cd7a4-106">Attributes and Elements</span></span>  

 <span data-ttu-id="cd7a4-107">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="cd7a4-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd7a4-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="cd7a4-108">Attributes</span></span>  

 `None`  
  
### <a name="child-elements"></a><span data-ttu-id="cd7a4-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="cd7a4-109">Child Elements</span></span>  

 `None`  
  
### <a name="parent-elements"></a><span data-ttu-id="cd7a4-110">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="cd7a4-110">Parent Elements</span></span>  
  
|<span data-ttu-id="cd7a4-111">Elemento</span><span class="sxs-lookup"><span data-stu-id="cd7a4-111">Element</span></span>|<span data-ttu-id="cd7a4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="cd7a4-112">Description</span></span>|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|<span data-ttu-id="cd7a4-113">Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="cd7a4-113">Contains a collection of configuration settings for the named <xref:System.Runtime.Caching.MemoryCache> instances.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd7a4-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="cd7a4-114">Remarks</span></span>  

 <span data-ttu-id="cd7a4-115">O `remove` elemento remove uma `namedCache` entrada da coleção de cache nomeado para um cache de memória.</span><span class="sxs-lookup"><span data-stu-id="cd7a4-115">The `remove` element removes a `namedCache` entry from the named cache collection for a memory cache.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7a4-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="cd7a4-116">See also</span></span>

- [<span data-ttu-id="cd7a4-117">\<namedCaches> Elemento (configurações de cache)</span><span class="sxs-lookup"><span data-stu-id="cd7a4-117">\<namedCaches> Element (Cache Settings)</span></span>](namedcaches-element-cache-settings.md)
