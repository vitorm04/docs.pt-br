---
title: '&lt;Remova&gt; elemento para &lt;namedCaches&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- remove element for namedCaches
- <remove> element for namedCaches
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d31caf88e1376025484ed6d65d5277c015e70b5e
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613733"
---
# <a name="ltremovegt-element-for-ltnamedcachesgt"></a>&lt;Remova&gt; elemento para &lt;namedCaches&gt;
Remove uma entrada de cache nomeado da coleção de `namedCaches` para um cache de memória.  
  
 \<system.runtime.caching>  
\<memoryCache>  
\<namedCaches >  
\<remove>  
  
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
|[\<namedCaches>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|Contém uma coleção de definições de configuração para nomeado <xref:System.Runtime.Caching.MemoryCache> instâncias.|  
  
## <a name="remarks"></a>Comentários  
 O `remove` elemento remove uma `namedCache` entrada da coleção para um cache de memória cache nomeado.  
  
## <a name="see-also"></a>Consulte também  
- [\<namedCaches > (configurações de Cache)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)
