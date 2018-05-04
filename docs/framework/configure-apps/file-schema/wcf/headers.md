---
title: '&lt;cabeçalhos&gt;'
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 7683b07093719cda6b210a4174d47e5785d4644d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltheadersgt"></a>&lt;cabeçalhos&gt;
Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico. Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade exige que os clientes do ponto de extremidade incluir cabeçalhos de SOAP direcionados a intermediários. Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizado. As entradas na coleção de cabeçalho do ponto de extremidade são elementos XML definido pelo usuário. Cada elemento deve ser bem formado XML.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<headers>  
    <Region xmlns="Uri">"String"</Region>  
        <Member xmlns="Uri">"String"</Member>  
</headers>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|Região||  
|Membro||  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Configura os diferentes tipos de pontos de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade. Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, onde o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário quando houver várias instâncias.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Headers%2A>  
 <xref:System.ServiceModel.Channels.AddressHeaderCollection>  
 [Pontos de extremidade: endereços, associações e contratos](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
