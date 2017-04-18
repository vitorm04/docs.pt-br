---
title: "Como: criar uma árvore de um XmlReader (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: a8dff4e518d8850b4050389e5677ac81ecd1e074
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Como: criar uma árvore de um XmlReader (Visual Basic)
Este tópico mostra como criar uma árvore XML diretamente de um <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> Para criar um <xref:System.Xml.Linq.XElement>de um <xref:System.Xml.XmlReader>, você deve posicionar o <xref:System.Xml.XmlReader>em um nó de elemento.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XElement> O <xref:System.Xml.XmlReader>ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader>é posicionado em um nó de texto, um erro será gerado.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader> Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader>em um elemento antes de criar uma árvore XML de <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> </xref:System.Xml.XmlReader>  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 O código a seguir cria um objeto `T:System.Xml.XmlReader` e depois lê os nós até encontrar o primeiro nó do elemento. Em seguida, carrega o <xref:System.Xml.Linq.XElement>objeto.</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim r As XmlReader = XmlReader.Create("books.xml")  
Do While r.NodeType <> XmlNodeType.Element  
    r.Read()  
Loop  
Dim e As XElement = XElement.Load(r)  
Console.WriteLine(e)  
```  
  
 Este exemplo gera a seguinte saída:  
  
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
  
## <a name="see-also"></a>Consulte também  
 [Análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
