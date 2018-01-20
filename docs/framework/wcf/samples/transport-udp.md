---
title: 'Transporte: UDP'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
caps.latest.revision: "48"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b7bb9f60340915f27c451d05bfbc28e1670c9d83
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="transport-udp"></a>Transporte: UDP
O transporte UDP demonstra como implementar UDP unicast e multicast como um personalizado [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] transporte. O exemplo descreve o procedimento recomendado para a criação de um transporte personalizado no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], usando a estrutura de canal e seguindo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] práticas recomendadas. As etapas para criar um transporte personalizado são da seguinte maneira:  
  
1.  Decidir qual o canal [padrões de troca de mensagem](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel ou IReplyChannel) a ChannelFactory e ChannelListener oferecerá suporte. Em seguida, decida se você oferecer suporte as sessão variações dessas interfaces.  
  
2.  Crie uma fábrica de canal e ouvinte que dão suporte ao padrão de troca de mensagem.  
  
3.  Certifique-se de que todas as exceções específicas de rede são normalizadas para a classe derivada apropriada de <xref:System.ServiceModel.CommunicationException>.  
  
4.  Adicionar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento que adiciona o transporte personalizado para uma pilha de canais. Para obter mais informações, consulte [adicionando um elemento de associação](#AddingABindingElement).  
  
5.  Adicione uma seção de extensão do elemento de associação para expor o novo elemento de associação para o sistema de configuração.  
  
6.  Adicione extensões de metadados para recursos para outros pontos de extremidade de comunicação.  
  
7.  Adicione uma associação que pré-configura em uma pilha de elementos de associação de acordo com um perfil bem definido. Para obter mais informações, consulte [adicionar uma associação padrão](#AddingAStandardBinding).  
  
8.  Adicione uma seção de associação e o elemento de configuração de associação para expor a associação para o sistema de configuração. Para obter mais informações, consulte [adicionando suporte de configuração](#AddingConfigurationSupport).  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a>Padrões de troca de mensagem  
 A primeira etapa na gravação de um transporte personalizado é decidir quais padrões de troca de mensagens (MEPs) são necessários para o transporte. Há três MEPs à sua escolha:  
  
-   Datagrama (IInputChannel/IOutputChannel)  
  
     Ao usar um datagrama MEPS, um cliente envia uma mensagem usando uma troca de "disparar e esquecer". Um disparar e esquecer exchange é aquela que requer confirmação fora de banda de entrega bem-sucedida. A mensagem pode ser perdido em trânsito e nunca alcançar o serviço. Se a operação de envio for concluído com êxito no lado do cliente, ele não garante que o ponto de extremidade remoto recebeu a mensagem. O datagrama é um componente fundamental para mensagens, como você pode criar seus próprios protocolos sobre ele — incluindo protocolos confiáveis e seguro. Canais de datagrama do cliente implementam a <xref:System.ServiceModel.Channels.IOutputChannel> canais de datagrama de interface e o serviço implementam o <xref:System.ServiceModel.Channels.IInputChannel> interface.  
  
-   Solicitação-resposta (IRequestChannel/IReplyChannel)  
  
     Neste MEPS, uma mensagem é enviada, e uma resposta é recebida. O padrão consiste em pares de solicitação-resposta. Exemplos de chamadas de solicitação-resposta são chamadas de procedimento remoto (RPC) e o navegador obtém. Esse padrão também é conhecido como Half-Duplex. Este MEPS canais de cliente implementam <xref:System.ServiceModel.Channels.IRequestChannel> e canais de serviço implementam <xref:System.ServiceModel.Channels.IReplyChannel>.  
  
-   Duplex (IDuplexChannel)  
  
     O MEPS duplex permite que um número arbitrário de mensagens sejam enviadas por um cliente e recebidos em qualquer ordem. O duplex MEPS é como uma conversa telefônica, onde cada palavra que está sendo falada é uma mensagem. Como ambos os lados podem enviar e receber este MEPS, a interface implementada por canais de cliente e de serviço é <xref:System.ServiceModel.Channels.IDuplexChannel>.  
  
 Cada um desses MEPs também pode oferecer suporte a sessões. A funcionalidade adicional fornecida por um canal de reconhecimento de sessão é que ele correlaciona todas as mensagens enviadas e recebidas em um canal. O padrão de solicitação-resposta é uma sessão de duas mensagens independente, como a solicitação e resposta são correlacionadas. Em contraste, o padrão de solicitação-resposta que oferece suporte a sessões implica que todos os pares de solicitação/resposta naquele canal são correlacionados com o outro. Isso lhe dá um total de seis MEPs — datagrama, solicitação-resposta, Duplex, datagrama com sessões de solicitação-resposta com sessões e Duplex com sessões — à sua escolha.  
  
> [!NOTE]
>  Para o transporte UDP, a MEPS somente com suporte é datagrama, como UDP inerentemente é um protocolo de "disparar e esquecer".  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a>Ciclo de vida do objeto de ICommunicationObject e o WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]tem uma máquina de estado comum que é usada para gerenciar o ciclo de vida de objetos, como <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, e <xref:System.ServiceModel.Channels.IChannelListener> que são usados para comunicação. Há cinco estados em que esses objetos de comunicação podem existir. Esses estados são representados pelo <xref:System.ServiceModel.CommunicationState> enumeração e são da seguinte maneira:  
  
-   Criado: Esse é o estado de um <xref:System.ServiceModel.ICommunicationObject> quando ele é instanciado pela primeira vez. Nenhuma entrada/saída (e/s) ocorre nesse estado.  
  
-   Abrindo: Transição de objetos para esse estado quando <xref:System.ServiceModel.ICommunicationObject.Open%2A> é chamado. Neste ponto propriedades são feitas imutáveis e pode começar a entrada/saída. Esta transição é válida somente do estado criado.  
  
-   Aberto: A transição de objetos para esse estado quando o processo de abertura é concluída. Esta transição é válida somente do estado de abertura. Neste ponto, o objeto é totalmente pode ser usado para transferência.  
  
-   Fechamento: Transição de objetos para esse estado quando <xref:System.ServiceModel.ICommunicationObject.Close%2A> é chamado para um desligamento normal. Esta transição é válida somente do estado aberto.  
  
-   Fechado: No fechada objetos de estado não são mais utilizáveis. Em geral, mais alta configuração ainda será acessível para inspeção, mas não há comunicação pode ocorrer. Esse estado é equivalente à que está sendo descartado.  
  
-   Com falha: No estado com falha, os objetos são acessíveis para inspeção, mas não mais utilizável. Quando ocorre um erro não recuperável, o objeto faz a transição para esse estado. A transição só é válida desse estado é para o `Closed` estado.  
  
 Há eventos que acionam para cada transição de estado. O <xref:System.ServiceModel.ICommunicationObject.Abort%2A> método pode ser chamado a qualquer momento e faz com que o objeto transição imediatamente do estado atual para o estado fechado. Chamando <xref:System.ServiceModel.ICommunicationObject.Abort%2A> encerra qualquer trabalho não concluído.  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a>Fábrica de canal e ouvinte de canal  
 A próxima etapa na gravação de um transporte personalizado é criar uma implementação de <xref:System.ServiceModel.Channels.IChannelFactory> de canais de cliente e de <xref:System.ServiceModel.Channels.IChannelListener> para canais de serviço. A camada do canal usa um padrão de fábrica para a construção de canais. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece auxiliares da classe base para esse processo.  
  
-   O <xref:System.ServiceModel.Channels.CommunicationObject> classe implementa <xref:System.ServiceModel.ICommunicationObject> e impõe a máquina de estado descrita anteriormente na etapa 2. 

-   O '<xref:System.ServiceModel.Channels.ChannelManagerBase> classe implementa <xref:System.ServiceModel.Channels.CommunicationObject> e fornece uma classe base unificada para <xref:System.ServiceModel.Channels.ChannelFactoryBase> e <xref:System.ServiceModel.Channels.ChannelListenerBase>. O <xref:System.ServiceModel.Channels.ChannelManagerBase> classe funciona em conjunto com <xref:System.ServiceModel.Channels.ChannelBase>, que é uma classe base que implementa <xref:System.ServiceModel.Channels.IChannel>.  
  
-   O '<xref:System.ServiceModel.Channels.ChannelFactoryBase> classe implementa <xref:System.ServiceModel.Channels.ChannelManagerBase> e <xref:System.ServiceModel.Channels.IChannelFactory> e consolida o `CreateChannel` sobrecargas em uma `OnCreateChannel` método abstract.  
  
-   O <xref:System.ServiceModel.Channels.ChannelListenerBase> classe implementa <xref:System.ServiceModel.Channels.IChannelListener>. Cuida do gerenciamento de estado básica.  
  
 Neste exemplo, a implementação de fábrica está contida em UdpChannelFactory.cs e a implementação de ouvinte está contida no UdpChannelListener.cs. O <xref:System.ServiceModel.Channels.IChannel> implementações estão em UdpOutputChannel.cs e UdpInputChannel.cs.  
  
### <a name="the-udp-channel-factory"></a>A fábrica de canais de UDP  
 O `UdpChannelFactory` deriva de <xref:System.ServiceModel.Channels.ChannelFactoryBase>. O exemplo substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> para fornecer acesso para a versão de mensagem do codificador de mensagem. O exemplo também substitui <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> para que podemos pode subdividir a instância do <xref:System.ServiceModel.Channels.BufferManager> quando a máquina de estado faz a transição.  
  
#### <a name="the-udp-output-channel"></a>O canal de saída de UDP  
 O `UdpOutputChannel` implementa <xref:System.ServiceModel.Channels.IOutputChannel>. O construtor valida os argumentos e constrói um destino <xref:System.Net.EndPoint> objeto com base no <xref:System.ServiceModel.EndpointAddress> que é passado.  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 O canal pode ser fechado normalmente ou maneira brusca. Se o canal está fechado normalmente o soquete é fechado e é feita uma chamada para a classe base `OnClose` método. Se isso gera uma exceção, a infraestrutura de chamadas `Abort` garantir que o canal é limpa.  
  
```csharp
this.socket.Close(0);  
```  
  
 Depois de implementar `Send()` e `BeginSend()` / `EndSend()`. Isso é dividido em duas seções principais. Primeiro, a serialização da mensagem em uma matriz de bytes.  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 Em seguida, podemos enviar os dados resultantes na conexão.  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a>O UdpChannelListener  
 O ' UdpChannelListener que implementa o exemplo deriva o <xref:System.ServiceModel.Channels.ChannelListenerBase> classe. Ele usa um único soquete UDP para receber datagramas. O `OnOpen` método recebe dados usando o soquete UDP em um loop assíncrono. Os dados, em seguida, são convertidos em mensagens usando a estrutura de codificação de mensagem.  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 Como o mesmo canal de datagrama representa mensagens que chegam de várias fontes, o `UdpChannelListener` um ouvinte de singleton. Há, a maioria, um ativo <xref:System.ServiceModel.Channels.IChannel>' associado a este ouvinte de cada vez. O exemplo gera outra somente se um canal que é retornado pelo `AcceptChannel` método subsequentemente é descartado. Quando uma mensagem é recebida, ele é enfileirado para este canal de singleton.  
  
#### <a name="udpinputchannel"></a>UdpInputChannel  
 O `UdpInputChannel` classe implementa `IInputChannel`. Ele consiste em uma fila de mensagens de entrada que é preenchida pelo `UdpChannelListener`do soquete. Essas mensagens são removidas da fila pelo `IInputChannel.Receive` método.  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a>Adicionando um elemento de associação  
 Agora que os canais e fábricas são criados, devemos expor-los no tempo de execução de ServiceModel por meio de uma associação. Uma associação é uma coleção de elementos de associação que representa a pilha de comunicação associada com um endereço de serviço. Cada elemento na pilha é representado por um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento.  
  
 No exemplo, o elemento de associação é `UdpTransportBindingElement`, que é derivado de <xref:System.ServiceModel.Channels.TransportBindingElement>. Ela substitui os seguintes métodos para criar as fábricas associadas nossa associação.  
  
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
  
 Ele também contém membros para clonagem de `BindingElement` e retornando nosso esquema (soap.udp).  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a>Adicionando suporte a metadados para um elemento de associação de transporte  
 Para integrar nosso transporte para o sistema de metadados, é deve dar suporte tanto a importação e exportação de política. Isso permite que clientes da nossa associação por meio de gerar o [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
### <a name="adding-wsdl-support"></a>Adicionando suporte a WSDL  
 O elemento de associação de transporte em uma associação é responsável para exportar e importar informações de endereçamento nos metadados. Ao usar uma associação SOAP, o elemento de associação de transporte também deve exportar uma URI de transporte correta nos metadados.  
  
#### <a name="wsdl-export"></a>Exportação WSDL  
 Para exportar informações de endereçamento de `UdpTransportBindingElement` implementa o `IWsdlExportExtension` interface. O `ExportEndpoint` método adiciona as informações de endereçamento corretas para a porta WSDL.  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 O `UdpTransportBindingElement` implementação o `ExportEndpoint` método também exporta um transporte URI quando o ponto de extremidade usa uma associação SOAP.  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a>Importação WSDL  
 Para estender o sistema de importação WSDL para lidar com a importação de endereços, devemos adicionar a configuração a seguir para o arquivo de configuração para Svcutil.exe conforme mostrado no arquivo Svcutil.exe.config.  
  
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
  
 Ao executar o Svcutil.exe, há duas opções para obter o Svcutil.exe para carregar as extensões de importação WSDL:  
  
1.  Ponto Svcutil.exe para nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.  
  
2.  Adicione a seção de configuração para Svcutil.exe.config no mesmo diretório que o Svcutil.exe.  
  
 O `UdpBindingElementImporter` tipo implementa o `IWsdlImportExtension` interface. O `ImportEndpoint` método importa o endereço da porta WSDL.  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a>Adicionando suporte a política  
 O elemento de associação personalizada pode exportar declarações de política na associação WSDL para um ponto de extremidade de serviço para expressar os recursos desse elemento de associação.  
  
#### <a name="policy-export"></a>Exportação de diretivas  
 O `UdpTransportBindingElement` tipo implementa `IPolicyExportExtension` para adicionar suporte para exportação de política. Como resultado, `System.ServiceModel.MetadataExporter` inclui `UdpTransportBindingElement` na geração de política para qualquer associação que o inclua.  
  
 Em `IPolicyExportExtension.ExportPolicy`, adicionamos uma asserção para UDP e outra asserção se estamos no modo de multicast. Isso ocorre porque o modo multicast afeta como a pilha de comunicação é construída e, portanto, deve ser coordenada entre os dois lados.  
  
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
  
 Como os elementos de associação de transporte personalizado serão responsáveis pela manipulação de endereçamento, o `IPolicyExportExtension` implementação no `UdpTransportBindingElement` também deve tratar exportando as apropriado declarações de política WS-Addressing para indicar a versão do WS-Addressing está sendo usado.  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a>Importação da política  
 Para estender o sistema de importação da política, devemos adicionar a configuração a seguir para o arquivo de configuração para Svcutil.exe conforme mostrado no arquivo Svcutil.exe.config.  
  
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
  
 Em seguida, implementamos `IPolicyImporterExtension` de nossa classe registrada (`UdpBindingElementImporter`). Em `ImportPolicy()`, podemos examinar as asserções em nosso namespace e processar os para gerar o transporte e verifique se ela é difundida via multicast. Nós também deve remover as asserções que tratamos da lista de declarações de associação. Novamente, ao executar o Svcutil.exe, há duas opções para integração:  
  
1.  Ponto Svcutil.exe para nosso arquivo de configuração usando o /SvcutilConfig:\<arquivo >.  
  
2.  Adicione a seção de configuração para Svcutil.exe.config no mesmo diretório que o Svcutil.exe.  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a>Adicionar uma associação padrão  
 Nosso elemento de associação pode ser usado de duas maneiras a seguir:  
  
-   Por meio de uma associação personalizada: uma associação personalizada permite que o usuário criar seu próprios associação com base em um conjunto arbitrário de elementos de associação.  
  
-   Usando uma associação fornecida pelo sistema que inclui o nosso elemento de associação. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Fornece um número dessas associações definidas pelo sistema, como `BasicHttpBinding`, `NetTcpBinding`, e `WsHttpBinding`. Cada uma dessas vinculações está associada um perfil bem definido.  
  
 O exemplo implementa a associação de perfil em `SampleProfileUdpBinding`, que é derivado de <xref:System.ServiceModel.Channels.Binding>. O `SampleProfileUdpBinding` contém até quatro elementos de associação nele: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, e `ReliableSessionBindingElement`.  
  
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
  
### <a name="adding-a-custom-standard-binding-importer"></a>Adicionando um padrão personalizado importador de associação  
 Svcutil.exe e `WsdlImporter` tipo, por padrão, reconhece e importa associações definidas pelo sistema. Caso contrário, a associação é importada como um `CustomBinding` instância. Para habilitar o Svcutil.exe e o `WsdlImporter` para importar o `SampleProfileUdpBinding` o `UdpBindingElementImporter` também atua como um importador de associação padrão personalizada.  
  
 Implementa um importador de associação padrão personalizada a `ImportEndpoint` método o `IWsdlImportExtension` interface para examinar o `CustomBinding` instância importada de metadados para ver se ele pode ter sido gerado por uma associação padrão específica.  
  
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
  
 Em geral, implementar um importador de associação padrão personalizado envolve verificando as propriedades dos elementos de associação importados para verificar que somente as propriedades que podem ser definidas por meio da associação padrão foram alterados e todas as outras propriedades são seus padrões. Uma estratégia básica para implementar um importador de associação padrão é criar uma instância da associação padrão, para propagar as propriedades de elementos de associação para a instância de associação padrão que oferece suporte a associação padrão e comparar a associação elementos de associação padrão com os elementos de associação importados.  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a>Adicionando suporte à configuração  
 Para expor o nosso transporte por meio de configuração, devemos implementar duas seções de configuração. A primeira é uma `BindingElementExtensionElement` para `UdpTransportBindingElement`. Isso é para que `CustomBinding` implementações podem fazer referência a nosso elemento de associação. O segundo é um `Configuration` para nosso `SampleProfileUdpBinding`.  
  
### <a name="binding-element-extension-element"></a>Elemento de extensão de elemento de associação  
 A seção `UdpTransportElement` é um `BindingElementExtensionElement` que expõe `UdpTransportBindingElement` para o sistema de configuração. Com algumas substituições básico, definimos nosso nome da seção de configuração, o tipo de elemento de associação de nosso e como criar nosso elemento de associação. Podemos pode registrar a seção de extensão em um arquivo de configuração, conforme mostrado no código a seguir.  
  
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
  
 A extensão pode ser referenciada de associações personalizadas para usar UDP como o transporte.  
  
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
 A seção `SampleProfileUdpBindingCollectionElement` é um `StandardBindingCollectionElement` que expõe `SampleProfileUdpBinding` para o sistema de configuração. A maior parte da implementação é delegada ao `SampleProfileUdpBindingConfigurationElement`, que é derivado de `StandardBindingElement`. O `SampleProfileUdpBindingConfigurationElement` tem propriedades que correspondem às propriedades em `SampleProfileUdpBinding`, funções e para mapear o `ConfigurationElement` associação. Por fim, substituir o `OnApplyConfiguration` método no nosso `SampleProfileUdpBinding`, conforme mostrado no código de exemplo a seguir.  
  
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
  
 Para registrar esse manipulador com o sistema de configuração, adicionamos a seção a seguir ao arquivo de configuração relevantes.  
  
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
  
 Em seguida, pode ser referenciada na seção de configuração do serviceModel.  
  
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
  
## <a name="the-udp-test-service-and-client"></a>O cliente e serviço de teste UDP  
 Código de teste para usar esse transporte de exemplo está disponível nos diretórios UdpTestService e UdpTestClient. O código de serviço consiste em dois testes — um teste configura pontos de extremidade e associações de código e outro faz isso por meio da configuração. Ambos os testes usam dois pontos de extremidade. Um ponto de extremidade usa o `SampleUdpProfileBinding` com [ \<reliableSession >](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) definido como `true`. Outro ponto de extremidade usa uma associação personalizada com `UdpTransportBindingElement`. Isso é equivalente a usar `SampleUdpProfileBinding` com [ \<reliableSession >](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) definido como `false`. Ambos os testes de criarem um serviço, adicionar um ponto de extremidade para cada associação, abra o serviço e aguarde até que o usuário pressionar ENTER antes de fechar o serviço.  
  
 Quando você inicia o aplicativo de teste de serviço, você verá a seguinte saída.  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 Você pode executar o aplicativo de cliente de teste com os pontos de extremidade publicados. O aplicativo de teste do cliente cria um cliente para cada ponto de extremidade e envia mensagens de cinco para cada ponto de extremidade. A seguinte saída é no cliente.  
  
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
  
 Para executar o aplicativo cliente em pontos de extremidade publicados usando a configuração, pressione a tecla ENTER no serviço e, em seguida, execute novamente o cliente de teste. Você verá a seguinte saída no serviço.  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 Executando o cliente novamente produz o mesmo como os resultados anteriores.  
  
 Para gerar novamente o código de cliente e a configuração usando Svcutil.exe, inicie o aplicativo de serviço e em seguida, execute o seguinte Svcutil.exe do diretório raiz do exemplo.  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTranport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 Observe que o Svcutil.exe não gerar a configuração de extensão de associação para o `SampleProfileUdpBinding`, portanto, você deve adicioná-lo manualmente.  
  
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
  
1.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
2.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
3.  Consulte a seção "O UDP serviço e cliente de teste" anterior.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
