---
title: dataContractSerializer
ms.date: 03/30/2017
ms.assetid: a47513a4-a96c-4350-8586-daacb05dee71
ms.openlocfilehash: 933d49092c392fa293468d546e521bf7ed858376
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539838"
---
# <a name="datacontractserializer"></a>dataContractSerializer
Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<endpointBehaviors>  
\<behavior>  
\<dataContractSerializer>  
  
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
|ignoreExtensionDataObject|Um valor booliano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade, quando ele está sendo serializado ou desserializado.|  
|maxItemsInObjectGraph|Um inteiro que especifica o número máximo de itens para serializar ou desserializar.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um comportamento de ponto de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Consulte o <xref:System.Runtime.Serialization.DataContractSerializer> documentação para obter mais informações sobre tipos conhecidos.  
  
> [!CAUTION]
>  O `<dataContractSerializer>` elemento de comportamento (se houver) sempre deverá aparecer antes do `<enableWebScript>` elemento de comportamento no arquivo de configuração. Caso contrário, o comportamento resultante será indefinido.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
- [Serialização e transferência de dados](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
