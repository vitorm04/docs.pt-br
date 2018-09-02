---
title: '&lt;webSocketSettings&gt;'
ms.date: 03/30/2017
ms.assetid: bbf97e02-8dd1-4922-acac-3cd33397b249
ms.openlocfilehash: e5f34dca83c8d3d08d27fb72bee5af2a89ac6b9f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416422"
---
# <a name="ltwebsocketsettingsgt"></a>&lt;webSocketSettings&gt;
Um elemento de configuração usado para especificar configurações de soquete da Web.  
  
\<system.ServiceModel>  
\<associações >  
\<netHttpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netHttpBinding>  
  <binding>   
    <webSocketSettings createNotificationOnConnection="boolean" 
                       disablePayloadMasking="boolean" 
                       keepAliveInterval="TimeSpan" 
                       maxPendingConnections="Integer" 
                       receiveBufferSize="Integer" 
                       sendBufferSize="Integer" 
                       subProtocol="String" 
                       transportUsage="WhenDuplex/Always/Never"/>
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
                              disablePayloadMasking="false  
                              keepAliveInterval="00:10:00"  
                              maxPendingConnections="100"  
                              receiveBufferSize="1000"  
                              sendBufferSize="1000"  
                              subProtocol="Soap"  
                              transportUsage="WhenDuplex/Always/Never"/>  
  
        </binding>  
      </netHttpBinding>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
