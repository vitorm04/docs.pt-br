---
title: "Preservar o espaço em branco ao serializar3 | Microsoft Docs"
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
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
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
ms.openlocfilehash: 1d6cebecd75bedc393b06261c1955a554c9cf18c
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-serializing"></a>Preservar espaço em branco para serializar
Este tópico descreve como controlar o espaço em branco para serializar uma árvore XML.  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem nenhum nó de texto de espaço em branco (isto é, não preservar espaço em branco), executar algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente os espaços em branco significativos na árvore XML são preservados. Este é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Você pode não querer modificar este recuo de nenhuma forma. Para fazer isso em [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], você preserva o espaço em branco quando você carregar ou analisar XML e desativa o formatação quando você serializa XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Comportamento de espaço em branco de métodos que serialize árvores XML  
 Os seguintes métodos nas classes <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XDocument> serializam uma árvore XML. Você pode serializar uma árvore XML para um arquivo, um <xref:System.IO.TextReader> ou um <xref:System.Xml.XmlReader>. O método de `ToString` serializa a uma cadeia de caracteres.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName>  
  
 Se o método não utilizar <xref:System.Xml.Linq.SaveOptions> como um argumento, o método formatará (recuará) o XML serializado. Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartado.  
  
 Se o método utilizar <xref:System.Xml.Linq.SaveOptions> como um argumento, você poderá especificar que o método não formata (recua) o XML serializado. Nesse caso, qualquer espaço em branco na árvore XML é preservada.  
  
## <a name="see-also"></a>Consulte também  
 [Serializando árvores XML (C#)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)
