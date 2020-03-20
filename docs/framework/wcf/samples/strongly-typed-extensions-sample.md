---
title: Exemplo de extensões fortemente tipadas
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 3cfbcddfdc7700618d499dd41d3a8c3b629bf550
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183309"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="07992-102">Exemplo de extensões fortemente tipadas</span><span class="sxs-lookup"><span data-stu-id="07992-102">Strongly-Typed Extensions Sample</span></span>
<span data-ttu-id="07992-103">A amostra <xref:System.ServiceModel.Syndication.SyndicationFeed> usa a classe para efeitos do exemplo.</span><span class="sxs-lookup"><span data-stu-id="07992-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="07992-104">No entanto, os padrões demonstrados nesta amostra podem ser usados com todas as classes de Sindicância que suportam dados de extensão.</span><span class="sxs-lookup"><span data-stu-id="07992-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="07992-105">O modelo de objeto<xref:System.ServiceModel.Syndication.SyndicationFeed>sindicância (, e <xref:System.ServiceModel.Syndication.SyndicationItem>classes relacionadas) suporta acesso livremente digitado a dados de extensão usando as <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> propriedades e. <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A></span><span class="sxs-lookup"><span data-stu-id="07992-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="07992-106">Esta amostra mostra como fornecer acesso fortemente digitado aos dados <xref:System.ServiceModel.Syndication.SyndicationFeed> de <xref:System.ServiceModel.Syndication.SyndicationItem> extensão, implementando classes derivadas personalizadas e que disponibilizam certas extensões específicas do aplicativo como propriedades fortemente digitadas.</span><span class="sxs-lookup"><span data-stu-id="07992-106">This sample shows how to provide strongly-typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly-typed properties.</span></span>  
  
 <span data-ttu-id="07992-107">Como exemplo, esta amostra mostra como implementar um elemento de extensão definido no RFC de extensões de rosca do Átomo proposto.</span><span class="sxs-lookup"><span data-stu-id="07992-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="07992-108">Isto é apenas para fins de demonstração e esta amostra não se destina a ser uma implementação completa da especificação proposta.</span><span class="sxs-lookup"><span data-stu-id="07992-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="07992-109">XML de exemplo</span><span class="sxs-lookup"><span data-stu-id="07992-109">Sample XML</span></span>  
 <span data-ttu-id="07992-110">O exemplo XML a seguir mostra uma entrada `<in-reply-to>` Atom 1.0 com um elemento de extensão adicional.</span><span class="sxs-lookup"><span data-stu-id="07992-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
```xml  
<entry>  
    <id>tag:example.org,2005:1,2</id>  
    <title type="text">Another response to the original</title>  
    <summary type="text">  
         This is a response to the original entry</summary>  
    <updated>2006-03-01T12:12:13Z</updated>  
    <link href="http://www.example.org/entries/1/2" />  
    <in-reply-to p3:ref="tag:example.org,2005:1"
                 p3:href="http://www.example.org/entries/1"
                 p3:type="application/xhtml+xml"
                 xmlns:p3="http://contoso.org/syndication/thread/1.0"
                 xmlns="http://contoso.org/syndication/thread/1.0">  
      <anotherElement xmlns="http://www.w3.org/2005/Atom">  
                     Some more data</anotherElement>  
      <aDifferentElement xmlns="http://www.w3.org/2005/Atom">  
                     Even more data</aDifferentElement>  
    </in-reply-to>  
</entry>  
```  
  
 <span data-ttu-id="07992-111">O `<in-reply-to>` elemento especifica três atributos necessários (`ref`e `type` `href`) ao mesmo tempo que permite a presença de atributos de extensão adicionais e elementos de extensão.</span><span class="sxs-lookup"><span data-stu-id="07992-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="07992-112">Modelando o elemento In-Reply-To</span><span class="sxs-lookup"><span data-stu-id="07992-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="07992-113">Nesta amostra, `<in-reply-to>` o elemento é modelado <xref:System.Xml.Serialization.IXmlSerializable>como CLR que <xref:System.Runtime.Serialization.DataContractSerializer>implementa, o que permite seu uso com o .</span><span class="sxs-lookup"><span data-stu-id="07992-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="07992-114">Também implementa alguns métodos e propriedades para acessar os dados do elemento, como mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="07992-114">It also implements some methods and properties for accessing the element’s data, as shown in the following sample code.</span></span>  
  
```csharp  
[XmlRoot(ElementName = "in-reply-to", Namespace = "http://contoso.org/syndication/thread/1.0")]  
public class InReplyToElement : IXmlSerializable  
{  
    internal const string ElementName = "in-reply-to";  
    internal const string NsUri =
                  "http://contoso.org/syndication/thread/1.0";  
    private Dictionary<XmlQualifiedName, string> extensionAttributes;  
    private Collection<XElement> extensionElements;  
  
    public InReplyToElement()  
    {  
        this.extensionElements = new Collection<XElement>();  
        this.extensionAttributes = new Dictionary<XmlQualifiedName,
                                                          string>();  
    }  
  
    public Dictionary<XmlQualifiedName, string> AttributeExtensions  
    {  
        get { return this.extensionAttributes; }  
    }  
  
    public Collection<XElement> ElementExtensions  
    {  
        get { return this.extensionElements; }  
    }  
  
    public Uri Href  
    { get; set; }  
  
    public string MediaType  
    { get; set; }  
  
    public string Ref  
    { get; set; }  
  
    public Uri Source  
    { get; set; }  
}  
```  
  
 <span data-ttu-id="07992-115">A `InReplyToElement` classe implementa propriedades para`HRef` `MediaType`o `Source`atributo necessário ( , <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>e ) bem como coleções para guardar e .</span><span class="sxs-lookup"><span data-stu-id="07992-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="07992-116">A `InReplyToElement` classe implementa a interface, que permite o <xref:System.Xml.Serialization.IXmlSerializable> controle direto sobre como as instâncias do objeto são lidas e escritas para XML.</span><span class="sxs-lookup"><span data-stu-id="07992-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="07992-117">O `ReadXml` método primeiro lê os `Ref` `HRef`valores `MediaType` para o <xref:System.Xml.XmlReader> , e `Source`propriedades a partir do passado para ele.</span><span class="sxs-lookup"><span data-stu-id="07992-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="07992-118">Quaisquer atributos desconhecidos <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> são armazenados na coleção.</span><span class="sxs-lookup"><span data-stu-id="07992-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="07992-119">Quando todos os atributos <xref:System.Xml.XmlReader.ReadStartElement> foram lidos, é chamado para avançar o leitor para o próximo elemento.</span><span class="sxs-lookup"><span data-stu-id="07992-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="07992-120">Como o elemento modelado por esta classe não tem `XElement` filhos obrigatórios, <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> os elementos da criança são tamponados em instâncias e armazenados na coleção, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="07992-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```csharp
public void ReadXml(System.Xml.XmlReader reader)  
{  
    bool isEmpty = reader.IsEmptyElement;  
  
    if (reader.HasAttributes)  
    {  
        for (int i = 0; i < reader.AttributeCount; i++)  
        {  
            reader.MoveToNextAttribute();  
  
            if (reader.NamespaceURI == "")  
            {  
                if (reader.LocalName == "ref")  
                {  
                    this.Ref = reader.Value;  
                }  
                else if (reader.LocalName == "href")  
                {  
                    this.Href = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "source")  
                {  
                    this.Source = new Uri(reader.Value);  
                }  
                else if (reader.LocalName == "type")  
                {  
                    this.MediaType = reader.Value;  
                }  
                else  
                {  
                    this.AttributeExtensions.Add(new
                                 XmlQualifiedName(reader.LocalName,
                                 reader.NamespaceURI),
                                 reader.Value);  
                }  
            }  
        }  
    }  
  
    reader.ReadStartElement();  
  
    if (!isEmpty)  
    {  
        while (reader.IsStartElement())  
        {  
            ElementExtensions.Add(  
                  (XElement) XElement.ReadFrom(reader));  
        }  
        reader.ReadEndElement();  
    }  
}  
```  
  
 <span data-ttu-id="07992-121">Em `WriteXml`, `InReplyToElement` o método primeiro escreve `Ref` `HRef`os `Source`valores do , , e `MediaType` propriedades como atributos XML (`WriteXml` não `WriteXml`é responsável por escrever o elemento externo real em si, como o feito pelo chamador de ).</span><span class="sxs-lookup"><span data-stu-id="07992-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="07992-122">Ele também escreve o <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> conteúdo do e para o escritor, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="07992-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```csharp
public void WriteXml(System.Xml.XmlWriter writer)  
{  
    if (this.Ref != null)  
    {  
        writer.WriteAttributeString("ref", InReplyToElement.NsUri,
                                            this.Ref);  
    }  
    if (this.Href != null)  
    {  
        writer.WriteAttributeString("href", InReplyToElement.NsUri,
                                                this.Href.ToString());  
    }  
    if (this.Source != null)  
    {  
        writer.WriteAttributeString("source", InReplyToElement.NsUri,
                                              this.Source.ToString());  
    }  
    if (this.MediaType != null)  
    {  
        writer.WriteAttributeString("type", InReplyToElement.NsUri,
                                                    this.MediaType);  
    }  
  
    foreach (KeyValuePair<XmlQualifiedName, string> kvp in
                                             this.AttributeExtensions)  
    {  
        writer.WriteAttributeString(kvp.Key.Name, kvp.Key.Namespace,
                                                   kvp.Value);  
    }  
  
    foreach (XElement element in this.ElementExtensions)  
    {  
        element.WriteTo(writer);  
    }  
}  
```  
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="07992-123">ThreadedFeed e ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="07992-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="07992-124">Na amostra, `SyndicationItems` `InReplyTo` com extensões são `ThreadedItem` modeladas pela classe.</span><span class="sxs-lookup"><span data-stu-id="07992-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="07992-125">Da mesma `ThreadedFeed` forma, `SyndicationFeed` a classe é um `ThreadedItem`cujos itens são todas as instâncias de .</span><span class="sxs-lookup"><span data-stu-id="07992-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="07992-126">A `ThreadedFeed` classe herda `SyndicationFeed` e `OnCreateItem` substitui `ThreadedItem`para retornar um .</span><span class="sxs-lookup"><span data-stu-id="07992-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="07992-127">Também implementa um método de `Items` acesso `ThreadedItems`à coleção como , como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="07992-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedFeed : SyndicationFeed  
{  
    public ThreadedFeed()  
    {  
    }  
  
    public IEnumerable<ThreadedItem> ThreadedItems  
    {  
        get  
        {  
            return this.Items.Cast<ThreadedItem>();  
        }  
    }  
  
    protected override SyndicationItem CreateItem()  
    {  
        return new ThreadedItem();  
    }  
}  
```  
  
 <span data-ttu-id="07992-128">A `ThreadedItem` classe herda `SyndicationItem` `InReplyToElement` e faz como uma propriedade fortemente digitada.</span><span class="sxs-lookup"><span data-stu-id="07992-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly-typed property.</span></span> <span data-ttu-id="07992-129">Isso prevê um acesso programático conveniente aos dados de `InReplyTo` extensão.</span><span class="sxs-lookup"><span data-stu-id="07992-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="07992-130">Também implementa `TryParseElement` `WriteElementExtensions` e para leitura e escrita de seus dados de extensão, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="07992-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```csharp
public class ThreadedItem : SyndicationItem  
{  
    private InReplyToElement inReplyTo;  
    // Constructors  
        public ThreadedItem()  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
        public ThreadedItem(string title, string content, Uri itemAlternateLink, string id, DateTimeOffset lastUpdatedTime) : base(title, content, itemAlternateLink, id, lastUpdatedTime)  
        {  
            inReplyTo = new InReplyToElement();  
        }  
  
    public InReplyToElement InReplyTo  
    {  
        get { return this.inReplyTo; }  
    }  
  
    protected override bool TryParseElement(  
                        System.Xml.XmlReader reader,
                        string version)  
    {  
        if (version == SyndicationVersions.Atom10 &&  
            reader.NamespaceURI == InReplyToElement.NsUri &&  
            reader.LocalName == InReplyToElement.ElementName)  
        {  
            this.inReplyTo = new InReplyToElement();  
  
            this.InReplyTo.ReadXml(reader);  
  
            return true;  
        }  
        else  
        {  
            return base.TryParseElement(reader, version);  
        }  
    }  
  
    protected override void WriteElementExtensions(XmlWriter writer,
                                                 string version)  
    {  
        if (this.InReplyTo != null &&
                     version == SyndicationVersions.Atom10)  
        {  
            writer.WriteStartElement(InReplyToElement.ElementName,
                                           InReplyToElement.NsUri);  
            this.InReplyTo.WriteXml(writer);  
            writer.WriteEndElement();  
        }  
  
        base.WriteElementExtensions(writer, version);  
    }  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07992-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="07992-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="07992-132">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07992-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="07992-133">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07992-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="07992-134">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="07992-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="07992-135">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="07992-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="07992-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="07992-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="07992-137">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="07992-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07992-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="07992-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
