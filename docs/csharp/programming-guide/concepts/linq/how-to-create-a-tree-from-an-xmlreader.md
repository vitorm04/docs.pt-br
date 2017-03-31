---
title: "Como criar uma árvore de um XmlReader (C#) | Microsoft Docs"
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
ms.assetid: 60951c9c-7087-406c-b5bb-c60e58609b21
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d94b2238f6908a29efeb2465c1c11babc54a3704
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-tree-from-an-xmlreader-c"></a>Como criar uma árvore de um XmlReader (C#)
Este tópico mostra como criar uma árvore XML diretamente de um <xref:System.Xml.XmlReader>. Para criar um <xref:System.Xml.Linq.XElement> em um <xref:System.Xml.XmlReader>, você deve posicionar o <xref:System.Xml.XmlReader> em um nó de elemento. O <xref:System.Xml.XmlReader> ignorará comentários e instruções de processamento, mas se o <xref:System.Xml.XmlReader> estiver posicionado em um nó de texto, um erro será lançado. Para evitar esses erros, sempre posicione o <xref:System.Xml.XmlReader> em um elemento antes de criar uma árvore de XML do <xref:System.Xml.XmlReader>.  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: livros (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-books-linq-to-xml.md).  
  
 O código a seguir cria um objeto `T:System.Xml.XmlReader` e depois lê os nós até encontrar o primeiro nó do elemento. Em seguida, ele carrega o objeto <xref:System.Xml.Linq.XElement>.  
  
```csharp  
XmlReader r = XmlReader.Create("books.xml");  
while (r.NodeType != XmlNodeType.Element)  
    r.Read();  
XElement e = XElement.Load(r);  
Console.WriteLine(e);  
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
 [Analisando XML (C#)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)
