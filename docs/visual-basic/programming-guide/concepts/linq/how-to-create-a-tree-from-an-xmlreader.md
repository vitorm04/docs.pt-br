---
title: "Como: criar uma árvore de um XmlReader (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6de683d8-177d-402b-b0de-d0539f1ce5d8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ceae7c2bee85e7b368322c8ba195dea9feff672
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-tree-from-an-xmlreader-visual-basic"></a>Como: criar uma árvore de um XmlReader (Visual Basic)
Este tópico mostra como criar uma árvore de XML diretamente de <xref:System.Xml.XmlReader>. Para criar um <xref:System.Xml.Linq.XElement> de um <xref:System.Xml.XmlReader>, você deverá posicionar o <xref:System.Xml.XmlReader> em um nó de elemento. O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> estiver posicionado em um nó de texto, um erro será gerado. Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore de XML do <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 O código a seguir cria um objeto `T:System.Xml.XmlReader` e depois lê os nós até encontrar o primeiro nó do elemento. Ele em seguida carrega o objeto <xref:System.Xml.Linq.XElement>.  
  
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
