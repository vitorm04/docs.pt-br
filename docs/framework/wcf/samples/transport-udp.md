---
title: 'Transporte: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 3fd16ccd634b6875eae1e87547c35c6cba79c857
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143766"
---
# <a name="transport-udp"></a>Transporte: UDP
A amostra udp transport demonstra como implementar o UDP unicast e o multicast como um transporte personalizado da Windows Communication Foundation (WCF). A amostra descreve o procedimento recomendado para a criação de um transporte personalizado em WCF, usando a estrutura do canal e seguindo as práticas recomendadas do WCF. As etapas para criar um transporte personalizado são as seguintes:  
  
1. Decida qual dos padrões de troca de [mensagens](#MessageExchangePatterns) do canal (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) o ChannelFactory e o ChannelListener serão suportados. Em seguida, decida se você suportará as variações de sessão dessas interfaces.  
  
2. Crie uma fábrica de canais e ouvinte que suporte seu padrão de troca de mensagens.  
  
3. Certifique-se de que quaisquer exceções específicas da rede <xref:System.ServiceModel.CommunicationException>sejam normalizadas para a classe derivada apropriada de .  
  
4. Adicione [ \<](../../configure-apps/file-schema/wcf/bindings.md) um elemento de>de vinculação que adiciona o transporte personalizado a uma pilha de canais. Para obter mais informações, consulte [Adicionar um elemento de vinculação](#AddingABindingElement).  
  
5. Adicione uma seção de extensão de elemento de vinculação para expor o novo elemento de vinculação ao sistema de configuração.  
  
6. Adicione extensões de metadados para comunicar recursos a outros pontos finais.  
  
7. Adicione uma vinculação que pré-configura uma pilha de elementos de vinculação de acordo com um perfil bem definido. Para obter mais informações, consulte [Adicionar uma vinculação padrão](#AddingAStandardBinding).  
  
8. Adicione uma seção de vinculação e um elemento de configuração de vinculação para expor a vinculação ao sistema de configuração. Para obter mais informações, consulte [Adicionando suporte à configuração](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>
## <a name="message-exchange-patterns"></a>Padrões de troca de mensagens  
 O primeiro passo para escrever um transporte personalizado é decidir quais padrões de troca de mensagens (MEPs) são necessários para o transporte. Há três deputados para escolher:  
  
- Datagrama (IInputChannel/IOutputChannel)  
  
     Ao usar um MEP datagram, um cliente envia uma mensagem usando uma troca de "fogo e esquecimento". Uma troca de fogo e esquecimento é aquela que requer confirmação fora da banda de entrega bem sucedida. A mensagem pode ser perdida no trânsito e nunca chegar ao serviço. Se a operação de envio for concluída com sucesso no final do cliente, não garante que o ponto final remoto tenha recebido a mensagem. O datagrama é um bloco fundamental para mensagens, pois você pode construir seus próprios protocolos em cima dele — incluindo protocolos confiáveis e protocolos seguros. Os canais de <xref:System.ServiceModel.Channels.IOutputChannel> datagrama do cliente implementam os canais de datagrama de interface e serviço para implementar a <xref:System.ServiceModel.Channels.IInputChannel> interface.  
  
- Solicitação-Resposta (IRequestChannel/IReplyChannel)  
  
     Neste MEP, uma mensagem é enviada, e uma resposta é recebida. O padrão consiste em pares de solicitação e resposta. Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e GETs do navegador. Este padrão também é conhecido como Half-Duplex. Neste MEP, os <xref:System.ServiceModel.Channels.IRequestChannel> canais do <xref:System.ServiceModel.Channels.IReplyChannel>cliente implementam e os canais de atendimento implementam.  
  
- Duplex (IDuplexChannel)  
  
     O MEP duplex permite que um número arbitrário de mensagens seja enviada por um cliente e recebida em qualquer ordem. O deputado duplex é como uma conversa telefônica, onde cada palavra sendo falada é uma mensagem. Como ambos os lados podem enviar e receber neste MEP, <xref:System.ServiceModel.Channels.IDuplexChannel>a interface implementada pelo cliente e canais de atendimento é .  
  
 Cada um desses deputados também pode apoiar as sessões. A funcionalidade adicionada fornecida por um canal com reconhecimento de sessão é que correlaciona todas as mensagens enviadas e recebidas em um canal. O padrão Solicitação-Resposta é uma sessão autônoma de duas mensagens, já que a solicitação e a resposta estão correlacionadas. Em contraste, o padrão Solicitação-Resposta que suporta sessões implica que todos os pares de solicitação/resposta nesse canal estão correlacionados entre si. Isso lhe dá um total de seis MEPs — Datagram, Request-Response, Duplex, Datagram com sessões, Request-Response com sessões e Duplex com sessões — para escolher.  
  
> [!NOTE]
> Para o transporte UDP, o único MEP que é suportado é o Datagram, porque o UDP é inerentemente um protocolo de "fogo e esquecimento".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>O ICommunicationObject e o ciclo de vida do objeto WCF  
 O WCF possui uma máquina de estado comum <xref:System.ServiceModel.Channels.IChannel>que <xref:System.ServiceModel.Channels.IChannelFactory>é <xref:System.ServiceModel.Channels.IChannelListener> usada para gerenciar o ciclo de vida de objetos como , e que são usados para comunicação. Há cinco estados em que esses objetos de comunicação podem existir. Esses estados são <xref:System.ServiceModel.CommunicationState> representados pela enumeração, e são os seguintes:  
  
- Criado: Este é o <xref:System.ServiceModel.ICommunicationObject> estado de um quando é instanciado pela primeira vez. Não ocorre entrada/saída (I/O) neste estado.  
  
- Abertura: Objetos transitam <xref:System.ServiceModel.ICommunicationObject.Open%2A> para este estado quando é chamado. Neste ponto, as propriedades são imutáveis, e a entrada/saída pode começar. Esta transição é válida apenas a partir do estado Criado.  
  
- Aberto: Objetos transitam para este estado quando o processo aberto é concluído. Esta transição é válida apenas a partir do estado de abertura. Neste ponto, o objeto é totalmente utilizável para transferência.  
  
- Fechamento: Objetos transitam <xref:System.ServiceModel.ICommunicationObject.Close%2A> para este estado quando é chamado para um desligamento gracioso. Esta transição é válida apenas a partir do estado Aberto.  
  
- Fechado: No estado fechado, os objetos não são mais utilizáveis. Em geral, a maioria das configurações ainda é acessível para inspeção, mas nenhuma comunicação pode ocorrer. Este estado é equivalente a ser eliminado.  
  
- Defeituoso: No estado defeituoso, os objetos são acessíveis à inspeção, mas não podem mais ser utilizáveis. Quando ocorre um erro não recuperável, o objeto transita para este estado. A única transição válida deste `Closed` estado é para o estado.  
  
 Há eventos que disparam para cada transição de estado. O <xref:System.ServiceModel.ICommunicationObject.Abort%2A> método pode ser chamado a qualquer momento, e faz com que o objeto transite imediatamente de seu estado atual para o estado fechado. Ligar <xref:System.ServiceModel.ICommunicationObject.Abort%2A> termina qualquer trabalho inacabado.  
  
<a name="ChannelAndChannelListener"></a>
## <a name="channel-factory-and-channel-listener"></a>Fábrica de Canais e Ouvinte do Canal  
 O próximo passo na elaboração de um <xref:System.ServiceModel.Channels.IChannelFactory> transporte personalizado <xref:System.ServiceModel.Channels.IChannelListener> é criar uma implementação para canais de clientes e de canais de atendimento. A camada do canal usa um padrão de fábrica para a construção de canais. O WCF fornece ajudantes de classe base para este processo.  
  
- A <xref:System.ServiceModel.Channels.CommunicationObject> classe <xref:System.ServiceModel.ICommunicationObject> implementa e impõe a máquina estatal descrita anteriormente na Etapa 2.

- A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe <xref:System.ServiceModel.Channels.CommunicationObject> implementa e fornece <xref:System.ServiceModel.Channels.ChannelFactoryBase> uma <xref:System.ServiceModel.Channels.ChannelListenerBase>classe de base unificada para e . A <xref:System.ServiceModel.Channels.ChannelManagerBase> classe trabalha <xref:System.ServiceModel.Channels.ChannelBase>em conjunto com , que <xref:System.ServiceModel.Channels.IChannel>é uma classe de base que implementa .  
  
- A <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe <xref:System.ServiceModel.Channels.ChannelManagerBase> implementa e <xref:System.ServiceModel.Channels.IChannelFactory> `CreateChannel` consolida as `OnCreateChannel` sobrecargas em um método abstrato.  
  
- A <xref:System.ServiceModel.Channels.ChannelListenerBase> classe <xref:System.ServiceModel.Channels.IChannelListener>implementa. Cuida da gestão básica do Estado.  
  
 Nesta amostra, a implementação da fábrica está contida em UdpChannelFactory.cs e a implementação do ouvinte está contida em UdpChannelListener.cs. As <xref:System.ServiceModel.Channels.IChannel> implementações estão em UdpOutputChannel.cs e UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>A Fábrica de Canais UDP  
 O `UdpChannelFactory` derivado <xref:System.ServiceModel.Channels.ChannelFactoryBase>de . A amostra <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> substitui-se para fornecer acesso à versão da mensagem do codificador de mensagens. A amostra também <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> se sobrepõe para que <xref:System.ServiceModel.Channels.BufferManager> possamos derrubar nossa instância de quando a máquina de estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída do UDP  
 Os `UdpOutputChannel` implementos. <xref:System.ServiceModel.Channels.IOutputChannel> O construtor valida os argumentos e <xref:System.Net.EndPoint> constrói um <xref:System.ServiceModel.EndpointAddress> objeto de destino com base no que é passado.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 O canal pode ser fechado graciosamente ou sem graça. Se o canal estiver fechado graciosamente, o soquete `OnClose` é fechado e uma chamada é feita para o método de classe base. Se isso abrir uma exceção, a infra-estrutura liga `Abort` para garantir que o canal seja limpo.  
  
```csharp
this.socket.Close(0);  
```  
  
 Em seguida, `BeginSend()` / `EndSend()`implementamos `Send()` e . Isso se divide em duas seções principais. Primeiro serializamos a mensagem em uma matriz de bytes.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, enviamos os dados resultantes no fio.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>O UdpChannelListener  
 O `UdpChannelListener` que a amostra implementa <xref:System.ServiceModel.Channels.ChannelListenerBase> deriva da classe. Ele usa um único soquete UDP para receber datagramas. O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono. Os dados são então convertidos em mensagens usando o Quadro de Codificação de Mensagens.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Como o mesmo canal de datagrama representa mensagens que `UdpChannelListener` chegam de várias fontes, o é um ouvinte singleton. Há, no máximo, <xref:System.ServiceModel.Channels.IChannel> um ativo associado a este ouvinte de cada vez. A amostra só gera outra se um canal `AcceptChannel` que é devolvido pelo método for posteriormente eliminado. Quando uma mensagem é recebida, ela é enfileirada neste canal singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 A `UdpInputChannel` classe `IInputChannel`implementa. Consiste em uma fila de mensagens recebidas que `UdpChannelListener`é preenchida pelo soquete. Essas mensagens são enfileiradas `IInputChannel.Receive` pelo método.  
  
<a name="AddingABindingElement"></a>
## <a name="adding-a-binding-element"></a>Adicionando um elemento de vinculação  
 Agora que as fábricas e canais foram construídos, devemos expô-los ao tempo de execução serviceModel através de uma vinculação. Uma vinculação é uma coleção de elementos de ligação que representa a pilha de comunicação associada a um endereço de serviço. Cada elemento na pilha é [ \<](../../configure-apps/file-schema/wcf/bindings.md) representado por um elemento de>de ligação.  
  
 Na amostra, o elemento `UdpTransportBindingElement`de ligação <xref:System.ServiceModel.Channels.TransportBindingElement>é , que deriva de . Ele substitui os seguintes métodos para construir as fábricas associadas à nossa ligação.  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 Ele também contém membros `BindingElement` para clonagem e devolução do nosso esquema (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Adicionando suporte a metadados para um elemento de vinculação de transporte  
 Para integrar nosso transporte ao sistema de metadados, devemos apoiar tanto a importação quanto a exportação da política. Isso nos permite gerar clientes de nossa vinculação através da [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Adicionando suporte ao WSDL  
 O elemento de vinculação de transporte em uma vinculação é responsável pela exportação e importação de informações de endereçamento em metadados. Ao usar uma vinculação SOAP, o elemento de ligação de transporte também deve exportar um URI de transporte correto em metadados.  
  
#### <a name="wsdl-export"></a>Exportação wsdl  
 Para exportar informações `UdpTransportBindingElement` endereçadas, implementa a `IWsdlExportExtension` interface. O `ExportEndpoint` método adiciona as informações corretas de endereçamento à porta WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 A `UdpTransportBindingElement` implementação `ExportEndpoint` do método também exporta um URI de transporte quando o ponto final usa uma vinculação SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importação de WSDL  
 Para estender o sistema de importação WSDL para lidar com a importação dos endereços, devemos adicionar a seguinte configuração ao arquivo de configuração para Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Ao executar o Svcutil.exe, existem duas opções para obter Svcutil.exe para carregar as extensões de importação WSDL:  
  
1. Point Svcutil.exe para o nosso arquivo de configuração\<usando o /SvcutilConfig: arquivo>.  
  
2. Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.  
  
 O `UdpBindingElementImporter` tipo implementa a `IWsdlImportExtension` interface. O `ImportEndpoint` método importa o endereço da porta WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Adicionando suporte a políticas  
 O elemento de vinculação personalizado pode exportar afirmações de diretiva na vinculação WSDL para um ponto final de serviço para expressar as capacidades desse elemento de vinculação.  
  
#### <a name="policy-export"></a>Exportação de políticas  
 O `UdpTransportBindingElement` tipo `IPolicyExportExtension` implementa para adicionar suporte à política de exportação. Como resultado, `System.ServiceModel.MetadataExporter` inclui `UdpTransportBindingElement` na geração de políticas para qualquer vinculação que a inclua.  
  
 Em `IPolicyExportExtension.ExportPolicy`, adicionamos uma afirmação para UDP e outra afirmação se estivermos no modo multicast. Isso porque o modo multicast afeta a forma como a pilha de comunicação é construída e, portanto, deve ser coordenada entre ambos os lados.  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix,
        UdpPolicyStrings.MulticastAssertion,
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 Como os elementos de vinculação de `IPolicyExportExtension` transporte personalizados são responsáveis pelo manuseio da abordagem, a implementação no também `UdpTransportBindingElement` deve lidar com a exportação das afirmações apropriadas da política ws-addressing para indicar a versão do WS-Addressing a ser usado.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importação de políticas  
 Para estender o sistema de importação de políticas, devemos adicionar a seguinte configuração ao arquivo de configuração de Svcutil.exe, conforme mostrado no arquivo Svcutil.exe.config.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Então implementamos `IPolicyImporterExtension` a partir`UdpBindingElementImporter`de nossa classe registrada ( ). Em `ImportPolicy()`, nós olhamos através das afirmações em nosso namespace, e processar os para gerar o transporte e verificar se ele é multicast. Também devemos remover as afirmações que lidamos da lista de afirmações vinculantes. Novamente, ao executar o Svcutil.exe, há duas opções de integração:  
  
1. Point Svcutil.exe para o nosso arquivo de configuração\<usando o /SvcutilConfig: arquivo>.  
  
2. Adicione a seção de configuração ao Svcutil.exe.config no mesmo diretório que Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>
## <a name="adding-a-standard-binding"></a>Adicionando uma vinculação padrão  
 Nosso elemento de ligação pode ser usado das seguintes maneiras:  
  
- Através de uma vinculação personalizada: uma vinculação personalizada permite que o usuário crie sua própria vinculação com base em um conjunto arbitrário de elementos de vinculação.  
  
- Usando uma vinculação fornecida pelo sistema que inclui nosso elemento de vinculação. O WCF fornece uma série dessas ligações `BasicHttpBinding`definidas pelo sistema, tais como , `NetTcpBinding`e `WsHttpBinding`. Cada uma dessas ligações está associada a um perfil bem definido.  
  
 A amostra implementa `SampleProfileUdpBinding`a vinculação <xref:System.ServiceModel.Channels.Binding>do perfil em , que deriva de . O `SampleProfileUdpBinding` contém até quatro elementos `UdpTransportBindingElement` `TextMessageEncodingBindingElement CompositeDuplexBindingElement`de `ReliableSessionBindingElement`ligação dentro dele: , e .  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a>Adicionando um importador de vinculação padrão personalizado  
 Svcutil.exe e `WsdlImporter` o tipo, por padrão, reconhece e importa vinculações definidas pelo sistema. Caso contrário, a vinculação `CustomBinding` é importada como instância. Para habilitar svcutil.exe e `SampleProfileUdpBinding` `UdpBindingElementImporter` `WsdlImporter` importar o também atua como um importador de vinculação padrão personalizado.  
  
 Um importador de vinculação `ImportEndpoint` padrão `IWsdlImportExtension` personalizado implementa `CustomBinding` o método na interface para examinar a instância importada de metadados para ver se ele poderia ter sido gerado por uma vinculação padrão específica.  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 Geralmente, a implementação de um importador de vinculação padrão personalizado envolve verificar as propriedades dos elementos de ligação importados para verificar se apenas as propriedades que poderiam ter sido definidas pela vinculação padrão foram alteradas e todas as outras propriedades são seus padrões. Uma estratégia básica para implementar um importador de vinculação padrão é criar uma instância da vinculação padrão, propagar as propriedades dos elementos vinculantes à instância de vinculação padrão que a vinculação padrão suporta, e comparar a vinculação elementos da vinculação padrão com os elementos de ligação importados.  
  
<a name="AddingConfigurationSupport"></a>
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para expor nosso transporte através da configuração, devemos implementar duas seções de configuração. O primeiro `BindingElementExtensionElement` é `UdpTransportBindingElement`um para. Isso é para `CustomBinding` que as implementações possam referenciar nosso elemento de vinculação. O segundo `Configuration` é `SampleProfileUdpBinding`um para o nosso.  
  
### <a name="binding-element-extension-element"></a>Elemento de extensão do elemento de vinculação  
 A `UdpTransportElement` seção `BindingElementExtensionElement` é `UdpTransportBindingElement` uma que se expõe ao sistema de configuração. Com algumas substituições básicas, definimos nosso nome da seção de configuração, o tipo de nosso elemento de vinculação e como criar nosso elemento de vinculação. Podemos então registrar nossa seção de extensão em um arquivo de configuração, conforme mostrado no código a seguir.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 A extensão pode ser referenciada a partir de vinculações personalizadas para usar UDP como transporte.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a>Seção de Vinculação  
 A `SampleProfileUdpBindingCollectionElement` seção `StandardBindingCollectionElement` é `SampleProfileUdpBinding` uma que se expõe ao sistema de configuração. A maior parte da implementação `SampleProfileUdpBindingConfigurationElement`é delegada `StandardBindingElement`ao , que deriva de . O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding` `ConfigurationElement` , e funções para mapear a partir da vinculação. Por fim, `OnApplyConfiguration` anular o `SampleProfileUdpBinding`método em nosso , como mostrado no código de amostra a seguir.  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 Para registrar este manipulador com o sistema de configuração, adicionamos a seguinte seção ao arquivo de configuração relevante.  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 Em seguida, ele pode ser referenciado a partir da seção de configuração serviceModel.  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a>O serviço de teste e o cliente do UDP  
 O código de teste para o uso deste transporte de amostras está disponível nos diretórios UdpTestService e UdpTestClient. O código de serviço consiste em dois testes — um teste configura vinculações e pontos finais a partir do código e o outro o faz através da configuração. Ambos os testes usam dois pontos finais. Um ponto final `SampleUdpProfileBinding` usa o conjunto `true`de>de Sessão [ \<confiável](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido para . O outro ponto final usa `UdpTransportBindingElement`uma vinculação personalizada com . Isso equivale ao `SampleUdpProfileBinding` uso com [ \<>de sessão confiável](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido para `false`. Ambos os testes criam um serviço, adicionam um ponto final para cada vinculação, abrem o serviço e esperam que o usuário acerte ENTER antes de fechar o serviço.  
  
 Ao iniciar o aplicativo de teste de serviço, você deve ver a seguinte saída.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Em seguida, você pode executar o aplicativo cliente de teste contra os pontos finais publicados. O aplicativo de teste do cliente cria um cliente para cada ponto final e envia cinco mensagens para cada ponto final. A seguinte saída está no cliente.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 A seguir está a saída completa do serviço.  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 Para executar o aplicativo cliente contra pontos finais publicados usando a configuração, clique em ENTER no serviço e, em seguida, execute o cliente de teste novamente. Você deve ver a seguinte saída no serviço.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Executar o cliente novamente rende o mesmo que os resultados anteriores.  
  
 Para regenerar o código e a configuração do cliente usando o Svcutil.exe, inicie o aplicativo de serviço e execute o seguinte Svcutil.exe a partir do diretório raiz da amostra.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Observe que o Svcutil.exe não gera `SampleProfileUdpBinding`a configuração de extensão de vinculação para o , portanto, você deve adicioná-lo manualmente.  
  
```xml
<configuration>  
  <system.serviceModel>
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Consulte a seção anterior "O Serviço de Teste e cliente udp".  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
