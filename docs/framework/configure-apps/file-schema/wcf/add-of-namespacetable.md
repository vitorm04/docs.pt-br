---
title: '&lt;adicionar&gt; &lt;namespaceTable&gt;'
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 5ae672f12a2ef58efc9738624c113855e59e02b6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a>&lt;adicionar&gt; &lt;namespaceTable&gt;
Representa um elemento de configuração que contém o namespace para mapeamento de prefixo que pode ser usado em filtros de XPath para roteamento.  
  
 \<system.serviceModel>  
\<roteamento >  
\<namespaceTable >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|namespace|Uma cadeia de caracteres que contém o namespace.|  
|Prefixo|Uma cadeia de caracteres que contém o prefixo para esse namespace.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usadas em filtros de XPath para roteamento.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
