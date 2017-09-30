---
title: '&lt;basicHttpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- basicHttpBinding Element
ms.assetid: 85cf1a4f-26c2-48c7-bda6-6c960d5d3fb3
caps.latest.revision: 43
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1551802b3d946de7b1198244ab9d7056e3e74e78
ms.contentlocale: pt-br
ms.lasthandoff: 09/25/2017

---
# <a name="ltbasichttpbindinggt"></a>&lt;basicHttpBinding&gt;
Representa uma associação que um serviço [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] pode usar para configurar e expor pontos de extremidade que podem se comunicar com serviços e clientes Web baseados em ASMX e outros serviços que estão em conformidade com o WS-I Basic Profile 1.1.  
  
 \<sistema. ServiceModel >  
\<associações >  
\<basicHttpBinding >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<basicHttpBinding>  
   <binding   
       allowCookies="Boolean"  
       bypassProxyOnLocal="Boolean"  
       closeTimeout="TimeSpan"   
       envelopeVersion="None/Soap11/Soap12"  
       hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
       maxBufferPoolSize="Integer"  
       maxBufferSize="Integer"  
       maxReceivedMessageSize="Integer"  
       messageEncoding="Text/Mtom"  
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
</basicHttpBinding>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`allowCookies`|Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras. O padrão é `false`.<br /><br /> Você pode usar essa propriedade quando você interage com os serviços Web ASMX que usam cookies. Dessa forma, você poderá ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras desse serviço.|  
|`bypassProxyOnLocal`|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.<br /><br /> Um recurso de Internet é local se ele tem um endereço local. Um endereço local é aquele que está no mesmo computador, a rede local ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como no URIs "http://webserver/" e "http://localhost/".<br /><br /> Definir este atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais. Se esse atributo for `true`, solicitações aos recursos da Internet locais não usar o servidor proxy. Use o nome do host (em vez de localhost) se desejar que os clientes para passar por um proxy ao conversar com serviços no mesmo computador, quando esse atributo é definido como `true`.<br /><br /> Quando esse atributo é `false`, todas as solicitações de Internet são feitas por meio do servidor proxy.|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para uma operação de fechamento concluir. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`envelopeVersion`|Especifica a versão do SOAP que é usado para as mensagens processadas por essa associação. O único valor válido é Soap11.|  
|`hostnameComparisonMode`|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
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
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas >](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|Define as restrições na complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associações >](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O BasicHttpBinding usa HTTP como o transporte para enviar mensagens de SOAP 1.1. Um serviço pode usar essa associação para expor pontos de extremidade que está de acordo com WS-I BP 1.1, como aqueles que clientes ASMX consumam. Da mesma forma, um cliente pode usar o BasicHttpBinding para se comunicar com serviços expor pontos de extremidade que está de acordo com WS-I BP 1.1, como serviços Web ASMX ou serviços configurados com o BasicHttpBinding.  
  
 A segurança é desativada por padrão, mas podem ser adicionada, definindo o atributo de modo do [ \<segurança >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) elemento filho com um valor diferente de `None`. Ele usa um "Texto" mensagem codificação e UTF-8 codificação de texto por padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso de <xref:System.ServiceModel.BasicHttpBinding> que fornece interoperabilidade de comunicação e o máximo HTTP com o primeiro - e second - generation serviços da Web. A associação é especificada nos arquivos de configuração do cliente e do serviço. O tipo de associação é especificado usando o `binding` atributo o `<endpoint>` elemento. Se você quiser configurar a associação básica e alterar algumas de suas configurações, é necessário definir uma configuração de associação. O ponto de extremidade deve fazer referência a configuração de associação por nome usando o `bindingConfiguration` atributo o `<endpoint>` elemento, conforme mostrado no código de configuração a seguir para o serviço.  
  
```xml  
<system.serviceModel>   
  <services>  
    <service   
        type="Microsoft.ServiceModel.Samples.CalculatorService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
       <endpoint address=""  
             binding="basicHttpBinding"  
             bindingConfiguration="Binding1"   
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
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
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
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
             binding="basicHttpBinding"  
             contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  <bindings>  
     <basicHttpBinding>  
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
               messageEncoding="Text"   
               textEncoding="utf-8"  
               bypassProxyOnLocal="false"  
               useDefaultWebProxy="true" >  
              <security mode="None" />  
         </binding>  
     </basicHttpBinding>  
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
 [Usando associações para configurar clientes e serviços do Windows Communication Foundation](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)   
 [\<associação >](../../../../../docs/framework/misc/binding.md)

