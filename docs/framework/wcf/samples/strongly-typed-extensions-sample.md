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
# <a name="strongly-typed-extensions-sample"></a>Exemplo de extensões fortemente tipadas
A amostra <xref:System.ServiceModel.Syndication.SyndicationFeed> usa a classe para efeitos do exemplo. No entanto, os padrões demonstrados nesta amostra podem ser usados com todas as classes de Sindicância que suportam dados de extensão.  
  
 O modelo de objeto<xref:System.ServiceModel.Syndication.SyndicationFeed>sindicância (, e <xref:System.ServiceModel.Syndication.SyndicationItem>classes relacionadas) suporta acesso livremente digitado a dados de extensão usando as <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> propriedades e. <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> Esta amostra mostra como fornecer acesso fortemente digitado aos dados <xref:System.ServiceModel.Syndication.SyndicationFeed> de <xref:System.ServiceModel.Syndication.SyndicationItem> extensão, implementando classes derivadas personalizadas e que disponibilizam certas extensões específicas do aplicativo como propriedades fortemente digitadas.  
  
 Como exemplo, esta amostra mostra como implementar um elemento de extensão definido no RFC de extensões de rosca do Átomo proposto. Isto é apenas para fins de demonstração e esta amostra não se destina a ser uma implementação completa da especificação proposta.  
  
## <a name="sample-xml"></a>XML de exemplo  
 O exemplo XML a seguir mostra uma entrada `<in-reply-to>` Atom 1.0 com um elemento de extensão adicional.  
  
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
  
 O `<in-reply-to>` elemento especifica três atributos necessários (`ref`e `type` `href`) ao mesmo tempo que permite a presença de atributos de extensão adicionais e elementos de extensão.  
  
## <a name="modeling-the-in-reply-to-element"></a>Modelando o elemento In-Reply-To  
 Nesta amostra, `<in-reply-to>` o elemento é modelado <xref:System.Xml.Serialization.IXmlSerializable>como CLR que <xref:System.Runtime.Serialization.DataContractSerializer>implementa, o que permite seu uso com o . Também implementa alguns métodos e propriedades para acessar os dados do elemento, como mostrado no código de amostra a seguir.  
  
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
  
 A `InReplyToElement` classe implementa propriedades para`HRef` `MediaType`o `Source`atributo necessário ( , <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>e ) bem como coleções para guardar e .  
  
 A `InReplyToElement` classe implementa a interface, que permite o <xref:System.Xml.Serialization.IXmlSerializable> controle direto sobre como as instâncias do objeto são lidas e escritas para XML. O `ReadXml` método primeiro lê os `Ref` `HRef`valores `MediaType` para o <xref:System.Xml.XmlReader> , e `Source`propriedades a partir do passado para ele. Quaisquer atributos desconhecidos <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> são armazenados na coleção. Quando todos os atributos <xref:System.Xml.XmlReader.ReadStartElement> foram lidos, é chamado para avançar o leitor para o próximo elemento. Como o elemento modelado por esta classe não tem `XElement` filhos obrigatórios, <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> os elementos da criança são tamponados em instâncias e armazenados na coleção, como mostrado no código a seguir.  
  
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
  
 Em `WriteXml`, `InReplyToElement` o método primeiro escreve `Ref` `HRef`os `Source`valores do , , e `MediaType` propriedades como atributos XML (`WriteXml` não `WriteXml`é responsável por escrever o elemento externo real em si, como o feito pelo chamador de ). Ele também escreve o <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> conteúdo do e para o escritor, como mostrado no código a seguir.  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed e ThreadedItem  
 Na amostra, `SyndicationItems` `InReplyTo` com extensões são `ThreadedItem` modeladas pela classe. Da mesma `ThreadedFeed` forma, `SyndicationFeed` a classe é um `ThreadedItem`cujos itens são todas as instâncias de .  
  
 A `ThreadedFeed` classe herda `SyndicationFeed` e `OnCreateItem` substitui `ThreadedItem`para retornar um . Também implementa um método de `Items` acesso `ThreadedItems`à coleção como , como mostrado no código a seguir.  
  
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
  
 A `ThreadedItem` classe herda `SyndicationItem` `InReplyToElement` e faz como uma propriedade fortemente digitada. Isso prevê um acesso programático conveniente aos dados de `InReplyTo` extensão. Também implementa `TryParseElement` `WriteElementExtensions` e para leitura e escrita de seus dados de extensão, como mostrado no código a seguir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
