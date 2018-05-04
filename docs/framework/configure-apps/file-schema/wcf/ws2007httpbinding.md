---
title: '&lt;ws2007HttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 8586ecc9-bdaa-44d6-8d4d-7038e4ea1741
ms.openlocfilehash: 6531e35cbed56029a8f772f0cd63aad521a166ef
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltws2007httpbindinggt"></a>&lt;ws2007HttpBinding&gt;
Define uma associação interoperável que fornece suporte para as versões corretas do <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, e <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementos de associação.  
  
 \<system.serviceModel>  
\<associações >  
\<ws2007HttpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ws2007HttpBinding>  
    <binding   
        allowCookies="Boolean"  
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"  
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
  
textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
        <security mode="Message/None/Transport/TransportWithCredential">  
           <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
                proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
                realm="string"   
                                />  
          <message clientCredentialType ="Certificate/IssuedToken/None/UserName/Windows"  
           negotiateServiceCredential="Boolean"  
           algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
           establishSecurityContext="Boolean"   
           negotiateServiceCredential="Boolean"/>  
        </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007HttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowCookies`|Um valor que indica se o cliente aceita cookies e os propaga em solicitações futuras. O padrão é `false`.<br /><br /> Você pode usar essa propriedade quando você interage com os serviços da Web do ASP.NET (ASMX) que usam cookies. Isso garante que os cookies que o servidor retorna são copiados automaticamente para todas as solicitações futuras de cliente para esse serviço.|  
|`bypassProxyOnLocal`|Um valor que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo para concluir uma operação de fechamento. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`hostnameComparisonMode`|Especifica o modo de comparação de nome de host HTTP usado para analisar o Uniform Resource Identifier (URIs). Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
|`maxBufferPoolSize`|O tamanho do pool de buffer máximo para esta associação. O padrão é 524.288 bytes (512 × 1.024). Muitas partes do Windows Communication Foundation (WCF) usam buffers. Criação e destruição de buffers de cada vez que elas são usadas é caro, como coleta de lixo para buffers. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Isso evita a sobrecarga na criação e destruição de buffers.|  
|`maxReceivedMessageSize`|O tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, o que pode receber um canal configurado com essa associação. O remetente de uma mensagem exceder esse limite recebe uma falha SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|`messageEncoding`|Define o codificador usado para codificar a mensagem. Os valores válidos incluem o seguinte:<br /><br /> -   `Text`: Use um codificador de mensagem de texto.<br />-   `Mtom`: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).<br /><br /> O padrão é `Text`.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|O nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`proxyAddress`|Um URI que especifica o endereço do proxy HTTP. Se `useSystemWebProxy` é `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`textEncoding`|Especifica a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos incluem o seguinte:<br /><br /> -   `UnicodeFffeTextEncoding`: Unicode Big Endian codificação.<br />-   `Utf16TextEncoding`: codificação de 16 bits.<br />-   `Utf8TextEncoding`: codificação de 8 bits.<br /><br /> O padrão é `Utf8TextEncoding`.<br /><br /> Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|`transactionFlow`|Um valor que especifica se a associação oferece suporte a fluxo de transações de WS. O padrão é `false`.|  
|`useDefaultWebProxy`|Um valor que especifica se o proxy HTTP configurado automaticamente do sistema é usado. O padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que pontos de extremidade configurados com essa associação podem processar. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O `WS2007HttpBinding` adiciona uma associação fornecida pelo sistema semelhante ao `WSHttpBinding` , mas usa a organização para as versões de avanço de Structured Information Standards (OASIS) padrão dos protocolos TransactionFlow, ReliableSession e segurança. Nenhuma alteração para as configurações padrão ou de modelo de objeto é necessária ao usar essa associação.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
    <system.ServiceModel>  
        <bindings>  
            <ws2007HttpBinding>  
                <binding   
                    closeTimeout="00:00:10"  
                    openTimeout="00:00:20"   
                    receiveTimeout="00:00:30"  
                    sendTimeout="00:00:40"  
                    bypassProxyOnLocal="false"  
                    transactionFlow="false"   
                    hostNameComparisonMode="WeakWildcard"  
                    maxReceivedMessageSize="1000"  
                    messageEncoding="Mtom"   
                    proxyAddress="http://www.contoso.com"  
                    textEncoding="utf-16"  
                    useDefaultWebProxy="false">  
                    <reliableSession ordered="false"  
                         inactivityTimeout="00:02:00"  
                         enabled="true" />  
                    <security mode="Transport">  
                         <transport clientCredentialType="Digest"  
                            proxyCredentialType="None"  
                            realm="someRealm" />  
                         <message clientCredentialType="Windows"  
                            negotiateServiceCredential="false"  
                            algorithmSuite="Aes128"   
                            defaultProtectionLevel="None" />  
                    </security>  
                </binding>  
           </ws2007HttpBinding>  
        </bindings>  
    </system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WS2007HttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007HttpBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
