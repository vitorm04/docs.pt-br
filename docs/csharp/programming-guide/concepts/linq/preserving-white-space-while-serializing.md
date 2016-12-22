---
title: "Preservar espa&#231;o em branco para serializar | Microsoft Docs"
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
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Preservar espa&#231;o em branco para serializar
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como controlar o espaço em branco ao serializar uma árvore XML.  
  
 Um cenário comum é ler o XML recuado, criar uma árvore XML na memória sem quaisquer nós de texto de espaço em branco \(isto é, não preservar espaço em branco\), execute algumas operações no XML e, em seguida, salvar o XML com recuo. Quando você serializa o XML com formatação, somente significativo espaço em branco na árvore XML é preservado. Esse é o comportamento padrão para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].  
  
 Outro cenário comum é ler e modificar XML que já foi recuado intencionalmente. Não convém modificar este recuo de nenhuma forma. Para fazer isso no [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], preservar espaço em branco quando você carregar ou analisar o XML e desativa a formatação ao serializar o XML.  
  
## Comportamento de espaço em branco de métodos que Serialize árvores XML  
 Os seguintes métodos na <xref:System.Xml.Linq.XElement> e <xref:System.Xml.Linq.XDocument> classes serializar uma árvore XML. Você pode serializar uma árvore XML em um arquivo, um <xref:System.IO.TextReader>, ou um <xref:System.Xml.XmlReader>. O `ToString` método serializa para uma cadeia de caracteres.  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=fullName>  
  
 Se o método não utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, o método irá formatar \(corte\) XML serializável. Nesse caso, qualquer espaço em branco irrisória na árvore XML é descartada.  
  
 Se o método utiliza <xref:System.Xml.Linq.SaveOptions> como um argumento, em seguida, você pode especificar que o método não formatar o XML serializado \(recuo\). Nesse caso, qualquer espaço em branco na árvore XML é preservada.  
  
## Consulte também  
 [Serializando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)