---
title: "Como: capturar a an&#225;lise de erros (c#) | Microsoft Docs"
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
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Como: capturar a an&#225;lise de erros (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico mostra como detectar XML mal formado ou inválido.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] é implementada usando <xref:System.Xml.XmlReader>. Se XML mal formado ou inválido for passado para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], subjacente <xref:System.Xml.XmlReader> classe lançará uma exceção. Os vários métodos que analisam XML, como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, não capturar a exceção; a exceção pode ser capturada pelo seu aplicativo.  
  
## Exemplo  
 O código a seguir tenta analisar XML inválido:  
  
```c#  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 Quando você executa esse código, ele gera a seguinte exceção:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Para obter informações sobre as exceções que você pode esperar a <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, e <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> métodos lançar, consulte o <xref:System.Xml.XmlReader> documentação.  
  
## Consulte também  
 [Análise de XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/parsing-xml.md)