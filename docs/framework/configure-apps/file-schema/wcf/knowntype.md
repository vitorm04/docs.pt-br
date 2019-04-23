---
title: <knownType>
ms.date: 03/30/2017
ms.assetid: ee2b7be3-7148-4a3a-b861-48e7330615e5
ms.openlocfilehash: 4d3dd9042951ffb46b8e0a3f7bb7bcdee23fd58b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148831"
---
# <a name="knowntype"></a>\<knownType>
Especifica um tipo a ser usado por <xref:System.Runtime.Serialization.DataContractSerializer> durante a desserialização. O elemento Especifica um "tipo conhecido" que é retornado por um campo ou propriedade de um "tipo declarado". Para obter mais informações, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 \<system.runtime.serialization>  
\<dataContractSerializer>  
\<declaredTypes > elemento  
\<Adicionar > de \<declaredTypes >  
\<knownType > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<knownType type="String">
  <parameter index="Integer"
             type="String" />
</knownType>
```  
  
## <a name="type"></a>Tipo  
 `string`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Especifica o tipo (incluindo namespace) nome do assembly, versão, cultura e token de chave pública.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<parameter>](../../../../../docs/framework/configure-apps/file-schema/wcf/parameter.md)|Especifica um índice de parâmetro quando o tipo declarado é um tipo genérico.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)|Adiciona um tipo declarado para a coleção de tipos declarados.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Consulte a [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL"/>
</add>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
