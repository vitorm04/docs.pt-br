---
title: 'Transporte: UDP'
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 8d72ab5c7d8c461cd2ce4d4003d449ac9fe7e807
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62007715"
---
# <a name="transport-udp"></a>Transporte: UDP
O exemplo de transporte UDP demonstra como implementar UDP unicast e multicast como um transporte personalizado do Windows Communication Foundation (WCF). O exemplo descreve o procedimento recomendado para a criação de um transporte personalizado no WCF, usando a estrutura de canais e seguir as práticas recomendadas do WCF. As etapas para criar um transporte personalizado são da seguinte maneira:  
  
1. Decida qual do canal [padrões de troca de mensagem](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) seus ChannelFactory e ChannelListener dará suporte. Em seguida, decida se você oferece suporte as sessão variações dessas interfaces.  
  
2. Crie uma fábrica de canais e um ouvinte que dão suporte ao padrão de troca de mensagem.  
  
3. Certifique-se de que todas as exceções específicas de rede são normalizadas para a classe derivada apropriada de <xref:System.ServiceModel.CommunicationException>.  
  
4. Adicionar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento que adiciona o transporte personalizado a uma pilha de canais. Para obter mais informações, consulte [adicionando um elemento de associação](#AddingABindingElement).  
  
5. Adicione uma seção de extensão de elemento de associação para expor o novo elemento de associação para o sistema de configuração.  
  
6. Adicione extensões de metadados para recursos para outros pontos de extremidade de comunicação.  
  
7. Adicione uma associação que pré-configura uma pilha de elementos de associação de acordo com um perfil bem definido. Para obter mais informações, consulte [adicionando uma associação padrão](#AddingAStandardBinding).  
  
8. Adicione uma seção de associação e o elemento de configuração de associação para expor a associação para o sistema de configuração. Para obter mais informações, consulte [adicionando o suporte à configuração](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem  
 A primeira etapa ao escrever um transporte personalizado é decidir quais padrões de troca de mensagens (MEPs) são necessários para o transporte. Há três MEPs à sua escolha:  
  
- Datagrama (IInputChannel/IOutputChannel)  
  
     Ao usar um datagrama MEP, um cliente envia uma mensagem usando uma troca de "disparar e esquecer". A disparar e esquecer exchange é aquela que requer a confirmação de out-of-band de entrega bem-sucedida. A mensagem poderá ser perdida em trânsito e nunca alcançar o serviço. Se a operação de envio for concluído com êxito no lado do cliente, ele não garante que o ponto de extremidade remoto recebeu a mensagem. O datagrama é um bloco de construção fundamental para mensagens, como você pode criar seus próprios protocolos nela — incluindo protocolos confiáveis e segura. Implementam canais de datagrama de cliente a <xref:System.ServiceModel.Channels.IOutputChannel> canais de datagrama de interface e o serviço de implementam o <xref:System.ServiceModel.Channels.IInputChannel> interface.  
  
- Solicitação-resposta (IRequestChannel/IReplyChannel)  
  
     Neste MEP, uma mensagem é enviada e uma resposta é recebida. O padrão consiste em pares de solicitação-resposta. Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e o navegador obtém. Esse padrão também é conhecido como Half-Duplex. Este MEP, canais de cliente implementam <xref:System.ServiceModel.Channels.IRequestChannel> e implementam canais de serviço <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
- Duplex (IDuplexChannel)  
  
     O MEP duplex permite que um número arbitrário de mensagens a serem enviadas por um cliente e recebidos em qualquer ordem. O MEP duplex é como uma conversa de telefone, em que cada palavra que está sendo falada é uma mensagem. Porque ambos os lados podem enviar e receber essa MEP, a interface implementada por canais de cliente e o serviço é <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Cada uma dessas MEPs também pode dar suporte a sessões. A funcionalidade adicional fornecida por um canal de reconhecimento de sessão é que ele se correlaciona a todas as mensagens enviadas e recebidas em um canal. O padrão de solicitação-resposta é uma sessão de duas mensagens autônoma, como a solicitação e resposta são correlacionadas. Em contraste, o padrão de solicitação-resposta que dá suporte a sessões implica que todos os pares de solicitação/resposta naquele canal estão correlacionados entre si. Isso lhe dá um total de seis MEPs — datagrama, solicitação-resposta, Duplex, datagrama com sessões de solicitação-resposta com sessões e Duplex com sessões — à sua escolha.  
  
> [!NOTE]
>  Para o transporte UDP, o MEP única com suporte é datagrama, porque o UDP é inerentemente um protocolo de "disparar e esquecer".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Ciclo de vida do objeto de ICommunicationObject e o WCF  
 O WCF possui uma máquina de estado comum que é usada para gerenciar o ciclo de vida de objetos, como <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, e <xref:System.ServiceModel.Channels.IChannelListener> que são usados para comunicação. Há cinco estados em que esses objetos de comunicação podem existir. Esses estados são representados pelo <xref:System.ServiceModel.CommunicationState> enumeração e são da seguinte maneira:  
  
- Criado: Este é o estado de um <xref:System.ServiceModel.ICommunicationObject> quando ela é instanciada pela primeira vez. Nenhuma entrada/saída (e/s) ocorre nesse estado.  
  
- Ao abrir: Transição de objetos a esse estado quando <xref:System.ServiceModel.ICommunicationObject.Open%2A> é chamado. Neste momento as propriedades são transformadas em imutáveis e podem começar a entrada/saída. Essa transição é válida somente do estado criado.  
  
- Aberto: Transição de objetos nesse estado quando o processo de abertura é concluída. Essa transição é válida somente do estado de abertura. Neste ponto, o objeto é totalmente pode ser usado para transferência.  
  
- Fechamento: Transição de objetos a esse estado quando <xref:System.ServiceModel.ICommunicationObject.Close%2A> é chamado para um desligamento normal. Essa transição é válida somente de estado aberto.  
  
- Fechado: No fechado objetos de estado não são mais utilizáveis. Em geral, mais alta configuração ainda será acessível para inspeção, mas nenhuma comunicação pode ocorrer. Esse estado é equivalente ao que está sendo descartado.  
  
- Com falha: No estado com falha, os objetos são acessíveis para inspeção, mas não é mais utilizável. Quando ocorre um erro não recuperável, o objeto faz a transição para esse estado. A transição válida apenas desse estado é para o `Closed` estado.  
  
 Há eventos que são disparados para cada transição de estado. O <xref:System.ServiceModel.ICommunicationObject.Abort%2A> método pode ser chamado a qualquer momento e faz com que o objeto para fazer a transição imediata do estado atual para o estado fechado. Chamar <xref:System.ServiceModel.ICommunicationObject.Abort%2A> encerra qualquer trabalho não concluído.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Fábrica de canais e ouvinte de canais  
 A próxima etapa na escrita de um transporte personalizado é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> canais de cliente e de <xref:System.ServiceModel.Channels.IChannelListener> para canais de serviço. A camada de canais usa um padrão de fábrica para a construção de canais. O WCF fornece auxiliares da classe base para esse processo.  
  
- O <xref:System.ServiceModel.Channels.CommunicationObject> implementos de classe <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita anteriormente na etapa 2. 

- O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase>. O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.  
  
- O <xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida os `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstrato.  
  
- O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Ele cuida do gerenciamento de estado básica.  
  
 Neste exemplo, a implementação de fábrica está contida em UdpChannelFactory.cs e a implementação do ouvinte está contida no UdpChannelListener.cs. O <xref:System.ServiceModel.Channels.IChannel> implementações estão em UdpOutputChannel.cs e UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>A fábrica de canais de UDP  
 O `UdpChannelFactory` deriva <xref:System.ServiceModel.Channels.ChannelFactoryBase>. O exemplo substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para fornecer acesso à versão de mensagem do codificador de mensagem. O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> , de modo que podemos pode subdividir nossa instância do <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída UDP  
 O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>. O construtor valida os argumentos e constrói um destino <xref:System.Net.EndPoint> objeto com base no <xref:System.ServiceModel.EndpointAddress> que é passado.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 O canal pode ser fechado normalmente ou de maneira brusca. Se o canal seja fechado normalmente o soquete é fechado e é feita uma chamada para a classe base `OnClose` método. Se isso gerar uma exceção, a infraestrutura chame `Abort` garantir que o canal é limpa.  
  
```csharp
this.socket.Close(0);  
```  
  
 Em seguida, implementamos `Send()` e `BeginSend()` / `EndSend()`. Isso se divide em duas seções principais. Primeiro, serializar a mensagem em uma matriz de bytes.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, enviamos os dados resultantes durante a transmissão.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>O UdpChannelListener  
 O `UdpChannelListener` que a amostra implementa deriva o <xref:System.ServiceModel.Channels.ChannelListenerBase> classe. Ele usa um único soquete UDP para receber datagramas. O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono. Os dados, em seguida, são convertidos em mensagens usando a estrutura de codificação de mensagem.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Como o mesmo canal de datagrama representa mensagens que chegam de várias fontes, o `UdpChannelListener` é um ouvinte de singleton. Há, na maioria dos, um ativo <xref:System.ServiceModel.Channels.IChannel> associado com este ouvinte de cada vez. O exemplo gera outra somente se um canal que é retornado pelo `AcceptChannel` método subsequentemente é descartado. Quando uma mensagem é recebida, ele é enfileirado nesse canal de singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 O `UdpInputChannel` classe implementa `IInputChannel`. Ele consiste em uma fila de mensagens de entrada que é preenchida pelo `UdpChannelListener`do soquete. Essas mensagens são removidas da fila pelo `IInputChannel.Receive` método.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Agora que os canais e fábricas são criados, devemos expor-los para o tempo de execução de ServiceModel por meio de uma associação. Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada com um endereço de serviço. Cada elemento da pilha é representado por um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento.  
  
 No exemplo, é o elemento de associação `UdpTransportBindingElement`, que é derivada de <xref:System.ServiceModel.Channels.TransportBindingElement>. Ele substitui os seguintes métodos para compilar as fábricas associadas à nossa associação.  
  
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
  
 Ele também contém membros para clonagem de `BindingElement` e retornando o nosso esquema (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Adicionando suporte a metadados para um elemento de associação de transporte  
 Para integrar nosso transporte no sistema de metadados, podemos deve dar suporte tanto a importação e exportação de política. Isso nos permite gerar clientes de nossa ligação por meio de [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Adicionando suporte a WSDL  
 O elemento de associação de transporte em uma associação é responsável por exportação e importação de informações de endereçamento nos metadados. Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar um URI de transporte correto nos metadados.  
  
#### <a name="wsdl-export"></a>Exportação WSDL  
 Para exportar informações de endereçamento de `UdpTransportBindingElement` implementa o `IWsdlExportExtension` interface. O `ExportEndpoint` método adiciona as informações de endereçamento corretas para a porta WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 O `UdpTransportBindingElement` implementação do `ExportEndpoint` método também exporta um transporte URI quando o ponto de extremidade usa uma associação SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importação WSDL  
 Para estender o sistema de importação WSDL para lidar com os endereços a importação, devemos adicionar a seguinte configuração ao arquivo de configuração para Svcutil.exe conforme mostrado no arquivo de svcutil.  
  
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
  
 Ao executar Svcutil.exe, há duas opções para obtenção de Svcutil.exe para carregar as extensões de importação WSDL:  
  
1. Ponto Svcutil.exe ao nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.  
  
2. Adicione a seção de configuração para svcutil no mesmo diretório que Svcutil.exe.  
  
 O `UdpBindingElementImporter` tipo implementa o `IWsdlImportExtension` interface. O `ImportEndpoint` método importa o endereço da porta WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Adicionando suporte à política  
 O elemento de associação personalizada pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.  
  
#### <a name="policy-export"></a>Exportação de política  
 O `UdpTransportBindingElement` tipo implementa `IPolicyExportExtension` para adicionar suporte para exportação de política. Como resultado, `System.ServiceModel.MetadataExporter` inclui `UdpTransportBindingElement` na geração de política para qualquer ligação que inclui-lo.  
  
 No `IPolicyExportExtension.ExportPolicy`, podemos adicionar uma asserção para UDP e outra asserção se estivermos no modo multicast. Isso ocorre porque afeta o modo de multicast, como a pilha de comunicação é construída e, portanto, deve ser coordenada entre os dois lados.  
  
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
  
 Porque os elementos de associação de transporte personalizado serão responsáveis por lidar endereçamento, o `IPolicyExportExtension` implementação no `UdpTransportBindingElement` também deve tratar exportando as declarações de política WS-Addressing, com apropriada para indicar a versão do WS-Addressing que está sendo usado.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importação da política  
 Para estender o sistema de importação da política, devemos adicionar a seguinte configuração ao arquivo de configuração para Svcutil.exe conforme mostrado no arquivo de svcutil.  
  
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
  
 Em seguida, implementamos `IPolicyImporterExtension` de nossa classe registrada (`UdpBindingElementImporter`). No `ImportPolicy()`, podemos examinar as declarações no nosso espaço para nome e processar aqueles para gerar o transporte e verificar se ele é multicast. Podemos também deve remover as declarações que lidamos com na lista de asserções de associação. Novamente, ao executar Svcutil.exe, há duas opções para a integração:  
  
1. Ponto Svcutil.exe ao nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.  
  
2. Adicione a seção de configuração para svcutil no mesmo diretório que Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Adicionar uma associação padrão  
 Nosso elemento de associação pode ser usado de duas maneiras a seguir:  
  
- Por meio de uma ligação personalizada: Uma associação personalizada permite ao usuário criar sua próprias associação com base em um conjunto arbitrário de elementos de associação.  
  
- Usando uma associação fornecida pelo sistema que inclui nosso elemento de associação. O WCF fornece uma série dessas associações definidas pelo sistema, como `BasicHttpBinding`, `NetTcpBinding`, e `WsHttpBinding`. Cada uma dessas vinculações está associada um perfil bem definido.  
  
 O exemplo implementa a associação de perfil em `SampleProfileUdpBinding`, que é derivada de <xref:System.ServiceModel.Channels.Binding>. O `SampleProfileUdpBinding` contém até quatro elementos de associação dentro dele: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, e `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Adicionando uma ligação importador de padrão personalizado  
 Svcutil.exe e o `WsdlImporter` tipo, por padrão, reconhece e importa as associações definidas pelo sistema. Caso contrário, a associação obtém importada como um `CustomBinding` instância. Para habilitar o Svcutil.exe e o `WsdlImporter` para importar o `SampleProfileUdpBinding` o `UdpBindingElementImporter` também atua como um importador de associação padrão personalizada.  
  
 Um importador de associação padrão personalizada implementa o `ImportEndpoint` método na `IWsdlImportExtension` interface para examinar o `CustomBinding` importada dos metadados para ver se ele pode ter sido gerado por uma associação padrão específica de instância.  
  
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
  
 Em geral, implementar um importador de associação padrão personalizado envolve verificar as propriedades dos elementos de associação importados para verificar que somente as propriedades que poderiam ter sido definidas por associação padrão foram alterados e todas as outras propriedades são seus valores padrão. Uma estratégia básica para implementar um importador de associação padrão é criar uma instância de associação padrão, propagar as propriedades de elementos de associação para a instância de associação padrão que dá suporte à associação padrão e comparar a associação elementos de associação padrão com os elementos de associação importados.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para expor nossos transporte através da configuração, devemos implementar duas seções de configuração. A primeira é uma `BindingElementExtensionElement` para `UdpTransportBindingElement`. Isso é, de modo que `CustomBinding` implementações podem fazer referência a nosso elemento de associação. O segundo é um `Configuration` para nosso `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Elemento de extensão de elemento de associação  
 A seção `UdpTransportElement` é um `BindingElementExtensionElement` que expõe `UdpTransportBindingElement` ao sistema de configuração. Com algumas substituições básicas, definimos nosso nome de seção de configuração, o tipo de nosso elemento de associação e como criar nosso elemento de associação. Pode, em seguida, registramos nossa seção de extensão em um arquivo de configuração, conforme mostrado no código a seguir.  
  
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
  
 A extensão pode ser referenciada de ligações personalizadas para usar UDP como o transporte.  
  
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
  
### <a name="binding-section"></a>Seção de associação  
 A seção `SampleProfileUdpBindingCollectionElement` é um `StandardBindingCollectionElement` que expõe `SampleProfileUdpBinding` ao sistema de configuração. A maior parte da implementação é delegada para o `SampleProfileUdpBindingConfigurationElement`, que é derivada de `StandardBindingElement`. O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades nos `SampleProfileUdpBinding`e funções para mapear o `ConfigurationElement` associação. Por fim, substitua os `OnApplyConfiguration` método no nosso `SampleProfileUdpBinding`, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Para registrar esse manipulador com o sistema de configuração, podemos adicionar a seção a seguir ao arquivo de configuração relevantes.  
  
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
  
 Em seguida, pode ser referenciada da seção de configuração de serviceModel.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>O serviço de teste do UDP e o cliente  
 Código de teste para usar esse transporte de exemplo está disponível nos diretórios UdpTestService e UdpTestClient. O código de serviço consiste em dois testes — um teste configura as associações e pontos de extremidade do código e o outro faz isso por meio da configuração. Ambos os testes usam dois pontos de extremidade. Um ponto de extremidade usa o `SampleUdpProfileBinding` com [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido como `true`. Outro ponto de extremidade usa uma associação personalizada com `UdpTransportBindingElement`. Isso é equivalente a usar `SampleUdpProfileBinding` com [ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) definido como `false`. Ambos os testes de criarem um serviço, adicionar um ponto de extremidade para cada associação, abra o serviço e aguarde até que o usuário pressionar ENTER antes de fechar o serviço.  
  
 Quando você inicia o aplicativo de serviço de teste, você verá a saída a seguir.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Em seguida, você pode executar o aplicativo de cliente de teste contra os pontos de extremidade publicados. O aplicativo de teste do cliente cria um cliente para cada ponto de extremidade e envia mensagens de cinco para cada ponto de extremidade. É a seguinte saída no cliente.  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 A seguir está a saída completa no serviço.  
  
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
  
 Para executar o aplicativo cliente para pontos de extremidade publicados usando a configuração, pressionar ENTER no serviço e, em seguida, execute novamente o cliente de teste. Você deve ver a saída a seguir no serviço.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Executando o cliente novamente produz o mesmo como os resultados anteriores.  
  
 Para regenerar o código do cliente e a configuração usando Svcutil.exe, inicie o aplicativo de serviço e em seguida, execute o seguinte Svcutil.exe do diretório raiz do exemplo.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Observe que Svcutil.exe não gerar a configuração de extensão de associação para o `SampleProfileUdpBinding`, portanto, você deve adicioná-lo manualmente.  
  
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
  
1. Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3. Consulte a seção "O UDP serviço e cliente de teste" anterior.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
