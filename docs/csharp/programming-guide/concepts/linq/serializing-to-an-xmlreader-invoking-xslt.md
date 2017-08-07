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
# <a name="serializing-to-an-xmlreader-invoking-xslt-c"></a>Serializando para um XmlReader (invocando XSLT) (C#)
Quando você usa os recursos de interoperabilidade de <xref:System.Xml?displayProperty=fullName> de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], você pode usar <xref:System.Xml.Linq.XNode.CreateReader%2A> para criar um <xref:System.Xml.XmlReader>. O módulo que lê deste <xref:System.Xml.XmlReader> lê os nós da árvore XML e processa-os de acordo.  
  
## <a name="invoking-an-xslt-transformation"></a>Chamando uma transformação XSLT  
 Um uso possível para este método é ao chamar uma transformação XSLT. Você pode criar uma árvore XML, cria <xref:System.Xml.XmlReader> de árvore XML, cria um novo documento e em seguida, cria <xref:System.Xml.XmlWriter> para gravar no novo documento. Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e em <xref:System.Xml.XmlWriter>. Depois que a transformação for concluída com êxito, a nova árvore XML será preenchida com os resultados da transformação.  
  
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
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Serializando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)

