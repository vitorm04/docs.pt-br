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
# <a name="remove-element-for-namedcaches"></a>Elemento \<remove> para \<namedCaches>

Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.runtime.caching>**](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<memoryCache>**](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedCaches>**](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## <a name="type"></a>Tipo  

 `None`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  

 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  

 `None`  
  
### <a name="child-elements"></a>Elementos filho  

 `None`  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namedCaches>](namedcaches-element-cache-settings.md)|Contém uma coleção de definições de configuração para as <xref:System.Runtime.Caching.MemoryCache> instâncias nomeadas.|  
  
## <a name="remarks"></a>Comentários  

 O `remove` elemento remove uma `namedCache` entrada da coleção de cache nomeado para um cache de memória.  
  
## <a name="see-also"></a>Veja também

- [\<namedCaches> Elemento (configurações de cache)](namedcaches-element-cache-settings.md)
