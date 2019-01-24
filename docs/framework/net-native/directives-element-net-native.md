---
title: Elemento &lt;Directives&gt; (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 497ec1a432352e3b9f50bd94e03e95e98edcfd55
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725631"
---
# <a name="ltdirectivesgt-element-net-native"></a>Elemento &lt;Directives&gt; (.NET Nativo)
O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET nativo.  
  
 `<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">` 
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <!-- child elements -->   
</Directives>  
```  
  
## <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`xmlns`|O namespace XML. Seu valor é sempre **"http://schemas.microsoft.com/netfx/2013/01/metadata"**.|  
  
## <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Application>](../../../docs/framework/net-native/application-element-net-native.md)|Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.|  
|[\<Library>](../../../docs/framework/net-native/library-element-net-native.md)|Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Cada arquivo de diretivas de tempo de execução pode conter somente um elemento `<Directives>`.  
  
 O elemento `<Directives>` pode conter zero ou um elemento [\<Application>](../../../docs/framework/net-native/application-element-net-native.md) e zero, um ou mais elementos [\<Library>](../../../docs/framework/net-native/library-element-net-native.md).  
  
## <a name="see-also"></a>Consulte também
- [Referência do arquivo de configuração das diretivas de tempo de execução (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de tempo de execução](../../../docs/framework/net-native/runtime-directive-elements.md)
