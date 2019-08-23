---
title: <add>do <declaredTypes> elemento
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 1ea008dcc72d555b00e9648ace95bb9522ffc2c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920183"
---
# <a name="add-of-declaredtypes-element"></a>\<Adicionar > do \<elemento declaredTypes >
Adiciona um tipo usado pelo durante <xref:System.Runtime.Serialization.DataContractSerializer> a desserialização. Cada tipo declarado inclui os tipos conhecidos que serão retornados como um campo ou Propriedade do tipo declarado.  
  
 system.runtime.serialization  
\<dataContractSerializer>  
\<declaredTypes>  
\<Adicionar > de \<declaredTypes >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add type="String">
  <knownType type="String">
    <parameter index="Integer"
               type="String" />
  </knownType>
</add>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|tipo|Atributo de cadeia de caracteres obrigatório.<br /><br /> Especifica o nome do tipo (incluindo o namespace), o nome do assembly, o número de versão, a cultura e o token de chave pública.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<knownType >](knowntype.md)|Especifica o tipo conhecido para o tipo declarado que está sendo adicionado. Se o tipo declarado for um tipo genérico, você também deverá adicionar um elemento de parâmetro ao `<knownType>` elemento para especificar qual parâmetro genérico é usado para retornar o tipo conhecido.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<declaredTypes>](declaredtypes.md)|Contém os tipos que exigem tipos conhecidos durante a <xref:System.Runtime.Serialization.DataContractSerializer>desserialização pelo.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md) e. <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 Consulte o [ \<> do DataContractSerializer](datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.  
  
> [!NOTE]
> Se você adicionar o <xref:System.Object> tipo como um `<declaredType>`, um <xref:System.Configuration.ConfigurationErrorsException> será lançado. Isso ocorre porque o <xref:System.Object> tipo não pode ser usado como um tipo declarado na configuração.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<add type="MyCompany.Library.Shape,
           MyAssembly, Version=2.0.0.0, Culture=neutral,
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">
  <knownType type="MyCompany.Library.Circle,
                   MyAssembly, Version=2.0.0.0, Culture=neutral,
                   PublicKeyToken=XXXXXX,
                   processorArchitecture=MSIL" />
</add>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- [Tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md)
- [\<dataContractSerializer>](datacontractserializer-element.md)
- [\<Adicionar > de \<declaredTypes >](add-of-declaredtypes-element.md)
