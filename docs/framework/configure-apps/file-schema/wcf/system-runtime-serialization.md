---
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: b67f51e634d1294830690dad8c8cffb1fc9a6cd2
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399457"
---
# <a name="systemruntimeserialization"></a>\<system.runtime.serialization>
Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp; **\<> System. Runtime. Serialization**  
  
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
 As seções a seguir descrevem atributos, elementos filho e elementos pai  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|Permite que a adição de tipos conhecidos seja usada na desserialização.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[Elemento \<configuration>](../configuration-element.md)|O elemento de nível superior para configuração.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization>
- [Usando contratos de dados](../../../wcf/feature-details/using-data-contracts.md)
- [Tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md)
 