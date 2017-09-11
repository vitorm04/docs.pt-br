---
title: "Serializando com uma declaração XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 50707da956df593f176764bed94adfc6aec3dfa5
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a><span data-ttu-id="bf495-102">Serializando com uma declaração XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf495-102">Serializing with an XML Declaration (Visual Basic)</span></span>
<span data-ttu-id="bf495-103">Este tópico descreve como controlar se a serialização gera uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="bf495-103">This topic describes how to control whether serialization generates an XML declaration.</span></span>  
  
## <a name="xml-declaration-generation"></a><span data-ttu-id="bf495-104">Geração da declaração XML</span><span class="sxs-lookup"><span data-stu-id="bf495-104">XML Declaration Generation</span></span>  
 <span data-ttu-id="bf495-105">Serializando um <xref:System.IO.File>ou um <xref:System.IO.TextWriter>usando o <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>método ou o <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>método gera uma declaração XML.</xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> </xref:System.IO.TextWriter> </xref:System.IO.File></span><span class="sxs-lookup"><span data-stu-id="bf495-105">Serializing to a <xref:System.IO.File> or a <xref:System.IO.TextWriter> using the <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> method or the <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> method generates an XML declaration.</span></span> <span data-ttu-id="bf495-106">Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador (especificado em uma <xref:System.Xml.XmlWriterSettings>objeto) determinam se uma declaração XML é gerada ou não.</xref:System.Xml.XmlWriterSettings> </xref:System.Xml.XmlWriter></span><span class="sxs-lookup"><span data-stu-id="bf495-106">When you serialize to an <xref:System.Xml.XmlWriter>, the writer settings (specified in an <xref:System.Xml.XmlWriterSettings> object) determine whether an XML declaration is generated or not.</span></span>  
  
 <span data-ttu-id="bf495-107">Se você estiver serialização para uma cadeia de caracteres usando o método `ToString`, o XML resultante não incluirá uma declaração XML.</span><span class="sxs-lookup"><span data-stu-id="bf495-107">If you are serializing to a string using the `ToString` method, the resulting XML will not include an XML declaration.</span></span>  
  
### <a name="serializing-with-an-xml-declaration"></a><span data-ttu-id="bf495-108">Serializando com uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="bf495-108">Serializing with an XML Declaration</span></span>  
 <span data-ttu-id="bf495-109">O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e, em seguida, imprime o arquivo de console:</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="bf495-109">The following example creates an <xref:System.Xml.Linq.XElement>, saves the document to a file, and then prints the file to the console:</span></span>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 <span data-ttu-id="bf495-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bf495-110">This example produces the following output:</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a><span data-ttu-id="bf495-111">Serializando sem uma declaração XML</span><span class="sxs-lookup"><span data-stu-id="bf495-111">Serializing without an XML Declaration</span></span>  
 <span data-ttu-id="bf495-112">O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement>a um <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="bf495-112">The following example shows how to save an <xref:System.Xml.Linq.XElement> to an <xref:System.Xml.XmlWriter>.</span></span>  
  
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
  
 <span data-ttu-id="bf495-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="bf495-113">This example produces the following output:</span></span>  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bf495-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf495-114">See Also</span></span>  
 [<span data-ttu-id="bf495-115">Serializando árvores XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bf495-115">Serializing XML Trees (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
