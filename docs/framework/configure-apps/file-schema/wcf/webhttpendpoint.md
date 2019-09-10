---
title: <webHttpEndpoint>
ms.date: 03/30/2017
ms.assetid: ecaaeb6f-ebd0-411d-8b53-92477cd45347
ms.openlocfilehash: 8d4f55fd5b51ea77839b7fdbb930e937f5700417
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854803"
---
# <a name="webhttpendpoint"></a>\<> webHttpEndpoint
Este elemento de configuração define um ponto de extremidade padrão com uma associação [ \<WebHttpBinding fixa >](webhttpbinding.md) que adiciona automaticamente o comportamento de [ \<> Webhttp](webhttp.md) . Use esse ponto de extremidade ao escrever um serviço REST.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> standardEndpoints**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> webHttpEndpoint**  
  
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
|automaticFormatSelectionEnabled|Um valor booliano que indica se a seleção automática de formato está habilitada.<br /><br /> Quando a seleção de formato automático está habilitada, a infraestrutura `Accept` analisa o cabeçalho da mensagem de solicitação e determina o formato de resposta mais apropriado. Se o `Accept` cabeçalho não especificar um formato de resposta adequado, a infraestrutura usará `Content-Type` a da mensagem de solicitação ou o formato de resposta padrão da operação.|  
|defaultOutgoingResponseFormat|Um atributo que especifica o formato de resposta de saída padrão. Este atributo é do <xref:System.ServiceModel.Web.WebMessageFormat> tipo|  
|helpEnabled|Um valor booliano que indica se a página de ajuda HTTP está habilitada para o ponto de extremidade.|  
|webEndpointType|Uma cadeia de caracteres que especifica o tipo do ponto de extremidade.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|Uma coleção de pontos de extremidade padrão que são pontos de extremidade predefinidos com uma ou mais de suas propriedades (endereço, associação, contrato) fixa.|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Description.WebHttpEndpoint>
- <xref:System.ServiceModel.Configuration.WebHttpEndpointElement>
