---
title: '&lt;udpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa291901-8340-45c6-9c44-5d9281c70bc3
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f43462ac42c59407ae90f2d342a445a688e1b26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltudpbindinggt"></a>&lt;udpBinding&gt;
Um elemento de configuração usado para configurar o <xref:System.ServiceModel.UdpBinding> associação.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<udpBinding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<udpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       duplicateMessageHistoryLength="Integer"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"       maxPendingMessagesTotalSize="Integer"  
       maxReceivedMessageSize="Integer"       maxRetransmitCount="Integer"  
       multicastInterfaceId="Integer"  
              name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
       textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
       timeToLive="TimeSpan">  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`duplicateMessageHistoryLength`|Um valor inteiro que especifica o comprimento do histórico de mensagens duplicadas.|  
|`maxBufferPoolSize`|Um valor inteiro que especifica a quantidade máxima de memória que é alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal. O valor padrão é 524288 (0x80000) bytes.|  
|`maxBufferSize`|Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação. O valor padrão é 65.536 bytes.|  
|`maxPendingMessagesTotalSize`|Um valor inteiro que especifica o número máximo de mensagens que são recebidos, mas ainda não foram removidas da fila de entrada para uma instância de canal individual.|  
|`maxReceivedMessageSize`|Um inteiro positivo que define o tamanho máximo, em bytes, incluindo os cabeçalhos de uma mensagem que pode ser recebido em um canal configurado com essa associação. O remetente recebe uma falha de SOAP se a mensagem é muito grande para o receptor. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65.536 bytes.|  
|`maxRetransmitCount`|Um valor inteiro que especifica o número máximo de mensagens de retransmissão.|  
|`multicastInterfaceId`|Um valor inteiro que especifica a ID de interface de multicast.|  
|`name`|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço. Além disso, esse nome é exclusivo entre as associações do mesmo tipo. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`textEncoding`|Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos incluem o seguinte:<br /><br /> -BigEndianUnicode: O Unicode BigEndian codificação.<br />-Unicode: codificação de 16 bits.<br />-UTF8: codificação de 8 bits<br /><br /> O padrão é UTF8. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|`timeToLive`|Um valor timespan que especifica o tempo de vida para a associação.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O UdpBinding permite que os serviços do WCF para se comunicar por meio do transporte UDP. Permite trocas de mensagens de "disparar e esquecer" onde um cliente envia uma mensagem para um serviço e espera sem resposta de volta.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como configurar o <xref:System.ServiceModel.UdpBinding> usando o <`udpBinding`> elemento.  
  
```xml  
<udpBinding>  
        <binding  closeTimeout="00:10:00"  
                   duplicateMessageHistoryLength="100"  
                   maxBufferPoolSize="100"  
                   maxPendingMessagesTotalSize="100000"  
                   maxReceivedMessageSize="65536"  
                    maxRetransmitCount="10"  
                   multicastInterfaceId="00000"  
                   name="myUdpBinding"  
                   openTimeout="00:10:00"  
                   receiveTimeout="00:10:00"  
                   sendTimeout="00:10:00"  
                   textEncoding="utf-8"  
                   timeToLive="00:10:00"  
          <readerQuotas/>   
        </binding>  
      </udpBinding>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
