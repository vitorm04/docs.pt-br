---
title: <add> De <namespaceTable>
ms.date: 03/30/2017
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
ms.openlocfilehash: 0e463ffa87e67bc5f100f9acf38ace6450b0ce40
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268698"
---
# <a name="add-of-namespacetable"></a>\<Adicionar > de \<namespaceTable >
Representa um elemento de configuração que contém um namespace para o prefixo de mapeamento que pode ser usado em filtros de XPath para roteamento.  
  
 \<system.serviceModel>  
\<routing>  
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
  
```csharp  
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
|[\<namespaceTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|Representa uma seção de configuração para definir um conjunto de elementos que contêm namespace para mapeamentos de prefixo que pode ser usado em filtros de XPath para roteamento.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>
