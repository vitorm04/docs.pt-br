---
title: '&lt;webHttpEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: b69ace451e90c824cdf8b911d596fdd158eb3f73
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491713"
---
# <a name="ltwebhttpendpointgt"></a>&lt;webHttpEndpoint&gt;
Este elemento de configuração define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento. Use esse ponto de extremidade ao escrever um serviço REST.  
  
\<system.ServiceModel>  
\<standardEndpoints>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webHttpEndpoint>
      <standardEndpoint automaticFormatSelectionEnabled="String"
                        defaultOutgoingResponseFormat="Xml/Json"
                        helpEnabled="Boolean"
                        webEndpointType="String" />
    </webHttpEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|automaticFormatSelectionEnabled|Um valor booliano que indica se a seleção automática de formato está habilitada.<br /><br /> Quando a seleção automática de formato estiver habilitada, a infra-estrutura analisa o `Accept` cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado. Se o `Accept` cabeçalho não especifica um formato de resposta adequada, a infraestrutura usa a `Content-Type` da mensagem de solicitação ou o formato da resposta da operação padrão.|  
|defaultOutgoingResponseFormat|Um atributo que especifica o formato de resposta de saída padrão. Esse atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo|  
|helpEnabled|Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.|  
|webEndpointType|Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|Uma coleção de pontos de extremidade padrão que são definidos previamente os pontos de extremidade com um ou mais das suas propriedades (endereço, associação, contrato) fixo.|  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
