---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 660497012dd057e4ecf95524833e2573fe03a8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670671"
---
# <a name="headers"></a>\<headers>
Um ponto de extremidade pode ser tratado por um ou mais cabeçalhos SOAP, além de seu URI básico. Um conjunto de cenários em que isso é útil é um conjunto de cenários de intermediários SOAP em que um ponto de extremidade requer que os clientes desse ponto de extremidade incluir os cabeçalhos SOAP destinados a intermediários. Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizado. As entradas na coleção de cabeçalho do ponto de extremidade são os elementos XML definidos pelo usuário. Cada elemento tem que ser bem formada XML.  
  
 \<system.ServiceModel>  
\<client>  
\<endpoint>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<headers>
  <region xmlns="Uri">"String"</region>
  <member xmlns="Uri">"String"</member>
</headers>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
 Elementos XML definido pelo usuário.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-of-client.md)|Configura os diferentes tipos de pontos de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Os cabeçalhos opcionais fornecem informações mais detalhadas de endereçamento para identificar ou interagir com o ponto de extremidade. Por exemplo, os cabeçalhos podem indicar qual instância de um serviço para usar para processar uma mensagem de entrada de um determinado usuário, quando várias instâncias estiverem disponíveis, onde o ponto de extremidade deve enviar uma mensagem de resposta ou como processar uma mensagem de entrada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [Pontos de extremidade: Endereços, associações e contratos](../../../../../docs/framework/wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
