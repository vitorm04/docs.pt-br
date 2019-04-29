---
title: 'Como: Localizar o elemento raiz (XPath-LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 72c3aed5-9522-4454-a876-2070aad13f2e
ms.openlocfilehash: 0936300a51c697eaff5a1aeafff70e37b04a2a96
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780452"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-visual-basic"></a>Como: Localizar o elemento raiz (XPath-LINQ to XML) (Visual Basic)
Este tópico mostra como obter o elemento raiz com XPath e [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 A expressão XPath é:  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>Exemplo  
 Este exemplo localiza o elemento raiz.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Várias ordens de compra (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```vb  
Dim po As XDocument = XDocument.Load("PurchaseOrders.xml")  
  
' LINQ to XML query  
Dim el1 As XElement = po.Root  
  
' XPath expression  
Dim el2 As XElement = po.XPathSelectElement("/PurchaseOrders")  
  
If el1 Is el2 Then  
    Console.WriteLine("Results are identical")  
Else  
    Console.WriteLine("Results differ")  
End If  
Console.WriteLine(el1.Name)  
```  
  
 Este exemplo gera a seguinte saída:  
  
```  
Results are identical  
PurchaseOrders  
```  
  
## <a name="see-also"></a>Consulte também

- [LINQ to XML para os usuários do XPath (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-for-xpath-users.md)
