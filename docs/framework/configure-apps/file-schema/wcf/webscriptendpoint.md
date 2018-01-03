---
title: '&lt;webScriptEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 855a0fc0727bf0559b922317d439f7550f18d9ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltwebscriptendpointgt"></a>&lt;webScriptEndpoint&gt;
Este elemento de configuração define um ponto de extremidade padrão fixa [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento. Use esse ponto de extremidade quando você estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.  
  
\<sistema. ServiceModel >  
\<standardEndpoints >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String"/>
    </webScriptEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|webEndpointType|Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Uma coleção de pontos de extremidade padrão que são predefinidas pontos de extremidade com um ou mais de suas propriedades (endereço, associação, contrato) fixo.|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.WebScriptEndpoint>  
 <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
