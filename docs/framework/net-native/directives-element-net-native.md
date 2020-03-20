---
title: <Directives> (.NET Nativo)
ms.date: 03/30/2017
ms.assetid: 444846f3-48d5-4341-a43e-69f7221389eb
ms.openlocfilehash: 49c1aaf005b80a6c1c1fa382eebc2cb0dbfa4be7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181053"
---
# <a name="directives-element-net-native"></a>\<Diretrizes> Elemento (.NET Nativo)
O elemento raiz em cada arquivo de diretivas de tempo de execução para .NET Native.  
  
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
|`xmlns`|O namespace XML. Seu valor é sempre **"http://schemas.microsoft.com/netfx/2013/01/metadata.**|  
  
## <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de aplicação](application-element-net-native.md)|Serve como um contêiner para os tipos amplos de aplicativos cujos metadados estão disponíveis para reflexão.|  
|[\<>da biblioteca](library-element-net-native.md)|Define o assembly cujos tipos de filho e membros de tipo necessitam de metadados no tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Cada arquivo de diretivas de runtime pode conter somente um elemento `<Directives>`.  
  
 O `<Directives>` elemento pode conter elemento sem zero ou um [ \<aplicativo>,](application-element-net-native.md) e zero, um ou mais [ \<](library-element-net-native.md) elementos de>de Biblioteca.  
  
## <a name="see-also"></a>Confira também

- [Referência do arquivo de configuração das diretivas de runtime (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [Elementos da diretiva de runtime](runtime-directive-elements.md)
