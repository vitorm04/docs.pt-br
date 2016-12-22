---
title: "Serializando arquivos, o TextWriters, e o XmlWriters | Microsoft Docs"
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
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Serializando arquivos, o TextWriters, e o XmlWriters
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode serializar árvores XML a um <xref:System.IO.File>, um <xref:System.IO.TextWriter>, ou um <xref:System.Xml.XmlWriter>.  
  
 Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>, em uma cadeia de caracteres usando o `ToString` método.  
  
 Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName> método.  
  
 Ocomportamento padrão quando serializar a um arquivo é formatar o documento XML resultante \(recuo\). Quando você recua, espaço em branco irrisória na árvore XML não é preservado. Para serializar com formatação, use uma das sobrecargas dos métodos a seguir não são <xref:System.Xml.Linq.SaveOptions> como um argumento:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Se você quiser a opção não recuar e preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos métodos a seguir que usa <xref:System.Xml.Linq.SaveOptions> como um argumento:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Para obter exemplos, consulte o tópico de referência apropriado.  
  
## Consulte também  
 [Serializando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)