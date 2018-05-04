---
title: '&lt;DataContractSerializer&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- dataContractSerializer element
- <dataContractSerializer> element
- DataContractSerializer
- KnownTypes
ms.assetid: f41fb4d5-24e7-4059-8010-286a30bfea93
ms.openlocfilehash: 5f2a05fdf2e38923205092b232995a70a87f7e87
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltdatacontractserializergt"></a>&lt;DataContractSerializer&gt;
Contém dados de configuração para o <xref:System.Runtime.Serialization.DataContractSerializer>. Esse elemento ocorre em duas hierarquias diferentes. Um é listado a seguinte seção de hierarquia de esquema e o outro está listado na seção comentários.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<dataContractSerializer >  
  
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
|IgnoreExtensionDataObject|Um valor booleano que especifica se deve ignorar os dados fornecidos pelo ponto de extremidade quando ele está sendo serializado ou desserializado. Esse atributo é configurável somente no `<dataContractSerializer>` sob o `<behavior>` elemento.|  
|MaxItemsInObjectGraph|Um inteiro que especifica o número máximo de itens para serializar ou desserializar. Esse atributo é 65536.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<comportamento >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)|Uma coleção de configurações para o comportamento de um serviço.|  
|[\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)|Representa o elemento raiz para o <xref:System.Runtime.Serialization> seção de namespace e contém elementos para configurar as opções do <xref:System.Runtime.Serialization.DataContractSerializer>.|  
  
## <a name="remarks"></a>Comentários  
 Conforme mencionado na introdução deste tópico, este é a segunda hierarquia na qual o \<X509Extension > elemento ocorre.  
  
 [\<system.runtime.serialization>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-runtime-serialization.md)  
  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
  
 Para obter mais informações sobre tipos conhecidos, consulte <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.ServiceModel.Configuration.DataContractSerializerElement>  
 [Tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [Serialização e transferência de dados](../../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
