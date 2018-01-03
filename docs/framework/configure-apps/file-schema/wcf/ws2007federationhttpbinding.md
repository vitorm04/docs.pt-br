---
title: '&lt;WS2007FederationHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9af4ec79-cdef-457e-9dca-09d5eb821594
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 28e4cc9189c144404bcfe2b7f8e255a74eef76c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltws2007federationhttpbindinggt"></a>&lt;WS2007FederationHttpBinding&gt;
Uma associação segura e interoperável que deriva de [ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e suporta segurança federada.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<WS2007FederationHttpBinding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
           <message negotiateServiceCredential="Boolean"  
                algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                issuedTokenType="string"  
                issuedKeyType="SymmetricKey/PublicKey"  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</ws2007FederationHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`bypassProxyOnLocal`|Um valor que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`hostnameComparisonMode`|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
|`maxBufferPoolSize`|O tamanho do pool de buffer máximo para esta associação. O padrão é 524.288 bytes (512 * 1024). Muitas partes do [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] usar buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|`maxReceivedMessageSize`|O tamanho máximo da mensagem, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação. O remetente de uma mensagem que exceda esse limite recebe uma falha SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|`messageEncoding`|Define o codificador usado para codificar a mensagem. Os valores válidos incluem o seguinte:<br /><br /> -Texto: Use um codificador de mensagem de texto.<br />-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).<br /><br /> O padrão é texto.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|O nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`privactyNoticeAt`|Um URI no qual o aviso de privacidade está localizado.|  
|`privactyNoticeVersion`|A versão do aviso de privacidade atual.|  
|`proxyAddress`|Um URI que especifica o endereço do proxy HTTP. Se `useDefaultWebProxy` é `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`textEncoding`|Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos incluem o seguinte:<br /><br /> -BigEndianUnicode: Big Endian codificação Unicode.<br />-Unicode: codificação de 16 bits.<br />-UTF8: codificação de 8 bits.<br /><br /> O padrão é UTF8. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|`transactionFlow`|Um valor que especifica se a associação oferece suporte a fluxo de transações de WS. O padrão é `false`.|  
|`useDefaultWebProxy`|Um valor que indica se o proxy HTTP configurado automaticamente do sistema é usado. O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`. O padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|Define as configurações de segurança para a mensagem. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 Federação é a capacidade de compartilhar identidades entre várias empresas ou domínios confiáveis para autenticação e autorização. Ele usa o protocolo WS-Trust para mapear a representação da identidade de domínio de uma relação de confiança para outro. Associação HTTP federada dá suporte à segurança SOAP, bem como a segurança de modo misto, mas não dá suporte a segurança de transporte. Serviços configurados com essa associação devem usar o transporte HTTP. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][ \<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<ws2007FederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://www.contoso.com"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</ws2007FederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WS2007FederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WS2007FederationHttpBindingElement>  
 [\<wsFederationHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
