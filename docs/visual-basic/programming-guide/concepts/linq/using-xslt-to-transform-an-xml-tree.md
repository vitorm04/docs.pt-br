---
title: Usando XSLT para transformar uma árvore XML
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: 5332eb0a4fa8a2bd855421d674fe9f0de2ccb5f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364429"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="e093e-102">Usando o XSLT para transformar uma árvore XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e093e-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>

<span data-ttu-id="e093e-103">Você pode criar uma árvore XML, criar um <xref:System.Xml.XmlReader> na árvore XML, criar um novo documento e criar um <xref:System.Xml.XmlWriter> que gravarão no novo documento.</span><span class="sxs-lookup"><span data-stu-id="e093e-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="e093e-104">Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> para a transformação.</span><span class="sxs-lookup"><span data-stu-id="e093e-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="e093e-105">Depois que a transformação for concluída com êxito, a nova árvore XML será populada com os resultados da transformação.</span><span class="sxs-lookup"><span data-stu-id="e093e-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>

## <a name="example"></a><span data-ttu-id="e093e-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e093e-106">Example</span></span>

```vb
Dim xslMarkup As XDocument = _
    <?xml version='1.0'?>
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
    </xsl:stylesheet>

Dim xmlTree As XElement = _
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()

Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = _
        New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transform and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

<span data-ttu-id="e093e-107">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="e093e-107">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="e093e-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="e093e-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e093e-109">Programação de LINQ to XML avançada (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e093e-109">Advanced LINQ to XML Programming (Visual Basic)</span></span>](advanced-linq-to-xml-programming.md)
