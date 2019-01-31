---
title: <extensions> Seção
ms.date: 03/30/2017
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
ms.openlocfilehash: 0f77f621bbf9bbef00b206ef43a174f6f69364d5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55268282"
---
# <a name="extensions-section"></a>\<Extensões > seção
Esta seção de configuração contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.  
  
\<system.ServiceModel>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <extensions>
    <bindingExtensions>
    </bindingExtensions>
    <behaviorExtensions>
    </behaviorExtensions>
    <bindingElementExtensions>
    </bindingElementExtensions>
    <endpointExtensions>
    </endpointExtensions>
  </extensions>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behaviorExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Esta seção contém os elementos filho que especificam extensões de comportamento, que permitem ao usuário personalizar os comportamentos de serviço ou ponto de extremidade.|  
|[\<bindingElementExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo.|  
|[\<bindingExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Esta seção contém os elementos filho que especificam extensões de associação, que permitem ao usuário personalizar as associações.|  
|[\<endpointExtensions>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Esta seção contém os elementos filho que registra os pontos de extremidade padrão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|sistema.ServiceModel|O elemento raiz de todos os elementos de configuração do WCF.|
