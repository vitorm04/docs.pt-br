---
title: Alterando propriedades de prefixo de namespace
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7ce6e4b705188b9c1d0949703991633e3f450689
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="changing-namespace-prefix-properties"></a>Alterando propriedades de prefixo de namespace
O **XmlNode** classe permite que você altere o prefixo de namespace associado a um determinado nó. Por exemplo, o código a seguir mostra o prefixo de um elemento que está sendo alterado.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Saída**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 Altere o prefixo de um nó não altera seu namespace. O namespace somente pode ser definida quando o nó é criado. Quando você mantém a árvore, novos atributos de namespace podem ser persistentes para fora para satisfazer o prefixo você definir. Se o novo namespace não pode ser criada, então o prefixo é alterado para que as conservas do nó seu nome e local namespace. O exemplo a seguir mostra um atributo do namespace sendo adicionado.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Saída**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Quando a árvore foram mantida em uma cadeia de caracteres como resultado da chamada para **doc. InnerXml**, o `xmlns:a='123'` atributo foi adicionado para preservar o espaço para nome do `test` elemento. Foi `'123'`, e permanece `'123'`.  
  
## <a name="see-also"></a>Consulte também  
 [XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
