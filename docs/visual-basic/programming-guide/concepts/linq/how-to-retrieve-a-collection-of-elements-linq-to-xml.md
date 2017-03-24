---
title: "Como: recuperar uma coleção de elementos (LINQ to XML) (Visual Basic) | Documentos do Microsoft"
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
ms.assetid: 2269f9de-8fb9-4666-b8a1-a4e754fa6a81
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bfe4450d268125f021795dfb61885f4c2cb81151
ms.lasthandoff: 03/13/2017


---
# <a name="how-to-retrieve-a-collection-of-elements-linq-to-xml-visual-basic"></a>Como: recuperar uma coleção de elementos (LINQ to XML) (Visual Basic)
Este tópico demonstra o <xref:System.Xml.Linq.XContainer.Elements%2A>método.</xref:System.Xml.Linq.XContainer.Elements%2A> Esse método retorna uma coleção de elementos filho de um elemento.  
  
## <a name="example"></a>Exemplo  
 Este exemplo efetua iterações através dos elementos filho do elemento de `purchaseOrder` .  
  
 Este exemplo usa o seguinte documento XML: [arquivo XML de exemplo: ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
Dim childElements As IEnumerable(Of XElement)  
childElements = _  
    From el In po.Elements() _  
    Select el  
For Each el As XElement In childElements  
    Console.WriteLine("Name: " & el.Name.ToString())  
Next  
```  
  
 Este exemplo gerencia a seguinte saída.  
  
```  
Name: Address  
Name: Address  
Name: DeliveryNotes  
Name: Items  
```  
  
## <a name="see-also"></a>Consulte também  
 [Eixos LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
