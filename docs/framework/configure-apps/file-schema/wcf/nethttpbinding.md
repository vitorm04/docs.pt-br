---
title: <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: b0d81ca0-87c5-4090-8baa-e390fd3656d2
ms.openlocfilehash: ff589c502333851de4dcf23101bb14fac767d25d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933080"
---
# <a name="nethttpbinding"></a>\<netHttpBinding>
Representa uma associação que um serviço Windows Communication Foundation (WCF) pode usar para configurar e expor pontos de extremidade que são capazes de se comunicar via HTTP. Quando usado com um contrato duplex, os Web Sockets serão usados; caso contrário, HTTP será usado.  
  
 \<system.ServiceModel>  
\<bindings>  
\<netHttpBinding>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<netHttpBinding>
  <binding allowCookies="Boolean"
           bypassProxyOnLocal="Boolean"
           closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxReceivedMessageSize="Integer"
           messageEncoding="Binary/Text/Mtom"
           name="String"
           openTimeout="TimeSpan"
           proxyAddress="URI"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/Utf8TextEncoding"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"
           useDefaultWebProxy="Boolean">
    <security mode="None/Transport/Message/TransportWithMessageCredential/TransportCredentialOnly">
      <transport clientCredentialType="None/Basic/Digest/Ntlm/Windows/Certificate"
                 proxyCredentialType="None/Basic/Digest/Ntlm/Windows"
                 realm="string" />
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="UserName/Certificate" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
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
|`allowCookies`|Um valor booliano que indica se o cliente aceita cookies e os propaga em solicitações futuras. O padrão é `false`.<br /><br /> Você pode usar essa propriedade ao interagir com serviços Web ASMX que usam cookies. Dessa forma, você pode ter certeza de que os cookies retornados do servidor são copiados automaticamente para todas as solicitações de cliente futuras para esse serviço.|  
|`bypassProxyOnLocal`|Um valor booliano que indica se deve ignorar o servidor proxy para endereços locais. O padrão é `false`.<br /><br /> Um recurso da Internet será local se ele tiver um endereço local. Um endereço local é aquele que está no mesmo computador, o local LAN ou da intranet e é identificado, sintaticamente, pela falta de um ponto (.) como os URIs "http://webserver/" e "http://localhost/".<br /><br /> Definir esse atributo determina se os pontos de extremidade configurados com o BasicHttpBinding usam o servidor proxy ao acessar recursos locais. Se esse atributo for `true`, as solicitações para os recursos locais da Internet não usarão o servidor proxy. Use o nome do host (em vez de localhost) se desejar que os clientes passem por um proxy ao se comunicar com os serviços no mesmo computador quando esse `true`atributo for definido como.<br /><br /> Quando esse atributo é `false`, todas as solicitações da Internet são feitas por meio do servidor proxy.|  
|`closeTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de fechamento. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`hostNameComparisonMode`|Especifica o modo de comparação de nome de host HTTP usado para analisar URIs. Esse atributo é do tipo <xref:System.ServiceModel.HostNameComparisonMode>, que indica se o nome do host é usado para acessar o serviço ao corresponder ao URI. O valor padrão é <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, que ignora o nome do host na correspondência.|  
|`maxBufferPoolSize`|Um valor inteiro que especifica a quantidade máxima de memória alocada para uso pelo Gerenciador dos buffers de mensagens que recebem mensagens do canal. O valor padrão é 524288 (0x80000) bytes.<br /><br /> O Gerenciador de buffer minimiza o custo do uso de buffers usando um pool de buffers. Os buffers são necessários para processar mensagens pelo serviço quando elas saem do canal. Se não houver memória suficiente no pool de buffers para processar a carga de mensagens, o Gerenciador de buffer deverá alocar memória adicional do heap do CLR, o que aumenta a sobrecarga da coleta de lixo. A alocação extensiva do heap de lixo do CLR é uma indicação de que o tamanho do pool de buffers é muito pequeno e que o desempenho pode ser melhorado com uma alocação maior aumentando o limite especificado por esse atributo.|  
|`maxBufferSize`|Um valor inteiro que especifica o tamanho máximo, em bytes, de um buffer que armazena mensagens enquanto elas são processadas para um ponto de extremidade configurado com essa associação. O valor padrão é 65.536 bytes.|  
|`maxReceivedMessageSize`|Um inteiro positivo que define o tamanho máximo da mensagem, em bytes, incluindo cabeçalhos, para uma mensagem que pode ser recebida em um canal configurado com essa associação. O remetente receberá uma falha de SOAP se a mensagem for muito grande para o destinatário. O receptor remove a mensagem e cria uma entrada do evento no log de rastreamento. O padrão é 65.536 bytes.|  
|`messageEncoding`|Define o codificador usado para codificar a mensagem SOAP. Os valores válidos incluem o seguinte:<br /><br /> Texto Use um codificador de mensagem de texto.<br />MTOM Use um codificador MTOM (mecanismo de organização de transmissão de mensagens 1,0).<br /><br /> O padrão é texto. Esse atributo é do tipo <xref:System.ServiceModel.WSMessageEncoding>.|  
|`name`|Uma cadeia de caracteres que contém o nome da configuração da associação. Esse valor deve ser exclusivo porque é usado como uma identificação para a associação. Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço. Além disso, esse nome é exclusivo entre associações do mesmo tipo. A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).|  
|`namespace`|Especifica o namespace XML da associação. O valor padrão é "http://tempuri.org/Bindings". Cada associação tem um `name` atributo `namespace` e que, juntos, o identifica exclusivamente nos metadados do serviço.|  
|`openTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de abertura. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`proxyAddress`|Um URI que contém o endereço do proxy HTTP. Se `useSystemWebProxy` é definido como `true`, essa configuração deve ser `null`. O padrão é `null`.|  
|`receiveTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de recebimento. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:10:00.|  
|`sendTimeout`|Um <xref:System.TimeSpan> valor que especifica o intervalo de tempo fornecido para a conclusão de uma operação de envio. Esse valor deve ser maior ou igual a <xref:System.TimeSpan.Zero>. O padrão é 00:01:00.|  
|`textEncoding`|Define a codificação do conjunto de caracteres a ser usada para emitir mensagens na associação. Os valores válidos incluem o seguinte:<br /><br /> BigEndianUnicode Codificação BigEndian Unicode.<br />Unicode codificação de 16 bits.<br />UTF8 codificação de 8 bits<br /><br /> O padrão é UTF8. Esse atributo é do tipo <xref:System.Text.Encoding>.|  
|`transferMode`|Um valor <xref:System.ServiceModel.TransferMode> válido que especifica se as mensagens são armazenadas em buffer ou transmitidas em uma solicitação ou resposta.|  
|`useDefaultWebProxy`|Um valor booliano que especifica se o proxy HTTP configurado automaticamente do sistema deve ser usado, se disponível. O padrão é `true`.|  
|||  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|Define as configurações de segurança para a associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>.|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|Define as restrições sobre a complexidade de mensagens SOAP que podem ser processadas por pontos de extremidade configurados com essa associação. Esse elemento é do tipo <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|Esse elemento contém uma coleção de associações padrão e personalizadas.|  
  
## <a name="remarks"></a>Comentários  
 O NetHttpBinding usa HTTP como o transporte para enviar mensagens. Quando usado com um contrato duplex, os Web Sockets serão usados.  Quando usado com um contrato de solicitação-resposta, NetHttpBinding se comportará como um BasicHttpBinding com um codificador binário.  
  
 A segurança é desativada por padrão, mas pode ser adicionada, definindo o atributo mode do `None` [ \<elemento filho Security >](security-of-basichttpbinding.md) como um valor diferente de. Ele usa uma codificação de mensagem "texto" e codificação de texto UTF-8 por padrão.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso <xref:System.ServiceModel.NetHttpBinding> do que fornece comunicação http e a interoperabilidade máxima com serviços da Web de primeira e segunda geração. A associação é especificada nos arquivos de configuração para o cliente e o serviço. O tipo de associação é especificado usando `binding` o atributo `<endpoint>` do elemento. Se você quiser configurar a ligação básica e alterar algumas de suas configurações, será necessário definir uma configuração de associação. O ponto de extremidade deve referenciar a configuração de associação por `bindingConfiguration` nome usando o `<endpoint>` atributo do elemento, conforme mostrado no código de configuração a seguir para o serviço.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
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
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
## <a name="example"></a>Exemplo  
 A partir do, não é necessário que as associações e os comportamentos tenham um nome. [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] A funcionalidade do exemplo anterior pode ser realizada removendo o bindingConfiguration do endereço do ponto de extremidade e o nome da associação.  
  
```xml  
<system.serviceModel>
  <services>
    <service type="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <endpoint address=""
                binding="netHttpBinding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>
  <bindings>
    <netHttpBinding>
      <binding hostNameComparisonMode="StrongWildcard"
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
               useDefaultWebProxy="true">
        <security mode="None" />
      </binding>
    </netHttpBinding>
  </bindings>
</system.serviceModel>
```  
  
 Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.Configuration.BasicHttpBindingElement>
- [Associações](../../../wcf/bindings.md)
- [Configurando associações fornecidas pelo sistema](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Usando associações para configurar serviços e clientes](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
