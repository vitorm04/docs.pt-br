---
title: "Serializando com uma declara&#231;&#227;o XML (Visual Basic) | Microsoft Docs"
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
ms.assetid: 8726f79e-2bb0-4ba0-969d-197cca591647
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Serializando com uma declara&#231;&#227;o XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como controlar se a serialização gera uma declaração XML.  
  
## Geração da declaração XML  
 Serializando um <xref:System.IO.File> ou um <xref:System.IO.TextWriter> usando o <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> método ou o <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> método gera uma declaração XML. Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador \(especificado em uma <xref:System.Xml.XmlWriterSettings> objeto\) determinam se uma declaração XML é gerada ou não.  
  
 Se você estiver serialização para uma cadeia de caracteres usando o `ToString` método, o XML resultante não incluirá uma declaração XML.  
  
### Serializando com uma declaração XML  
 O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e, em seguida, imprime o arquivo no console:  
  
```vb  
Dim root As XElement = <Root>  
                           <Child>child content</Child>  
                       </Root>  
root.Save("Root.xml")  
Dim str As String = File.ReadAllText("Root.xml")  
Console.WriteLine(str)  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<Root>  
  <Child>child content</Child>  
</Root>  
```  
  
### Serializando sem uma declaração XML  
 O exemplo a seguir mostra como salvar um <xref:System.Xml.Linq.XElement> para um <xref:System.Xml.XmlWriter>.  
  
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
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## Consulte também  
 [Serializando árvores XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)