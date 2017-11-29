---
title: "Como: recuperar um único elemento filho (LINQ para XML) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 580315fda6ef6f1919f7f2aabc0cf3604a5c4337
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Como: recuperar um único elemento filho (LINQ para XML) (Visual Basic)
Este tópico explica como recuperar um único elemento filho, considerando o nome do elemento filho. Quando você souber que o nome do elemento filho e que há apenas um elemento com esse nome, pode ser conveniente recuperar apenas um elemento, em vez de uma coleção.  
  
 O método <xref:System.Xml.Linq.XContainer.Element%2A> retorna o primeiro filho <xref:System.Xml.Linq.XElement> com o <xref:System.Xml.Linq.XName> especificado.  
  
 Se você quiser recuperar um único elemento filho no Visual Basic, uma abordagem comum é usar a propriedade XML e, em seguida, recuperar o primeiro elemento usando a notação do indexador de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso do método <xref:System.Xml.Linq.XContainer.Element%2A>. Este exemplo usa a árvore XML chamada `po` e localiza o primeiro elemento chamado `Comment`.  
  
 O exemplo do Visual Basic mostra o uso da notação do indexador de matriz para recuperar um único elemento.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim e As XElement = po.<DeliveryNotes>(0)  
Console.WriteLine(e)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<DeliveryNotes>Please leave packages in shed by driveway.</DeliveryNotes>  
```  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra o mesmo código para XML que está em um namespace. Para obter mais informações, consulte [trabalhando com Namespaces de XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: ordem de compra típica em um namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrderInNamespace.xml")  
        Dim e As XElement = po.<aw:DeliveryNotes>(0)  
        Console.WriteLine(e)  
    End Sub  
End Module  
```  
  
 Este exemplo gera a seguinte saída:  
  
```xml  
<aw:DeliveryNotes xmlns:aw="http://www.adventure-works.com">Please leave packages in shed by driveway.</aw:DeliveryNotes>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
