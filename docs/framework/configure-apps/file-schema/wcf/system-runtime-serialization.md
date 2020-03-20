---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: c93a1f482882cc8cd9d229d82597efa64ba209bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152964"
---
# <a name="systemruntimeserialization"></a>\<system.runtime.serialization>
Representa o elemento raiz <xref:System.Runtime.Serialization> para a seção namespace <xref:System.Runtime.Serialization.DataContractSerializer>e contém elementos para definir as opções do .  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialização>**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos da criança e elementos dos pais  
  
### <a name="attributes"></a>Atributos  
 Nenhum.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de dataContractSerializer](datacontractserializer-of-system-runtime-serialization.md)|Permite que a adição de tipos conhecidos seja usada quando a desserialização.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<elemento> de configuração](../configuration-element.md)|O elemento de nível superior para configuração.|  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Serialization>
- [Usando contratos de dados](../../../wcf/feature-details/using-data-contracts.md)
- [Tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md)
