---
title: 'Como: controle prefixos de Namespace (Visual Basic) (LINQ to XML) | Documentos do Microsoft'
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
ms.assetid: 2fcf28a5-31b6-409d-84ea-27c22f71fc9f
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
ms.openlocfilehash: 9b559b54ffaa53b2ae5cd3b6c6d2d4db3ebe0a04
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-control-namespace-prefixes-visual-basic-linq-to-xml"></a>Como: Controle prefixos de namespace (Visual Basic) (LINQ to XML)
Este tópico descreve como você pode controlar prefixos de namespace.  
  
## <a name="example"></a>Exemplo  
  
### <a name="description"></a>Descrição  
 Esse exemplo declara dois namespaces. Especifica que o `http://www.adventure-works.com` namespace tem o prefixo `aw`e que o `www.fourthcoffee.com` namespace tem o prefixo `fc`.  
  
### <a name="code"></a>Código  
  
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
  
### <a name="comments"></a>Comentários  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:Root xmlns:fc="www.fourthcoffee.com" xmlns:aw="http://www.adventure-works.com">  
  <fc:Child>  
    <aw:DifferentChild>other content</aw:DifferentChild>  
  </fc:Child>  
  <aw:Child2>c2 content</aw:Child2>  
  <fc:Child3>c3 content</fc:Child3>  
</aw:Root>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)
