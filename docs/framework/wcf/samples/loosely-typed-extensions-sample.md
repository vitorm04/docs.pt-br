---
title: Exemplo de extensões tipadas vagamente
ms.date: 03/30/2017
ms.assetid: 56ce265b-8163-4b85-98e7-7692a12c4357
ms.openlocfilehash: 9ad00c1e76d14b32cb28216cfdbb1a01f82a70cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="loosely-typed-extensions-sample"></a><span data-ttu-id="420e5-102">Exemplo de extensões tipadas vagamente</span><span class="sxs-lookup"><span data-stu-id="420e5-102">Loosely-Typed Extensions Sample</span></span>
<span data-ttu-id="420e5-103">O modelo de objeto de distribuição fornece suporte rico para trabalhar com dados de extensão — informações que está presentes em um feed de distribuição da representação XML, mas não são explicitamente expostos pelas classes como <xref:System.ServiceModel.Syndication.SyndicationFeed> e <xref:System.ServiceModel.Syndication.SyndicationItem>.</span><span class="sxs-lookup"><span data-stu-id="420e5-103">The Syndication object model provides rich support for working with extension data—information that is present in a syndication feed's XML representation but not explicitly exposed by classes such as <xref:System.ServiceModel.Syndication.SyndicationFeed> and <xref:System.ServiceModel.Syndication.SyndicationItem>.</span></span> <span data-ttu-id="420e5-104">Este exemplo ilustra as técnicas básicas para trabalhar com dados de extensão.</span><span class="sxs-lookup"><span data-stu-id="420e5-104">This sample illustrates the basic techniques for working with extension data.</span></span>  
  
 <span data-ttu-id="420e5-105">O exemplo usa o <xref:System.ServiceModel.Syndication.SyndicationFeed> classe para fins de exemplo.</span><span class="sxs-lookup"><span data-stu-id="420e5-105">The sample uses the <xref:System.ServiceModel.Syndication.SyndicationFeed> class for the purposes of the example.</span></span> <span data-ttu-id="420e5-106">No entanto, os padrões demonstrados neste exemplo podem ser usados com todas as classes de distribuição que oferecem suporte a dados de extensão:</span><span class="sxs-lookup"><span data-stu-id="420e5-106">However, the patterns demonstrated in this sample can be used with all of the Syndication classes that support extension data:</span></span>  
  
 <xref:System.ServiceModel.Syndication.SyndicationFeed>  
  
 <xref:System.ServiceModel.Syndication.SyndicationItem>  
  
 <xref:System.ServiceModel.Syndication.SyndicationCategory>  
  
 <xref:System.ServiceModel.Syndication.SyndicationPerson>  
  
 <xref:System.ServiceModel.Syndication.SyndicationLink>  
  
## <a name="sample-xml"></a><span data-ttu-id="420e5-107">Exemplo de XML</span><span class="sxs-lookup"><span data-stu-id="420e5-107">Sample XML</span></span>  
 <span data-ttu-id="420e5-108">Para referência, o seguinte documento XML é usado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="420e5-108">For reference, the following XML document is used in this sample.</span></span>  
  
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
  
 <span data-ttu-id="420e5-109">Este documento contém as seguintes partes dos dados de extensão:</span><span class="sxs-lookup"><span data-stu-id="420e5-109">This document contains the following pieces of extension data:</span></span>  
  
-   <span data-ttu-id="420e5-110">O `myAttribute` atributo o `<feed>` elemento.</span><span class="sxs-lookup"><span data-stu-id="420e5-110">The `myAttribute` attribute of the `<feed>` element.</span></span>  
  
-   <span data-ttu-id="420e5-111">`<simpleString>` elemento.</span><span class="sxs-lookup"><span data-stu-id="420e5-111">`<simpleString>` element.</span></span>  
  
-   <span data-ttu-id="420e5-112">`<DataContractExtension>` elemento.</span><span class="sxs-lookup"><span data-stu-id="420e5-112">`<DataContractExtension>` element.</span></span>  
  
-   <span data-ttu-id="420e5-113">`<XmlSerializerExtension>` elemento.</span><span class="sxs-lookup"><span data-stu-id="420e5-113">`<XmlSerializerExtension>` element.</span></span>  
  
-   <span data-ttu-id="420e5-114">`<xElementExtension>` elemento.</span><span class="sxs-lookup"><span data-stu-id="420e5-114">`<xElementExtension>` element.</span></span>  
  
## <a name="writing-extension-data"></a><span data-ttu-id="420e5-115">Gravando dados de extensão</span><span class="sxs-lookup"><span data-stu-id="420e5-115">Writing Extension Data</span></span>  
 <span data-ttu-id="420e5-116">Extensões de atributo são criadas com a adição de entradas para o <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="420e5-116">Attribute extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection as shown in the following sample code.</span></span>  
  
```  
//Attribute extensions are stored in a dictionary indexed by   
// XmlQualifiedName  
feed.AttributeExtensions.Add(new XmlQualifiedName("myAttribute", ""), "someValue");  
```  
  
 <span data-ttu-id="420e5-117">Extensões de elemento são criadas com a adição de entradas para o <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="420e5-117">Element extensions are created by adding entries to the <xref:System.ServiceModel.Syndication.SyndicationFeed.ElementExtensions%2A> collection.</span></span> <span data-ttu-id="420e5-118">Essas extensões podem valores básicos, como cadeias de caracteres, serializações de XML de objetos do .NET Framework ou nós XML codificados manualmente.</span><span class="sxs-lookup"><span data-stu-id="420e5-118">These extensions can by basic values such as strings, XML serializations of .NET Framework objects, or XML nodes coded by hand.</span></span>  
  
 <span data-ttu-id="420e5-119">O código de exemplo a seguir cria um elemento de extensão denominado `simpleString`.</span><span class="sxs-lookup"><span data-stu-id="420e5-119">The following sample code creates an extension element named `simpleString`.</span></span>  
  
```  
feed.ElementExtensions.Add("simpleString", "", "hello, world!");  
```  
  
 <span data-ttu-id="420e5-120">O namespace XML para este elemento é o namespace vazio ("") e seu valor é um nó de texto que contém a cadeia de caracteres "Olá, mundo!".</span><span class="sxs-lookup"><span data-stu-id="420e5-120">The XML namespace for this element is the empty namespace ("") and its value is a text node that contains the string "hello, world!".</span></span>  
  
 <span data-ttu-id="420e5-121">Uma maneira de criar extensões de elementos complexos que consistem em vários elementos aninhados é usar as APIs do .NET Framework para serialização (tanto o <xref:System.Runtime.Serialization.DataContractSerializer> e <xref:System.Xml.Serialization.XmlSerializer> são suportados) conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="420e5-121">One way to create complex element extensions that consist of many nested elements is to use the .NET Framework APIs for serialization (both the <xref:System.Runtime.Serialization.DataContractSerializer> and the <xref:System.Xml.Serialization.XmlSerializer> are supported) as shown in the following examples.</span></span>  
  
```  
feed.ElementExtensions.Add( new DataContractExtension() { Key = "X", Value = 4 } );  
feed.ElementExtensions.Add( new XmlSerializerExtension { Key = "Y", Value = 8 }, new XmlSerializer( typeof( XmlSerializerExtension ) ) );  
```  
  
 <span data-ttu-id="420e5-122">Neste exemplo, o `DataContractExtension` e `XmlSerializerExtension` são criados para serem usados com um serializador de tipos personalizados.</span><span class="sxs-lookup"><span data-stu-id="420e5-122">In this example, the `DataContractExtension` and `XmlSerializerExtension` are custom types written for use with a serializer.</span></span>  
  
 <span data-ttu-id="420e5-123">O <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> classe também pode ser usada para criar extensões de elemento de um <xref:System.Xml.XmlReader> instância.</span><span class="sxs-lookup"><span data-stu-id="420e5-123">The <xref:System.ServiceModel.Syndication.SyndicationElementExtensionCollection> class can also be used to create element extensions from an <xref:System.Xml.XmlReader> instance.</span></span> <span data-ttu-id="420e5-124">Isso permite fácil integração com XML processamento APIs, como <xref:System.Xml.Linq.XElement> conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="420e5-124">This allows for easy integration with XML processing APIs such as <xref:System.Xml.Linq.XElement> as shown in the following sample code.</span></span>  
  
```  
feed.ElementExtensions.Add(new XElement("xElementExtension",  
        new XElement("Key", new XAttribute("attr1", "someValue"), "Z"),  
        new XElement("Value", new XAttribute("attr1", "someValue"),   
        "15")).CreateReader());  
```  
  
## <a name="reading-extension-data"></a><span data-ttu-id="420e5-125">Lendo dados de extensão</span><span class="sxs-lookup"><span data-stu-id="420e5-125">Reading Extension Data</span></span>  
 <span data-ttu-id="420e5-126">Os valores para as extensões de atributo podem ser obtidos pesquisando o atributo de <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> coleção por seu <xref:System.Xml.XmlQualifiedName> conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="420e5-126">The values for attribute extensions can be obtained by looking up the attribute in the <xref:System.ServiceModel.Syndication.SyndicationFeed.AttributeExtensions%2A> collection by its <xref:System.Xml.XmlQualifiedName> as shown in the following sample code.</span></span>  
  
```  
Console.WriteLine( feed.AttributeExtensions[ new XmlQualifiedName( "myAttribute", "" )]);  
```  
  
 <span data-ttu-id="420e5-127">Extensões de elemento são acessadas usando o `ReadElementExtensions<T>` método.</span><span class="sxs-lookup"><span data-stu-id="420e5-127">Element extensions are accessed using the `ReadElementExtensions<T>` method.</span></span>  
  
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
  
 <span data-ttu-id="420e5-128">Também é possível obter um `XmlReader` em extensões de elementos individuais usando o <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> método.</span><span class="sxs-lookup"><span data-stu-id="420e5-128">It is also possible to obtain an `XmlReader` at individual element extensions by using the <xref:System.ServiceModel.Syndication.SyndicationElementExtension.GetReader> method.</span></span>  
  
```  
foreach (SyndicationElementExtension extension in feed2.ElementExtensions.Where<SyndicationElementExtension>(x => x.OuterName == "xElementExtension"))  
{  
    XNode xelement = XElement.ReadFrom(extension.GetReader());  
    Console.WriteLine(xelement.ToString());  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="420e5-129">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="420e5-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="420e5-130">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="420e5-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="420e5-131">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="420e5-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="420e5-132">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="420e5-132">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="420e5-133">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="420e5-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="420e5-134">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="420e5-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="420e5-135">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="420e5-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="420e5-136">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="420e5-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\LooselyTypedExtensions`  
  
## <a name="see-also"></a><span data-ttu-id="420e5-137">Consulte também</span><span class="sxs-lookup"><span data-stu-id="420e5-137">See Also</span></span>  
 [<span data-ttu-id="420e5-138">Extensões fortemente tipadas</span><span class="sxs-lookup"><span data-stu-id="420e5-138">Strongly-Typed Extensions</span></span>](../../../../docs/framework/wcf/samples/strongly-typed-extensions-sample.md)  
 [<span data-ttu-id="420e5-139">Sindicalização do WCF</span><span class="sxs-lookup"><span data-stu-id="420e5-139">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
