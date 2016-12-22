---
title: "Eixos LINQ to XML (c#) | Microsoft Docs"
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
ms.assetid: 3f7d54ff-b608-43a1-9e2d-e70668b72df8
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Eixos LINQ to XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Depois de ter criado uma árvore XML ou carregar um documento XML em uma árvore XML, você pode consultá\-lo para localizar elementos e atributos e recuperar seus valores.  
  
 Antes de você pode criar consultas, você deve entender o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] eixos. Há dois tipos de métodos de eixo: primeiro, há os métodos que chamam em uma única <xref:System.Xml.Linq.XElement> objeto <xref:System.Xml.Linq.XDocument> objeto, ou <xref:System.Xml.Linq.XNode> objeto. Esses métodos operam em um único objeto e retornar uma coleção de <xref:System.Xml.Linq.XElement>, <xref:System.Xml.Linq.XAttribute>, ou <xref:System.Xml.Linq.XNode> objetos. Em segundo lugar, há métodos de extensão que operam em coleções e retornam coleções. Os métodos de extensão enumerar a coleção de origem, chame o método de eixo apropriado em cada item na coleção e concatenar os resultados.  
  
## Nesta seção  
  
|Tópico|Descrição|  
|------------|---------------|  
|[LINQ to XML Axes Overview \(C\#\)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes-overview.md)|Define os eixos e explica como eles são usados no contexto de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] consultas.|  
|[How to: Retrieve a Collection of Elements \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Retrieve%20a%20Collection%20of%20Elements%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Apresenta o <xref:System.Xml.Linq.XContainer.Elements%2A> método. Esse método recupera uma coleção dos elementos filho de um elemento.|  
|[How to: Retrieve the Value of an Element \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Retrieve%20the%20Value%20of%20an%20Element%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Mostra como obter os valores dos elementos.|  
|[How to: Filter on Element Names \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Filter%20on%20Element%20Names%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Mostra como filtrar em nomes de elementos ao usar eixos.|  
|[How to: Chain Axis Method Calls \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Chain%20Axis%20Method%20Calls%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Mostra como encadear chamadas a métodos de eixos.|  
|[How to: Retrieve a Single Child Element \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Retrieve%20a%20Single%20Child%20Element%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Mostra como recuperar um único elemento filho de um elemento, dado o nome de marca do elemento filho.|  
|[How to: Retrieve a Collection of Attributes \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Retrieve%20a%20Collection%20of%20Attributes%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Apresenta o <xref:System.Xml.Linq.XElement.Attributes%2A> método. Esse método recupera os atributos de um elemento.|  
|[How to: Retrieve a Single Attribute \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Retrieve%20a%20Single%20Attribute%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Mostra como recuperar um único atributo de um elemento, dado o nome do atributo.|  
|[How to: Retrieve the Value of an Attribute \(LINQ to XML\) \(C\#\)](../Topic/How%20to:%20Retrieve%20the%20Value%20of%20an%20Attribute%20\(LINQ%20to%20XML\)%20\(C%23\).md)|Mostra como obter os valores dos atributos.|  
|[How to: Retrieve the Shallow Value of an Element \(C\#\)](../Topic/How%20to:%20Retrieve%20the%20Shallow%20Value%20of%20an%20Element%20\(C%23\).md)|Mostra como recuperar o valor raso de um elemento.|  
  
## Consulte também  
 [Métodos de extensão](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)   
 [Guia de programação \(LINQ to XML\) \(c\#\)](../../../../csharp/programming-guide/concepts/linq/programming-guide-linq-to-xml.md)