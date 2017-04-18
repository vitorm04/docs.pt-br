---
title: "Como: capturar a análise de erros (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
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
ms.openlocfilehash: 0c4ba619d1f269352b3288f6cadf3b6f37a0dc2d
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-catch-parsing-errors-visual-basic"></a>Como: capturar a análise de erros (Visual Basic)
Este tópico mostra como detectar XML mal formado ou inválido.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]é implementada usando <xref:System.Xml.XmlReader>.</xref:System.Xml.XmlReader> Se XML mal formado ou inválido for passado para [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)], subjacente <xref:System.Xml.XmlReader>classe lançará uma exceção.</xref:System.Xml.XmlReader> Os vários métodos que analisam XML, como <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, não capturar a exceção; a exceção pode ser capturada pelo seu aplicativo.</xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
 Observe que você não pode obter análise erros se você usar literais XML. O compilador do Visual Basic irá capturar erros de XML mal formado ou inválido.  
  
## <a name="example"></a>Exemplo  
 O código a seguir tenta analisar XML válido:  
  
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
  
 Quando você executa esse código, gerencie a seguinte exceção:  
  
```  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Para obter informações sobre as exceções que você pode esperar a <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>, e <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>métodos lançar, consulte o <xref:System.Xml.XmlReader>documentação.</xref:System.Xml.XmlReader> </xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName> </xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
## <a name="see-also"></a>Consulte também  
 [Análise de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
