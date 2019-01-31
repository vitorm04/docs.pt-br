---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 7677d7f4c0ef7927fd50885bb887dccaa62a27b4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55286780"
---
# <a name="standardendpoints"></a>\<standardEndpoints>
Esta seção de configuração permite que você defina uma coleção de pontos de extremidade padrão que são pontos de extremidade pré-configurados reutilizáveis. Um ponto de extremidade padrão terá um ou mais do endereço, associação e atributos de contrato definido como um valor fixo. Por exemplo, o ponto de extremidade de descoberta o contrato é fixo. Você também pode usar pontos de extremidade padrão para estender o ponto de extremidade de serviço com novas propriedades semelhantes à definição de ligações personalizadas.  
  
 \<system.ServiceModel>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|Define um ponto de extremidade padrão com um contrato de anúncio fixo. Um serviço pode, opcionalmente, anunciar sua disponibilidade, enviando uma mensagem de comunicado online e offline, quando ele é aberto ou fechado, respectivamente. Um serviço do Windows Communication Foundation (WCF) especifica os pontos de extremidade de comunicado na [ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) elemento e usa o AnnouncementClient para executar os anúncios. Um cliente que desejarem escutar o comunicado de outro serviço, na verdade, está atuando como um serviço WCF. Portanto, você precisa configurar os pontos de extremidade de comunicado para esse cliente na [ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) seção.|  
|[\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|Define um ponto de extremidade padrão com um contrato de correção da descoberta. Quando adicionado à configuração de serviço, ele especifica onde a escutar as mensagens de descoberta. Quando adicionado à configuração de cliente, ele especifica para onde enviar as consultas de descoberta.|  
|[\<dynamicEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/dynamicendpoint.md)|Este elemento de configuração define um ponto de extremidade padrão que contém informações para permitir que um aplicativo funcione como um programa cliente que pode encontrar o endereço do ponto de extremidade dinamicamente em tempo de execução.|  
|[\<mexEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/mexendpoint.md)|Define um ponto de extremidade padrão com um contrato IMetadataExchange fixo. Uma vez que todos os pontos de extremidade de troca de metadados especificam IMetadataExchange como seu contrato, você pode usar esse ponto padrão em vez de definir um por conta própria.|  
|[\<udpAnnoucementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpannoucementendpoint.md)|Define um ponto de extremidade padrão que é usado pelos serviços para enviar mensagens de comunicado por uma associação de UDP. Ele tem um contrato fixo e oferece suporte a duas versões de descoberta. Além disso, ele tem uma associação de UDP fixa e um valor de endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery versão 1.1). Você pode especificar o endereço multicast a ser usado para enviar e receber mensagens de comunicado.|  
|[\<udpDiscoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/udpdiscoveryendpoint.md)|Define um ponto de extremidade padrão que é pré-configurado para operações de descoberta através de um UDP multicast de associação. Esse ponto de extremidade tem um contrato fixo e oferece suporte a duas versões do protocolo WS-Discovery. Além disso, ele tem uma associação de UDP fixa e um endereço padrão, conforme as especificações do WS-Discovery (WS-Discovery de abril de 2005 ou WS-Discovery V1.1).|  
|[\<webHttpEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpendpoint.md)|Define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<webHttp >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) comportamento. Use esse ponto de extremidade ao escrever um serviço REST.|  
|[\<webScriptEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/webscriptendpoint.md)|Define um ponto de extremidade padrão com um fixo [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) associação que automaticamente adiciona o [ \<enableWebScript >](../../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) comportamento. Use esse ponto de extremidade quando você estiver escrevendo um serviço que é chamado de um aplicativo ASP.NET AJAX.|  
|[\<workflowControlEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/workflowcontrolendpoint.md)|Define um ponto de extremidade padrão para controlar a execução de instâncias de fluxo de trabalho (criar, executar, suspender, finalizar, etc).|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|\<system.ServiceModel>|O elemento raiz de todos os elementos de configuração do WCF.|  
  
## <a name="see-also"></a>Consulte também
- [Pontos de extremidade padrão](../../../../../docs/framework/wcf/feature-details/standard-endpoints.md)
