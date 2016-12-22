---
title: "Como: capturar a an&#225;lise de erros (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: capturar a an&#225;lise de erros (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como detectar XML mal formado ou inválido.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é implementada usando <xref:System.Xml.XmlReader>. Se XML mal formado ou inválido for passado para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], subjacente <xref:System.Xml.XmlReader> classe lançará uma exceção. Os vários métodos que analisam XML, como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, não capturar a exceção; a exceção pode ser capturada pelo seu aplicativo.  
  
 Observe que não é possível obter análise erros se você usar literais XML. O compilador do Visual Basic irá capturar erros de XML mal formado ou inválido.  
  
## Exemplo  
 O código a seguir tenta analisar XML inválido:  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 Quando você executa esse código, ele gera a seguinte exceção:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Para obter informações sobre as exceções que você pode esperar a <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, e <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> métodos lançar, consulte o <xref:System.Xml.XmlReader> documentação.  
  
## Consulte também  
 [Análise de XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)