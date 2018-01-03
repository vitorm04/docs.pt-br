---
title: "seção de &lt;extensões&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53a59fb6-dede-47ec-9384-b3c2e8f0c1fa
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04905ae0f40a1f9ca88b4a04d4e49b0ce895ca56
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltextensionsgt-section"></a>seção de &lt;extensões&gt;
Esta seção de configuração contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.  
  
\<sistema. ServiceModel >  
  
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
|[\<behaviorExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md)|Esta seção contém os elementos filho que especificam extensões de comportamento, que permitem que o usuário personalize os comportamentos de serviço ou o ponto de extremidade.|  
|[\<bindingElementExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingelementextensions.md)|Esta seção permite o uso de um elemento de associação personalizada de um computador ou arquivo de configuração do aplicativo.|  
|[\<bindingExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindingextensions.md)|Esta seção contém os elementos filho que especificam extensões de associação, que permitem que o usuário personalize associações.|  
|[\<endpointExtensions >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointextensions.md)|Esta seção contém os elementos filho que registra a pontos de extremidade padrão.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|sistema.ServiceModel|O elemento raiz de todos os elementos de configuração do WCF.|
