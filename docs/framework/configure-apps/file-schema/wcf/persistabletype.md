---
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: 939a29e90ee21e94ccb78842d6f7224e9a6288d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783312"
---
# <a name="persistabletype"></a>\<persistableType>
Especifica todos os tipos persistentes.  
  
 \<system.ServiceModel>  
\<comContracts>  
\<comContract>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|id|Um atributo necessário que contém uma cadeia de caracteres que especifica um identificador exclusivo para um tipo persistente.|  
|name|Um atributo opcional que contém uma cadeia de caracteres que especifica o nome do tipo persistente.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<persistableTypes>](../../../../../docs/framework/configure-apps/file-schema/wcf/persistabletypes.md)|Uma coleção de elementos `persistableType`.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)
- [Integração de aplicativos COM+](../../../../../docs/framework/wcf/feature-details/integrating-with-com-plus-applications.md)
- [Como: Definir as configurações de serviço COM+](../../../../../docs/framework/wcf/feature-details/how-to-configure-com-service-settings.md)
