---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: e6524c18780c062c3b5b7dfc2509449cb208e270
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400440"
---
# <a name="datacontractserializer"></a>dataContractSerializer
Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do dataContractSerializer**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<dataContractSerializer ignoreExtensionDataObject="Boolean"
                        maxItemsInObjectGraph="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|ignoreExtensionDataObject|Um valor booliano que especifica se os dados fornecidos pelo ponto de extremidade devem ser ignorados, quando ele está sendo serializado ou desserializado.|  
|maxItemsInObjectGraph|Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Consulte a <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.  
  
> [!CAUTION]
> O `<dataContractSerializer>` elemento Behavior (se presente) sempre deve aparecer antes do `<enableWebScript>` elemento Behavior no arquivo de configuração. Caso contrário, o comportamento resultante será indefinido.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md)
- [Serialização e transferência de dados](../../../wcf/feature-details/data-transfer-and-serialization.md)
