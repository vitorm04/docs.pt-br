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
# <a name="custom-message-encoder-custom-text-encoder"></a><span data-ttu-id="fccff-102">Codificador personalizado de mensagem: codificador personalizado de texto</span><span class="sxs-lookup"><span data-stu-id="fccff-102">Custom Message Encoder: Custom Text Encoder</span></span>

<span data-ttu-id="fccff-103">Esta amostra demonstra como implementar um codificador de mensagens de texto personalizado usando o Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="fccff-103">This sample demonstrates how to implement a custom text message encoder using Windows Communication Foundation (WCF).</span></span>

> [!WARNING]
> <span data-ttu-id="fccff-104">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="fccff-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fccff-105">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="fccff-105">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="fccff-106">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="fccff-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fccff-107">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="fccff-107">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Text`

<span data-ttu-id="fccff-108">O <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> do WCF suporta apenas as codificações UTF-8, UTF-16 e Unicode de grande endiana.</span><span class="sxs-lookup"><span data-stu-id="fccff-108">The <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF supports only the UTF-8, UTF-16 and big-endian Unicode encodings.</span></span> <span data-ttu-id="fccff-109">O codificador de mensagens de texto personalizado nesta amostra suporta todas as codificações de caracteres suportadas pela plataforma que podem ser necessárias para interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="fccff-109">The custom text message encoder in this sample supports all platform-supported character encodings that may be required for interoperability.</span></span> <span data-ttu-id="fccff-110">A amostra consiste em um programa de console cliente (.exe), uma biblioteca de serviços (.dll) hospedada pelo Internet Information Services (IIS) e uma biblioteca de codificadores de mensagens de texto (.dll).</span><span class="sxs-lookup"><span data-stu-id="fccff-110">The sample consists of a client console program (.exe), a service library (.dll) hosted by Internet Information Services (IIS), and a text message encoder library (.dll).</span></span> <span data-ttu-id="fccff-111">O serviço implementa um contrato que define um padrão de comunicação solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="fccff-111">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="fccff-112">O contrato é `ICalculator` definido pela interface, que expõe as operações matemáticas (Adicionar, Subtrair, Multiplicar e Dividir).</span><span class="sxs-lookup"><span data-stu-id="fccff-112">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="fccff-113">O cliente faz solicitações síncronas para uma determinada operação matemática e o serviço responde com o resultado.</span><span class="sxs-lookup"><span data-stu-id="fccff-113">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="fccff-114">Tanto o cliente `CustomTextMessageEncoder` quanto o <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>serviço usam o padrão em vez do padrão .</span><span class="sxs-lookup"><span data-stu-id="fccff-114">Both client and service uses the `CustomTextMessageEncoder` instead of the default <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>.</span></span>

<span data-ttu-id="fccff-115">A implementação do codificador personalizado consiste em uma fábrica de codificador de mensagens, um codificador de mensagens, um elemento de vinculação de codificação de mensagens e um manipulador de configuração e demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fccff-115">The custom encoder implementation consists of a message encoder factory, a message encoder, a message encoding binding element and a configuration handler, and demonstrates the following:</span></span>

- <span data-ttu-id="fccff-116">Construindo uma fábrica de codificador e codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="fccff-116">Building a custom encoder and encoder factory.</span></span>

- <span data-ttu-id="fccff-117">Criando um elemento de vinculação para um codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="fccff-117">Creating a binding element for a custom encoder.</span></span>

- <span data-ttu-id="fccff-118">Usando a configuração de vinculação personalizada para integrar elementos de vinculação personalizados.</span><span class="sxs-lookup"><span data-stu-id="fccff-118">Using the custom binding configuration for integrating custom binding elements.</span></span>

- <span data-ttu-id="fccff-119">Desenvolvendo um manipulador de configuração personalizado para permitir a configuração de arquivo de um elemento de vinculação personalizado.</span><span class="sxs-lookup"><span data-stu-id="fccff-119">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="fccff-120">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="fccff-120">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="fccff-121">Instale ASP.NET 4.0 usando o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="fccff-121">Install ASP.NET 4.0 using the following command.</span></span>

    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable
    ```

2. <span data-ttu-id="fccff-122">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fccff-122">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

3. <span data-ttu-id="fccff-123">Para construir a solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fccff-123">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

4. <span data-ttu-id="fccff-124">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="fccff-124">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

## <a name="message-encoder-factory-and-the-message-encoder"></a><span data-ttu-id="fccff-125">Fábrica de codificadores de mensagens e o codificador de mensagens</span><span class="sxs-lookup"><span data-stu-id="fccff-125">Message Encoder Factory and the Message Encoder</span></span>

<span data-ttu-id="fccff-126">Quando <xref:System.ServiceModel.ServiceHost> o canal do cliente é aberto, o componente `CustomTextMessageBindingElement` tempo de projeto cria o `CustomTextMessageEncoderFactory`.</span><span class="sxs-lookup"><span data-stu-id="fccff-126">When the <xref:System.ServiceModel.ServiceHost> or the client channel is opened, the design time component `CustomTextMessageBindingElement` creates the `CustomTextMessageEncoderFactory`.</span></span> <span data-ttu-id="fccff-127">A fábrica `CustomTextMessageEncoder`cria o.</span><span class="sxs-lookup"><span data-stu-id="fccff-127">The factory creates the `CustomTextMessageEncoder`.</span></span> <span data-ttu-id="fccff-128">O codificador de mensagens opera tanto no modo de streaming quanto no modo tampão.</span><span class="sxs-lookup"><span data-stu-id="fccff-128">The message encoder operates both in the streaming mode and the buffered mode.</span></span> <span data-ttu-id="fccff-129">Ele usa <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> o e para ler e escrever as mensagens, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="fccff-129">It uses the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to read and write the messages respectively.</span></span> <span data-ttu-id="fccff-130">Ao contrário dos leitores e escritores XML otimizados do WCF que suportam apenas UTF-8, UTF-16 e Unicode de grande endério, esses leitores e escritores suportam toda a codificação suportada pela plataforma.</span><span class="sxs-lookup"><span data-stu-id="fccff-130">As opposed to the optimized XML readers and writers of WCF that support only UTF-8, UTF-16 and big-endian Unicode, these readers and writers support all platform-supported encoding.</span></span>

<span data-ttu-id="fccff-131">O exemplo de código a seguir mostra o CustomTextMessageEncoder.</span><span class="sxs-lookup"><span data-stu-id="fccff-131">The following code example shows the CustomTextMessageEncoder.</span></span>

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

<span data-ttu-id="fccff-132">O exemplo de código a seguir mostra como construir a fábrica de codificadores de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fccff-132">The following code example shows how to build the message encoder factory.</span></span>

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

## <a name="message-encoding-binding-element"></a><span data-ttu-id="fccff-133">Elemento de vinculação de codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="fccff-133">Message Encoding Binding Element</span></span>

<span data-ttu-id="fccff-134">Os elementos de vinculação permitem a configuração da pilha de tempo de execução wcf.</span><span class="sxs-lookup"><span data-stu-id="fccff-134">The binding elements allow the configuration of the WCF run-time stack.</span></span> <span data-ttu-id="fccff-135">Para usar o codificador de mensagens personalizado em um aplicativo WCF, é necessário um elemento de vinculação que cria a fábrica de codificador de mensagens com as configurações apropriadas no nível apropriado na pilha de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fccff-135">To use the custom message encoder in a WCF application, a binding element is required that creates the message encoder factory with the appropriate settings at the appropriate level in the run-time stack.</span></span>

<span data-ttu-id="fccff-136">O `CustomTextMessageBindingElement` deriva da <xref:System.ServiceModel.Channels.BindingElement> classe base e <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> herda da classe.</span><span class="sxs-lookup"><span data-stu-id="fccff-136">The `CustomTextMessageBindingElement` derives from the <xref:System.ServiceModel.Channels.BindingElement> base class and inherits from the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> class.</span></span> <span data-ttu-id="fccff-137">Isso permite que outros componentes do WCF reconheçam esse elemento de vinculação como sendo um elemento de encodificação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="fccff-137">This allows other WCF components to recognize this binding element as being a message encoding binding element.</span></span> <span data-ttu-id="fccff-138">A implementação do <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> retorna uma instância da fábrica de codificador de mensagens correspondente com configurações apropriadas.</span><span class="sxs-lookup"><span data-stu-id="fccff-138">The implementation of <xref:System.ServiceModel.Channels.MessageEncodingBindingElement.CreateMessageEncoderFactory%2A> returns an instance of the matching message encoder factory with appropriate settings.</span></span>

<span data-ttu-id="fccff-139">O `CustomTextMessageBindingElement` expõe configurações `MessageVersion` `ContentType`para `Encoding` , e através de propriedades.</span><span class="sxs-lookup"><span data-stu-id="fccff-139">The `CustomTextMessageBindingElement` exposes settings for `MessageVersion`, `ContentType`, and `Encoding` through properties.</span></span> <span data-ttu-id="fccff-140">O codificador suporta as versões Soap11Addressing e Soap12Addressing1.</span><span class="sxs-lookup"><span data-stu-id="fccff-140">The encoder supports both Soap11Addressing and Soap12Addressing1 versions.</span></span> <span data-ttu-id="fccff-141">O padrão é Soap11Addressing1.</span><span class="sxs-lookup"><span data-stu-id="fccff-141">The default is Soap11Addressing1.</span></span> <span data-ttu-id="fccff-142">O valor padrão `ContentType` do é "text/xml".</span><span class="sxs-lookup"><span data-stu-id="fccff-142">The default value of the `ContentType` is "text/xml".</span></span> <span data-ttu-id="fccff-143">A `Encoding` propriedade permite definir o valor da codificação de caracteres desejada.</span><span class="sxs-lookup"><span data-stu-id="fccff-143">The `Encoding` property allows you to set the value of the desired character encoding.</span></span> <span data-ttu-id="fccff-144">O cliente e serviço de amostra utiliza a codificação de caracteres ISO-8859-1 (Latin1), que não é suportada pelo <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> WCF.</span><span class="sxs-lookup"><span data-stu-id="fccff-144">The sample client and service uses the ISO-8859-1 (Latin1) character encoding, which is not supported by the <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> of WCF.</span></span>

<span data-ttu-id="fccff-145">O código a seguir mostra como criar programaçãomente a vinculação usando o codificador de mensagens de texto personalizado.</span><span class="sxs-lookup"><span data-stu-id="fccff-145">The following code shows how to programmatically create the binding using the custom text message encoder.</span></span>

```csharp
ICollection<BindingElement> bindingElements = new List<BindingElement>();
HttpTransportBindingElement httpBindingElement = new HttpTransportBindingElement();
CustomTextMessageBindingElement textBindingElement = new CustomTextMessageBindingElement();
bindingElements.Add(textBindingElement);
bindingElements.Add(httpBindingElement);
CustomBinding binding = new CustomBinding(bindingElements);
```

## <a name="adding-metadata-support-to-the-message-encoding-binding-element"></a><span data-ttu-id="fccff-146">Adicionando suporte a metadados ao elemento de vinculação de codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="fccff-146">Adding Metadata Support to the Message Encoding Binding Element</span></span>

<span data-ttu-id="fccff-147">Qualquer tipo que <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> deriva é responsável pela atualização da versão da vinculação SOAP no documento WSDL gerado para o serviço.</span><span class="sxs-lookup"><span data-stu-id="fccff-147">Any type that derives from <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> is responsible for updating the version of the SOAP binding in the WSDL document generated for the service.</span></span> <span data-ttu-id="fccff-148">Isso é feito implementando `ExportEndpoint` <xref:System.ServiceModel.Description.IWsdlExportExtension> o método na interface e, em seguida, modificando o WSDL gerado.</span><span class="sxs-lookup"><span data-stu-id="fccff-148">This is done by implementing the `ExportEndpoint` method on the <xref:System.ServiceModel.Description.IWsdlExportExtension> interface and then modifying the generated WSDL.</span></span> <span data-ttu-id="fccff-149">Nesta amostra, `CustomTextMessageBindingElement` utiliza-se a lógica de `TextMessageEncodingBindingElement`exportação wsdl a partir do .</span><span class="sxs-lookup"><span data-stu-id="fccff-149">In this sample, the `CustomTextMessageBindingElement` uses the WSDL export logic from the `TextMessageEncodingBindingElement`.</span></span>

<span data-ttu-id="fccff-150">Para esta amostra, a configuração do cliente está configurada à mão.</span><span class="sxs-lookup"><span data-stu-id="fccff-150">For this sample, the client configuration is hand configured.</span></span> <span data-ttu-id="fccff-151">Você não pode usar svcutil.exe para `CustomTextMessageBindingElement` gerar a configuração do cliente porque não exporta uma afirmação de política para descrever seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="fccff-151">You cannot use Svcutil.exe to generate the client configuration because the `CustomTextMessageBindingElement` does not export a policy assertion to describe its behavior.</span></span> <span data-ttu-id="fccff-152">Você geralmente deve <xref:System.ServiceModel.Description.IPolicyExportExtension> implementar a interface em um elemento de vinculação personalizado para exportar uma afirmação de política personalizada que descreve o comportamento ou o recurso implementado satisfaz o elemento de vinculação.</span><span class="sxs-lookup"><span data-stu-id="fccff-152">You should generally implement the <xref:System.ServiceModel.Description.IPolicyExportExtension> interface on a custom binding element to export a custom policy assertion that describes the behavior or capability implemented by the binding element.</span></span> <span data-ttu-id="fccff-153">Para obter um exemplo de como exportar uma afirmação de política para um elemento de vinculação personalizado, consulte a amostra [Transport: UDP.](../../../../docs/framework/wcf/samples/transport-udp.md)</span><span class="sxs-lookup"><span data-stu-id="fccff-153">For an example of how to export a policy assertion for a custom binding element, see the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>

## <a name="message-encoding-binding-configuration-handler"></a><span data-ttu-id="fccff-154">Manipulador de configuração de codificação de codificação de mensagens</span><span class="sxs-lookup"><span data-stu-id="fccff-154">Message Encoding Binding Configuration Handler</span></span>
<span data-ttu-id="fccff-155">A seção anterior mostra como usar o codificador de mensagens de texto personalizado programáticamente.</span><span class="sxs-lookup"><span data-stu-id="fccff-155">The previous section shows how to use the custom text message encoder programmatically.</span></span> <span data-ttu-id="fccff-156">O `CustomTextMessageEncodingBindingSection` implemento é um manipulador de configuração que permite especificar o uso de um codificador de mensagens de texto personalizado dentro de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="fccff-156">The `CustomTextMessageEncodingBindingSection` implements a configuration handler that allows you to specify the use of a custom text message encoder within a configuration file.</span></span> <span data-ttu-id="fccff-157">A `CustomTextMessageEncodingBindingSection` classe deriva <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> da classe.</span><span class="sxs-lookup"><span data-stu-id="fccff-157">The `CustomTextMessageEncodingBindingSection` class derives from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="fccff-158">A `BindingElementType` propriedade informa o sistema de configuração do tipo de elemento de vinculação a ser criado para esta seção.</span><span class="sxs-lookup"><span data-stu-id="fccff-158">The `BindingElementType` property informs the configuration system of the type of binding element to create for this section.</span></span>

<span data-ttu-id="fccff-159">Todas as configurações `CustomTextMessageBindingElement` definidas por são expostas `CustomTextMessageEncodingBindingSection`como as propriedades no .</span><span class="sxs-lookup"><span data-stu-id="fccff-159">All of the settings defined by `CustomTextMessageBindingElement` are exposed as the properties in the `CustomTextMessageEncodingBindingSection`.</span></span> <span data-ttu-id="fccff-160">O <xref:System.Configuration.ConfigurationPropertyAttribute> serviço auxilia no mapeamento dos atributos do elemento de configuração às propriedades e na definição de valores padrão se o atributo não estiver definido.</span><span class="sxs-lookup"><span data-stu-id="fccff-160">The <xref:System.Configuration.ConfigurationPropertyAttribute> assists in mapping the configuration element attributes to the properties and setting default values if the attribute is not set.</span></span> <span data-ttu-id="fccff-161">Depois que os valores da configuração são carregados <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> e aplicados às propriedades do tipo, o método é chamado, que converte as propriedades em uma instância concreta de um elemento vinculante.</span><span class="sxs-lookup"><span data-stu-id="fccff-161">After the values from configuration are loaded and applied to the properties of the type, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span>

<span data-ttu-id="fccff-162">Este manipulador de configuração mapeia para a seguinte representação no App.config ou Web.config para o serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="fccff-162">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>

```xml
<customTextMessageEncoding encoding="utf-8" contentType="text/xml" messageVersion="Soap11Addressing1" />
```

<span data-ttu-id="fccff-163">A amostra usa a codificação ISO-8859-1.</span><span class="sxs-lookup"><span data-stu-id="fccff-163">The sample uses the ISO-8859-1 encoding.</span></span>

<span data-ttu-id="fccff-164">Para usar este manipulador de configuração, ele deve ser registrado usando o seguinte elemento de configuração.</span><span class="sxs-lookup"><span data-stu-id="fccff-164">To use this configuration handler it must be registered using the following configuration element.</span></span>

```xml
<extensions>
    <bindingElementExtensions>
        <add name="customTextMessageEncoding" type="
Microsoft.ServiceModel.Samples.CustomTextMessageEncodingBindingSection,
                  CustomTextMessageEncoder" />
    </bindingElementExtensions>
</extensions>
```
