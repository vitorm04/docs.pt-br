---
title: '&lt;webHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 84179d77-825d-44b9-895a-ab08e7aa044d
ms.openlocfilehash: 3a5a0844da401607b2049069e7195fa996c62fba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365534"
---
# <a name="ltwebhttpbindinggt"></a>&lt;webHttpBinding&gt;
Define um elemento de associação que é usado para configurar pontos de extremidade para serviços Web do Windows Communication Foundation (WCF) que respondem às solicitações HTTP em vez de mensagens SOAP.  
  
\<system.ServiceModel>  
\<associações >  
\<webHttpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<webHttpBinding>  
  <binding   
    allowCookies="Boolean"  
    bypassProxyOnLocal="Boolean"  
    closeTimeout="TimeSpan"  
    hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
    maxBufferPoolSize="integer"  
    maxBufferSize="integer"  
    maxReceivedMessageSize="Integer"  
    name="string"  
    openTimeout="TimeSpan"   
    proxyAddress="URI"  
    receiveTimeout="TimeSpan"  
    sendTimeout="TimeSpan"  
    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
    useDefaultWebProxy="Boolean" 
    writeEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding">  
  <security mode="None/Transport/TransportCredentialOnly">  
    <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
               proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
               realm="string" />  
  </security>  
  <readerQuotas maxArrayLength="Integer" 
                maxBytesPerRead="Integer" 
                maxDepth="Integer" 
                maxNameTableCharCount="Integer" 
                maxStringContentLength="Integer" />  
  </binding>  
</webHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|allowCookies|Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras. O padrão é falso.<br /><br /> Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies. Dessa forma, você poderá ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras desse serviço.|  
|bypassProxyOnLocal|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.|  
|closeTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|hostnameComparisonMode|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
|maxBufferPoolSize|Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação. O padrão é 524.288 bytes (512 * 1024). Muitas partes do Windows Communication Foundation (WCF) usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxBufferSize|Um inteiro que especifica a quantidade máxima de memória que é alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal. O valor padrão é buckets 524.288 (0x80000) bytes.|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação. O remetente de uma mensagem exceder esse limite recebem uma falha. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536. **Observação:** aumentar esse valor sozinho não é suficiente em modo compatível com ASP.NET. Você também deve aumentar o valor de `httpRuntime` (consulte [httpRuntime Element (ASP.NET Settings Schema)](http://msdn.microsoft.com/library/e9b81350-8aaf-47cc-9843-5f7d0c59f369)).|  
|name|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|proxyAddress|Um URI que especifica o endereço do proxy HTTP. Se `useSystemWebProxy` é `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|receiveTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|sendTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|transferMode.|Um <xref:System.ServiceModel.TransferMode> valor que indica se o serviço configurado com a associação usa transmitidos ou armazenados em buffer (ou ambos) modos de transferência de mensagem. O padrão é `Buffered`.|  
|useDefaultWebProxy|Um valor booleano que especifica se o proxy HTTP configurado automaticamente do sistema é usado. O padrão é `true`.|  
|writeEncoding|Especifica a codificação de caracteres é usada para o texto da mensagem. Os valores válidos incluem o seguinte:<br /><br /> UnicodeFffeTextEncoding: O Unicode BigEndian codificação.<br /><br /> Utf16TextEncoding: codificação de 16 bits.<br /><br /> Utf8TextEncoding: codificação de 8 bits.<br /><br /> O padrão é Utf8TextEncoding.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens POX que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-webhttpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WebHttpSecurityElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O modelo de programação WCF Web permite aos desenvolvedores expor serviços Web WCF por meio de solicitações HTTP que usam "plain old XML" estilo (POX) de mensagens em vez de mensagens baseadas em SOAP. Para os clientes se comunicam com um serviço usando solicitações HTTP, um ponto de extremidade do serviço deve ser configurado com o [ \<webHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md) que tem o \<WebHttpBehavior > anexado a ele.  
  
 Suporte em WCF para distribuição e do ASP. Integração de AJAX são desenvolvidos com base no modelo de programação da Web. Para obter mais informações sobre o modelo, consulte [modelo de programação do WCF Web HTTP](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WebHttpBinding>  
 <xref:System.ServiceModel.Configuration.WebHttpBindingElement>  
 [Modelo de programação HTTP Web do WCF](../../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
