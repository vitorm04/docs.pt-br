---
title: Exemplo de extensões tipadas vagamente
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 19d39e4a70022304262c5872636d3ea03a3b861b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668477"
---
# <a name="loosely-typed-extensions-sample"></a>Exemplo de extensões tipadas vagamente
O modelo de objeto de Sindicalização fornece suporte avançado para trabalhar com dados de extensão — informações que está presentes em um feed de sindicalização da representação XML, mas não são explicitamente expostas pelas classes, como <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem>. Este exemplo ilustra as técnicas básicas para trabalhar com dados de extensão.  
  
 O exemplo usa o <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para os fins do exemplo. No entanto, os padrões demonstrados nesse exemplo podem ser usados com todas as classes de distribuição que dão suporte a dados de extensão:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>XML de exemplo  
 Para referência, o seguinte documento XML é usado neste exemplo.  
  
```xml  
<?xml version="1.0" encoding="IBM437"?>  
<feed myAttribute="someValue" xmlns="http://www.w3.org/2005/Atom">  
  <title type="text"></title>  
  <id>uuid:8f60c7b3-a3c0-4de7-a642-2165d77ce3c1;id=1</id>  
  <updated>2007-09-07T22:15:34Z</updated>  
  <simpleString xmlns="">hello, world!</simpleString>  
  <simpleString xmlns="">another simple string</simpleString>  
  <DataContractExtension xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.d  
atacontract.org/2004/07/Microsoft.Syndication.Samples">  
    <Key>X</Key>  
    <Value>4</Value>  
  </DataContractExtension>  
  <XmlSerializerExtension xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://ww  
w.w3.org/2001/XMLSchema" xmlns="">  
    <Key>Y</Key>  
    <Value>8</Value>  
  </XmlSerializerExtension>  
  <xElementExtension xmlns="">  
    <Key attr1="someValue">Z</Key>  
    <Value attr1="someValue">15</Value>  
  </xElementExtension>  
</feed>  
```  
  
 Este documento contém as seguintes partes de dados de extensão:  
  
-   O `myAttribute` atributo do `<feed>` elemento.  
  
-   `<simpleString>` elemento.  
  
-   `<DataContractExtension>` elemento.  
  
-   `<XmlSerializerExtension>` elemento.  
  
-   `<xElementExtension>` elemento.  
  
## <a name="writing-extension-data"></a>Gravação de dados de extensão  
 Extensões de atributo são criadas adicionando entradas ao <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção conforme mostrado no código de exemplo a seguir.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Extensões de elemento são criadas adicionando entradas ao <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção. Essas extensões podem por valores básicos, como cadeias de caracteres, serializações de XML de objetos do .NET Framework ou nós XML codificados manualmente.  
  
 O código de exemplo a seguir cria um elemento de extensão chamado `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 O namespace XML para este elemento é o namespace vazio ("") e seu valor é um nó de texto que contém a cadeia de caracteres "hello, world!".  
  
 Uma maneira para criar extensões de elemento complexo que consistem em muitos elementos aninhados é usar as APIs do .NET Framework para serialização (tanto a <xref:System.Runtime.Serialization.DataContractSerializer> e o <xref:System.Xml.Serialization.XmlSerializer> têm suporte) conforme mostrado nos exemplos a seguir.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Neste exemplo, o `DataContractExtension` e `XmlSerializerExtension` são escritos para uso com um serializador de tipos personalizados.  
  
 O <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> classe também pode ser usada para criar extensões de elemento de um <xref:System.Xml.XmlReader> instância. Isso permite fácil integração com XML processamento de APIs, como <xref:System.Xml.Linq.XElement> conforme mostrado no código de exemplo a seguir.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Lendo dados de extensão  
 Os valores para as extensões de atributo podem ser obtidos examinando o atributo na <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção por seu <xref:System.Xml.XmlQualifiedName> conforme mostrado no código de exemplo a seguir.  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Extensões de elemento são acessadas usando o `ReadElementExtensions<T>` método.  
  
```  
foreach( string s in feed2.ElementExtensions.ReadElementExtensions<string>("simpleString", ""))  
{  
    Console.WriteLine(s);  
}  
  
foreach (DataContractExtension dce in feed2.ElementExtensions.ReadElementExtensions<DataContractExtension>("DataContractExtension",  
"http://schemas.datacontract.org/2004/07/SyndicationExtensions"))  
{  
    Console.WriteLine(dce.ToString());  
}  
  
foreach (XmlSerializerExtension xse in feed2.ElementExtensions.ReadElementExtensions<XmlSerializerExtension>("XmlSerializerExtension", "", new XmlSerializer(typeof(XmlSerializerExtension))))  
{  
    Console.WriteLine(xse.ToString());  
}  
```  
  
 Também é possível obter um `XmlReader` em extensões de elemento individual usando o <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> método.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Consulte também
- [Extensões fortemente tipadas](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
