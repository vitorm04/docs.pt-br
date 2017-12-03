---
title: "Exemplo de extensões tipadas vagamente"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 280445240dae215013069c65ab12b9e38227f5c1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="loosely-typed-extensions-sample"></a>Exemplo de extensões tipadas vagamente
O modelo de objeto de distribuição fornece suporte rico para trabalhar com dados de extensão — informações que está presentes em um feed de distribuição da representação XML, mas não são explicitamente expostos pelas classes como <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem>. Este exemplo ilustra as técnicas básicas para trabalhar com dados de extensão.  
  
 O exemplo usa o <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para fins de exemplo. No entanto, os padrões demonstrados neste exemplo podem ser usados com todas as classes de distribuição que oferecem suporte a dados de extensão:  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a>Exemplo de XML  
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
  
 Este documento contém as seguintes partes dos dados de extensão:  
  
-   O `myAttribute` atributo o `<feed>` elemento.  
  
-   `<simpleString>`elemento.  
  
-   `<DataContractExtension>`elemento.  
  
-   `<XmlSerializerExtension>`elemento.  
  
-   `<xElementExtension>`elemento.  
  
## <a name="writing-extension-data"></a>Gravando dados de extensão  
 Extensões de atributo são criadas com a adição de entradas para o <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção conforme mostrado no código de exemplo a seguir.  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 Extensões de elemento são criadas com a adição de entradas para o <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção. Essas extensões podem valores básicos, como cadeias de caracteres, serializações de XML de objetos do .NET Framework ou nós XML codificados manualmente.  
  
 O código de exemplo a seguir cria um elemento de extensão denominado `simpleString`.  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 O namespace XML para este elemento é o namespace vazio ("") e seu valor é um nó de texto que contém a cadeia de caracteres "Olá, mundo!".  
  
 Uma maneira de criar extensões de elementos complexos que consistem em vários elementos aninhados é usar as APIs do .NET Framework para serialização (tanto o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> são suportados) conforme mostrado nos exemplos a seguir.  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 Neste exemplo, o `DataContractExtension` e `XmlSerializerExtension` são criados para serem usados com um serializador de tipos personalizados.  
  
 O <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> classe também pode ser usada para criar extensões de elemento de um <xref:System.Xml.XmlReader> instância. Isso permite fácil integração com XML processamento APIs, como <xref:System.Xml.Linq.XElement> conforme mostrado no código de exemplo a seguir.  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a>Lendo dados de extensão  
 Os valores para as extensões de atributo podem ser obtidos pesquisando o atributo de <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção por seu <xref:System.Xml.XmlQualifiedName> conforme mostrado no código de exemplo a seguir.  
  
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
  
 Também é possível obter um `XmlReader` em extensões de elementos individuais usando o <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> método.  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a>Consulte também  
 [Extensões fortemente tipadas](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [Sindicalização do WCF](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
