---
title: 'Como: Projetar um novo tipo (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 8cfb24f5-89b2-4cfb-b85d-e7963f8f1845
ms.openlocfilehash: a94180705674c8aee3ce45607f89fdbba1c873b7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757125"
---
# <a name="how-to-project-a-new-type-linq-to-xml-visual-basic"></a>Como: Projetar um novo tipo (LINQ to XML) (Visual Basic)
Outros exemplos nesta seção mostraram consultas que os resultados de retorno como <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, <xref:System.Collections.Generic.IEnumerable%601> de `string`, e <xref:System.Collections.Generic.IEnumerable%601> de `int`. Esses são tipos comuns de resultado, mas não são adequados para cada cenário. Em muitos casos você desejará suas consultas para retornar <xref:System.Collections.Generic.IEnumerable%601> de qualquer outro tipo.  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como instanciar objetos na cláusula `Select` . O código define primeiro uma nova classe com um construtor, e altera a declaração de `Select` de modo que a expressão é uma nova instância da nova classe.  
  
 Este exemplo usa o seguinte documento XML: [Arquivo XML de exemplo: Ordem de compra típica (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml.md).  
  
```vb  
Public Class NameQty  
    Public name As String  
    Public qty As Integer  
    Public Sub New(ByVal n As String, ByVal q As Integer)  
        name = n  
        qty = q  
    End Sub  
End Class  
  
Public Class Program  
    Shared Sub Main()  
        Dim po As XElement = XElement.Load("PurchaseOrder.xml")  
  
        Dim nqList As IEnumerable(Of NameQty) = _  
            From n In po...<Item> _  
            Select New NameQty( _  
                n.<ProductName>.Value, CInt(n.<Quantity>.Value))  
  
        For Each n As NameQty In nqList  
            Console.WriteLine(n.name & ":" & n.qty)  
        Next  
    End Sub  
End Class  
```  
  
 Este exemplo usa o método de `M:System.Xml.Linq.XElement.Element` que foi introduzido no tópico [Como: Recuperar um único elemento filho (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/how-to-retrieve-a-single-child-element-linq-to-xml.md). Também usa conversões para recuperar os valores dos elementos que são retornados pelo método de `M:System.Xml.Linq.XElement.Element` .  
  
 Este exemplo gera a seguinte saída:  
  
```  
Lawnmower:1  
Baby Monitor:2  
```  
  
## <a name="see-also"></a>Consulte também

- [Projeções e transformações (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
