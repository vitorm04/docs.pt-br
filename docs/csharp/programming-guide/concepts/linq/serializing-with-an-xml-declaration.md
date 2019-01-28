---
title: Serializando com uma declaração XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 4f5dd9a7e392acff30814db4a483b297494b68b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702399"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="d0211-102">Serializando com uma declaração XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d0211-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="d0211-103">Este tópico descreve como controlar se a serialização gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="d0211-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="d0211-104">Geração da declaração XML</span><span class="sxs-lookup"><span data-stu-id="d0211-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="d0211-105">Serializar para um <xref:System.IO.File> ou <xref:System.IO.TextWriter> usando o método <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou o método <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="d0211-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="d0211-106">Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador (especificadas em um objeto <xref:System.Xml.XmlWriterSettings>) determinam se uma declaração XML é gerada ou não.</span><span class="sxs-lookup"><span data-stu-id="d0211-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="d0211-107">Se você estiver serialização para uma cadeia de caracteres usando o método `ToString`, o XML resultante não incluirá uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="d0211-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="d0211-108">Serializando com uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="d0211-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="d0211-109">O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e imprime o arquivo no console:</span><span class="sxs-lookup"><span data-stu-id="d0211-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="d0211-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d0211-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="d0211-111">Serializando sem uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="d0211-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="d0211-112">O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement> em um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="d0211-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```csharp  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 <span data-ttu-id="d0211-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="d0211-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0211-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0211-114">See also</span></span>

- [<span data-ttu-id="d0211-115">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="d0211-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
