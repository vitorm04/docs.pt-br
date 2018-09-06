---
title: 'Codificador de mensagem personalizado: codificador de compactação'
ms.date: 03/30/2017
ms.assetid: 57450b6c-89fe-4b8a-8376-3d794857bfd7
ms.openlocfilehash: b70875e385fa32256476f6d1ae53e8cc1f5ff9de
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735868"
---
# <a name="custom-message-encoder-compression-encoder"></a><span data-ttu-id="e2766-102">Codificador de mensagem personalizado: codificador de compactação</span><span class="sxs-lookup"><span data-stu-id="e2766-102">Custom Message Encoder: Compression Encoder</span></span>
<span data-ttu-id="e2766-103">Este exemplo demonstra como implementar um codificador personalizado usando a plataforma do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e2766-103">This sample demonstrates how to implement a custom encoder using the Windows Communication Foundation (WCF) platform.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2766-104">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e2766-104">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2766-105">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e2766-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2766-106">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e2766-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2766-107">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e2766-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="sample-details"></a><span data-ttu-id="e2766-108">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="e2766-108">Sample Details</span></span>  
 <span data-ttu-id="e2766-109">Esse exemplo consiste em um programa de console de cliente (.exe), um programa de console de serviço auto-hospedado (.exe) e a biblioteca de compactação do codificador de mensagem (. dll).</span><span class="sxs-lookup"><span data-stu-id="e2766-109">This sample consists of a client console program (.exe), a self-hosted service console program (.exe) and a compression message encoder library (.dll).</span></span> <span data-ttu-id="e2766-110">O serviço implementa um contrato que define um padrão de comunicação de solicitação-resposta.</span><span class="sxs-lookup"><span data-stu-id="e2766-110">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="e2766-111">O contrato é definido o `ISampleServer` interface, que expõe as cadeias de caracteres básicas ecoar operações (`Echo` e `BigEcho`).</span><span class="sxs-lookup"><span data-stu-id="e2766-111">The contract is defined by the `ISampleServer` interface, which exposes basic string echoing operations (`Echo` and `BigEcho`).</span></span> <span data-ttu-id="e2766-112">O cliente faz solicitações síncronas para uma determinada operação e as respostas de serviço, repetindo a mensagem de volta ao cliente.</span><span class="sxs-lookup"><span data-stu-id="e2766-112">The client makes synchronous requests to a given operation and the service replies by repeating the message back to the client.</span></span> <span data-ttu-id="e2766-113">Atividade de cliente e o serviço está visível nas janelas do console.</span><span class="sxs-lookup"><span data-stu-id="e2766-113">Client and service activity is visible in the console windows.</span></span> <span data-ttu-id="e2766-114">A intenção deste exemplo é mostrar como escrever um codificador personalizado e demonstrar o impacto da compactação de uma mensagem durante a transmissão.</span><span class="sxs-lookup"><span data-stu-id="e2766-114">The intent of this sample is to show how to write a custom encoder and demonstrate the impact of compression of a message on the wire.</span></span> <span data-ttu-id="e2766-115">Você pode adicionar instrumentação ao codificador de mensagem de compactação para calcular o tamanho da mensagem, o tempo de processamento ou ambos.</span><span class="sxs-lookup"><span data-stu-id="e2766-115">You can add instrumentation to the compression message encoder to calculate message size, processing time, or both.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2766-116">No .NET Framework 4, descompactação automática foi habilitada em um cliente WCF se o servidor está enviando uma resposta compactada (criada com um algoritmo, como GZip ou Deflate).</span><span class="sxs-lookup"><span data-stu-id="e2766-116">In the .NET Framework 4, automatic decompression has been enabled on a WCF client if the server is sending a compressed response (created with an algorithm such as GZip or Deflate).</span></span> <span data-ttu-id="e2766-117">Se o serviço Web está hospedada no servidor de informações da Internet (IIS), o IIS pode ser configurado para o serviço enviar uma resposta compactada.</span><span class="sxs-lookup"><span data-stu-id="e2766-117">If the service is Web-hosted in Internet Information Server (IIS), then IIS can be configured for the service to send a compressed response.</span></span> <span data-ttu-id="e2766-118">Este exemplo pode ser usado se o requisito é fazer a compactação e descompactação no cliente e o serviço ou se o serviço for auto-hospedado.</span><span class="sxs-lookup"><span data-stu-id="e2766-118">This sample can be used if the requirement is to do compression and decompression on both the client and the service or if the service is self-hosted.</span></span>  
  
 <span data-ttu-id="e2766-119">O exemplo demonstra como criar e integrar um codificador de mensagem personalizado em um aplicativo WCF.</span><span class="sxs-lookup"><span data-stu-id="e2766-119">The sample demonstrates how to build and integrate a custom message encoder into a WCF application.</span></span> <span data-ttu-id="e2766-120">A biblioteca GZipEncoder.dll é implantada com o cliente e o serviço.</span><span class="sxs-lookup"><span data-stu-id="e2766-120">The library GZipEncoder.dll is deployed with both the client and the service.</span></span> <span data-ttu-id="e2766-121">Este exemplo também demonstra o impacto da compactação de mensagens.</span><span class="sxs-lookup"><span data-stu-id="e2766-121">This sample also demonstrates the impact of compressing messages.</span></span> <span data-ttu-id="e2766-122">O código GZipEncoder.dll demonstra o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e2766-122">The code in GZipEncoder.dll demonstrates the following:</span></span>  
  
-   <span data-ttu-id="e2766-123">Criação de um codificador personalizado e a fábrica de codificador.</span><span class="sxs-lookup"><span data-stu-id="e2766-123">Building a custom encoder and encoder factory.</span></span>  
  
-   <span data-ttu-id="e2766-124">Desenvolvendo um elemento de associação para um codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2766-124">Developing a binding element for a custom encoder.</span></span>  
  
-   <span data-ttu-id="e2766-125">Usando a configuração de ligação personalizada para a integração de elementos de associação personalizados.</span><span class="sxs-lookup"><span data-stu-id="e2766-125">Using the custom binding configuration for integrating custom binding elements.</span></span>  
  
-   <span data-ttu-id="e2766-126">Desenvolvendo um manipulador de configuração personalizadas para permitir a configuração de arquivo de um elemento de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2766-126">Developing a custom configuration handler to allow file configuration of a custom binding element.</span></span>  
  
 <span data-ttu-id="e2766-127">Como indicado anteriormente, há várias camadas que são implementadas em um codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2766-127">As indicated previously, there are several layers that are implemented in a custom encoder.</span></span> <span data-ttu-id="e2766-128">Para ilustrar melhor a relação entre cada uma dessas camadas, uma ordem simplificada de eventos de inicialização do serviço está na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2766-128">To better illustrate the relationship between each of these layers, a simplified order of events for service start-up is in the following list:</span></span>  
  
1.  <span data-ttu-id="e2766-129">O servidor for iniciado.</span><span class="sxs-lookup"><span data-stu-id="e2766-129">The server starts.</span></span>  
  
2.  <span data-ttu-id="e2766-130">As informações de configuração é lido.</span><span class="sxs-lookup"><span data-stu-id="e2766-130">The configuration information is read.</span></span>  
  
    1.  <span data-ttu-id="e2766-131">A configuração do serviço registra o manipulador de configuração personalizada.</span><span class="sxs-lookup"><span data-stu-id="e2766-131">The service configuration registers the custom configuration handler.</span></span>  
  
    2.  <span data-ttu-id="e2766-132">O host de serviço é criado e aberto.</span><span class="sxs-lookup"><span data-stu-id="e2766-132">The service host is created and opened.</span></span>  
  
    3.  <span data-ttu-id="e2766-133">O elemento de configuração personalizada cria e retorna o elemento de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2766-133">The custom configuration element creates and returns the custom binding element.</span></span>  
  
    4.  <span data-ttu-id="e2766-134">O elemento de associação personalizada cria e retorna uma fábrica de codificador de mensagem.</span><span class="sxs-lookup"><span data-stu-id="e2766-134">The custom binding element creates and returns a message encoder factory.</span></span>  
  
3.  <span data-ttu-id="e2766-135">Uma mensagem é recebida.</span><span class="sxs-lookup"><span data-stu-id="e2766-135">A message is received.</span></span>  
  
4.  <span data-ttu-id="e2766-136">A fábrica de codificador de mensagem retorna um codificador de mensagem para leitura da mensagem e gravar a resposta.</span><span class="sxs-lookup"><span data-stu-id="e2766-136">The message encoder factory returns a message encoder for reading in the message and writing out the response.</span></span>  
  
5.  <span data-ttu-id="e2766-137">A camada de codificador é implementada como uma fábrica de classes.</span><span class="sxs-lookup"><span data-stu-id="e2766-137">The encoder layer is implemented as a class factory.</span></span> <span data-ttu-id="e2766-138">Somente a fábrica de classes do codificador deve estar publicamente exposta para o codificador personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2766-138">Only the encoder class factory must be publicly exposed for the custom encoder.</span></span> <span data-ttu-id="e2766-139">O objeto de fábrica é retornado pelo elemento de associação quando o <xref:System.ServiceModel.ServiceHost> ou <xref:System.ServiceModel.ChannelFactory%601> objeto é criado.</span><span class="sxs-lookup"><span data-stu-id="e2766-139">The factory object is returned by the binding element when the <xref:System.ServiceModel.ServiceHost> or <xref:System.ServiceModel.ChannelFactory%601> object is created.</span></span> <span data-ttu-id="e2766-140">Codificadores de mensagem podem operar em um modo em buffer ou de streaming.</span><span class="sxs-lookup"><span data-stu-id="e2766-140">Message encoders can operate in a buffered or streaming mode.</span></span> <span data-ttu-id="e2766-141">Este exemplo demonstra o modo com buffer e modo de streaming.</span><span class="sxs-lookup"><span data-stu-id="e2766-141">This sample demonstrates both buffered mode and streaming mode.</span></span>  
  
 <span data-ttu-id="e2766-142">Para cada modo, há um que acompanha `ReadMessage` e `WriteMessage` método em abstrata `MessageEncoder` classe.</span><span class="sxs-lookup"><span data-stu-id="e2766-142">For each mode there is an accompanying `ReadMessage` and `WriteMessage` method on the abstract `MessageEncoder` class.</span></span> <span data-ttu-id="e2766-143">A maioria do trabalho de codificação ocorre nesses métodos.</span><span class="sxs-lookup"><span data-stu-id="e2766-143">A majority of the encoding work takes place in these methods.</span></span> <span data-ttu-id="e2766-144">O exemplo encapsula o texto existente e codificadores de mensagem binária.</span><span class="sxs-lookup"><span data-stu-id="e2766-144">The sample wraps the existing text and binary message encoders.</span></span> <span data-ttu-id="e2766-145">Isso permite que o exemplo delegar a leitura e gravação da representação de transmissão de mensagens para o codificador interno e permite que o codificador de compactação compactar ou descompactar os resultados.</span><span class="sxs-lookup"><span data-stu-id="e2766-145">This allows the sample to delegate the reading and writing of the wire representation of messages to the inner encoder and allows the compression encoder to compress or decompress the results.</span></span> <span data-ttu-id="e2766-146">Porque não há nenhum pipeline para codificação de mensagem, isso é o único modelo para usar vários codificadores no WCF.</span><span class="sxs-lookup"><span data-stu-id="e2766-146">Because there is no pipeline for message encoding, this is the only model for using multiple encoders in WCF.</span></span> <span data-ttu-id="e2766-147">Depois que a mensagem foi descompactada, a mensagem resultante é passada acima da pilha para lidar com a pilha de canais.</span><span class="sxs-lookup"><span data-stu-id="e2766-147">Once the message has been decompressed, the resulting message is passed up the stack for the channel stack to handle.</span></span> <span data-ttu-id="e2766-148">Durante a compactação, a mensagem compactada resultante é gravada diretamente para o fluxo fornecido.</span><span class="sxs-lookup"><span data-stu-id="e2766-148">During compression, the resulting compressed message is written directly to the stream provided.</span></span>  
  
 <span data-ttu-id="e2766-149">Este exemplo usa os métodos auxiliares (`CompressBuffer` e `DecompressBuffer`) para executar conversão dos buffers para fluxos de usar o `GZipStream` classe.</span><span class="sxs-lookup"><span data-stu-id="e2766-149">This sample uses helper methods (`CompressBuffer` and `DecompressBuffer`) to perform conversion from buffers to streams to use the `GZipStream` class.</span></span>  
  
 <span data-ttu-id="e2766-150">O armazenados em buffer `ReadMessage` e `WriteMessage` classes de usar o `BufferManager` classe.</span><span class="sxs-lookup"><span data-stu-id="e2766-150">The buffered `ReadMessage` and `WriteMessage` classes make use of the `BufferManager` class.</span></span> <span data-ttu-id="e2766-151">O codificador é acessível somente por meio da fábrica de codificador.</span><span class="sxs-lookup"><span data-stu-id="e2766-151">The encoder is accessible only through the encoder factory.</span></span> <span data-ttu-id="e2766-152">Abstrata `MessageEncoderFactory` classe fornece uma propriedade chamada `Encoder` para acessar o codificador atual e um método chamado `CreateSessionEncoder` para criação de um codificador que oferece suporte a sessões.</span><span class="sxs-lookup"><span data-stu-id="e2766-152">The abstract `MessageEncoderFactory` class provides a property named `Encoder` for accessing the current encoder and a method named `CreateSessionEncoder` for creating an encoder that supports sessions.</span></span> <span data-ttu-id="e2766-153">Tal um codificador pode ser usado no cenário em que o canal dá suporte a sessões, é solicitado e é confiável.</span><span class="sxs-lookup"><span data-stu-id="e2766-153">Such an encoder can be used in the scenario where the channel supports sessions, is ordered and is reliable.</span></span> <span data-ttu-id="e2766-154">Esse cenário permite que a otimização em cada sessão dos dados gravados para a transmissão.</span><span class="sxs-lookup"><span data-stu-id="e2766-154">This scenario allows for optimization in each session of the data written to the wire.</span></span> <span data-ttu-id="e2766-155">Se isso não for desejado, o método base não deve ser sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="e2766-155">If this is not desired, the base method should not be overloaded.</span></span> <span data-ttu-id="e2766-156">O `Encoder` propriedade fornece um mecanismo para acessar o codificador de menos de sessão e a implementação padrão da `CreateSessionEncoder` método retorna o valor da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2766-156">The `Encoder` property provides a mechanism for accessing the session-less encoder and the default implementation of the `CreateSessionEncoder` method returns the value of the property.</span></span> <span data-ttu-id="e2766-157">Porque o exemplo encapsula um codificador existente para fornecer a compactação, o `MessageEncoderFactory` implementação aceita um `MessageEncoderFactory` que representa a fábrica de codificador interno.</span><span class="sxs-lookup"><span data-stu-id="e2766-157">Because the sample wraps an existing encoder to provide compression, the `MessageEncoderFactory` implementation accepts a `MessageEncoderFactory` that represents the inner encoder factory.</span></span>  
  
 <span data-ttu-id="e2766-158">Agora que o codificador e a fábrica de codificador são definidos, pode ser usados com um cliente WCF e serviço.</span><span class="sxs-lookup"><span data-stu-id="e2766-158">Now that the encoder and encoder factory are defined, they can be used with a WCF client and service.</span></span> <span data-ttu-id="e2766-159">No entanto, esses codificadores devem ser adicionados à pilha de canal.</span><span class="sxs-lookup"><span data-stu-id="e2766-159">However, these encoders must be added to the channel stack.</span></span> <span data-ttu-id="e2766-160">Você pode derivar classes do <xref:System.ServiceModel.ServiceHost> e <xref:System.ServiceModel.ChannelFactory%601> classes e substituir o `OnInitialize` métodos para adicionar essa fábrica de codificador manualmente.</span><span class="sxs-lookup"><span data-stu-id="e2766-160">You can derive classes from the <xref:System.ServiceModel.ServiceHost> and <xref:System.ServiceModel.ChannelFactory%601> classes and override the `OnInitialize` methods to add this encoder factory manually.</span></span> <span data-ttu-id="e2766-161">Você também pode expor a fábrica de codificador por meio de um elemento de associação personalizado.</span><span class="sxs-lookup"><span data-stu-id="e2766-161">You can also expose the encoder factory through a custom binding element.</span></span>  
  
 <span data-ttu-id="e2766-162">Para criar um novo elemento de associação personalizado, derive uma classe do <xref:System.ServiceModel.Channels.BindingElement> classe.</span><span class="sxs-lookup"><span data-stu-id="e2766-162">To create a new custom binding element, derive a class from the <xref:System.ServiceModel.Channels.BindingElement> class.</span></span> <span data-ttu-id="e2766-163">No entanto, há vários tipos de elementos de associação.</span><span class="sxs-lookup"><span data-stu-id="e2766-163">There are, however, several types of binding elements.</span></span> <span data-ttu-id="e2766-164">Para garantir que o elemento de associação personalizado é reconhecido como uma elemento de associação de codificação de mensagem, você também deve implementar o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="e2766-164">To ensure that the custom binding element is recognized as a message encoding binding element, you also must implement the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>.</span></span> <span data-ttu-id="e2766-165">O <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> expõe um método para criar uma nova fábrica de codificador de mensagem (`CreateMessageEncoderFactory`), que é implementado para retornar uma instância da fábrica de codificador de mensagem correspondente.</span><span class="sxs-lookup"><span data-stu-id="e2766-165">The <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> exposes a method for creating a new message encoder factory (`CreateMessageEncoderFactory`), which is implemented to return an instance of the matching message encoder factory.</span></span> <span data-ttu-id="e2766-166">Além disso, o <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> tem uma propriedade para indicar a versão de endereçamento.</span><span class="sxs-lookup"><span data-stu-id="e2766-166">Additionally, the <xref:System.ServiceModel.Channels.MessageEncodingBindingElement> has a property to indicate the addressing version.</span></span> <span data-ttu-id="e2766-167">Como este exemplo encapsula os codificadores existentes, a implementação de exemplo também encapsula o codificador existente, elementos de associação e usa um codificador interno, elemento de associação como um parâmetro para o construtor e expõe por meio de uma propriedade.</span><span class="sxs-lookup"><span data-stu-id="e2766-167">Because this sample wraps the existing encoders, the sample implementation also wraps the existing encoder binding elements and takes an inner encoder binding element as a parameter to the constructor and exposes it through a property.</span></span> <span data-ttu-id="e2766-168">O código de exemplo a seguir mostra a implementação do `GZipMessageEncodingBindingElement` classe.</span><span class="sxs-lookup"><span data-stu-id="e2766-168">The following sample code shows the implementation of the `GZipMessageEncodingBindingElement` class.</span></span>  
  
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
  
 <span data-ttu-id="e2766-169">Observe que `GZipMessageEncodingBindingElement` classe implementa o `IPolicyExportExtension` interface, para que esse elemento de associação pode ser exportado como uma política nos metadados, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2766-169">Note that `GZipMessageEncodingBindingElement` class implements the `IPolicyExportExtension` interface, so that this binding element can be exported as a policy in metadata, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="e2766-170">O `GZipMessageEncodingBindingElementImporter` classe implementa as `IPolicyImportExtension` interface, essa classe importa a política para `GZipMessageEncodingBindingElement`.</span><span class="sxs-lookup"><span data-stu-id="e2766-170">The `GZipMessageEncodingBindingElementImporter` class implements the `IPolicyImportExtension` interface, this class imports policy for `GZipMessageEncodingBindingElement`.</span></span> <span data-ttu-id="e2766-171">Ferramenta de Svcutil.exe pode ser usada para importar as políticas para o arquivo de configuração para lidar com `GZipMessageEncodingBindingElement`, o seguinte deve ser adicionado para svcutil.</span><span class="sxs-lookup"><span data-stu-id="e2766-171">Svcutil.exe tool can be used to import policies to the configuration file, to handle `GZipMessageEncodingBindingElement`, the following should be added to Svcutil.exe.config.</span></span>  
  
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
  
 <span data-ttu-id="e2766-172">Agora que há um elemento de associação correspondente para o codificador de compactação, ele pode ser programaticamente conectado o serviço ou cliente, criando um novo objeto de associação personalizado e adicionando o elemento de associação personalizado a ele, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2766-172">Now that there is a matching binding element for the compression encoder, it can be programmatically hooked into the service or client by constructing a new custom binding object and adding the custom binding element to it, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="e2766-173">Embora isso possa ser suficiente para a maioria dos cenários de usuário, que dão suporte a uma configuração de arquivo é essencial se um serviço deve ser hospedado na Web.</span><span class="sxs-lookup"><span data-stu-id="e2766-173">While this may be sufficient for the majority of user scenarios, supporting a file configuration is critical if a service is to be Web-hosted.</span></span> <span data-ttu-id="e2766-174">Para suportar o cenário hospedado na Web, você deve desenvolver um manipulador de configuração personalizadas para permitir que um elemento de associação personalizado ser configurável em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e2766-174">To support the Web-hosted scenario, you must develop a custom configuration handler to allow a custom binding element to be configurable in a file.</span></span>  
  
 <span data-ttu-id="e2766-175">Você pode criar um manipulador de configuração para o elemento de associação sobre o sistema de configuração fornecido pelo [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e2766-175">You can build a configuration handler for the binding element on top of the configuration system provided by the [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)].</span></span> <span data-ttu-id="e2766-176">O manipulador de configuração para o elemento de associação deve derivar de <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe.</span><span class="sxs-lookup"><span data-stu-id="e2766-176">The configuration handler for the binding element must derive from the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> class.</span></span> <span data-ttu-id="e2766-177">O `BindingElementType` propriedade é usada para informar o sistema de configuração do tipo de elemento de associação a ser criado para esta seção.</span><span class="sxs-lookup"><span data-stu-id="e2766-177">The `BindingElementType` property is used to inform the configuration system of the type of binding element to create for this section.</span></span> <span data-ttu-id="e2766-178">Todos os aspectos do `BindingElement` que pode ser conjunto deve ser exposto como propriedades no <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe derivada.</span><span class="sxs-lookup"><span data-stu-id="e2766-178">All aspects of the `BindingElement` that can be set should be exposed as properties in the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class.</span></span> <span data-ttu-id="e2766-179">O <xref:System.Configuration.ConfigurationPropertyAttribute> é usado para ajudar a mapear os atributos do elemento de configuração para as propriedades e definir valores padrão se atributos estão ausentes.</span><span class="sxs-lookup"><span data-stu-id="e2766-179">The <xref:System.Configuration.ConfigurationPropertyAttribute> is used to assist in mapping the configuration element attributes to the properties and setting default values if attributes are missing.</span></span> <span data-ttu-id="e2766-180">Depois que os valores de configuração são carregados e aplicados a propriedades, o <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> método é chamado, que converte as propriedades em uma instância concreta de um elemento de associação.</span><span class="sxs-lookup"><span data-stu-id="e2766-180">After the values from configuration are loaded and applied to the properties, the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.CreateBindingElement%2A> method is called, which converts the properties into a concrete instance of a binding element.</span></span> <span data-ttu-id="e2766-181">O <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> método é usado para converter as propriedades no <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> classe derivada para os valores a serem definidos no elemento de associação newlycreated.</span><span class="sxs-lookup"><span data-stu-id="e2766-181">The <xref:System.ServiceModel.Configuration.BindingElementExtensionElement.ApplyConfiguration%2A> method is used to convert the properties on the <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> derived class into the values to be set on the newlycreated binding element.</span></span>  
  
 <span data-ttu-id="e2766-182">O código de exemplo a seguir mostra a implementação do `GZipMessageEncodingElement`.</span><span class="sxs-lookup"><span data-stu-id="e2766-182">The following sample code shows the implementation of the `GZipMessageEncodingElement`.</span></span>  
  
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
  
 <span data-ttu-id="e2766-183">Esse manipulador de configuração é mapeado para a seguinte representação no App. config ou Web. config para o serviço ou cliente.</span><span class="sxs-lookup"><span data-stu-id="e2766-183">This configuration handler maps to the following representation in the App.config or Web.config for the service or client.</span></span>  
  
```xml  
<gzipMessageEncoding innerMessageEncoding="textMessageEncoding" />  
```  
  
 <span data-ttu-id="e2766-184">Para usar esse manipulador de configuração, ele deve ser registrado dentro do [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) elemento, conforme mostrado no seguinte exemplo de configuração.</span><span class="sxs-lookup"><span data-stu-id="e2766-184">To use this configuration handler, it must be registered within the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) element, as shown in the following sample configuration.</span></span>  
  
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
  
 <span data-ttu-id="e2766-185">Quando você executar o servidor, as respostas e solicitações de operação são exibidas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="e2766-185">When you run the server, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="e2766-186">Pressione ENTER na janela para desligar o servidor.</span><span class="sxs-lookup"><span data-stu-id="e2766-186">Press ENTER in the window to shut down the server.</span></span>  
  
```  
Press Enter key to Exit.  
  
        Server Echo(string input) called:  
        Client message: Simple hello  
  
        Server BigEcho(string[] input) called:  
        64 client messages  
```  
  
 <span data-ttu-id="e2766-187">Quando você executa o cliente, as respostas e solicitações de operação são exibidas na janela do console.</span><span class="sxs-lookup"><span data-stu-id="e2766-187">When you run the client, the operation requests and responses are displayed in the console window.</span></span> <span data-ttu-id="e2766-188">Pressione ENTER na janela do cliente para desligar o cliente.</span><span class="sxs-lookup"><span data-stu-id="e2766-188">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Calling Echo(string):  
Server responds: Simple hello Simple hello  
  
Calling BigEcho(string[]):  
Server responds: Hello 0  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e2766-189">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e2766-189">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e2766-190">Instalar [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 usando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="e2766-190">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command:</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="e2766-191">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2766-191">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="e2766-192">Para criar a solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2766-192">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="e2766-193">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e2766-193">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e2766-194">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e2766-194">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e2766-195">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e2766-195">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e2766-196">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e2766-196">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e2766-197">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e2766-197">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageEncoder\Compression`  
  
## <a name="see-also"></a><span data-ttu-id="e2766-198">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2766-198">See Also</span></span>
