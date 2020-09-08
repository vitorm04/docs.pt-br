---
title: Como popular uma árvore XML com um XmlWriter-LINQ to XML
description: Para preencher uma árvore XML em C# e Visual Basic, crie um XMLWriter usando createwriter e, em seguida, grave no XmlWriter.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: cd5674d1-5c54-4efc-ba68-e23b2875295f
ms.openlocfilehash: 3f8005eca009ae5f2102444a5494336d2caa2450
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552008"
---
# <a name="how-to-populate-an-xml-tree-with-an-xmlwriter-linq-to-xml"></a><span data-ttu-id="c89df-103">Como popular uma árvore XML com um XmlWriter (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="c89df-103">How to populate an XML tree with an XmlWriter (LINQ to XML)</span></span>

<span data-ttu-id="c89df-104">Uma maneira de preencher uma árvore XML é usar <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para criar um <xref:System.Xml.XmlWriter> e escrever no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="c89df-104">One way to populate an XML tree is to use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter>, and then write to the <xref:System.Xml.XmlWriter>.</span></span> <span data-ttu-id="c89df-105">A árvore XML é preenchida com todos os nós que são escritos no <xref:System.Xml.XmlWriter>.</span><span class="sxs-lookup"><span data-stu-id="c89df-105">The XML tree is populated with all nodes that are written to the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="c89df-106">Normalmente, você usaria esse método ao usar LINQ to XML com outra classe que espera gravar em um <xref:System.Xml.XmlWriter> , como <xref:System.Xml.Xsl.XslCompiledTransform> .</span><span class="sxs-lookup"><span data-stu-id="c89df-106">You'd typically use this method when you use LINQ to XML with another class that expects to write to an <xref:System.Xml.XmlWriter>, such as <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

## <a name="example-create-an-xmlwriter-to-accept-the-output-of-an-xslt-transformation"></a><span data-ttu-id="c89df-107">Exemplo: criar um XmlWriter para aceitar a saída de uma transformação XSLT</span><span class="sxs-lookup"><span data-stu-id="c89df-107">Example: Create an XmlWriter to accept the output of an XSLT transformation</span></span>

<span data-ttu-id="c89df-108">Você pode usar <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para criar um <xref:System.Xml.XmlWriter> para aceitar a saída de uma transformação XSLT.</span><span class="sxs-lookup"><span data-stu-id="c89df-108">You can use <xref:System.Xml.Linq.XContainer.CreateWriter%2A> to create an <xref:System.Xml.XmlWriter> to accept the output of an XSLT transformation.</span></span> <span data-ttu-id="c89df-109">Isso é mostrado no exemplo a seguir, que faz o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c89df-109">This is shown in the following example, which does the following:</span></span>

- <span data-ttu-id="c89df-110">Cria uma árvore XML e uma <xref:System.Xml.XmlReader> para leitura a partir dela.</span><span class="sxs-lookup"><span data-stu-id="c89df-110">Creates an XML tree and an <xref:System.Xml.XmlReader> to read from it.</span></span>
- <span data-ttu-id="c89df-111">Cria uma nova árvore e uma <xref:System.Xml.XmlWriter> para gravar nela.</span><span class="sxs-lookup"><span data-stu-id="c89df-111">Creates a new tree and an <xref:System.Xml.XmlWriter> to write to it.</span></span>
- <span data-ttu-id="c89df-112">Invoca a transformação XSLT, fornecendo-a com o  <xref:System.Xml.XmlReader> e o <xref:System.Xml.XmlWriter> .</span><span class="sxs-lookup"><span data-stu-id="c89df-112">Invokes the XSLT transformation, providing it with the  <xref:System.Xml.XmlReader> and the <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="c89df-113">Em seguida, a transformação popula a nova árvore.</span><span class="sxs-lookup"><span data-stu-id="c89df-113">The transformation then populates the new tree.</span></span>

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
using (XmlWriter writer = newTree.CreateWriter())
{
    // Load the style sheet.
    XslCompiledTransform xslt = new XslCompiledTransform();
    xslt.Load(XmlReader.Create(new StringReader(xslMarkup)));

    // Execute the transformation and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer);
}

Console.WriteLine(newTree);
```

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

Dim xmlTree As XDocument = _
    <?xml version='1.0'?>
    <Parent>
        <Child1>Child1 data</Child1>
        <Child2>Child2 data</Child2>
    </Parent>

Dim newTree As XDocument = New XDocument()
Using writer As XmlWriter = newTree.CreateWriter()
    ' Load the style sheet.
    Dim xslt As XslCompiledTransform = New XslCompiledTransform()
    xslt.Load(xslMarkup.CreateReader())

    ' Execute the transformation and output the results to a writer.
    xslt.Transform(xmlTree.CreateReader(), writer)
End Using

Console.WriteLine(newTree)
```

<span data-ttu-id="c89df-114">Esse exemplo gera a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="c89df-114">This example produces the following output:</span></span>

```xml
<Root>
  <C1>Child1 data</C1>
  <C2>Child2 data</C2>
</Root>
```

## <a name="see-also"></a><span data-ttu-id="c89df-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="c89df-115">See also</span></span>

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A>
- <xref:System.Xml.XmlWriter>
- <xref:System.Xml.Xsl.XslCompiledTransform>
- [<span data-ttu-id="c89df-116">Árvores XML</span><span class="sxs-lookup"><span data-stu-id="c89df-116">XML trees</span></span>](functional-construction.md)
