---
title: Serializando arquivos, o TextWriters e o XmlWriters1
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bd3ea6f7-895b-4ff4-a625-fe2bb55b1886
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c2207ee3cf5bf1c89a01ba14875e788ceb53b01c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="serializing-to-files-textwriters-and-xmlwriters"></a>Serializando arquivos, o TextWriters, e o XmlWriters
Você pode serializar árvores XML a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, ou a <xref:System.Xml.XmlWriter>.  
  
 Você pode serializar qualquer componente XML, incluindo <xref:System.Xml.Linq.XDocument> e <xref:System.Xml.Linq.XElement>, uma cadeia de caracteres usando o método `ToString` .  
  
 Se você desejar suprimir formatação ao serializar a uma cadeia de caracteres, você pode usar o método de <xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType> .  
  
 O comportamento padrão ao serializar para um arquivo é formatar (recuar) o documento XML resultante. Quando você identar, o espaço em branco irrisória na árvore XML não é preservada. Para serializar com formatação, use uma das sobrecargas dos seguintes métodos que não têm <xref:System.Xml.Linq.SaveOptions> como um argumento:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Se você desejar que a opção não recuar e não preservar espaço em branco irrisória na árvore XML, use uma das sobrecargas dos seguintes métodos que leva <xref:System.Xml.Linq.SaveOptions> como um argumento:  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
 Para exemplos, consulte o tópico de referência apropriado.  
  
## <a name="see-also"></a>Consulte também  
 [Serializando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
