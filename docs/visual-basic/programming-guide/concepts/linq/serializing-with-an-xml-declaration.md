---
title: Serializando com uma declaração XML
ms.date: 07/20/2015
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
ms.openlocfilehash: 96c95b4c94290016684721a194ca31a836a49740
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350628"
---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="51f0c-102">Serializing with an XML Declaration (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51f0c-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="51f0c-103">Este tópico descreve como controlar se a serialização gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="51f0c-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="51f0c-104">Geração da declaração XML</span><span class="sxs-lookup"><span data-stu-id="51f0c-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="51f0c-105">Serializar para um <xref:System.IO.File> ou <xref:System.IO.TextWriter> usando o método <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou o método <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="51f0c-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType> method generates an XML declaration.</span></span> <span data-ttu-id="51f0c-106">Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador (especificadas em um objeto <xref:System.Xml.XmlWriterSettings>) determinam se uma declaração XML é gerada ou não.</span><span class="sxs-lookup"><span data-stu-id="51f0c-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="51f0c-107">Se você estiver serialização para uma cadeia de caracteres usando o método `ToString`, o XML resultante não incluirá uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="51f0c-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="51f0c-108">Serializando com uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="51f0c-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="51f0c-109">O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e imprime o arquivo no console:</span><span class="sxs-lookup"><span data-stu-id="51f0c-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="51f0c-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="51f0c-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="51f0c-111">Serializando sem uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="51f0c-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="51f0c-112">O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement> em um <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="51f0c-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 <span data-ttu-id="51f0c-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="51f0c-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="51f0c-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="51f0c-114">See also</span></span>

- [<span data-ttu-id="51f0c-115">Serializing XML Trees (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51f0c-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
