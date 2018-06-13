---
title: Serializando com uma declaração XML (C#)
ms.date: 07/20/2015
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 3f331f1226e7e5a905471f4a793f9a415bdd858a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33329781"
---
# <a name="serializing-with-an-xml-declaration-c"></a><span data-ttu-id="45f82-102">Serializando com uma declaração XML (C#)</span><span class="sxs-lookup"><span data-stu-id="45f82-102">Serializing with an XML Declaration (C#)</span></span>
<span data-ttu-id="45f82-103">Este tópico descreve como controlar se a serialização gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="45f82-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="45f82-104">Geração da declaração XML</span><span class="sxs-lookup"><span data-stu-id="45f82-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="45f82-105">Serializar para um <xref:System.IO.File> ou <xref:System.IO.TextWriter> usando o método <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou o método <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="45f82-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="45f82-106">Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador (especificadas em um objeto <xref:System.Xml.XmlWriterSettings>) determinam se uma declaração XML é gerada ou não.</span><span class="sxs-lookup"><span data-stu-id="45f82-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="45f82-107">Se você estiver serialização para uma cadeia de caracteres usando o método `ToString`, o XML resultante não incluirá uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="45f82-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="45f82-108">Serializando com uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="45f82-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="45f82-109">O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e imprime o arquivo no console:</span><span class="sxs-lookup"><span data-stu-id="45f82-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
```  
  
 <span data-ttu-id="45f82-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="45f82-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="45f82-111">Serializando sem uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="45f82-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="45f82-112">O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement> em um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="45f82-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="45f82-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="45f82-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45f82-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45f82-114">See Also</span></span>  
 [<span data-ttu-id="45f82-115">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="45f82-115">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
