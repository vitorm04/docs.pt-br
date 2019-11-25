---
title: Usando XSLT para transformar uma árvore XML (C#)
ms.date: 07/20/2015
ms.assetid: 373a2699-d4c5-471b-9bda-c1f0ab73b477
ms.openlocfilehash: 7ebcfbd6be86fdd5e12bfc48a0fe80a084c6f9b5
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140916"
---
# <a name="using-xslt-to-transform-an-xml-tree-c"></a><span data-ttu-id="ba04e-102">Usando XSLT para transformar uma árvore XML (C#)</span><span class="sxs-lookup"><span data-stu-id="ba04e-102">Using XSLT to Transform an XML Tree (C#)</span></span>
<span data-ttu-id="ba04e-103">Você pode criar uma árvore XML, criar um <xref:System.Xml.XmlReader> na árvore XML, criar um novo documento e criar um <xref:System.Xml.XmlWriter> que gravarão no novo documento.</span><span class="sxs-lookup"><span data-stu-id="ba04e-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="ba04e-104">Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> para a transformação.</span><span class="sxs-lookup"><span data-stu-id="ba04e-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="ba04e-105">Depois que a transformação for concluída com êxito, a nova árvore XML será populada com os resultados da transformação.</span><span class="sxs-lookup"><span data-stu-id="ba04e-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba04e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ba04e-106">Example</span></span>  
  
```csharp  
string xslt = @"<?xml version='1.0'?>  
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

var oldDocument = new XDocument(
    new XElement("Parent",
        new XElement("Child1", "Child1 data"),
        new XElement("Child2", "Child2 data")
    )
);

var newDocument = new XDocument();

using (var stringReader = new StringReader(xslt))
{
    using (XmlReader xsltReader = XmlReader.Create(stringReader))
    {
        var transformer = new XslCompiledTransform();
        transformer.Load(xsltReader);
        using (XmlReader oldDocumentReader = oldDocument.CreateReader())
        {
            using (XmlWriter newDocumentWriter = newDocument.CreateWriter())
            {
                transformer.Transform(oldDocumentReader, newDocumentWriter);
            }
        }
    }
}

string result = newDocument.ToString();
Console.WriteLine(result);
```  
  
 <span data-ttu-id="ba04e-107">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ba04e-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ba04e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ba04e-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
