---
title: <dataContractSerializer>
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 7e440810fee1dddb7025d1385b1edb4838d98a39
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925920"
---
# <a name="datacontractserializer"></a>\<dataContractSerializer>
Contém dados de configuração para <xref:System.Runtime.Serialization.DataContractSerializer>o. Esse elemento ocorre em duas hierarquias diferentes. Uma é listada na seção hierarquia de esquema a seguir e a outra é listada na seção comentários.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<> de portais  
\<> de comportamento  
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
|ignoreExtensionDataObject|Um valor booliano que especifica se é para ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado. Esse atributo é configurável somente no `<dataContractSerializer>` `<behavior>` elemento abaixo.|  
|maxItemsInObjectGraph|Um inteiro que especifica o número máximo de itens a serem serializados ou desserializados. Esse atributo é 65536.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-servicebehaviors.md)|Uma coleção de configurações para o comportamento de um serviço.|  
|[\<system.runtime.serialization>](system-runtime-serialization.md)|Representa o elemento raiz da <xref:System.Runtime.Serialization> seção namespace e contém elementos para definir as opções <xref:System.Runtime.Serialization.DataContractSerializer>do.|  
  
## <a name="remarks"></a>Comentários  
 Conforme indicado na introdução deste tópico, esta é a segunda hierarquia na qual o \<elemento de > X509Extension ocorre.  
  
 [\<system.runtime.serialization>](system-runtime-serialization.md)  
  
 [\<dataContractSerializer>](datacontractserializer-element.md)  
  
 Para obter mais informações sobre tipos conhecidos, <xref:System.Runtime.Serialization.DataContractSerializer>consulte.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.ServiceModel.Configuration.DataContractSerializerElement>
- [Tipos conhecidos de contrato de dados](../../../wcf/feature-details/data-contract-known-types.md)
- [Serialização e transferência de dados](../../../wcf/feature-details/data-transfer-and-serialization.md)
