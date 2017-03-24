---
title: "Serializando com uma declaração XML (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 373df9b28ae7434d33ae81eba701d289cf1aa4f7
ms.lasthandoff: 03/13/2017

---
# <a name="serializing-with-an-xml-declaration-visual-basic"></a>Serializando com uma declaração XML (Visual Basic)
Este tópico descreve como controlar se a serialização gera uma declaração XML.  
  
## <a name="xml-declaration-generation"></a>Geração da declaração XML  
 Serializando um <xref:System.IO.File>ou um <xref:System.IO.TextWriter>usando o <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName>método ou o <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName>método gera uma declaração XML.</xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> </xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> </xref:System.IO.TextWriter> </xref:System.IO.File> Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador (especificado em uma <xref:System.Xml.XmlWriterSettings>objeto) determinam se uma declaração XML é gerada ou não.</xref:System.Xml.XmlWriterSettings> </xref:System.Xml.XmlWriter>  
  
 Se você estiver serialização para uma cadeia de caracteres usando o método `ToString`, o XML resultante não incluirá uma declaração XML.  
  
### <a name="serializing-with-an-xml-declaration"></a>Serializando com uma declaração XML  
 O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e, em seguida, imprime o arquivo de console:</xref:System.Xml.Linq.XElement>  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### <a name="serializing-without-an-xml-declaration"></a>Serializando sem uma declaração XML  
 O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement>a um <xref:System.Xml.XmlWriter>.</xref:System.Xml.XmlWriter> </xref:System.Xml.Linq.XElement>  
  
```vb  
Dim sb As StringBuilder = New StringBuilder()  
Dim xws As XmlWriterSettings = New XmlWriterSettings()  
xws.OmitXmlDeclaration = True  
  
Using xw As XmlWriter = XmlWriter.Create(sb, xws)  
    Dim root = <Root>  
                   <Child>child content</Child>  
               </Root>  
    root.Save(xw)  
End Using  
Console.WriteLine(sb.ToString())  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Serializando árvores XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
