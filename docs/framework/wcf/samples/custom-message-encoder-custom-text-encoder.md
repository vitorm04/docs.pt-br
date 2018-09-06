---
title: 'Codificador personalizado de mensagem: codificador personalizado de texto'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: aeb1690d7ead9116bd9c4afe3c64d65d8f51ad50
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43800685"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Codificador personalizado de mensagem: codificador personalizado de texto
Este exemplo demonstra como implementar um codificador de mensagem de texto personalizado usando o Windows Communication Foundation (WCF).  
  
> [!WARNING]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`  
  
 O <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> do WCF dá suporte a apenas as codificações UTF-8, UTF-16 e Unicode de Endean grande. O codificador de mensagem de texto personalizado neste exemplo dá suporte a todas as plataforma suportada codificação de caracteres que podem ser necessárias para a interoperabilidade. O exemplo consiste em um programa de console de cliente (.exe), uma biblioteca de serviço (. dll) hospedado pelo Internet Information Services (IIS) e uma biblioteca de codificador de mensagem de texto (. dll). O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta. O contrato é definido o `ICalculator` interface, que expõe operações matemáticas (Adicionar, subtrair, multiplicar e dividir). O cliente faz solicitações síncronas para uma operação matemática determinado e as respostas de serviço com o resultado. Cliente e o serviço usa o `CustomTextMessageEncoder` em vez do padrão <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.  
  
 A implementação do codificador personalizado consiste em uma fábrica de codificador de mensagem, um codificador de mensagem, uma elemento de associação e um manipulador de configuração de codificação de mensagem e demonstra o seguinte:  
  
-   Criação de um codificador personalizado e a fábrica de codificador.  
  
-   Criando um elemento de associação para um codificador personalizado.  
  
-   Usando a configuração de ligação personalizada para a integração de elementos de associação personalizados.  
  
-   Desenvolvendo um manipulador de configuração personalizadas para permitir a configuração de arquivo de um elemento de associação personalizado.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o comando a seguir.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="message-encoder-factory-and-the-message-encoder"></a>Fábrica de codificador de mensagem e o codificador de mensagem  
 Quando o <xref:System.ServiceModel.ServiceHost> ou o cliente de canal é aberto, o componente de tempo de design `CustomTextMessageBindingElement` cria o `CustomTextMessageEncoderFactory`. A fábrica cria o `CustomTextMessageEncoder`. O codificador de mensagem opera no modo de streaming e o modo em buffer. Ele usa o <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> para ler e gravar as mensagens, respectivamente. Em vez dos leitores XML otimizado e a gravadores do WCF que dão suporte apenas UTF-8, UTF-16 e Unicode Big-Endean esses leitores e gravadores de suporte à codificação de todas as plataforma com suporte.  
  
 O exemplo de código a seguir mostra o CustomTextMessageEncoder.  
  
```csharp  
public class CustomTextMessageEncoder : MessageEncoder  
{  
    private CustomTextMessageEncoderFactory factory;  
    private XmlWriterSettings writerSettings;  
    private string contentType;  
  
    public CustomTextMessageEncoder(CustomTextMessageEncoderFactory factory)  
    {  
        this.factory = factory;  
  
        this.writerSettings = new XmlWriterSettings();  
        this.writerSettings.Encoding = Encoding.GetEncoding(factory.CharSet);  
        this.contentType = string.Format("{0}; charset={1}",   
            this.factory.MediaType, this.writerSettings.Encoding.HeaderName);  
    }  
  
    public override string ContentType  
    {  
        get  
        {  
            return this.contentType;  
        }  
    }  
  
    public override string MediaType  
    {  
        get   
        {  
            return factory.MediaType;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {  
            return this.factory.MessageVersion;  
        }  
    }  
  
    public override Message ReadMessage(ArraySegment<byte> buffer, BufferManager bufferManager, string contentType)  
    {     
        byte[] msgContents = new byte[buffer.Count];  
        Array.Copy(buffer.Array, buffer.Offset, msgContents, 0, msgContents.Length);  
        bufferManager.ReturnBuffer(buffer.Array);  
  
        MemoryStream stream = new MemoryStream(msgContents);  
        return ReadMessage(stream, int.MaxValue);  
    }  
  
    public override Message ReadMessage(Stream stream, int maxSizeOfHeaders, string contentType)  
    {  
        XmlReader reader = XmlReader.Create(stream);  
        return Message.CreateMessage(reader, maxSizeOfHeaders, this.MessageVersion);  
    }  
  
    public override ArraySegment<byte> WriteMessage(Message message, int maxMessageSize, BufferManager bufferManager, int messageOffset)  
    {  
        MemoryStream stream = new MemoryStream();  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
  
        byte[] messageBytes = stream.GetBuffer();  
        int messageLength = (int)stream.Position;  
        stream.Close();  
  
        int totalLength = messageLength + messageOffset;  
        byte[] totalBytes = bufferManager.TakeBuffer(totalLength);  
        Array.Copy(messageBytes, 0, totalBytes, messageOffset, messageLength);  
  
        ArraySegment<byte> byteArray = new ArraySegment<byte>(totalBytes, messageOffset, messageLength);  
        return byteArray;  
    }  
  
    public override void WriteMessage(Message message, Stream stream)  
    {  
        XmlWriter writer = XmlWriter.Create(stream, this.writerSettings);  
        message.WriteMessage(writer);  
        writer.Close();  
    }  
}  
```  
  
 O exemplo de código a seguir mostra como criar a fábrica de codificador de mensagem.  
  
```csharp  
public class CustomTextMessageEncoderFactory : MessageEncoderFactory  
{  
    private MessageEncoder encoder;  
    private MessageVersion version;  
    private string mediaType;  
    private string charSet;  
  
    internal CustomTextMessageEncoderFactory(string mediaType, string charSet,  
        MessageVersion version)  
    {  
        this.version = version;  
        this.mediaType = mediaType;  
        this.charSet = charSet;  
        this.encoder = new CustomTextMessageEncoder(this);  
    }  
  
    public override MessageEncoder Encoder  
    {  
        get   
        {   
            return this.encoder;  
        }  
    }  
  
    public override MessageVersion MessageVersion  
    {  
        get   
        {   
            return this.version;  
        }  
    }  
  
    internal string MediaType  
    {  
        get  
        {  
            return this.mediaType;  
        }  
    }  
  
    internal string CharSet  
    {  
        get  
        {  
            return this.charSet;  
        }  
    }  
}  
```  
  
## <a name="message-encoding-binding-element"></a>Elemento de associação de codificação de mensagem  
 Os elementos de associação permitem a configuração da pilha de tempo de execução do WCF. Para usar o codificador de mensagem personalizado em um aplicativo WCF, um elemento de associação é necessário que cria a fábrica de codificador de mensagem com as configurações apropriadas no nível apropriado na pilha de tempo de execução.  
  
 O `CustomTextMessageBindingElement` deriva de <xref:System.ServiceModel.Channels.BindingElement> classe base e herda o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> classe. Isso permite que outros componentes do WCF para reconhecer esse elemento de associação como sendo um elemento de associação de codificação de mensagem. A implementação de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> retorna uma instância da fábrica de codificador de mensagem correspondente com as configurações apropriadas.  
  
 O `CustomTextMessageBindingElement` expõe as configurações de `MessageVersion`, `ContentType`, e `Encoding` por meio das propriedades. O codificador dá suporte a versões Soap11Addressing e Soap12Addressing1. O padrão é Soap11Addressing1. O valor padrão de `ContentType` é "text/xml". O `Encoding` propriedade permite que você defina o valor da codificação de caractere desejado. O exemplo de cliente e o serviço usa a codificação de caracteres de ISO-8859-1 (Latim1), que não é compatível com o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> do WCF.  
  
 O código a seguir mostra como criar programaticamente uma associação usando o codificador de mensagem de texto personalizado.  
  
```  
ICollection<BindingElement> bindingElements = new List<BindingElement>();  
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();  
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();  
bindingElements.Add(textBindingElement);  
bindingElements.Add(httpBindingElement);  
CustomBinding binding = new CustomBinding(bindingElements);  
```  
  
## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Adicionando suporte a metadados para a elemento de associação de codificação de mensagem  
 Qualquer tipo que deriva de <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> é responsável por atualizar a versão da associação SOAP no documento WSDL gerado para o serviço. Isso é feito com a implementação de `ExportEndpoint` método no <xref:System.ServiceModel.Description.IWsdlExportExtension> interface e, em seguida, modificando o WSDL gerado. Neste exemplo, o `CustomTextMessageBindingElement` usa a lógica de exportação WSDL do `TextMessageEncodingBinidngElement`.  
  
 Para este exemplo, a configuração do cliente é configurado de mão. É possível usar Svcutil.exe para gerar a configuração do cliente, pois o `CustomTextMessageBindingElement` não exporta uma declaração de política para descrever seu comportamento. Em geral, você deve implementar o <xref:System.ServiceModel.Description.IPolicyExportExtension> interface em um elemento de associação personalizada para exportar uma declaração de política personalizada que descreve o comportamento ou um recurso implementado pelo elemento de associação. Para obter um exemplo de como exportar uma declaração de política para um elemento de associação personalizado, consulte a [transporte: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) exemplo.  
  
## <a name="message-encoding-binding-configuration-handler"></a>Manipulador de configuração de associação de codificação de mensagem  
 A seção anterior mostra como usar o codificador de mensagem de texto personalizado por meio de programação. O `CustomTextMessageEncodingBindingSection` implementa um manipulador de configuração que permite que você especifique o uso de um codificador de mensagem de texto personalizado dentro de um arquivo de configuração. O `CustomTextMessageEncodingBindingSection` classe deriva de <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe. O `BindingElementType` propriedade informa o sistema de configuração do tipo de elemento de associação a ser criado para esta seção.  
  
 Todas as configurações definidas pelo `CustomTextMessageBindingElement` são expostos como propriedades no `CustomTextMessageEncodingBindingSection`. O <xref:System.Configuration.ConfigurationPropertyAttribute> ajuda a mapear os atributos do elemento de configuração para as propriedades e configuração de valores padrão se o atributo não for definido. Depois que os valores de configuração são carregados e aplicados às propriedades do tipo, o <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> método é chamado, que converte as propriedades em uma instância concreta de um elemento de associação.  
  
 Esse manipulador de configuração é mapeado para a seguinte representação no App. config ou Web. config para o serviço ou cliente.  
  
```xml  
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />  
```  
  
 O exemplo usa a codificação ISO-8859-1.  
  
 Para usar esse manipulador de configuração que devem ser registrado usando o seguinte elemento de configuração.  
  
```xml  
<extensions>  
    <bindingElementExtensions>  
        <add name="customTextMessageEncoding" type="   
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,   
                  CustomTextMessageEncoder" />  
    </bindingElementExtensions>  
</extensions>  
```  
  
## <a name="see-also"></a>Consulte também
