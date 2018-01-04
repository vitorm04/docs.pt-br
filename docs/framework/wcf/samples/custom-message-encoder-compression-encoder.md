---
title: "Codificador de mensagem personalizado: codificador de compactação"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 517b37ca1ed92cf36f447a4d634b8f487f2b4abe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-message-encoder-compression-encoder"></a>Codificador de mensagem personalizado: codificador de compactação
Este exemplo demonstra como implementar um codificador personalizado usando o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] plataforma.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Este exemplo consiste em um programa de console de cliente (.exe), um programa de console de serviço auto-hospedado (.exe) e a biblioteca de compactação do codificador de mensagem (. dll). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido pelo `ISampleServer` interface, que expõe as cadeias de caracteres básicas repetir operações (`Echo` e `BigEcho`). O cliente faz solicitações síncronas para uma determinada operação e as respostas do serviço, repetindo a mensagem de volta ao cliente. Atividade de cliente e o serviço é visível nas janelas do console. A intenção deste exemplo é mostrar como escrever um codificador personalizado e demonstrar o impacto da compactação de uma mensagem na conexão. Você pode adicionar a instrumentação para o codificador de mensagem de compactação para calcular o tamanho da mensagem, o tempo de processamento ou ambos.  
  
> [!NOTE]
>  No .NET Framework 4, descompactação automática foi habilitada em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente se o servidor está enviando uma resposta compactada (criada com um algoritmo, como GZip ou Deflate). Se o serviço Web hospedado no servidor de informações da Internet (IIS), o IIS pode ser configurado para o serviço enviar uma resposta compactada. Este exemplo pode ser usado se o requisito é fazer a compactação e descompactação no cliente e o serviço ou se o serviço é hospedado automaticamente.  
  
 O exemplo demonstra como criar e integrar um codificador de mensagem personalizada em um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo. A biblioteca GZipEncoder.dll é implantada com o cliente e o serviço. Este exemplo também demonstra o impacto da compactação de mensagens. O código GZipEncoder.dll demonstra o seguinte:  
  
-   Criando um codificador personalizado e a fábrica do codificador.  
  
-   Desenvolvendo um elemento de associação para um codificador personalizado.  
  
-   Usando a configuração de associação personalizada para a integração de elementos de associação personalizada.  
  
-   Desenvolvendo um manipulador de configuração personalizada para permitir a configuração de arquivo de um elemento de associação personalizada.  
  
 Como indicado anteriormente, existem várias camadas que são implementadas em um codificador personalizado. Para ilustrar melhor a relação entre cada uma dessas camadas, uma ordem simplificada de eventos de inicialização do serviço está na lista a seguir:  
  
1.  O servidor é iniciado.  
  
2.  As informações de configuração é lido.  
  
    1.  A configuração do serviço registra o manipulador de configuração personalizada.  
  
    2.  O host de serviço é criado e aberto.  
  
    3.  O elemento de configuração personalizada cria e retorna o elemento de associação personalizada.  
  
    4.  O elemento de associação personalizada cria e retorna uma fábrica de codificador de mensagem.  
  
3.  Uma mensagem é recebida.  
  
4.  A fábrica de codificador de mensagem retorna um codificador de mensagem para ler a mensagem e gravar a resposta.  
  
5.  A camada de codificador é implementada como uma fábrica de classes. A fábrica de classes codificador deve ser exposta publicamente para o codificador personalizado. O objeto de fábrica é retornado para o elemento de associação quando o <xref:System.ServiceModel.ServiceHost> ou <xref:System.ServiceModel.ChannelFactory%601> objeto é criado. Codificadores de mensagem podem operar em um modo de buffer ou de streaming. Este exemplo demonstra o modo com buffer e modo contínuo.  
  
 Para cada modo não há uma que acompanha `ReadMessage` e `WriteMessage` método abstrata `MessageEncoder` classe. A maioria do trabalho de codificação é feita nesses métodos. O exemplo encapsula o texto existente e codificadores de mensagem binária. Isso permite que o exemplo delegar a leitura e gravação da representação durante a transmissão de mensagens para o codificador interno e permite que o codificador de compactação compactar ou descompactar os resultados. Porque não há nenhum pipeline para codificação de mensagens, este é o modelo somente para o uso de vários codificadores em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Depois que a mensagem tem sido descompactada, a mensagem resultante é passada a pilha para lidar com a pilha de canais. Durante a compactação, a mensagem compactada resultante é gravada diretamente para o fluxo fornecido.  
  
 Este exemplo usa métodos auxiliares (`CompressBuffer` e `DecompressBuffer`) para executar a conversão de buffers para fluxos para usar o `GZipStream` classe.  
  
 O buffer `ReadMessage` e `WriteMessage` classes de usar o `BufferManager` classe. O codificador é acessível somente por meio da fábrica de codificador. O resumo `MessageEncoderFactory` classe fornece uma propriedade chamada `Encoder` para acessar o codificador atual e um método chamado `CreateSessionEncoder` para criação de um codificador que oferece suporte a sessões. Tal um codificador pode ser usado no cenário em que o canal dá suporte a sessões, é solicitado e é confiável. Este cenário permite a otimização em cada sessão de gravação de dados para a conexão. Se isso não for desejado, o método base não deve ser sobrecarregado. O `Encoder` propriedade fornece um mecanismo para acessar o codificador sessão menor e a implementação padrão da `CreateSessionEncoder` método retorna o valor da propriedade. Porque o exemplo encapsula um codificador existente para fornecer a compactação, o `MessageEncoderFactory` implementação aceita um `MessageEncoderFactory` que representa a fábrica interna de codificador.  
  
 Agora que o codificador e a fábrica de codificador são definidas, eles podem ser usados com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente e serviço. No entanto, esses codificadores devem ser adicionados à pilha de canais. Você pode derivar de classes do <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.ChannelFactory%601> classes e substituir o `OnInitialize` métodos para adicionar esta fábrica de codificador manualmente. Você também pode expor o alocador de codificador por meio de um elemento de associação personalizada.  
  
 Para criar um novo elemento de associação personalizada, derive uma classe a partir de <xref:System.ServiceModel.Channels.BindingElement> classe. No entanto, há vários tipos de elementos de associação. Para garantir que o elemento de associação personalizada é reconhecido como uma elemento de associação de codificação de mensagens, você também deve implementar o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>. O <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> expõe um método para criar uma nova fábrica de codificador de mensagem (`CreateMessageEncoderFactory`), que é implementado para retornar uma instância da fábrica de codificador de mensagem correspondente. Além disso, o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> tem uma propriedade para indicar a versão de endereçamento. Como este exemplo ajusta os codificadores existentes, a implementação de exemplo também ajusta o codificador existente elementos de associação e leva um codificador interno associando o elemento como um parâmetro para o construtor e expõe através de uma propriedade. O código de exemplo a seguir mostra a implementação do `GZipMessageEncodingBindingElement` classe.  
  
```  
public sealed class GZipMessageEncodingBindingElement   
                        : MessageEncodingBindingElement //BindingElement  
                        , IPolicyExportExtension  
{  
  
    //We use an inner binding element to store information   
    //required for the inner encoder.  
    MessageEncodingBindingElement innerBindingElement;  
  
        //By default, use the default text encoder as the inner encoder.  
        public GZipMessageEncodingBindingElement()  
            : this(new TextMessageEncodingBindingElement()) { }  
  
    public GZipMessageEncodingBindingElement(MessageEncodingBindingElement messageEncoderBindingElement)  
    {  
        this.innerBindingElement = messageEncoderBindingElement;  
    }  
  
    public MessageEncodingBindingElement InnerMessageEncodingBindingElement  
    {  
        get { return innerBindingElement; }  
        set { innerBindingElement = value; }  
    }  
  
    //Main entry point into the encoder binding element.   
    // Called by WCF to get the factory that creates the  
    //message encoder.  
    public override MessageEncoderFactory CreateMessageEncoderFactory()  
    {  
        return new   
GZipMessageEncoderFactory(innerBindingElement.CreateMessageEncoderFactory());  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get { return innerBindingElement.MessageVersion; }  
        set { innerBindingElement.MessageVersion = value; }  
    }  
  
    public override BindingElement Clone()  
    {  
        return new   
        GZipMessageEncodingBindingElement(this.innerBindingElement);  
    }  
  
    public override T GetProperty<T>(BindingContext context)  
    {  
        if (typeof(T) == typeof(XmlDictionaryReaderQuotas))  
        {  
            return innerBindingElement.GetProperty<T>(context);  
        }  
        else   
        {  
            return base.GetProperty<T>(context);  
        }  
    }  
  
    public override IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelFactory<TChannel>();  
    }  
  
    public override IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.BuildInnerChannelListener<TChannel>();  
    }  
  
    public override bool CanBuildChannelListener<TChannel>(BindingContext context)  
    {  
        if (context == null)  
            throw new ArgumentNullException("context");  
  
        context.BindingParameters.Add(this);  
        return context.CanBuildInnerChannelListener<TChannel>();  
    }  
  
    void IPolicyExportExtension.ExportPolicy(MetadataExporter exporter, PolicyConversionContext policyContext)  
    {  
        if (policyContext == null)  
        {  
            throw new ArgumentNullException("policyContext");  
        }  
       XmlDocument document = new XmlDocument();  
       policyContext.GetBindingAssertions().Add(document.CreateElement(  
            GZipMessageEncodingPolicyConstants.GZipEncodingPrefix,  
            GZipMessageEncodingPolicyConstants.GZipEncodingName,  
            GZipMessageEncodingPolicyConstants.GZipEncodingNamespace));  
    }  
}  
```  
  
 Observe que `GZipMessageEncodingBindingElement` classe implementa o `IPolicyExportExtension` interface, para que esse elemento de associação pode ser exportado como uma política em metadados, como mostrado no exemplo a seguir.  
  
```xml  
<wsp:Policy wsu:Id="BufferedHttpSampleServer_ISampleServer_policy">  
    <wsp:ExactlyOne>  
      <wsp:All>  
        <gzip:text xmlns:gzip=  
        "http://schemas.microsoft.com/ws/06/2004/mspolicy/netgzip1" />   
       <wsaw:UsingAddressing />   
     </wsp:All>  
   </wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 O `GZipMessageEncodingBindingElementImporter` classe implementa o `IPolicyImportExtension` interface, essa classe importa política para `GZipMessageEncodingBindingElement`. Ferramenta svcutil.exe pode ser usada para importar as políticas para o arquivo de configuração, para lidar com `GZipMessageEncodingBindingElement`, o seguinte deve ser adicionado ao Svcutil.exe.config.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="gzipMessageEncoding"   
          type=  
            "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
      </bindingElementExtensions>  
    </extensions>  
    <client>  
      <metadata>  
        <policyImporters>  
          <remove type=  
"System.ServiceModel.Channels.MessageEncodingBindingElementImporter, System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
          <extension type=  
"Microsoft.ServiceModel.Samples.GZipMessageEncodingBindingElementImporter, GZipEncoder, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 Agora que há um elemento de associação correspondente para o codificador de compactação, ele pode ser programaticamente conectado de serviço ou cliente, criando um novo objeto de associação personalizada e adicionar o elemento de associação personalizada, conforme mostrado no código de exemplo a seguir.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
GZipMessageEncodingBindingElement compBindingElement = new GZipMessageEncodingBindingElement ();  
bindingElements.Add(compBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
binding.Name = "SampleBinding";  
binding.Namespace = "http://tempuri.org/bindings";  
```  
  
 Embora isso possa ser suficiente para a maioria dos cenários de usuário, dando suporte a uma configuração de arquivo é essencial se um serviço deve ser hospedado na Web. Para suportar o cenário hospedado na Web, você deve desenvolver um manipulador de configuração personalizada para permitir que um elemento de associação personalizada a ser configurados em um arquivo.  
  
 Você pode criar um manipulador de configuração para o elemento de associação sobre o sistema de configuração fornecido pelo [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]. O manipulador de configuração para o elemento de associação deve derivar do <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe. O `BindingElementType` propriedade é usada para informar o sistema de configuração do tipo de elemento de associação para criar para essa seção. Todos os aspectos do `BindingElement` que pode ser conjunto deve ser exposto como propriedades na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe derivada. O <xref:System.Configuration.ConfigurationPropertyAttribute> é usado para auxiliar no mapeamento de atributos de elemento de configuração para as propriedades e definir valores padrão se atributos estão ausentes. Depois que os valores de configuração são carregados e aplicados às propriedades, o <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> método é chamado, que converte as propriedades em uma instância concreta de um elemento de associação. O <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> método é usado para converter as propriedades na <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe derivada para os valores a serem definidos no elemento de associação newlycreated.  
  
 O código de exemplo a seguir mostra a implementação do `GZipMessageEncodingElement`.  
  
```  
public class GZipMessageEncodingElement : BindingElementExtensionElement  
{  
    public GZipMessageEncodingElement()  
    {  
    }  
  
//Called by the WCF to discover the type of binding element this   
//config section enables  
    public override Type BindingElementType  
    {  
        get { return typeof(GZipMessageEncodingBindingElement); }  
    }  
  
    //The only property we need to configure for our binding element is   
    //the type of inner encoder to use. Here, we support text and  
    //binary.  
    [ConfigurationProperty("innerMessageEncoding",   
                         DefaultValue = "textMessageEncoding")]  
    public string InnerMessageEncoding  
    {  
        get { return (string)base["innerMessageEncoding"]; }  
        set { base["innerMessageEncoding"] = value; }  
    }  
  
    //Called by the WCF to apply the configuration settings (the   
    //property above) to the binding element  
    public override void ApplyConfiguration(BindingElement bindingElement)  
    {  
        GZipMessageEncodingBindingElement binding =   
                (GZipMessageEncodingBindingElement)bindingElement;  
        PropertyInformationCollection propertyInfo =   
                    this.ElementInformation.Properties;  
        if (propertyInfo["innerMessageEncoding"].ValueOrigin !=   
                                     PropertyValueOrigin.Default)  
        {  
            switch (this.InnerMessageEncoding)  
            {  
                case "textMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                      new TextMessageEncodingBindingElement();  
                    break;  
                case "binaryMessageEncoding":  
                    binding.InnerMessageEncodingBindingElement =   
                         new BinaryMessageEncodingBindingElement();  
                    break;  
            }  
        }  
    }  
  
    //Called by the WCF to create the binding element  
    protected override BindingElement CreateBindingElement()  
    {  
        GZipMessageEncodingBindingElement bindingElement =   
                new GZipMessageEncodingBindingElement();  
        this.ApplyConfiguration(bindingElement);  
        return bindingElement;  
    }  
}   
```  
  
 Este manipulador de configuração é mapeado para a representação seguinte no App. config ou Web. config para o serviço ou cliente.  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 Para usar este manipulador de configuração, ele deve ser registrado no [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, conforme mostrado no exemplo de configuração.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
       <add   
           name="gzipMessageEncoding"   
           type=  
           "Microsoft.ServiceModel.Samples.GZipMessageEncodingElement,  
           GZipEncoder, Version=1.0.0.0, Culture=neutral,   
           PublicKeyToken=null" />  
      </bindingElementExtensions>  
</extensions>  
```  
  
 Quando você executa o servidor, as respostas e solicitações de operação são exibidas na janela do console. Pressione ENTER na janela para desligar o servidor.  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 Quando você executa o cliente, as respostas e solicitações de operação são exibidas na janela do console. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o seguinte comando:  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para criar a solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a>Consulte também
