---
title: '&lt;wsDualHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsDualHttpBinding Element
ms.assetid: fd8ac4e2-5641-473b-9115-73f14ab1c065
ms.openlocfilehash: 8a0dd9dcb7720da7dfd809b09b039819ba2a34ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltwsdualhttpbindinggt"></a>&lt;wsDualHttpBinding&gt;
Define uma associação segura, confiável e interoperável adequada para contratos de serviço duplex ou comunicação através de intermediários SOAP.  
  
 \<system.ServiceModel>  
\<associações >  
\<wsDualHttpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<wsDualHttpBinding>  
        <binding name="string"  
        closeTimeout="TimeSpan"  
        openTimeout="TimeSpan"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        bypassProxyOnLocal="Boolean"  
        clientBaseAddress="URI"  
        transactionFlow="Boolean"   
        hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="Integer"  
        messageEncoding="Text/Mtom"   
        proxyAddress="URI"  
  
textEncoding="Unicode/BigEndianUnicode/UTF8"  
        useDefaultWebProxy="Boolean">  
        <reliableSession ordered="Boolean"  
            inactivityTimeout="TimeSpan" />  
        <security mode="None/Message">  
           <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
                negotiateServiceCredential="Boolean"  
                    algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />  
                </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsDualHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem os elementos pai de atributos e elementos filho  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|bypassProxyOnLocal|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.|  
|clientBaseAddress|Um URI que define o endereço base que o cliente aguarda para mensagens de resposta do serviço. Se especificado, esse endereço (mais por channelGUID) é usado para escuta. Se o valor não for especificado, o endereço base do cliente é gerado de forma específica de transporte. O padrão é `null`.|  
|closeTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|hostnameComparisonMode|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
|maxBufferPoolSize|Um inteiro que especifica o tamanho do pool de buffer máximo para esta associação. O padrão é 524.288 bytes (512 * 1024). Muitas partes do Windows Communication Foundation (WCF) usam buffers. Criação e destruição de buffers de cada vez que elas são usadas são caro e coleta de lixo para buffers também é cara. Com os pools de buffer, usar um buffer do pool, usá-lo e retorná-lo ao pool quando terminar. Portanto, a sobrecarga na criação e destruição de buffers é evitada.|  
|maxReceivedMessageSize|Um inteiro positivo que especifica o tamanho máximo, em bytes, incluindo os cabeçalhos, o que podem ser recebidos em um canal configurado com essa associação. O remetente de uma mensagem exceder esse limite recebem uma falha SOAP. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65536.|  
|messageEncoding|Define o codificador usado para codificar a mensagem. Os valores válidos incluem o seguinte:<br /><br /> -Texto: Use um codificador de mensagem de texto.<br />-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).<br />-O padrão é texto.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|name|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|openTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|proxyAddress|Um URI que especifica o endereço do proxy HTTP. Se `useDefaultWebProxy` é `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|receiveTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|sendTimeout|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|textEncoding|Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos incluem o seguinte:<br /><br /> -BigEndianUnicode: O Unicode BigEndian codificação.<br />-Unicode: codificação de 16 bits.<br />-UTF8: codificação de 8 bits<br /><br /> O padrão é UTF8. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|transactionFlow|Um valor booleano que especifica se a associação oferece suporte a fluxo de transações de WS. O padrão é `false`.|  
|useDefaultWebProxy|Um valor booliano que indica se o proxy HTTP configurado automaticamente do sistema é usado. O endereço de proxy deve ser `null` (ou seja, não definido) se esse atributo for `true`. O padrão é `true`.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsdualhttpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement>.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
|[reliableSession](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|Especifica se as sessões confiáveis são estabelecidas entre pontos de extremidade de canal.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O `WSDualHttpBinding` fornece o mesmo suporte para protocolos de serviço da Web como o `WSHttpBinding`, mas para uso com contratos duplex. `WSDualHttpBinding` só dá suporte à segurança SOAP e requer o sistema de mensagens confiável. Essa associação requer que o cliente tem um URI público que fornece um ponto de extremidade de retorno de chamada para o serviço. Isso é fornecido pelo `clientBaseAddress` atributo. Uma associação dupla expõe o endereço IP do cliente para o serviço. O cliente deve usar a segurança para garantir que ele só se conecta aos serviços-relações de confiança.  
  
 Essa associação pode ser usada para se comunicar com segurança por meio de um ou mais intermediários SOAP.  
  
 Por padrão, essa associação gera uma pilha de tempo de execução com o WS-ReliableMessaging de confiabilidade, WS-Security para segurança de mensagem e autenticação de HTTP para entrega de mensagens e uma codificação de mensagem de texto/XML.  
  
## <a name="example"></a>Exemplo  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsDualHttpBinding>  
    <binding   
        closeTimeout="00:00:10"  
        openTimeout="00:00:20"   
        receiveTimeout="00:00:30"  
        sendTimeout="00:00:40"  
        bypassProxyOnLocal="false"   
        clientBaseAddress="http://localhost:8001/client/"  
        transactionFlow="true"   
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="utf-16"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" />  
        <security mode="None">  
            <message clientCredentialType="None"  
                negotiateServiceCredential="false"  
                algorithmSuite="Aes128" />  
        </security>  
    </binding>  
</wsDualHttpBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.WSDualHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSDualHttpBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
