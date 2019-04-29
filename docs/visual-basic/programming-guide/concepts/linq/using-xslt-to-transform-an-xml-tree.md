---
title: Usando XSLT para transformar uma árvore XML (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 3390ca68-c270-4e1d-b64b-6a063a77017c
ms.openlocfilehash: a013e042bcaab321d8a5596368c349f296240d0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61908148"
---
# <a name="using-xslt-to-transform-an-xml-tree-visual-basic"></a><span data-ttu-id="3771f-102">Usando XSLT para transformar uma árvore XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3771f-102">Using XSLT to Transform an XML Tree (Visual Basic)</span></span>
<span data-ttu-id="3771f-103">Você pode criar uma árvore XML, criar um <xref:System.Xml.XmlReader> na árvore XML, criar um novo documento e criar um <xref:System.Xml.XmlWriter> que gravarão no novo documento.</span><span class="sxs-lookup"><span data-stu-id="3771f-103">You can create an XML tree, create an <xref:System.Xml.XmlReader> from the XML tree, create a new document, and create an <xref:System.Xml.XmlWriter> that will write into the new document.</span></span> <span data-ttu-id="3771f-104">Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> para a transformação.</span><span class="sxs-lookup"><span data-stu-id="3771f-104">Then, you can invoke the XSLT transformation, passing the <xref:System.Xml.XmlReader> and <xref:System.Xml.XmlWriter> to the transformation.</span></span> <span data-ttu-id="3771f-105">Depois que a transformação for concluída com êxito, a nova árvore XML será populada com os resultados da transformação.</span><span class="sxs-lookup"><span data-stu-id="3771f-105">After the transformation successfully completes, the new XML tree is populated with the results of the transform.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3771f-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3771f-106">Example</span></span>  
  
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
  
 <span data-ttu-id="3771f-107">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3771f-107">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3771f-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3771f-108">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3771f-109">LINQ to XML (Visual Basic) de programação avançada</span><span class="sxs-lookup"><span data-stu-id="3771f-109">Advanced LINQ to XML Programming (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-linq-to-xml-programming.md)
