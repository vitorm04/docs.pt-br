---
title: "Como: Controle prefixos de namespace (Visual Basic) (LINQ to XML) | Microsoft Docs"
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
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Como: Controle prefixos de namespace (Visual Basic) (LINQ to XML)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Este tópico descreve como você pode controlar prefixos de namespace.  
  
## Exemplo  
  
### Descrição  
 Este exemplo declara dois namespaces. Especifica que o `http://www.adventure-works.com` namespace tem o prefixo `aw`, e que o `www.fourthcoffee.com` namespace tem o prefixo `fc`.  
  
### Código  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
Imports <xmlns:fc="www.fourthcoffee.com">  
  
Module Module1  
  
    Sub Main()  
        Dim root As XElement = _  
            <aw:Root>  
                <fc:Child>  
                    <aw:DifferentChild>other content</aw:DifferentChild>  
                </fc:Child>  
                <aw:Child2>c2 content</aw:Child2>  
                <fc:Child3>c3 content</fc:Child3>  
            </aw:Root>  
        Console.WriteLine(root)  
    End Sub  
  
End Module  
```  
  
### Comentários  
 Este exemplo produz a seguinte saída:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## Consulte também  
 [Trabalhando com Namespaces XML \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)