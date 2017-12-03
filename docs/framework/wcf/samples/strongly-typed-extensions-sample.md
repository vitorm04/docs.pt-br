---
title: "Exemplo de extensões fortemente tipadas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02220f11-1a83-441c-9e5a-85f9a9367572
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6f6a1d205a0e8443d7dc81da53855a1b7920def
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="strongly-typed-extensions-sample"></a>Exemplo de extensões fortemente tipadas
O exemplo usa o <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para fins de exemplo. No entanto, os padrões demonstrados neste exemplo podem ser usados com todas as classes de distribuição que oferecem suporte a dados de extensão.  
  
 O modelo de objeto de agregação (<xref:System.ServiceModel.Syndication.SyndicationFeed>, <xref:System.ServiceModel.Syndication.SyndicationItem>, e classes relacionadas) oferece suporte a acesso tipadas vagamente para dados de extensão usando o <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> e <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> propriedades. Este exemplo mostra como fornecer acesso fortemente tipado para dados de extensão com a implementação personalizadas classes derivadas de <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> que disponibilizar algumas extensões específicas do aplicativo como propriedades fortemente tipada.  
  
 Por exemplo, este exemplo mostra como implementar um elemento de extensão definido no RFC do Atom Threading extensões proposta. Isso é para fins de demonstração e este exemplo não pretende ser uma implementação completa da especificação proposta.  
  
## <a name="sample-xml"></a>Exemplo de XML  
 O exemplo XML a seguir mostra uma entrada Atom 1.0 com adicional `<in-reply-to>` elemento de extensão.  
  
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
  
 O `<in-reply-to>` elemento Especifica três atributos necessários (`ref`, `type` e `href`) enquanto também permite que a presença de elementos de extensão e atributos de extensão adicional.  
  
## <a name="modeling-the-in-reply-to-element"></a>O elemento Responder In para de modelagem  
 Neste exemplo, o `<in-reply-to>` elemento é modelado como CLR implementa <xref:System.Xml.Serialization.IXmlSerializable>, que permite que seu uso com o <xref:System.Runtime.Serialization.DataContractSerializer>. Ele também implementa alguns métodos e propriedades para acessar dados do elemento, conforme mostrado no código de exemplo a seguir.  
  
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
  
 O `InReplyToElement` classe implementa propriedades para o atributo obrigatório (`HRef`, `MediaType`, e `Source`), bem como as coleções para manter <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> e <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A>.  
  
 O `InReplyToElement` classe implementa o <xref:System.Xml.Serialization.IXmlSerializable> interface, que permite o controle direto sobre como instâncias de objeto são ler e gravadas em XML. O `ReadXml` método primeiro lê os valores para o `Ref`, `HRef`, `Source`, e `MediaType` propriedades do <xref:System.Xml.XmlReader> passados para ele. Todos os atributos desconhecidos são armazenados no <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção. Quando todos os atributos são lidos, <xref:System.Xml.XmlReader.ReadStartElement> é chamado para avançar o leitor para o próximo elemento. Porque o elemento modelado por essa classe não tiver nenhum filho necessário, os elementos filho obtenham armazenados em buffer na `XElement` instâncias e armazenados no <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção, conforme mostrado no código a seguir.  
  
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
  
 Em `WriteXml`, o `InReplyToElement` método primeiro grava os valores da `Ref`, `HRef`, `Source`, e `MediaType` propriedades como atributos XML (`WriteXml` não é responsável por gravar o elemento externo real em si, que é feito pelo chamador de `WriteXml`). Ele também grava o conteúdo do <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> e <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> para o gravador, conforme mostrado no código a seguir.  
  
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
  
## <a name="threadedfeed-and-threadeditem"></a>ThreadedFeed e ThreadedItem  
 No exemplo, `SyndicationItems` com `InReplyTo` extensões são modeladas pela `ThreadedItem` classe. Da mesma forma, o `ThreadedFeed` classe é um `SyndicationFeed` cujos itens são todas as instâncias de `ThreadedItem`.  
  
 O `ThreadedFeed` classe herda de `SyndicationFeed` e substituições `OnCreateItem` para retornar um `ThreadedItem`. Ele também implementa um método para acessar o `Items` coleção como `ThreadedItems`, conforme mostrado no código a seguir.  
  
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
  
 A classe `ThreadedItem` herda de `SyndicationItem` e torna `InReplyToElement` como uma propriedade fortemente tipada. Isso fornece acesso programático conveniente para o `InReplyTo` dados de extensão. Ele também implementa `TryParseElement` e `WriteElementExtensions` para ler e gravar os dados de extensão, conforme mostrado no código a seguir.  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Syndication\StronglyTypedExtensions`  
  
## <a name="see-also"></a>Consulte também
