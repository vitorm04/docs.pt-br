---
title: Exemplo de extensões fortemente tipadas
ms.date: 03/30/2017
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
ms.openlocfilehash: 1fd873e02dcc1fc824c8b17c52231c80c61e7c60
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045478"
---
# <a name="strongly-typed-extensions-sample"></a><span data-ttu-id="902af-102">Exemplo de extensões fortemente tipadas</span><span class="sxs-lookup"><span data-stu-id="902af-102">Strongly-Typed Extensions Sample</span></span>
<span data-ttu-id="902af-103">O exemplo usa a <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para os fins do exemplo.</span><span class="sxs-lookup"><span data-stu-id="902af-103">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="902af-104">No entanto, os padrões demonstrados neste exemplo podem ser usados com todas as classes de distribuição que dão suporte a dados de extensão.</span><span class="sxs-lookup"><span data-stu-id="902af-104">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data.</span></span>  
  
 <span data-ttu-id="902af-105">O modelo de objeto de<xref:System.ServiceModel.Syndication.SyndicationFeed>distribuição <xref:System.ServiceModel.Syndication.SyndicationItem>(,, e classes relacionadas) dá suporte ao acesso de tipo inflexível para dados <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> de <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> extensão usando as propriedades e.</span><span class="sxs-lookup"><span data-stu-id="902af-105">The Syndication object model (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, and related classes) supports loosely-typed access to extension data by using the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> properties.</span></span> <span data-ttu-id="902af-106">Este exemplo mostra como fornecer acesso fortemente tipado a dados de extensão implementando classes derivadas personalizadas do <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> disponibilizando determinadas extensões específicas do aplicativo como propriedades fortemente tipadas.</span><span class="sxs-lookup"><span data-stu-id="902af-106">This sample shows how to provide strongly-typed access to extension data by implementing custom derived classes of <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem> that make available certain application-specific extensions as strongly-typed properties.</span></span>  
  
 <span data-ttu-id="902af-107">Por exemplo, este exemplo mostra como implementar um elemento de extensão definido na RFC de extensões de Threading Atom propostas.</span><span class="sxs-lookup"><span data-stu-id="902af-107">As an example, this sample shows how to implement an extension element defined in the proposed Atom Threading Extensions RFC.</span></span> <span data-ttu-id="902af-108">Isso é apenas para fins de demonstração e este exemplo não se destina a ser uma implementação completa da especificação proposta.</span><span class="sxs-lookup"><span data-stu-id="902af-108">This is for demonstration purposes only and this sample is not intended to be a full implementation of the proposed specification.</span></span>  
  
## <a name="sample-xml"></a><span data-ttu-id="902af-109">XML de exemplo</span><span class="sxs-lookup"><span data-stu-id="902af-109">Sample XML</span></span>  
 <span data-ttu-id="902af-110">O exemplo de XML a seguir mostra uma entrada Atom 1,0 com `<in-reply-to>` um elemento de extensão adicional.</span><span class="sxs-lookup"><span data-stu-id="902af-110">The following XML example shows an Atom 1.0 entry with an additional `<in-reply-to>` extension element.</span></span>  
  
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
  
 <span data-ttu-id="902af-111">O `<in-reply-to>` elemento especifica três atributos necessários (`ref`e `type` `href`), enquanto também permite a presença de atributos de extensão adicionais e elementos de extensão.</span><span class="sxs-lookup"><span data-stu-id="902af-111">The `<in-reply-to>` element specifies three required attributes (`ref`, `type` and `href`) while also allowing for the presence of additional extension attributes and extension elements.</span></span>  
  
## <a name="modeling-the-in-reply-to-element"></a><span data-ttu-id="902af-112">Modelando o elemento in-reply-to</span><span class="sxs-lookup"><span data-stu-id="902af-112">Modeling the In-Reply-To element</span></span>  
 <span data-ttu-id="902af-113">Neste exemplo, o `<in-reply-to>` elemento é modelado como CLR que implementa <xref:System.Xml.Serialization.IXmlSerializable>, que permite seu uso com o. <xref:System.Runtime.Serialization.DataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="902af-113">In this sample, the `<in-reply-to>` element is modeled as CLR that implements <xref:System.Xml.Serialization.IXmlSerializable>, which enables its use with the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="902af-114">Ele também implementa alguns métodos e propriedades para acessar os dados do elemento, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="902af-114">It also implements some methods and properties for accessing the element’s data, as shown in the following sample code.</span></span>  
  
```  
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
  
 <span data-ttu-id="902af-115">A `InReplyToElement` classe implementa propriedades para o atributo necessário (`HRef`, `MediaType`, e `Source`), bem como coleções para manter <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> e <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span><span class="sxs-lookup"><span data-stu-id="902af-115">The `InReplyToElement` class implements properties for the required attribute (`HRef`, `MediaType`, and `Source`) as well as collections to hold <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.</span></span>  
  
 <span data-ttu-id="902af-116">A `InReplyToElement` classe implementa a <xref:System.Xml.Serialization.IXmlSerializable> interface, que permite o controle direto sobre como as instâncias de objeto são lidas e gravadas em XML.</span><span class="sxs-lookup"><span data-stu-id="902af-116">The `InReplyToElement` class implements the <xref:System.Xml.Serialization.IXmlSerializable> interface, which allows direct control over how object instances are read from and written to XML.</span></span> <span data-ttu-id="902af-117">O `ReadXml` método primeiro lê os valores para as `Ref` `MediaType` propriedades `HRef`, `Source`, e do <xref:System.Xml.XmlReader> passado para ele.</span><span class="sxs-lookup"><span data-stu-id="902af-117">The `ReadXml` method first reads the values for the `Ref`, `HRef`, `Source`, and `MediaType` properties from the <xref:System.Xml.XmlReader> passed to it.</span></span> <span data-ttu-id="902af-118">Todos os atributos desconhecidos são <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> armazenados na coleção.</span><span class="sxs-lookup"><span data-stu-id="902af-118">Any unknown attributes are stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection.</span></span> <span data-ttu-id="902af-119">Quando todos os atributos foram lidos, <xref:System.Xml.XmlReader.ReadStartElement> é chamado para avançar o leitor para o próximo elemento.</span><span class="sxs-lookup"><span data-stu-id="902af-119">When all the attributes have been read, <xref:System.Xml.XmlReader.ReadStartElement> is called to advance the reader to the next element.</span></span> <span data-ttu-id="902af-120">Como o elemento modelado por essa classe não tem filhos necessários, os elementos filho são armazenados em `XElement` buffer em instâncias e armazenadas <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> na coleção, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="902af-120">Because the element modeled by this class has no required children, the child elements get buffered into `XElement` instances and stored in the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="902af-121">No `WriteXml`, o `InReplyToElement` método primeiro escreve os `Ref` `HRef` `MediaType` `WriteXml` valores das propriedades,, e como atributos XML (não é responsável por gravar o elemento externo real `Source` em si, como feito pelo chamador de `WriteXml`).</span><span class="sxs-lookup"><span data-stu-id="902af-121">In `WriteXml`, the `InReplyToElement` method first writes out the values of the `Ref`, `HRef`, `Source`, and `MediaType` properties as XML attributes (`WriteXml` is not responsible for writing the actual outer element itself, as that done by the caller of `WriteXml`).</span></span> <span data-ttu-id="902af-122">Ele também grava o conteúdo do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> e <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> para o gravador, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="902af-122">It also writes the contents of the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> and <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> to the writer, as shown in the following code.</span></span>  
  
```  
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
  
## <a name="threadedfeed-and-threadeditem"></a><span data-ttu-id="902af-123">ThreadedFeed e ThreadedItem</span><span class="sxs-lookup"><span data-stu-id="902af-123">ThreadedFeed and ThreadedItem</span></span>  
 <span data-ttu-id="902af-124">No exemplo, `SyndicationItems` com `InReplyTo` extensões `ThreadedItem` são modeladas pela classe.</span><span class="sxs-lookup"><span data-stu-id="902af-124">In the sample, `SyndicationItems` with `InReplyTo` extensions are modeled by the `ThreadedItem` class.</span></span> <span data-ttu-id="902af-125">Da mesma forma `ThreadedFeed` , a classe `SyndicationFeed` é uma cujos itens são todas `ThreadedItem`as instâncias de.</span><span class="sxs-lookup"><span data-stu-id="902af-125">Similarly, the `ThreadedFeed` class is a `SyndicationFeed` whose items are all instances of `ThreadedItem`.</span></span>  
  
 <span data-ttu-id="902af-126">A `ThreadedFeed` classe é herdada de `OnCreateItem` `SyndicationFeed` e substitui para `ThreadedItem`retornar um.</span><span class="sxs-lookup"><span data-stu-id="902af-126">The `ThreadedFeed` class inherits from `SyndicationFeed` and overrides `OnCreateItem` to return a `ThreadedItem`.</span></span> <span data-ttu-id="902af-127">Ele também implementa um método para acessar a `Items` coleção como `ThreadedItems`, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="902af-127">It also implements a method for accessing the `Items` collection as `ThreadedItems`, as shown in the following code.</span></span>  
  
```  
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
  
 <span data-ttu-id="902af-128">A classe `ThreadedItem` é herdada de `InReplyToElement` `SyndicationItem` e faz como uma propriedade fortemente tipada.</span><span class="sxs-lookup"><span data-stu-id="902af-128">The class `ThreadedItem` inherits from `SyndicationItem` and makes `InReplyToElement` as a strongly-typed property.</span></span> <span data-ttu-id="902af-129">Isso fornece acesso de programação conveniente aos dados `InReplyTo` de extensão.</span><span class="sxs-lookup"><span data-stu-id="902af-129">This provides for convenient programmatic access to the `InReplyTo` extension data.</span></span> <span data-ttu-id="902af-130">Ele também implementa `TryParseElement` e `WriteElementExtensions` para ler e gravar seus dados de extensão, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="902af-130">It also implements `TryParseElement` and `WriteElementExtensions` for reading and writing its extension data, as shown in the following code.</span></span>  
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="902af-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="902af-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="902af-132">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="902af-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="902af-133">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="902af-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="902af-134">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="902af-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="902af-135">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="902af-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="902af-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="902af-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="902af-137">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="902af-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="902af-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="902af-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
