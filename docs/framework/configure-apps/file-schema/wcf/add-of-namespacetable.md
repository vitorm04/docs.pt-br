---
title: <add> de <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 7e2a2e26099f2d31116e4a89297fc1ac984c480d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920075"
---
# <a name="add-of-namespacetable"></a>\<Adicionar > de \<NamespaceTable >
Representa um elemento de configuração que contém um namespace para mapeamento de prefixo que pode ser usado em filtros XPath para roteamento.  
  
 \<system.serviceModel>  
\<> de roteamento  
\<namespaceTable>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<routing>
  <namespaceTable>
    <add namespace="String"
         prefix="String" />
  </namespaceTable>
</routing>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|namespace|Uma cadeia de caracteres que contém o namespace.|  
|prefix|Uma cadeia de caracteres que contém o prefixo para este namespace.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<namespaceTable>](namespacetable.md)|Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que podem ser usados em filtros XPath para roteamento.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
