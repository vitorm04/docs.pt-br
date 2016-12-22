---
title: "Como: preencher uma &#225;rvore XML com um XmlWriter (LINQ to XML) (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 5792a0eb-94ee-440d-b601-58cca8c0ee0b
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: preencher uma &#225;rvore XML com um XmlWriter (LINQ to XML) (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Uma maneira de preencher uma árvore XML é usar <xref:System.Xml.Linq.XContainer.CreateWriter%2A> para criar um <xref:System.Xml.XmlWriter>, e, em seguida, gravar o <xref:System.Xml.XmlWriter>. A árvore XML é preenchida com todos os nós que são gravados para o <xref:System.Xml.XmlWriter>.  
  
 Você normalmente usaria esse método quando você usar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] com outra classe que espera escrever em um <xref:System.Xml.XmlWriter>, como <xref:System.Xml.Xsl.XslCompiledTransform>.  
  
## Exemplo  
 Um uso possível <xref:System.Xml.Linq.XContainer.CreateWriter%2A> é ao chamar uma transformação XSLT. Este exemplo cria uma árvore XML, cria um <xref:System.Xml.XmlReader> da árvore XML, cria um novo documento e, em seguida, cria um <xref:System.Xml.XmlWriter> para gravar no novo documento. Ele então chama a transformação XSLT, passando <xref:System.Xml.XmlReader> e <xref:System.Xml.XmlWriter>. Depois que a transformação for concluída com êxito, a nova árvore XML é preenchida com os resultados da transformação.  
  
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
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root>  
  <C1>Child1 data</C1>  
  <C2>Child2 data</C2>  
</Root>  
```  
  
## Consulte também  
 <xref:System.Xml.Linq.XContainer.CreateWriter%2A>   
 <xref:System.Xml.XmlWriter>   
 <xref:System.Xml.Xsl.XslCompiledTransform>   
 [Criando árvores XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)