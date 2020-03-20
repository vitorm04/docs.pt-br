---
title: 'Codificador personalizado de mensagem: codificador personalizado de texto'
ms.date: 03/30/2017
ms.assetid: 68ff5c74-3d33-4b44-bcae-e1d2f5dea0de
ms.openlocfilehash: 88aeeb4f1d09795b768441d2a572d959f27e0226
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79145105"
---
# <a name="custom-message-encoder-custom-text-encoder"></a>Codificador personalizado de mensagem: codificador personalizado de texto

Esta amostra demonstra como implementar um codificador de mensagens de texto personalizado usando o Windows Communication Foundation (WCF).

> [!WARNING]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

O <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> do WCF suporta apenas as codificações UTF-8, UTF-16 e Unicode de grande endiana. O codificador de mensagens de texto personalizado nesta amostra suporta todas as codificações de caracteres suportadas pela plataforma que podem ser necessárias para interoperabilidade. A amostra consiste em um programa de console cliente (.exe), uma biblioteca de serviços (.dll) hospedada pelo Internet Information Services (IIS) e uma biblioteca de codificadores de mensagens de texto (.dll). O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta. O contrato é `ICalculator` definido pela interface, que expõe as operações matemáticas (Adicionar, Subtrair, Multiplicar e Dividir). O cliente faz solicitações síncronas para uma determinada operação matemática e o serviço responde com o resultado. Tanto o cliente `CustomTextMessageEncoder` quanto o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>serviço usam o padrão em vez do padrão .

A implementação do codificador personalizado consiste em uma fábrica de codificador de mensagens, um codificador de mensagens, um elemento de vinculação de codificação de mensagens e um manipulador de configuração e demonstra o seguinte:

- Construindo uma fábrica de codificador e codificador personalizado.

- Criando um elemento de vinculação para um codificador personalizado.

- Usando a configuração de vinculação personalizada para integrar elementos de vinculação personalizados.

- Desenvolvendo um manipulador de configuração personalizado para permitir a configuração de arquivo de um elemento de vinculação personalizado.

## <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Instale ASP.NET 4.0 usando o seguinte comando.

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

3. Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).

4. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

## <a name="message-encoder-factory-and-the-message-encoder"></a>Fábrica de codificadores de mensagens e o codificador de mensagens

Quando <xref:System.ServiceModel.ServiceHost> o canal do cliente é aberto, o componente `CustomTextMessageBindingElement` tempo de projeto cria o `CustomTextMessageEncoderFactory`. A fábrica `CustomTextMessageEncoder`cria o. O codificador de mensagens opera tanto no modo de streaming quanto no modo tampão. Ele usa <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> o e para ler e escrever as mensagens, respectivamente. Ao contrário dos leitores e escritores XML otimizados do WCF que suportam apenas UTF-8, UTF-16 e Unicode de grande endério, esses leitores e escritores suportam toda a codificação suportada pela plataforma.

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
        this.contentType = $"{this.factory.MediaType}; charset={this.writerSettings.Encoding.HeaderName}";
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

O exemplo de código a seguir mostra como construir a fábrica de codificadores de mensagens.

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

## <a name="message-encoding-binding-element"></a>Elemento de vinculação de codificação de mensagens

Os elementos de vinculação permitem a configuração da pilha de tempo de execução wcf. Para usar o codificador de mensagens personalizado em um aplicativo WCF, é necessário um elemento de vinculação que cria a fábrica de codificador de mensagens com as configurações apropriadas no nível apropriado na pilha de tempo de execução.

O `CustomTextMessageBindingElement` deriva da <xref:System.ServiceModel.Channels.BindingElement> classe base e <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> herda da classe. Isso permite que outros componentes do WCF reconheçam esse elemento de vinculação como sendo um elemento de encodificação de mensagens. A implementação do <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> retorna uma instância da fábrica de codificador de mensagens correspondente com configurações apropriadas.

O `CustomTextMessageBindingElement` expõe configurações `MessageVersion` `ContentType`para `Encoding` , e através de propriedades. O codificador suporta as versões Soap11Addressing e Soap12Addressing1. O padrão é Soap11Addressing1. O valor padrão `ContentType` do é "text/xml". A `Encoding` propriedade permite definir o valor da codificação de caracteres desejada. O cliente e serviço de amostra utiliza a codificação de caracteres ISO-8859-1 (Latin1), que não é suportada pelo <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.

O código a seguir mostra como criar programaçãomente a vinculação usando o codificador de mensagens de texto personalizado.

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a>Adicionando suporte a metadados ao elemento de vinculação de codificação de mensagens

Qualquer tipo que <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> deriva é responsável pela atualização da versão da vinculação SOAP no documento WSDL gerado para o serviço. Isso é feito implementando `ExportEndpoint` <xref:System.ServiceModel.Description.IWsdlExportExtension> o método na interface e, em seguida, modificando o WSDL gerado. Nesta amostra, `CustomTextMessageBindingElement` utiliza-se a lógica de `TextMessageEncodingBindingElement`exportação wsdl a partir do .

Para esta amostra, a configuração do cliente está configurada à mão. Você não pode usar svcutil.exe para `CustomTextMessageBindingElement` gerar a configuração do cliente porque não exporta uma afirmação de política para descrever seu comportamento. Você geralmente deve <xref:System.ServiceModel.Description.IPolicyExportExtension> implementar a interface em um elemento de vinculação personalizado para exportar uma afirmação de política personalizada que descreve o comportamento ou o recurso implementado satisfaz o elemento de vinculação. Para obter um exemplo de como exportar uma afirmação de política para um elemento de vinculação personalizado, consulte a amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)

## <a name="message-encoding-binding-configuration-handler"></a>Manipulador de configuração de codificação de codificação de mensagens
A seção anterior mostra como usar o codificador de mensagens de texto personalizado programáticamente. O `CustomTextMessageEncodingBindingSection` implemento é um manipulador de configuração que permite especificar o uso de um codificador de mensagens de texto personalizado dentro de um arquivo de configuração. A `CustomTextMessageEncodingBindingSection` classe deriva <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> da classe. A `BindingElementType` propriedade informa o sistema de configuração do tipo de elemento de vinculação a ser criado para esta seção.

Todas as configurações `CustomTextMessageBindingElement` definidas por são expostas `CustomTextMessageEncodingBindingSection`como as propriedades no . O <xref:System.Configuration.ConfigurationPropertyAttribute> serviço auxilia no mapeamento dos atributos do elemento de configuração às propriedades e na definição de valores padrão se o atributo não estiver definido. Depois que os valores da configuração são carregados <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> e aplicados às propriedades do tipo, o método é chamado, que converte as propriedades em uma instância concreta de um elemento vinculante.

Este manipulador de configuração mapeia para a seguinte representação no App.config ou Web.config para o serviço ou cliente.

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

A amostra usa a codificação ISO-8859-1.

Para usar este manipulador de configuração, ele deve ser registrado usando o seguinte elemento de configuração.

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
