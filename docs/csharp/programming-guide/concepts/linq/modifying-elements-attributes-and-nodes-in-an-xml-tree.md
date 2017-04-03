---
title: "Modificando elementos, atributos e nós em uma árvore XML3 | Microsoft Docs"
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
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fa51b22af73d716b01444540edb7c8d814cd293
ms.lasthandoff: 03/13/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>Modificando elementos, atributos e nós em uma árvore XML
A tabela a seguir resume os métodos e as propriedades que você pode usar para modificar um elemento, seus elementos filho ou seus atributos.  
  
 Os seguintes métodos modificam um <xref:System.Xml.Linq.XElement>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>|Substitui um elemento pelo XML analisado.|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName>|Remove todo o conteúdo (nós filho e atributos) de um elemento.|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName>|Remove os atributos de um elemento.|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName>|Substitui todo o conteúdo (nós filho e atributos) de um elemento.|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName>|Substitui os atributos de um elemento.|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName>|Define o valor de um atributo. Cria o atributo se ele não existir. Se o valor for definido como `null`, o método removerá o atributo.|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName>|Define o valor de um elemento filho. Cria o elemento se ele não existir. Se o valor for definido como `null`, o método removerá o elemento.|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>|Substitui o conteúdo (nós filho) de um elemento pelo texto especificado.|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName>|Define o valor de um elemento.|  
  
 Os métodos a seguir modificam um <xref:System.Xml.Linq.XAttribute>.  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>|Define o valor de um atributo.|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName>|Define o valor de um atributo.|  
  
 Os métodos a seguir modificam um <xref:System.Xml.Linq.XNode> (incluindo um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName>|Substitui um nó pelo novo conteúdo.|  
  
 Os métodos a seguir modificam um <xref:System.Xml.Linq.XContainer> (um <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XDocument>).  
  
|Método|Descrição|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName>|Substitui os nós filho pelo novo conteúdo.|  
  
## <a name="see-also"></a>Consulte também  
 [Modificando árvores XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
