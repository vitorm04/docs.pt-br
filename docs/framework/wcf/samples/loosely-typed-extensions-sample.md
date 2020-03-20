---
title: Exemplo de extensões tipadas vagamente
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: b8d1d42864b8764551cc44a26d820090eb28971e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183543"
---
# <a name="loosely-typed-extensions-sample"></a>Exemplo de extensões tipadas vagamente
O modelo de objeto Syndication fornece um rico suporte para trabalhar com dados de extensão — informações que estão <xref:System.ServiceModel.Syndication.SyndicationFeed> presentes <xref:System.ServiceModel.Syndication.SyndicationItem>na representação XML de um feed de sindicância, mas não explicitamente expostas por classes como e . Esta amostra ilustra as técnicas básicas para trabalhar com dados de extensão.  
  
 A amostra <xref:System.ServiceModel.Syndication.SyndicationFeed> usa a classe para efeitos do exemplo. No entanto, os padrões demonstrados nesta amostra podem ser usados com todas as classes de Sindicância que suportam dados de extensão:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>XML de exemplo  
 Para referência, o seguinte documento XML é usado nesta amostra.  
  
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
  
 Este documento contém os seguintes dados de extensão:  
  
- O atributo `myAttribute` do elemento `<feed>`.  
  
- Elemento `<simpleString>`.  
  
- Elemento `<DataContractExtension>`.  
  
- Elemento `<XmlSerializerExtension>`.  
  
- Elemento `<xElementExtension>`.  
  
## <a name="writing-extension-data"></a>Dados de extensão de gravação  
 As extensões de atributo são <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> criadas adicionando entradas à coleção, conforme mostrado no código de amostra a seguir.  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 As extensões de elemento são criadas adicionando entradas à <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção. Essas extensões podem por valores básicos, como strings, serializações XML de objetos .NET Framework ou nós XML codificados à mão.  
  
 O código de amostra a `simpleString`seguir cria um elemento de extensão chamado .  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 O espaço de nome XML para este elemento é o namespace vazio (""") e seu valor é um nó de texto que contém a string "hello, world!".  
  
 Uma maneira de criar extensões de elementos complexos que consistem em muitos elementos <xref:System.Runtime.Serialization.DataContractSerializer> aninhados é usar as APIs do Quadro .NET para serialização (tanto as suportadas quanto as <xref:System.Xml.Serialization.XmlSerializer> suportadas) como mostrado nos exemplos a seguir.  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Neste exemplo, `DataContractExtension` os `XmlSerializerExtension` e são tipos personalizados escritos para uso com um serializador.  
  
 A <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> classe também pode ser usada para <xref:System.Xml.XmlReader> criar extensões de elemento a partir de uma instância. Isso permite uma fácil integração com APIs de processamento XML, como <xref:System.Xml.Linq.XElement> mostrado no código de amostra a seguir.  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Leitura de dados de extensão  
 Os valores para extensões de atributos podem <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ser <xref:System.Xml.XmlQualifiedName> obtidos pesquisando o atributo na coleção por seu conforme mostrado no código amostral a seguir.  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 Extensões de elemento são `ReadElementExtensions<T>` acessadas usando o método.  
  
```csharp  
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
  
 Também é possível obter `XmlReader` uma extensão de <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> elemento individual usando o método.  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Confira também

- [Extensões fortemente tipadas](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
