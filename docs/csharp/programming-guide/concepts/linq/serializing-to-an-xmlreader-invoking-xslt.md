---
title: Serializando para um XmlReader (invocando XSLT) (C#)
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 62127847c6eeefdc60bf8c4cb4cb8fac2fb2b8bb
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a><span data-ttu-id="786b5-102">Serializando para um XmlReader (invocando XSLT) (C#)</span><span class="sxs-lookup"><span data-stu-id="786b5-102">Serializing to an XmlReader (Invoking XSLT) (C#)</span></span>
<span data-ttu-id="786b5-103">Quando você usa os recursos de interoperabilidade de <xref:System.Xml?displayProperty=fullName> de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode usar <xref:System.Xml.Linq.XNode.CreateReader%2A> para criar um <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="786b5-103">When you use the <xref:System.Xml?displayProperty=fullName> interoperability capabilities of [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can use <xref:System.Xml.Linq.XNode.CreateReader%2A> to create an <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="786b5-104">O módulo que lê deste <xref:System.Xml.XmlReader> lê os nós da árvore XML e processa-os de acordo.</span><span class="sxs-lookup"><span data-stu-id="786b5-104">The module that reads from this <xref:System.Xml.XmlReader> reads the nodes from the XML tree and processes them accordingly.</span></span>  
  
## <a name="invoking-an-xslt-transformation"></a><span data-ttu-id="786b5-105">Chamando uma transformação XSLT</span><span class="sxs-lookup"><span data-stu-id="786b5-105">Invoking an XSLT Transformation</span></span>  
 <span data-ttu-id="786b5-106">Um uso possível para este método é ao chamar uma transformação XSLT.</span><span class="sxs-lookup"><span data-stu-id="786b5-106">One possible use for this method is when invoking an XSLT transformation.</span></span> <span data-ttu-id="786b5-107">Você pode criar uma árvore XML, cria <xref:System.Xml.XmlReader> de árvore XML, cria um novo documento e em seguida, cria <xref:System.Xml.XmlWriter> para gravar no novo documento.</span><span class="sxs-lookup"><span data-stu-id="786b5-107">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and then create an <xref:System.Xml.XmlWriter> to write into the new document.</span></span> <span data-ttu-id="786b5-108">Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e em <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="786b5-108">Then, you can invoke the XSLT transformation, passing in <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="786b5-109">Depois que a transformação for concluída com êxito, a nova árvore XML será preenchida com os resultados da transformação.</span><span class="sxs-lookup"><span data-stu-id="786b5-109">After the transformation successfully completes, the new XML tree is populated with the results of the transformation.</span></span>  
  
```csharp  
string xslMarkup = @"<?xml version='1.0'?>  
<xsl:stylesheet xmlns:xsl='http://www.w3.org/1999/XSL/Transform' version='1.0'>  
    <xsl:template match='/Parent'>  
        <Root>  
            <C1>  
            <xsl:value-of select='Child1'/>  
            </C1>  
            <C2>  
            <xsl:value-of select='Child2'/>  
            </C2>  
        </Root>  
    </xsl:template>  
</xsl:stylesheet>";  
  
XDocument xmlTree = new XDocument(  
    new XElement("Parent",  
        new XElement("Child1", "Child1 data"),  
        new XElement("Child2", "Child2 data")  
    )  
);  
  
XDocument newTree = new XDocument();  
using (XmlWriter writer = newTree.CreateWriter()) {  
    // Load the style sheet.  
    XslCompiledTransform xslt = new XslCompiledTransform();  
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));  
  
    // Execute the transformation and output the results to a writer.  
    xslt.Transform(xmlTree.CreateReader(), writer);  
}  
  
Console.WriteLine(newTree);  
```  
  
 <span data-ttu-id="786b5-110">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="786b5-110">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="786b5-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="786b5-111">See Also</span></span>  
 [<span data-ttu-id="786b5-112">Serializando árvores XML (C#)</span><span class="sxs-lookup"><span data-stu-id="786b5-112">Serializing XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

