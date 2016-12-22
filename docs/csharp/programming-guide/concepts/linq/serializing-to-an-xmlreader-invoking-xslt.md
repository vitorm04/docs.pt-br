---
title: "Serializando um XmlReader (chamada XSLT) (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 4cc3ee03-ef4c-429b-a408-fedd10b728cd
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Serializando um XmlReader (chamada XSLT) (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Quando você usa o <xref:System.Xml?displayProperty=fullName> os recursos de interoperabilidade [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você pode usar <xref:System.Xml.Linq.XNode.CreateReader%2A> para criar um <xref:System.Xml.XmlReader>. O módulo que lê a partir dessa <xref:System.Xml.XmlReader> lê os nós da árvore XML e processá\-las adequadamente.  
  
## Chamar uma transformação XSLT  
 Um uso possível para esse método é ao chamar uma transformação XSLT. Você pode criar uma árvore XML, criar um <xref:System.Xml.XmlReader> da árvore XML, crie um novo documento e, em seguida, criar um <xref:System.Xml.XmlWriter> para gravar no novo documento. Em seguida, você pode chamar a transformação XSLT, passando <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter>. Depois que a transformação for concluída com êxito, a nova árvore XML é preenchida com os resultados da transformação.  
  
```c#  
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
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## Consulte também  
 [Serializando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)