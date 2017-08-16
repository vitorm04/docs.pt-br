---
title: Serializando arquivos, TextWriters e XmlWriters3 | Documentos do Microsoft
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
ms.assetid: 7a0c24df-79ef-41a0-87f5-e6cf79382da9
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
ms.openlocfilehash: 98662b8d84459ed051d048084c2755fa7aaf8247
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializando arquivos, o TextWriters, e o XmlWriters
Você pode serializar árvores XML a um <xref:System.IO.File>, um <xref:System.IO.TextWriter>, ou <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.IO.TextWriter> </xref:System.IO.File>  
  
 Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument>e <xref:System.Xml.Linq.XElement>, em uma cadeia de caracteres usando o `ToString` método.</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XDocument>  
  
 Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>método.</xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=fullName>  
  
 Comportamento de Thedefault quando serializar a um arquivo é formatar o documento XML resultante (recuo). Quando você identar, o espaço em branco irrisória na árvore XML não é preservada. Para serializar com formatação, use uma das sobrecargas dos métodos a seguir não são <xref:System.Xml.Linq.SaveOptions>como um argumento:</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Se você quiser a opção não recuar e preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos métodos a seguir que usa <xref:System.Xml.Linq.SaveOptions>como um argumento:</xref:System.Xml.Linq.SaveOptions>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
 Para exemplos, consulte o tópico de referência apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Serializando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
