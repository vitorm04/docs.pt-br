---
title: '&lt;defaultPorts&gt;'
ms.date: 03/30/2017
ms.assetid: 725d4ee5-bd46-4f0e-9c20-30ba75d6eb2c
ms.openlocfilehash: 2f7de066a1b91e9fa22fbe0213e221c6f4bbe617
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747168"
---
# <a name="ltdefaultportsgt"></a>&lt;defaultPorts&gt;
Uma coleção de portas padrão listando os pontos de extremidade de comunicação padrão que o aplicativo cliente ouve.  
  
\<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors >  
\<comportamento >  
\<useRequestHeadersForMetadataAddress >  
\<defaultPorts >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add scheme="http" port="integer" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<Adicionar > de \<defaultPorts >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-defaultports.md)|Um comunicação ponto de extremidade padrão que o aplicativo cliente ouve.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<useRequestHeadersForMetadataAddress >](../../../../../docs/framework/configure-apps/file-schema/wcf/userequestheadersformetadataaddress.md)|Uma lista de portas padrão.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.DefaultPortElementCollection>
