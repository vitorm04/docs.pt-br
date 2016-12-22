---
title: "Como: criar uma &#225;rvore de um XmlReader (Visual Basic) | Microsoft Docs"
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
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: criar uma &#225;rvore de um XmlReader (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como criar uma árvore XML diretamente de um <xref:System.Xml.XmlReader>. Para criar um <xref:System.Xml.Linq.XElement> de um <xref:System.Xml.XmlReader>, você deve posicionar o <xref:System.Xml.XmlReader> em um nó de elemento. O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> é posicionado em um nó de texto, um erro será gerado. Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore XML do <xref:System.Xml.XmlReader>.  
  
## Exemplo  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros \(LINQ to XML\)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 O código a seguir cria um `T:System.Xml.XmlReader` objeto e, em seguida, lê os nós até encontrar o primeiro nó de elemento. Em seguida, carrega o <xref:System.Xml.Linq.XElement> objeto.  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Catalog>  
   <Book id="bk101">  
      <Author>Garghentini, Davide</Author>  
      <Title>XML Developer's Guide</Title>  
      <Genre>Computer</Genre>  
      <Price>44.95</Price>  
      <PublishDate>2000-10-01</PublishDate>  
      <Description>An in-depth look at creating applications   
      with XML.</Description>  
   </Book>  
   <Book id="bk102">  
      <Author>Garcia, Debra</Author>  
      <Title>Midnight Rain</Title>  
      <Genre>Fantasy</Genre>  
      <Price>5.95</Price>  
      <PublishDate>2000-12-16</PublishDate>  
      <Description>A former architect battles corporate zombies,   
      an evil sorceress, and her own childhood to become queen   
      of the world.</Description>  
   </Book>  
</Catalog>  
```  
  
## Consulte também  
 [Análise de XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)