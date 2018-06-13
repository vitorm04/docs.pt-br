---
title: '&lt;netHttpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: f6d3085ce999caad7e605341ecdb6d7099da3590
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751916"
---
# <a name="ltnethttpbindinggt"></a>&lt;netHttpBinding&gt;
Representa uma associação que um serviço do Windows Communication Foundation (WCF) pode usar para configurar e expor pontos de extremidade que podem se comunicar por HTTP. Quando usado com um contrato duplex, soquetes da Web será usado, caso contrário, o HTTP será usado.  
  
 \<system.ServiceModel>  
\<associações >  
\<netHttpBinding>  
  
## <a name="syntax"></a>Sintaxe  

```xml  
<netHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Binary/Text/Mtom"  
       name="string"   
       openTimeout="TimeSpan"   
       proxyAddress="URI"  
        receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan"  
              textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"  
              transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
       useDefaultWebProxy="Boolean"  
       <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">  
           <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"  
                  proxyCredentialType="None/Basic/Digest/Ntlm/Windows"  
                                    realm="string" />  
           <message   
                 algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
                            clientCredentialType="UserName/Certificate"/>  
       </security>  
       <readerQuotas   
            maxArrayLength="Integer"  
            maxBytesPerRead="Integer"  
            maxDepth="Integer"             maxNameTableCharCount="Integer"                maxStringContentLength="Integer" />  
   </binding>  
</netHttpBinding>  
```  
  
## <a name="type"></a>Tipo  
 `Type`  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowCookies`|Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras. O padrão é `false`.<br /><br /> Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies. Dessa forma, você poderá ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras desse serviço.|  
|`bypassProxyOnLocal`|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.<br /><br /> Um recurso de Internet é local se ele tem um endereço local. Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/"e"http://localhost/".<br /><br /> Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais. Se esse atributo for `true`, solicitações aos recursos da Internet locais não usar o servidor proxy. Use o nome do host (em vez de localhost) se desejar que os clientes para passar por um proxy ao conversar com serviços no mesmo computador, quando esse atributo é definido como `true`.<br /><br /> Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`hostnameComparisonMode`|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo `System.ServiceModel.HostnameComparisonMode`, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é `StrongWildcard`>, que ignora o nome do host na correspondência.|  
|`maxBufferPoolSize`|Um valor inteiro que especifica a quantidade máxima de memória que é alocada para uso pelo Gerenciador dos buffers de mensagem que recebem mensagens do canal. O valor padrão é 524288 (0x80000) bytes.<br /><br /> O Gerenciador de Buffer minimiza o custo do uso de buffers usando um pool de buffers. Buffers são necessários para processar mensagens pelo serviço quando estiverem fora do canal. Se não houver memória suficiente no pool de buffers para processar a carga da mensagem, o Gerenciador de Buffer deve alocar mais memória do heap CLR, o que aumenta a sobrecarga de coleta de lixo. Ampla alocação do heap de lixo CLR é uma indicação de que o tamanho do pool de buffer é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por este atributo.|  
|`maxBufferSize`|Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto eles são processados para um ponto de extremidade configurado com essa associação. O valor padrão é 65.536 bytes.|  
|`maxReceivedMessageSize`|Um inteiro positivo que define o tamanho máximo, em bytes, incluindo os cabeçalhos de uma mensagem que pode ser recebido em um canal configurado com essa associação. O remetente recebe uma falha de SOAP se a mensagem é muito grande para o receptor. O receptor descartará a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65.536 bytes.|  
|`messageEncoding`|Define o codificador usado para codificar a mensagem SOAP. Os valores válidos incluem o seguinte:<br /><br /> -Texto: Use um codificador de mensagem de texto.<br />-Mtom: Use um codificador de mensagem transmissão organização mecanismo 1.0 (MTOM).<br /><br /> O padrão é texto. Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo, porque ele é usado como uma identificação para a associação. Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço. Além disso, esse nome é exclusivo entre as associações do mesmo tipo. Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Especifica o namespace XML da associação. O valor padrão é "http://tempuri.org/Bindings". Cada associação tem um `name` e `namespace` de atributo que juntos exclusivamente identificá-lo nos metadados do serviço.|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de abertura concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`proxyAddress`|Um URI que contém o endereço do proxy HTTP. Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de recebimento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de envio concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`textEncoding`|Define a codificação a ser usada para emitir mensagens na associação de conjunto de caracteres. Os valores válidos incluem o seguinte:<br /><br /> -BigEndianUnicode: O Unicode BigEndian codificação.<br />-Unicode: codificação de 16 bits.<br />-UTF8: codificação de 8 bits<br /><br /> O padrão é UTF8. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|`transferMode`|Uma opção válida <xref:System.ServiceModel.TransferMode> valor que especifica se as mensagens são armazenados em buffer ou transmitidas em uma solicitação ou resposta.|  
|`useDefaultWebProxy`|Um valor booleano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível. O padrão é `true`.|  
|||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo `NetHttpSecurityElement`.|  
|[\<readerQuotas>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O NetHttpBinding usa HTTP como o transporte para enviar mensagens. Quando usado com um contrato duplex, soquetes da Web será usado.  Quando usado com um contrato de solicitação-resposta que NetHttpBinding irão se comportar como BasicHttpBinding com um codificador binário.  
  
 A segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho com um valor diferente de `None`. Ele usa um "Texto" mensagem codificação e UTF-8 codificação de texto por padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.NetHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTP com o primeiro - e second - generation serviços da Web. A associação é especificada nos arquivos de configuração do cliente e do serviço. O tipo de associação é especificado usando o `binding` atributo o `<endpoint>` elemento. Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação. O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo o `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
        <binding name="Binding1"   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
## <a name="example"></a>Exemplo  
 Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome. A funcionalidade do exemplo anterior pode ser feita, removendo o bindingConfiguration do endereço do ponto de extremidade e o gerenciamento de registros agrupados nome a associação.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="netHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <netHttpBinding>  
        <binding   
               hostNameComparisonMode="StrongWildcard"   
               receiveTimeout="00:10:00"  
               sendTimeout="00:10:00"  
               openTimeout="00:10:00"  
               closeTimeout="00:10:00"  
               maxReceivedMessageSize="65536"   
               maxBufferSize="65536"   
               maxBufferPoolSize="524288"   
               transferMode="Buffered"   
               messageEncoding="Binary"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </netHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>  
 [Associações](../../../../../docs/framework/wcf/bindings.md)  
 [Configurando associações fornecidas pelo sistema](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<associação >](../../../../../docs/framework/misc/binding.md)
