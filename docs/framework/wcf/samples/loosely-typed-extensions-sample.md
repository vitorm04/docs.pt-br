---
title: Exemplo de extensões tipadas vagamente
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 5d3defacc4a0acee69e32667d0d9213320b3ccec
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202222"
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="4f21f-102">Exemplo de extensões tipadas vagamente</span><span class="sxs-lookup"><span data-stu-id="4f21f-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="4f21f-103">O modelo de objeto de distribuição fornece suporte avançado para trabalhar com dados de extensão — informações que estão presentes na representação XML de um feed de agregação, mas não são explicitamente expostos por classes como <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem> .</span><span class="sxs-lookup"><span data-stu-id="4f21f-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="4f21f-104">Este exemplo ilustra as técnicas básicas para trabalhar com dados de extensão.</span><span class="sxs-lookup"><span data-stu-id="4f21f-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="4f21f-105">O exemplo usa a <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para os fins do exemplo.</span><span class="sxs-lookup"><span data-stu-id="4f21f-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="4f21f-106">No entanto, os padrões demonstrados neste exemplo podem ser usados com todas as classes de distribuição que dão suporte a dados de extensão:</span><span class="sxs-lookup"><span data-stu-id="4f21f-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="4f21f-107">XML de exemplo</span><span class="sxs-lookup"><span data-stu-id="4f21f-107">Sample XML</span></span>  
 <span data-ttu-id="4f21f-108">Para referência, o documento XML a seguir é usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4f21f-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="4f21f-109">Este documento contém as seguintes partes de dados de extensão:</span><span class="sxs-lookup"><span data-stu-id="4f21f-109">This document contains the following pieces of extension data:</span></span>  
  
- <span data-ttu-id="4f21f-110">O atributo `myAttribute` do elemento `<feed>`.</span><span class="sxs-lookup"><span data-stu-id="4f21f-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
- <span data-ttu-id="4f21f-111">Elemento `<simpleString>`.</span><span class="sxs-lookup"><span data-stu-id="4f21f-111">`<simpleString>` element.</span></span>  
  
- <span data-ttu-id="4f21f-112">Elemento `<DataContractExtension>`.</span><span class="sxs-lookup"><span data-stu-id="4f21f-112">`<DataContractExtension>` element.</span></span>  
  
- <span data-ttu-id="4f21f-113">Elemento `<XmlSerializerExtension>`.</span><span class="sxs-lookup"><span data-stu-id="4f21f-113">`<XmlSerializerExtension>` element.</span></span>  
  
- <span data-ttu-id="4f21f-114">Elemento `<xElementExtension>`.</span><span class="sxs-lookup"><span data-stu-id="4f21f-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="4f21f-115">Gravando dados de extensão</span><span class="sxs-lookup"><span data-stu-id="4f21f-115">Writing Extension Data</span></span>  
 <span data-ttu-id="4f21f-116">As extensões de atributo são criadas adicionando entradas à <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f21f-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```csharp  
//Attribute extensions are stored in a dictionary indexed by
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="4f21f-117">As extensões de elemento são criadas adicionando entradas à <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="4f21f-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="4f21f-118">Essas extensões podem ser por valores básicos, como cadeias de caracteres, serializações XML de objetos .NET Framework ou nós XML codificados manualmente.</span><span class="sxs-lookup"><span data-stu-id="4f21f-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="4f21f-119">O código de exemplo a seguir cria um elemento de extensão chamado `simpleString` .</span><span class="sxs-lookup"><span data-stu-id="4f21f-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```csharp  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="4f21f-120">O namespace XML para esse elemento é o namespace vazio ("") e seu valor é um nó de texto que contém a cadeia de caracteres "Olá, mundo!".</span><span class="sxs-lookup"><span data-stu-id="4f21f-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="4f21f-121">Uma maneira de criar extensões de elemento complexas que consistem em muitos elementos aninhados é usar as APIs de .NET Framework para serialização (tanto <xref:System.Runtime.Serialization.DataContractSerializer> quanto as <xref:System.Xml.Serialization.XmlSerializer> têm suporte), conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f21f-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```csharp  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="4f21f-122">Neste exemplo, `DataContractExtension` e `XmlSerializerExtension` são tipos personalizados escritos para uso com um serializador.</span><span class="sxs-lookup"><span data-stu-id="4f21f-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="4f21f-123">A <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> classe também pode ser usada para criar extensões de elemento de uma <xref:System.Xml.XmlReader> instância do.</span><span class="sxs-lookup"><span data-stu-id="4f21f-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="4f21f-124">Isso permite uma fácil integração com APIs de processamento XML, como <xref:System.Xml.Linq.XElement> mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f21f-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```csharp  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="4f21f-125">Lendo dados de extensão</span><span class="sxs-lookup"><span data-stu-id="4f21f-125">Reading Extension Data</span></span>  
 <span data-ttu-id="4f21f-126">Os valores para extensões de atributo podem ser obtidos pesquisando o atributo na <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção por seu <xref:System.Xml.XmlQualifiedName> , conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f21f-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```csharp  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="4f21f-127">As extensões de elemento são acessadas usando o `ReadElementExtensions<T>` método.</span><span class="sxs-lookup"><span data-stu-id="4f21f-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="4f21f-128">Também é possível obter um `XmlReader` em extensões de elemento individuais usando o <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> método.</span><span class="sxs-lookup"><span data-stu-id="4f21f-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```csharp  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f21f-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="4f21f-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="4f21f-130">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f21f-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="4f21f-131">Para criar a edição C# ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f21f-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="4f21f-132">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4f21f-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="4f21f-133">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="4f21f-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f21f-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="4f21f-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4f21f-135">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="4f21f-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f21f-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="4f21f-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="4f21f-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="4f21f-137">See also</span></span>

- [<span data-ttu-id="4f21f-138">Extensões com rigidez de tipos</span><span class="sxs-lookup"><span data-stu-id="4f21f-138">Strongly typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)
- [<span data-ttu-id="4f21f-139">Sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="4f21f-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
