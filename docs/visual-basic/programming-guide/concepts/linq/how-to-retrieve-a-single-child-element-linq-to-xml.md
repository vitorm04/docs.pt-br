---
title: "Como: recuperar um único elemento filho (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 0033e258-d9c4-4569-86f6-79b7c06d1204
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9e96e2e2270f16364b0a26a0b4f17c0d96d7c38b
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-a-single-child-element-linq-to-xml-visual-basic"></a>Como: recuperar um único elemento filho (LINQ to XML) (Visual Basic)
Este tópico explica como recuperar um único elemento filho, considerando o nome do elemento filho. Quando você souber que o nome do elemento filho e que há apenas um elemento com esse nome, pode ser conveniente recuperar apenas um elemento, em vez de uma coleção.  
  
 O <xref:System.Xml.Linq.XContainer.Element%2A>método retorna o primeiro filho <xref:System.Xml.Linq.XElement>com o <xref:System.Xml.Linq.XName>.</xref:System.Xml.Linq.XName> especificado</xref:System.Xml.Linq.XElement> </xref:System.Xml.Linq.XContainer.Element%2A>  
  
 Se você quiser recuperar um único elemento filho no Visual Basic, uma abordagem comum é usar a propriedade XML e, em seguida, recuperar o primeiro elemento usando a notação do indexador de matriz.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir demonstra o uso do <xref:System.Xml.Linq.XContainer.Element%2A>método.</xref:System.Xml.Linq.XContainer.Element%2A> Este exemplo usa a árvore XML chamada `po` e localiza o primeiro elemento chamado `Comment`.  
  
 O exemplo do Visual Basic mostra o uso da notação do indexador de matriz para recuperar um único elemento.  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
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
 O exemplo a seguir mostra o mesmo código para XML que está em um namespace. Para obter mais informações, consulte [trabalhar com Namespaces XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: ordem de compra típico em um Namespace](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-in-a-namespace.md).  
  
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
