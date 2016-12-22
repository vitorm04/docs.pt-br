---
title: "Serializando com uma declara&#231;&#227;o XML (c#) | Microsoft Docs"
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
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Serializando com uma declara&#231;&#227;o XML (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como controlar se a serialização gera uma declaração XML.  
  
## Geração da declaração XML  
 Serializando um <xref:System.IO.File> ou um <xref:System.IO.TextWriter> usando o <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=fullName> método ou o <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=fullName> método gera uma declaração XML. Quando você serializa para um <xref:System.Xml.XmlWriter>, as configurações do gravador \(especificado em uma <xref:System.Xml.XmlWriterSettings> objeto\) determinam se uma declaração XML é gerada ou não.  
  
 Se você estiver serialização para uma cadeia de caracteres usando o `ToString` método, o XML resultante não incluirá uma declaração XML.  
  
### Serializando com uma declaração XML  
 O exemplo a seguir cria um <xref:System.Xml.Linq.XElement>, salva o documento em um arquivo e, em seguida, imprime o arquivo no console:  
  
```c#  
XElement root = new XElement("Root",  
    new XElement("Child", "child content")  
);  
root.Save("Root.xml");  
string str = File.ReadAllText("Root.xml");  
Console.WriteLine(str);  
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
  
```c#  
StringBuilder sb = new StringBuilder();  
XmlWriterSettings xws = new XmlWriterSettings();  
xws.OmitXmlDeclaration = true;  
  
using (XmlWriter xw = XmlWriter.Create(sb, xws)) {  
    XElement root = new XElement("Root",  
        new XElement("Child", "child content")  
    );  
    root.Save(xw);  
}  
Console.WriteLine(sb.ToString());  
```  
  
 Este exemplo produz a seguinte saída:  
  
```xml  
<Root><Child>child content</Child></Root>  
```  
  
## Consulte também  
 [Serializando árvores XML \(c\#\)](../../../../csharp/programming-guide/concepts/linq/serializing-xml-trees.md)