---
title: <headers>
ms.date: 03/30/2017
ms.assetid: c79b897d-8ea3-40b5-a8b6-2471941f7ed3
ms.openlocfilehash: 76b3cbf6b867a983c203141bcd901b2b7b4038d5
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855175"
---
# <a name="headers"></a>\<cabeçalhos >
Um ponto de extremidade pode ser resolvido por um ou mais cabeçalhos SOAP além de seu URI básico. Um conjunto de cenários em que isso é útil é um conjunto de cenários intermediários de SOAP em que um ponto de extremidade exige que clientes desse ponto de extremidade incluam cabeçalhos SOAP direcionados a intermediários. Este elemento de configuração pode ser usado para definir esses cabeçalhos de endereço personalizados. As entradas na coleção de cabeçalhos do ponto de extremidade são elementos XML definidos pelo usuário. Cada elemento deve ser um XML bem formado.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do ponto de extremidade**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<cabeçalhos >**  
  
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
 Elementos XML definidos pelo usuário.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-of-client.md)|Configura tipos diferentes de pontos de extremidade.|  
  
## <a name="remarks"></a>Comentários  
 Os cabeçalhos opcionais fornecem informações de endereçamento mais detalhadas para identificar ou interagir com o ponto de extremidade. Por exemplo, os cabeçalhos podem indicar como processar uma mensagem de entrada, em que o ponto de extremidade deve enviar uma mensagem de resposta ou qual instância de um serviço usar para processar uma mensagem de entrada de um usuário específico quando várias instâncias estão disponíveis.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Headers%2A>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection>
- [Extremidade Endereços, associações e contratos](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
