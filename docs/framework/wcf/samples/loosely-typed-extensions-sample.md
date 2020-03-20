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
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="343ba-102">Exemplo de extensões tipadas vagamente</span><span class="sxs-lookup"><span data-stu-id="343ba-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="343ba-103">O modelo de objeto Syndication fornece um rico suporte para trabalhar com dados de extensão — informações que estão <xref:System.ServiceModel.Syndication.SyndicationFeed> presentes <xref:System.ServiceModel.Syndication.SyndicationItem>na representação XML de um feed de sindicância, mas não explicitamente expostas por classes como e .</span><span class="sxs-lookup"><span data-stu-id="343ba-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="343ba-104">Esta amostra ilustra as técnicas básicas para trabalhar com dados de extensão.</span><span class="sxs-lookup"><span data-stu-id="343ba-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="343ba-105">A amostra <xref:System.ServiceModel.Syndication.SyndicationFeed> usa a classe para efeitos do exemplo.</span><span class="sxs-lookup"><span data-stu-id="343ba-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="343ba-106">No entanto, os padrões demonstrados nesta amostra podem ser usados com todas as classes de Sindicância que suportam dados de extensão:</span><span class="sxs-lookup"><span data-stu-id="343ba-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="343ba-107">XML de exemplo</span><span class="sxs-lookup"><span data-stu-id="343ba-107">Sample XML</span></span>  
 <span data-ttu-id="343ba-108">Para referência, o seguinte documento XML é usado nesta amostra.</span><span class="sxs-lookup"><span data-stu-id="343ba-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="343ba-109">Este documento contém os seguintes dados de extensão:</span><span class="sxs-lookup"><span data-stu-id="343ba-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="343ba-110">O atributo `myAttribute` do elemento `<feed>`.</span><span class="sxs-lookup"><span data-stu-id="343ba-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="343ba-111">Elemento `<simpleString>`.</span><span class="sxs-lookup"><span data-stu-id="343ba-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="343ba-112">Elemento `<DataContractExtension>`.</span><span class="sxs-lookup"><span data-stu-id="343ba-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="343ba-113">Elemento `<XmlSerializerExtension>`.</span><span class="sxs-lookup"><span data-stu-id="343ba-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="343ba-114">Elemento `<xElementExtension>`.</span><span class="sxs-lookup"><span data-stu-id="343ba-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="343ba-115">Dados de extensão de gravação</span><span class="sxs-lookup"><span data-stu-id="343ba-115">Writing Extension Data</span></span>  
 <span data-ttu-id="343ba-116">As extensões de atributo são <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> criadas adicionando entradas à coleção, conforme mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="343ba-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="343ba-117">As extensões de elemento são criadas adicionando entradas à <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="343ba-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="343ba-118">Essas extensões podem por valores básicos, como strings, serializações XML de objetos .NET Framework ou nós XML codificados à mão.</span><span class="sxs-lookup"><span data-stu-id="343ba-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="343ba-119">O código de amostra a `simpleString`seguir cria um elemento de extensão chamado .</span><span class="sxs-lookup"><span data-stu-id="343ba-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="343ba-120">O espaço de nome XML para este elemento é o namespace vazio (""") e seu valor é um nó de texto que contém a string "hello, world!".</span><span class="sxs-lookup"><span data-stu-id="343ba-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="343ba-121">Uma maneira de criar extensões de elementos complexos que consistem em muitos elementos <xref:System.Runtime.Serialization.DataContractSerializer> aninhados é usar as APIs do Quadro .NET para serialização (tanto as suportadas quanto as <xref:System.Xml.Serialization.XmlSerializer> suportadas) como mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="343ba-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="343ba-122">Neste exemplo, `DataContractExtension` os `XmlSerializerExtension` e são tipos personalizados escritos para uso com um serializador.</span><span class="sxs-lookup"><span data-stu-id="343ba-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="343ba-123">A <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> classe também pode ser usada para <xref:System.Xml.XmlReader> criar extensões de elemento a partir de uma instância.</span><span class="sxs-lookup"><span data-stu-id="343ba-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="343ba-124">Isso permite uma fácil integração com APIs de processamento XML, como <xref:System.Xml.Linq.XElement> mostrado no código de amostra a seguir.</span><span class="sxs-lookup"><span data-stu-id="343ba-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="343ba-125">Leitura de dados de extensão</span><span class="sxs-lookup"><span data-stu-id="343ba-125">Reading Extension Data</span></span>  
 <span data-ttu-id="343ba-126">Os valores para extensões de atributos podem <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> ser <xref:System.Xml.XmlQualifiedName> obtidos pesquisando o atributo na coleção por seu conforme mostrado no código amostral a seguir.</span><span class="sxs-lookup"><span data-stu-id="343ba-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="343ba-127">Extensões de elemento são `ReadElementExtensions<T>` acessadas usando o método.</span><span class="sxs-lookup"><span data-stu-id="343ba-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="343ba-128">Também é possível obter `XmlReader` uma extensão de <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> elemento individual usando o método.</span><span class="sxs-lookup"><span data-stu-id="343ba-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="343ba-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="343ba-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="343ba-130">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="343ba-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="343ba-131">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="343ba-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="343ba-132">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="343ba-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="343ba-133">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="343ba-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="343ba-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="343ba-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="343ba-135">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="343ba-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="343ba-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="343ba-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="343ba-137">Confira também</span><span class="sxs-lookup"><span data-stu-id="343ba-137">See also</span></span>

- [<span data-ttu-id="343ba-138">Extensões fortemente tipadas</span><span class="sxs-lookup"><span data-stu-id="343ba-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="343ba-139">Sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="343ba-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
