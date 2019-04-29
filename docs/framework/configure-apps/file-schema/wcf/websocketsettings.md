---
title: <webSocketSettings>
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: 1101d021f3c7436c4f45a22a48e50f6d1553f753
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769740"
---
# <a name="websocketsettings"></a>\<webSocketSettings>
Um elemento de configuração usado para especificar configurações de soquete da Web.  
  
\<system.ServiceModel>  
\<bindings>  
\<netHttpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="Boolean"
                       disablePayloadMasking="Boolean"
                       keepAliveInterval="TimeSpan"
                       maxPendingConnections="Integer"
                       receiveBufferSize="Integer"
                       sendBufferSize="Integer"
                       subProtocol="String"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|createNotificationOnConnection|Especifica se uma notificação será enviada após a conexão.|  
|disablePayloadMasking|Especifica se o mascaramento de soquete da Web está desabilitado.|  
|keepAliveInterval|Especifica o intervalo de keep alive.|  
|maxPendingConnections|Especifica o número máximo de conexões aguardando a expedição no serviço.|  
|receiveBufferSize|Especifica o tamanho do buffer de recepção.|  
|sendBufferSize|Especifica o tamanho do buffer de envio.|  
|subProtocol|Especifica o subprotocolo do soquete da Web.|  
|transportUsage|Especifica quando usar soquetes da Web.|  
  
## <a name="transportusage-attribute"></a>transportUsage atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|WhenDuplex|Use o protocolo de soquete da Web quando o contrato é duplex.|  
|Sempre|Sempre use o protocolo de soquete da Web, independentemente do contrato.|  
|Nunca|Nunca use o protocolo de soquete da Web.|  
  
### <a name="child-elements"></a>Elementos filho  
 Nenhum  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|\<netHttpBinding>|Especifica o NetHttpBinding|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o \<webSocketSettings > elemento.  
  
```xml  
<netHttpBinding>
  <binding>
    <webSocketSettings createNotificationOnConnection="true"
                       disablePayloadMasking="false"
                       keepAliveInterval="00:10:00"
                       maxPendingConnections="100"
                       receiveBufferSize="1000"
                       sendBufferSize="1000"
                       subProtocol="Soap"
                       transportUsage="WhenDuplex/Always/Never" />
  </binding>
</netHttpBinding>
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
