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
# <a name="using-xslt-to-transform-an-xml-tree-c"></a>Usando XSLT para transformar uma árvore XML (C#)
Você pode criar uma árvore XML, criar um <xref:System.Xml.XmlReader> na árvore XML, criar um novo documento e criar um <xref:System.Xml.XmlWriter> que gravarão no novo documento. Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter> para a transformação. Depois que a transformação for concluída com êxito, a nova árvore XML será populada com os resultados da transformação.  
  
## <a name="example"></a>Exemplo  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Xml.Linq.XContainer.CreateWriter%2A?displayProperty=nameWithType>
- <xref:System.Xml.Linq.XNode.CreateReader%2A?displayProperty=nameWithType>
